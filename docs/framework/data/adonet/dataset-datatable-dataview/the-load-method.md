---
title: Load Yöntemi
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: ea437d1f8ed567934acafbd8db1f8dba8eb22bcc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177546"
---
# <a name="the-load-method"></a>Load Yöntemi

Bir <xref:System.Data.DataTable.Load%2A> <xref:System.Data.DataTable> veri kaynağından satırları içeren bir ile yüklemek için yöntemini kullanabilirsiniz. Bu, en basit biçimiyle bir **DataReader**olan tek bir parametreyi kabul eden aşırı yüklenmiş bir yöntemdir. Bu formda, yalnızca **DataTable** 'ı satırları ile yükler. İsteğe bağlı olarak, verilerin **DataTable**'a nasıl eklendiğini denetlemek için **LoadOption** parametresini belirtebilirsiniz.  
  
 **LoadOption** parametresi, veri kaynağından gelen verilerin tabloda zaten bulunan verilerle nasıl birleştirileceğini açıkladığı için **DataTable** 'ın zaten veri satırları içerdiği durumlarda faydalıdır. Örneğin, **PreserveCurrentValues** (varsayılan), bir satırın **DataTable**'a **eklenen** olarak işaretlendiği, **özgün** değerin veya her sütunun veri kaynağından eşleşen satırın içeriğine ayarlandığı durumlarda belirtir. **Geçerli** değer, satır eklendiğinde atanan değerleri korur ve satırın **RowState** değeri **değiştirildi**olarak ayarlanır.  
  
 Aşağıdaki tabloda, numaralandırma değerlerinin kısa bir açıklaması verilmiştir <xref:System.Data.LoadOption> .  
  
|LoadOption değeri|Açıklama|  
|----------------------|-----------------|  
|**OverwriteRow**|Gelen satırlarda zaten **DataTable**içinde olan bir satırla aynı **PrimaryKey** değeri varsa, her sütunun **özgün** ve **geçerli** değerleri gelen satırdaki değerlerle yerine, **RowState** özelliği de **Unchanged**olarak ayarlanır.<br /><br /> **DataTable** 'da zaten mevcut olmayan veri kaynağındaki satırlar, bir **RowState** değeri **değiştirilmeden**eklenir.<br /><br /> Bu seçenek, veri kaynağının içeriğiyle eşleşecek şekilde **DataTable** 'ın içeriğini yeniler.|  
|**PreserveCurrentValues (varsayılan)**|Gelen satırlarda zaten **DataTable**içinde olan bir satır Ile aynı **PrimaryKey** değeri varsa, **özgün** değer gelen satırın içeriğine ayarlanır ve **geçerli** değer değiştirilmez.<br /><br /> **RowState** **eklendiğinde** veya **değiştirilirse**, **değiştirildi**olarak ayarlanır.<br /><br /> **RowState** **silinmişse** **silinen kalır.**<br /><br /> Veri kaynağından **DataTable** 'da zaten mevcut olmayan satırlar eklenir ve **RowState** , **Unchanged**olarak ayarlanır.|  
|**UpdateCurrentValues**|Gelen satırlar zaten **DataTable**içinde olan satır Ile aynı **PrimaryKey** değerine sahip Ise, **geçerli** değer **özgün** değere kopyalanır ve **geçerli** değer, gelen satırın içeriğine ayarlanır.<br /><br /> **DataTable** Içindeki **RowState** **eklendiyse**, **RowState** **eklenmiş**olarak kalır. **Değiştirilmiş** veya **Silinmiş**olarak Işaretlenen satırlarda, **RowState** **değiştirilir**.<br /><br /> Veri kaynağından **DataTable** 'da zaten mevcut olmayan satırlar eklenir ve **RowState** , **eklendi**olarak ayarlanır.|  
  
 Aşağıdaki örnek, **Northwind** veritabanındaki çalışanların Doğum günlerini listesini göstermek için **Load** yöntemini kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
