---
title: Load Yöntemi
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173296"
---
# <a name="the-load-method"></a><span data-ttu-id="5f7d7-102">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f7d7-102">The Load Method</span></span>
<span data-ttu-id="5f7d7-103">Kullanabileceğiniz <xref:System.Data.DataTable.Load%2A> yüklemek için yöntemi bir <xref:System.Data.DataTable> bir veri kaynağından satırlarla.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="5f7d7-104">Bu, en basit şekliyle, tek bir parametre kabul eden aşırı yüklenmiş yöntem, bir **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="5f7d7-105">Yalnızca bu formda yükler **DataTable** satırlarla.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="5f7d7-106">İsteğe bağlı olarak belirleyebileceğiniz **LoadOption** veriler nasıl eklenir denetlemek için parametre **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="5f7d7-107">**LoadOption** parametredir durumlarda özellikle yararlı burada **DataTable** zaten veri satırını içeren, veri kaynağından gelen verileri açıklayan veri ile birleştirilir zaten tablodaki.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="5f7d7-108">Örneğin, **PreserveCurrentValues** belirten (varsayılan) burada bir satır olarak işaretlendiyse durumlarda **eklenen** içinde **DataTable**, **özgün** değerini veya her bir sütun ayarlanmış eşleşen satır içeriğini veri kaynağından.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="5f7d7-109">**Geçerli** değeri satır eklendiğinde, atanan değerleri koruyun ve **RowState** satırının ayarlanacak **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="5f7d7-110">Aşağıdaki tabloda, kısa bir açıklaması verilmektedir <xref:System.Data.LoadOption> sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="5f7d7-111">LoadOption değeri</span><span class="sxs-lookup"><span data-stu-id="5f7d7-111">LoadOption value</span></span>|<span data-ttu-id="5f7d7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f7d7-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5f7d7-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="5f7d7-113">**OverwriteRow**</span></span>|<span data-ttu-id="5f7d7-114">Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **özgün** ve **geçerli** her değerleri Sütun gelen satırın değerleriyle değiştirilir ve **RowState** özelliği **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5f7d7-115">Veri kaynağından zaten var olmayan satır **DataTable** ile eklenen bir **RowState** değerini **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5f7d7-116">Bu seçenek geçerli içeriğini yeniler **DataTable** böylece veri kaynağının içeriğiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="5f7d7-117">**PreserveCurrentValues (varsayılan)**</span><span class="sxs-lookup"><span data-stu-id="5f7d7-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="5f7d7-118">Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **özgün** değeri gelen satırın ve içeriğiniayarı**Geçerli** değeri değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="5f7d7-119">Varsa **RowState** olduğu **eklenen** veya **değiştirilen**, ayarlanır **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="5f7d7-120">Varsa **RowState** olduğu **silinmiş**, kaldığı **silinmiş**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="5f7d7-121">Veri kaynağından zaten var olmayan satır **DataTable** eklenen ve **RowState** ayarlanır **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="5f7d7-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="5f7d7-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="5f7d7-123">Gelen satır aynı varsa **PrimaryKey** değeri içinde satır olarak **DataTable**, **geçerli** değeri kopyalanır **özgün**değeri ve **geçerli** değeri sonra gelen satırın içeriğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="5f7d7-124">Varsa **RowState** içinde **DataTable** olduğu **eklenen**, **RowState** kalır **eklenen**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="5f7d7-125">Satır olarak işaretlenmiş için **değiştirilen** veya **silinmiş**, **RowState** olduğu **değiştirilen**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="5f7d7-126">Veri kaynağından zaten var olmayan satır **DataTable** eklenen ve **RowState** ayarlanır **eklenen**.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="5f7d7-127">Aşağıdaki örnek kullanımları **yük** çalışanlar için Doğum listesini görüntülemek için yöntemi **Northwind** veritabanı.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f7d7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f7d7-128">See also</span></span>

- [<span data-ttu-id="5f7d7-129">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="5f7d7-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5f7d7-130">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5f7d7-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
