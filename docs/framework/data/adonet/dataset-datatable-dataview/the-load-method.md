---
title: "Load yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e6c6ce0b722d901e38b728a710e3c49848fb918a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="the-load-method"></a>Load yöntemi
Kullanabileceğiniz <xref:System.Data.DataTable.Load%2A> yüklemek için yöntemi bir <xref:System.Data.DataTable> bir veri kaynağından satırlarla. Bu, en basit biçimiyle tek bir parametre kabul eder, aşırı yüklenmiş bir yöntemdir bir **DataReader**. Yalnızca bu formda yüklerken **DataTable** satırlarla. İsteğe bağlı olarak, belirtebilirsiniz **LoadOption** veriler nasıl eklenir denetlemek için parametre **DataTable**.  
  
 **LoadOption** parametredir durumlarda özellikle yararlı nerede **DataTable** zaten veri satırını içeren, veri kaynağından gelen verileri tanımlayan çünkü verilerle birlikte zaten tabloda. Örneğin, **PreserveCurrentValues** (varsayılan) belirleyen burada bir satır olarak işaretli durumlarda **eklenen** içinde **DataTable**, **özgün** değerini veya her bir sütun ayarlanmış eşleşen satır içeriğini veri kaynağından. **Geçerli** değeri satır eklendiğinde atanan değerlerini koruyun ve **RowState** satırının ayarlanacak **değiştirilen**.  
  
 Aşağıdaki tabloda kısa bir açıklamasını sağlar <xref:System.Data.LoadOption> numaralandırma değerleri.  
  
|LoadOption değeri|Açıklama|  
|----------------------|-----------------|  
|**OverwriteRow**|Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **özgün** ve **geçerli** her değerleri Sütun gelen satırda değerlerle değiştirilir ve **RowState** özelliği ayarlanmış **Unchanged**.<br /><br /> Satır içinde zaten yok veri kaynağından **DataTable** ile eklenen bir **RowState** değerini **Unchanged**.<br /><br /> Bu seçeneği etkin içeriğini yeniler **DataTable** böylece veri kaynağı içeriğini eşleşir.|  
|**PreserveCurrentValues (varsayılan)**|Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **özgün** değeri, gelen satır ve içeriğiniayarlanır**Geçerli** değeri değiştirilmedi.<br /><br /> Varsa **RowState** olan **eklenen** veya **değiştirilen**, ayarlanır **değiştirilen**.<br /><br /> Varsa **RowState** olan **silinmiş**, kaldığı **silinmiş**.<br /><br /> Satır içinde zaten yok veri kaynağından **DataTable** eklenen ve **RowState** ayarlanır **Unchanged**.|  
|**UpdateCurrentValues**|Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **geçerli** değeri kopyalanır **özgün**değeri ve **geçerli** değerini ardından gelen satırı içeriğini ayarlayın.<br /><br /> Varsa **RowState** içinde **DataTable** olan **eklenen**, **RowState** kalır **eklenen**. Satır olarak işaretlenmiş için **değiştirilen** veya **silinmiş**, **RowState** olan **değiştirilen**.<br /><br /> Satır içinde zaten yok veri kaynağından **DataTable** eklenen ve **RowState** ayarlanır **eklenen**.|  
  
 Aşağıdaki örnek kullanır **yük** çalışanları için Doğum listesini görüntülemek için yöntemini **Northwind** veritabanı.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
