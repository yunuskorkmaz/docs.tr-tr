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
# <a name="the-load-method"></a><span data-ttu-id="792de-102">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="792de-102">The Load Method</span></span>
<span data-ttu-id="792de-103">Bir veri <xref:System.Data.DataTable.Load%2A> kaynağından satırlarla a <xref:System.Data.DataTable> yüklemek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="792de-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="792de-104">Bu, en basit haliyle, tek bir parametre, bir **DataReader**kabul eden aşırı yüklü bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="792de-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="792de-105">Bu formda, **yalnızca Satırlarla DataTable** yükler.</span><span class="sxs-lookup"><span data-stu-id="792de-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="792de-106">İsteğe bağlı olarak, **Verilerin DataTable'a**nasıl eklenmesini denetlemek için **LoadOption** parametresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="792de-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="792de-107">**LoadOption** parametresi, veri kaynağından gelen verilerin tablodaki verilerle nasıl birleştirileceğini açıkladığı **için, DataTable'ın** zaten veri satırları içerdiği durumlarda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="792de-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="792de-108">Örneğin, **Koruma Geçerli Değerleri** (varsayılan) bir satır **ın DataTable'a** **Eklendi** olarak işaretlendiği durumlarda, **Özgün** değerin veya her sütunun veri kaynağından eşleşen satırın içeriğine ayarlandığı belirtilir.</span><span class="sxs-lookup"><span data-stu-id="792de-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="792de-109">**Geçerli** değer satır eklendiğinde atanan değerleri koruyacak ve satırın **Satır Durumu** **Değiştirildi**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="792de-110">Aşağıdaki tablo, numaralandırma değerlerinin <xref:System.Data.LoadOption> kısa bir açıklamasını verir.</span><span class="sxs-lookup"><span data-stu-id="792de-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="792de-111">LoadOption değeri</span><span class="sxs-lookup"><span data-stu-id="792de-111">LoadOption value</span></span>|<span data-ttu-id="792de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="792de-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="792de-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="792de-113">**OverwriteRow**</span></span>|<span data-ttu-id="792de-114">Gelen satırlar **DataTable'da**zaten bir satırla aynı **Birincil Anahtar** değerine sahipse, her sütunun **Özgün** ve **Geçerli** değerleri gelen satırdaki değerlerle değiştirilir ve **RowState** özelliği **Değişmeden**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="792de-115">**Veri Tablosu'nda** zaten bulunmayan veri kaynağından satırlar, **Değişmemiş** **bir Satır Durumu** değeriyle eklenir.</span><span class="sxs-lookup"><span data-stu-id="792de-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="792de-116">Bu seçenek, veri kaynağının içeriğiyle eşleşebilecek şekilde **DataTable'ın** içeriğini yeniler.</span><span class="sxs-lookup"><span data-stu-id="792de-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="792de-117">**Geçerli Değerleri Koruma (varsayılan)**</span><span class="sxs-lookup"><span data-stu-id="792de-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="792de-118">Gelen satırlar **DataTable'da**zaten bulunan bir satırla aynı **Birincil Anahtar** değerine sahipse, **Özgün** değer gelen satırın içeriğine ayarlanır ve **Geçerli** değer değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="792de-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="792de-119">**RowState** **Eklendi** veya **Değiştirilirse,** **Değiştirilecek**şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="792de-120">**RowState** **Silindiyse,** **Silinmiş**olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="792de-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="792de-121">**Veri Kaynağı'nda** zaten bulunmayan veri kaynağından satırlar eklenir ve **RowState** **Değişmeden**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="792de-122">**Güncel Geçerli Değerler**</span><span class="sxs-lookup"><span data-stu-id="792de-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="792de-123">Gelen satırlar **DataTable'daki**satırla aynı **Birincil Anahtar** değerine sahipse, **Geçerli** değer **Özgün** değere kopyalanır ve **Geçerli** değer gelen satırın içeriğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="792de-124">**DataTable'daki** **RowState** **eklendiyse,** **RowState** **eklendi**kalır.</span><span class="sxs-lookup"><span data-stu-id="792de-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="792de-125">**Değiştirilen** veya **Silinen**olarak işaretlenmiş satırlar için **RowState** **değiştirilir.**</span><span class="sxs-lookup"><span data-stu-id="792de-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="792de-126">**Veri Kaynağı'nda** zaten bulunmayan veri kaynağından satırlar eklenir ve **RowState** **Eklendi**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792de-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="792de-127">Aşağıdaki örnek, **Northwind** veritabanındaki çalışanların doğum günlerinin listesini görüntülemek için **Yükle** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="792de-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="792de-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="792de-128">See also</span></span>

- [<span data-ttu-id="792de-129">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="792de-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="792de-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="792de-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
