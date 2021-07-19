# export-JSON-excel-VBA


Sub ExportJSON()

    Dim DateTime As Range
    Dim Product As New Dictionary
        Product.Add "customerRef", ActiveWorkbook.Worksheets("Sheet2").Range("E46")
        Product.Add "requestedDeliveryDate", ActiveWorkbook.Worksheets("Sheet2").Range("E48")
    
    Dim Variants As New Collection
    Dim aVariant As Dictionary
    Set aVariant = New Dictionary
    Dim excelRange As Range
    Dim i As Long
    Dim cell As Variant
    Dim jsonFileObject As New FileSystemObject
    Dim jsonFileExport As TextStream
    
    'Set excelRange = Cells(10, 1).CurrentRegion
    'For i = 10 To 37
    
 
    
    
    
        'jsonDictionary("id") = Cells(i, 1)
        
        
        aVariant.Add "quantity", ActiveWorkbook.Worksheets("Sheet2").Range("D10")
        aVariant.Add "heigth", ActiveWorkbook.Worksheets("Sheet2").Range("C10")
        aVariant.Add "width", ActiveWorkbook.Worksheets("Sheet2").Range("B10")
        aVariant.Add "glass", 810
        aVariant.Add "miter", 0
        aVariant.Add "edge", 0
        aVariant.Add "ref", ActiveWorkbook.Worksheets("Sheet2").Range("A10")
        'aVariant("width") = Cells(i, 2)
        'aVariant.Add "heigth", Cells(i, 3)
        'aVariant.Add "quantity", Cells(i, 4)
        'aVariant.Add "glass", "263"
        'aVariant.Add "ref", Cells(i, 1)
        
        Variants.Add aVariant
        
        Product.Add "orderlines", Variants
        
    
        'Dim Body As New Dictionary
        'Body.Add "", Product
        'Set jsonDictionary = Nothing
    

    'Next i
    

MsgBox JsonConverter.ConvertToJson(Product, Whitespace:=3)
Set jsonFileExport = jsonFileObject.CreateTextFile("C:\JSON Test\Test-Glasbestelling.json", True)
    jsonFileExport.WriteLine (JsonConverter.ConvertToJson(Product, Whitespace:=3))
End Sub 
