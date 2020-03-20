---
title: Load Yöntemi
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150733"
---
# <a name="the-load-method"></a>Load Yöntemi
Bir veri <xref:System.Data.DataTable.Load%2A> kaynağından satırlarla a <xref:System.Data.DataTable> yüklemek için yöntemi kullanabilirsiniz. Bu, en basit haliyle, tek bir parametre, bir **DataReader**kabul eden aşırı yüklü bir yöntemdir. Bu formda, **yalnızca Satırlarla DataTable** yükler. İsteğe bağlı olarak, **Verilerin DataTable'a**nasıl eklenmesini denetlemek için **LoadOption** parametresini belirtebilirsiniz.  
  
 **LoadOption** parametresi, veri kaynağından gelen verilerin tablodaki verilerle nasıl birleştirileceğini açıkladığı **için, DataTable'ın** zaten veri satırları içerdiği durumlarda özellikle yararlıdır. Örneğin, **Koruma Geçerli Değerleri** (varsayılan) bir satır **ın DataTable'a** **Eklendi** olarak işaretlendiği durumlarda, **Özgün** değerin veya her sütunun veri kaynağından eşleşen satırın içeriğine ayarlandığı belirtilir. **Geçerli** değer satır eklendiğinde atanan değerleri koruyacak ve satırın **Satır Durumu** **Değiştirildi**olarak ayarlanır.  
  
 Aşağıdaki tablo, numaralandırma değerlerinin <xref:System.Data.LoadOption> kısa bir açıklamasını verir.  
  
|LoadOption değeri|Açıklama|  
|----------------------|-----------------|  
|**OverwriteRow**|Gelen satırlar **DataTable'da**zaten bir satırla aynı **Birincil Anahtar** değerine sahipse, her sütunun **Özgün** ve **Geçerli** değerleri gelen satırdaki değerlerle değiştirilir ve **RowState** özelliği **Değişmeden**olarak ayarlanır.<br /><br /> **Veri Tablosu'nda** zaten bulunmayan veri kaynağından satırlar, **Değişmemiş** **bir Satır Durumu** değeriyle eklenir.<br /><br /> Bu seçenek, veri kaynağının içeriğiyle eşleşebilecek şekilde **DataTable'ın** içeriğini yeniler.|  
|**Geçerli Değerleri Koruma (varsayılan)**|Gelen satırlar **DataTable'da**zaten bulunan bir satırla aynı **Birincil Anahtar** değerine sahipse, **Özgün** değer gelen satırın içeriğine ayarlanır ve **Geçerli** değer değiştirilmez.<br /><br /> **RowState** **Eklendi** veya **Değiştirilirse,** **Değiştirilecek**şekilde ayarlanır.<br /><br /> **RowState** **Silindiyse,** **Silinmiş**olarak kalır.<br /><br /> **Veri Kaynağı'nda** zaten bulunmayan veri kaynağından satırlar eklenir ve **RowState** **Değişmeden**olarak ayarlanır.|  
|**Güncel Geçerli Değerler**|Gelen satırlar **DataTable'daki**satırla aynı **Birincil Anahtar** değerine sahipse, **Geçerli** değer **Özgün** değere kopyalanır ve **Geçerli** değer gelen satırın içeriğine ayarlanır.<br /><br /> **DataTable'daki** **RowState** **eklendiyse,** **RowState** **eklendi**kalır. **Değiştirilen** veya **Silinen**olarak işaretlenmiş satırlar için **RowState** **değiştirilir.**<br /><br /> **Veri Kaynağı'nda** zaten bulunmayan veri kaynağından satırlar eklenir ve **RowState** **Eklendi**olarak ayarlanır.|  
  
 Aşağıdaki örnek, **Northwind** veritabanındaki çalışanların doğum günlerinin listesini görüntülemek için **Yükle** yöntemini kullanır.  
  
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
