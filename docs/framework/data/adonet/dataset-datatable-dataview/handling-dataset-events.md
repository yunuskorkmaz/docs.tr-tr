---
title: DataSet Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: b2b71dac58838a826933af570934bf4bbb35e025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784601"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="8a170-102">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="8a170-102">Handling DataSet Events</span></span>
<span data-ttu-id="8a170-103">Nesnesi üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, ve <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="8a170-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="8a170-104">MergeFailed olayı</span><span class="sxs-lookup"><span data-stu-id="8a170-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="8a170-105">Nesnenin en yaygın olarak kullanılan olayı `DataSet` , birleştirilmekte olan nesnelerin şeması çakıştığında olduğunda tetiklenir. `MergeFailed` `DataSet`</span><span class="sxs-lookup"><span data-stu-id="8a170-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="8a170-106">Bu, bir hedef ve kaynak <xref:System.Data.DataRow> aynı birincil anahtar değerine sahip olduğunda <xref:System.Data.DataSet.EnforceConstraints%2A> ve özelliği olarak `true`ayarlandığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="8a170-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="8a170-107">Örneğin, birleştirilebilen bir tablonun birincil anahtar sütunları iki `DataSet` nesne içindeki tablolar arasında aynıysa, bir özel durum oluşturulur `MergeFailed` ve olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="8a170-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="8a170-108">Olayageçirilen`MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> nesne, iki`DataSet` nesne arasındaki şemada çakışmayı tanımlayan bir özelliğe sahiptir ve çakışan tablonun adını tanımlayan bir özellik vardır. <xref:System.Data.MergeFailedEventArgs></span><span class="sxs-lookup"><span data-stu-id="8a170-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="8a170-109">Aşağıdaki kod parçası, `MergeFailed` olay için bir olay işleyicisinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a170-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="8a170-110">Başlatılmış olay</span><span class="sxs-lookup"><span data-stu-id="8a170-110">The Initialized Event</span></span>  
 <span data-ttu-id="8a170-111">Olay, `DataSet` Oluşturucu Yeni`DataSet`bir örneğini başlattıktan sonra oluşur. <xref:System.Data.DataSet.Initialized></span><span class="sxs-lookup"><span data-stu-id="8a170-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="8a170-112">Özelliği başlatmayı tamamladıysa, `DataSet` öğesini döndürür; Aksi takdirde döndürür `false`. <xref:System.Data.DataSet.IsInitialized%2A> `true`</span><span class="sxs-lookup"><span data-stu-id="8a170-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="8a170-113">, ' <xref:System.Data.DataSet.IsInitialized%2A> `false`Nin başlatılmasına başlayan yöntemi olarak ayarlanır. <xref:System.Data.DataSet.BeginInit%2A> `DataSet`</span><span class="sxs-lookup"><span data-stu-id="8a170-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="8a170-114">Öğesinin başlatılmasını sonlandıran `true`yöntemi, olarak ayarlar. <xref:System.Data.DataSet.EndInit%2A> `DataSet`</span><span class="sxs-lookup"><span data-stu-id="8a170-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="8a170-115">Bu yöntemler, başka bir bileşen tarafından kullanılmakta olan bir `DataSet` başlatmak için Visual Studio tasarım ortamı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a170-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="8a170-116">Bunları kodunuzda yaygın olarak kullanmayacak.</span><span class="sxs-lookup"><span data-stu-id="8a170-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="8a170-117">Atılmış olay</span><span class="sxs-lookup"><span data-stu-id="8a170-117">The Disposed Event</span></span>  
 <span data-ttu-id="8a170-118">`DataSet`, <xref:System.ComponentModel.MarshalByValueComponent> hemyöntemi<xref:System.ComponentModel.MarshalByValueComponent.Disposed>hem de olayını sunan sınıfından türetilir. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="8a170-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="8a170-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay, bileşen üzerinde atılmış olayı dinlemek için bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="8a170-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="8a170-120">Yöntemi çağrıldığında kodu <xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` yürütmek istiyorsanız, bir olayını kullanabilirsiniz. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="8a170-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="8a170-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>tarafından kullanılan kaynakları serbest bırakır <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="8a170-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a170-122">Ve `DataSet` nesneleri `DataTable` , ' dan <xref:System.ComponentModel.MarshalByValueComponent> devralınır<xref:System.Runtime.Serialization.ISerializable> ve uzaktan iletişim için arabirimi destekler.</span><span class="sxs-lookup"><span data-stu-id="8a170-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="8a170-123">Bunlar uzaktan kullanılabilecek tek ADO.NET nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="8a170-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="8a170-124">Daha fazla bilgi için bkz. [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8a170-124">For more information, see [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="8a170-125">İle `DataSet`çalışırken kullanılabilir diğer olaylar hakkında daha fazla bilgi için, bkz. [DataTable olaylarını işleme](handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="8a170-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a170-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a170-126">See also</span></span>

- [<span data-ttu-id="8a170-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8a170-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="8a170-128">[Veriler doğrulanıyor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8a170-128">[Validating Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="8a170-129">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8a170-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="8a170-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8a170-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
