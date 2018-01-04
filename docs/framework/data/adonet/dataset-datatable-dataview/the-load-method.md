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
# <a name="the-load-method"></a><span data-ttu-id="c8961-102">Load yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8961-102">The Load Method</span></span>
<span data-ttu-id="c8961-103">Kullanabileceğiniz <xref:System.Data.DataTable.Load%2A> yüklemek için yöntemi bir <xref:System.Data.DataTable> bir veri kaynağından satırlarla.</span><span class="sxs-lookup"><span data-stu-id="c8961-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="c8961-104">Bu, en basit biçimiyle tek bir parametre kabul eder, aşırı yüklenmiş bir yöntemdir bir **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="c8961-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="c8961-105">Yalnızca bu formda yüklerken **DataTable** satırlarla.</span><span class="sxs-lookup"><span data-stu-id="c8961-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="c8961-106">İsteğe bağlı olarak, belirtebilirsiniz **LoadOption** veriler nasıl eklenir denetlemek için parametre **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c8961-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="c8961-107">**LoadOption** parametredir durumlarda özellikle yararlı nerede **DataTable** zaten veri satırını içeren, veri kaynağından gelen verileri tanımlayan çünkü verilerle birlikte zaten tabloda.</span><span class="sxs-lookup"><span data-stu-id="c8961-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="c8961-108">Örneğin, **PreserveCurrentValues** (varsayılan) belirleyen burada bir satır olarak işaretli durumlarda **eklenen** içinde **DataTable**, **özgün** değerini veya her bir sütun ayarlanmış eşleşen satır içeriğini veri kaynağından.</span><span class="sxs-lookup"><span data-stu-id="c8961-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="c8961-109">**Geçerli** değeri satır eklendiğinde atanan değerlerini koruyun ve **RowState** satırının ayarlanacak **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="c8961-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="c8961-110">Aşağıdaki tabloda kısa bir açıklamasını sağlar <xref:System.Data.LoadOption> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="c8961-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="c8961-111">LoadOption değeri</span><span class="sxs-lookup"><span data-stu-id="c8961-111">LoadOption value</span></span>|<span data-ttu-id="c8961-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8961-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="c8961-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="c8961-113">**OverwriteRow**</span></span>|<span data-ttu-id="c8961-114">Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **özgün** ve **geçerli** her değerleri Sütun gelen satırda değerlerle değiştirilir ve **RowState** özelliği ayarlanmış **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="c8961-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="c8961-115">Satır içinde zaten yok veri kaynağından **DataTable** ile eklenen bir **RowState** değerini **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="c8961-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="c8961-116">Bu seçeneği etkin içeriğini yeniler **DataTable** böylece veri kaynağı içeriğini eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c8961-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="c8961-117">**PreserveCurrentValues (varsayılan)**</span><span class="sxs-lookup"><span data-stu-id="c8961-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="c8961-118">Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **özgün** değeri, gelen satır ve içeriğiniayarlanır**Geçerli** değeri değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="c8961-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="c8961-119">Varsa **RowState** olan **eklenen** veya **değiştirilen**, ayarlanır **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="c8961-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="c8961-120">Varsa **RowState** olan **silinmiş**, kaldığı **silinmiş**.</span><span class="sxs-lookup"><span data-stu-id="c8961-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="c8961-121">Satır içinde zaten yok veri kaynağından **DataTable** eklenen ve **RowState** ayarlanır **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="c8961-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="c8961-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="c8961-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="c8961-123">Gelen satırların aynı varsa **PrimaryKey** değeri zaten içinde satır olarak **DataTable**, **geçerli** değeri kopyalanır **özgün**değeri ve **geçerli** değerini ardından gelen satırı içeriğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8961-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="c8961-124">Varsa **RowState** içinde **DataTable** olan **eklenen**, **RowState** kalır **eklenen**.</span><span class="sxs-lookup"><span data-stu-id="c8961-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="c8961-125">Satır olarak işaretlenmiş için **değiştirilen** veya **silinmiş**, **RowState** olan **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="c8961-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="c8961-126">Satır içinde zaten yok veri kaynağından **DataTable** eklenen ve **RowState** ayarlanır **eklenen**.</span><span class="sxs-lookup"><span data-stu-id="c8961-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="c8961-127">Aşağıdaki örnek kullanır **yük** çalışanları için Doğum listesini görüntülemek için yöntemini **Northwind** veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c8961-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8961-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8961-128">See Also</span></span>  
 [<span data-ttu-id="c8961-129">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c8961-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="c8961-130">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c8961-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
