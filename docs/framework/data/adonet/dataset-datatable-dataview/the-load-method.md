---
title: Load yöntemi
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 21868f808a6d39c935b612f745d720180df2dd73
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507268"
---
# <a name="the-load-method"></a>Load yöntemi
Kullanabileceğiniz <xref:System.Data.DataTable.Load%2A> yüklemek için yöntemi bir <xref:System.Data.DataTable> bir veri kaynağından satırlarla. Bu, en basit şekliyle, tek bir parametre kabul eden aşırı yüklenmiş yöntem, bir **DataReader**. Yalnızca bu formda yükler **DataTable** satırlarla. İsteğe bağlı olarak belirleyebileceğiniz **LoadOption** veriler nasıl eklenir denetlemek için parametre **DataTable**.  
  
 **LoadOption** parametredir durumlarda özellikle yararlı burada **DataTable** zaten veri satırını içeren, veri kaynağından gelen verileri açıklayan veri ile birleştirilir zaten tablodaki. Örneğin, **PreserveCurrentValues** belirten (varsayılan) burada bir satır olarak işaretlendiyse durumlarda **eklenen** içinde **DataTable**, **özgün** değerini veya her bir sütun ayarlanmış eşleşen satır içeriğini veri kaynağından. **Geçerli** değeri satır eklendiğinde, atanan değerleri koruyun ve **RowState** satırının ayarlanacak **değiştirilen**.  
  
 Aşağıdaki tabloda, kısa bir açıklaması verilmektedir <xref:System.Data.LoadOption> sabit listesi değerleri.  
  
|LoadOption değeri|Açıklama|  
|----------------------|-----------------|  
|**OverwriteRow**|Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **özgün** ve **geçerli** her değerleri Sütun gelen satırın değerleriyle değiştirilir ve **RowState** özelliği **Unchanged**.<br /><br /> Veri kaynağından zaten var olmayan satır **DataTable** ile eklenen bir **RowState** değerini **Unchanged**.<br /><br /> Bu seçenek geçerli içeriğini yeniler **DataTable** böylece veri kaynağının içeriğiyle eşleşir.|  
|**PreserveCurrentValues (varsayılan)**|Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **özgün** değeri gelen satırın ve içeriğiniayarı**Geçerli** değeri değiştirilmedi.<br /><br /> Varsa **RowState** olduğu **eklenen** veya **değiştirilen**, ayarlanır **değiştirilen**.<br /><br /> Varsa **RowState** olduğu **silinmiş**, kaldığı **silinmiş**.<br /><br /> Veri kaynağından zaten var olmayan satır **DataTable** eklenen ve **RowState** ayarlanır **Unchanged**.|  
|**UpdateCurrentValues**|Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **geçerli** değeri kopyalanır **özgün**değeri ve **geçerli** değeri sonra gelen satırın içeriğini ayarlayın.<br /><br /> Varsa **RowState** içinde **DataTable** olduğu **eklenen**, **RowState** kalır **eklenen**. Satır olarak işaretlenmiş için **değiştirilen** veya **silinmiş**, **RowState** olduğu **değiştirilen**.<br /><br /> Veri kaynağından zaten var olmayan satır **DataTable** eklenen ve **RowState** ayarlanır **eklenen**.|  
  
 Aşağıdaki örnek kullanımları **yük** çalışanlar için Doğum listesini görüntülemek için yöntemi **Northwind** veritabanı.  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
