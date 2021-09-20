# TODO_Script
Google Sheets To Do Script

function onEdit(e) {
  addTimestamp(e)
}
function addTimestamp(e){
  const activeSheet = e.source.getActiveSheet()
  const modifiedCell = e.range

  const tf = activeSheet.createTextFinder("DONE")
  tf.matchEntireCell(true) 
  const cellDONE = tf.findNext()
  const row = cellDONE.getRow()
  const col = cellDONE.getColumn()
  
  // guard statement 
  if(!(modifiedCell.getColumn() === col && modifiedCell.getRow() > row)) return

  console.log(e.value)

  if(e.value === "TRUE"){ 
    modifiedCell.offset(0,3).setValue(new Date ())
  } else { 
    modifiedCell.offset(0,3).clearContent()
  }

//SpreadsheetApp.getActiveSpreadsheet().getActiveSheet().createTextFinder().offset ()
}
