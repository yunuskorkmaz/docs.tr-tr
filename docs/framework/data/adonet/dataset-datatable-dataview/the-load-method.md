---
description: 'Daha fazla bilgi edinin: Load yöntemi'
title: Load Yöntemi
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: a14008597d88ad4af93c3646998244d94b5561d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651528"
---
# <a name="the-load-method"></a><span data-ttu-id="36b10-103">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36b10-103">The Load Method</span></span>

<span data-ttu-id="36b10-104">Bir <xref:System.Data.DataTable.Load%2A> <xref:System.Data.DataTable> veri kaynağından satırları içeren bir ile yüklemek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b10-104">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="36b10-105">Bu, en basit biçimiyle bir **DataReader** olan tek bir parametreyi kabul eden aşırı yüklenmiş bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="36b10-105">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="36b10-106">Bu formda, yalnızca **DataTable** 'ı satırları ile yükler.</span><span class="sxs-lookup"><span data-stu-id="36b10-106">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="36b10-107">İsteğe bağlı olarak, verilerin **DataTable**'a nasıl eklendiğini denetlemek için **LoadOption** parametresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b10-107">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="36b10-108">**LoadOption** parametresi, veri kaynağından gelen verilerin tabloda zaten bulunan verilerle nasıl birleştirileceğini açıkladığı için **DataTable** 'ın zaten veri satırları içerdiği durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="36b10-108">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="36b10-109">Örneğin, **PreserveCurrentValues** (varsayılan), bir satırın **DataTable**'a **eklenen** olarak işaretlendiği, **özgün** değerin veya her sütunun veri kaynağından eşleşen satırın içeriğine ayarlandığı durumlarda belirtir.</span><span class="sxs-lookup"><span data-stu-id="36b10-109">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="36b10-110">**Geçerli** değer, satır eklendiğinde atanan değerleri korur ve satırın **RowState** değeri **değiştirildi** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-110">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="36b10-111">Aşağıdaki tabloda, numaralandırma değerlerinin kısa bir açıklaması verilmiştir <xref:System.Data.LoadOption> .</span><span class="sxs-lookup"><span data-stu-id="36b10-111">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="36b10-112">LoadOption değeri</span><span class="sxs-lookup"><span data-stu-id="36b10-112">LoadOption value</span></span>|<span data-ttu-id="36b10-113">Description</span><span class="sxs-lookup"><span data-stu-id="36b10-113">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="36b10-114">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="36b10-114">**OverwriteRow**</span></span>|<span data-ttu-id="36b10-115">Gelen satırlarda zaten **DataTable** içinde olan bir satırla aynı **PrimaryKey** değeri varsa, her sütunun **özgün** ve **geçerli** değerleri gelen satırdaki değerlerle yerine, **RowState** özelliği de **Unchanged** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-115">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="36b10-116">**DataTable** 'da zaten mevcut olmayan veri kaynağındaki satırlar, bir **RowState** değeri **değiştirilmeden** eklenir.</span><span class="sxs-lookup"><span data-stu-id="36b10-116">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="36b10-117">Bu seçenek, veri kaynağının içeriğiyle eşleşecek şekilde **DataTable** 'ın içeriğini yeniler.</span><span class="sxs-lookup"><span data-stu-id="36b10-117">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="36b10-118">**PreserveCurrentValues (varsayılan)**</span><span class="sxs-lookup"><span data-stu-id="36b10-118">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="36b10-119">Gelen satırlarda zaten **DataTable** içinde olan bir satır Ile aynı **PrimaryKey** değeri varsa, **özgün** değer gelen satırın içeriğine ayarlanır ve **geçerli** değer değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="36b10-119">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="36b10-120">**RowState** **eklendiğinde** veya **değiştirilirse**, **değiştirildi** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-120">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="36b10-121">**RowState** **silinmişse** **silinen kalır.**</span><span class="sxs-lookup"><span data-stu-id="36b10-121">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="36b10-122">Veri kaynağından **DataTable** 'da zaten mevcut olmayan satırlar eklenir ve **RowState** , **Unchanged** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-122">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="36b10-123">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="36b10-123">**UpdateCurrentValues**</span></span>|<span data-ttu-id="36b10-124">Gelen satırlar zaten **DataTable** içinde olan satır Ile aynı **PrimaryKey** değerine sahip Ise, **geçerli** değer **özgün** değere kopyalanır ve **geçerli** değer, gelen satırın içeriğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-124">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="36b10-125">**DataTable** Içindeki **RowState** **eklendiyse**, **RowState** **eklenmiş** olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="36b10-125">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="36b10-126">**Değiştirilmiş** veya **Silinmiş** olarak Işaretlenen satırlarda, **RowState** **değiştirilir**.</span><span class="sxs-lookup"><span data-stu-id="36b10-126">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="36b10-127">Veri kaynağından **DataTable** 'da zaten mevcut olmayan satırlar eklenir ve **RowState** , **eklendi** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-127">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="36b10-128">Aşağıdaki örnek, **Northwind** veritabanındaki çalışanların Doğum günlerini listesini göstermek için **Load** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36b10-128">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36b10-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36b10-129">See also</span></span>

- [<span data-ttu-id="36b10-130">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="36b10-130">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="36b10-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="36b10-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
