---
description: 'Daha fazla bilgi edinin: veri kümesi olaylarını Işleme'
title: DataSet Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: a0000396c7c1e2762a5a2937f7979d917257facc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652373"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="a9aae-103">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="a9aae-103">Handling DataSet Events</span></span>

<span data-ttu-id="a9aae-104"><xref:System.Data.DataSet>Nesnesi üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed> , <xref:System.Data.DataSet.Initialized> , ve <xref:System.Data.DataSet.MergeFailed> .</span><span class="sxs-lookup"><span data-stu-id="a9aae-104">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="a9aae-105">MergeFailed olayı</span><span class="sxs-lookup"><span data-stu-id="a9aae-105">The MergeFailed Event</span></span>  

 <span data-ttu-id="a9aae-106">Nesnenin en yaygın olarak kullanılan olayı, `DataSet` `MergeFailed` `DataSet` birleştirilmekte olan nesnelerin şeması çakıştığında olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a9aae-106">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="a9aae-107">Bu, bir hedef ve kaynak <xref:System.Data.DataRow> aynı birincil anahtar değerine sahip olduğunda ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği olarak ayarlandığında oluşur `true` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-107">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="a9aae-108">Örneğin, birleştirilebilen bir tablonun birincil anahtar sütunları iki nesne içindeki tablolar arasında aynıysa `DataSet` , bir özel durum oluşturulur ve `MergeFailed` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a9aae-108">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="a9aae-109"><xref:System.Data.MergeFailedEventArgs>Olaya geçirilen nesne `MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> , iki nesne arasındaki şemada çakışmayı tanımlayan bir özelliğe sahiptir `DataSet` ve <xref:System.Data.MergeFailedEventArgs.Table%2A> Çakışan tablonun adını tanımlayan bir özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="a9aae-109">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="a9aae-110">Aşağıdaki kod parçası, olay için bir olay işleyicisinin nasıl ekleneceğini gösterir `MergeFailed` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-110">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="a9aae-111">Başlatılmış olay</span><span class="sxs-lookup"><span data-stu-id="a9aae-111">The Initialized Event</span></span>  

 <span data-ttu-id="a9aae-112"><xref:System.Data.DataSet.Initialized>Olay, `DataSet` Oluşturucu yeni bir örneğini başlattıktan sonra oluşur `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-112">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="a9aae-113"><xref:System.Data.DataSet.IsInitialized%2A>Özelliği `true` `DataSet` başlatmayı tamamladıysa, öğesini döndürür; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-113">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="a9aae-114"><xref:System.Data.DataSet.BeginInit%2A>, ' Nin başlatılmasına başlayan yöntemi olarak `DataSet` ayarlanır <xref:System.Data.DataSet.IsInitialized%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-114">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="a9aae-115"><xref:System.Data.DataSet.EndInit%2A>Öğesinin başlatılmasını sonlandıran yöntemi, `DataSet` olarak ayarlar `true` .</span><span class="sxs-lookup"><span data-stu-id="a9aae-115">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="a9aae-116">Bu yöntemler, `DataSet` başka bir bileşen tarafından kullanılmakta olan bir başlatmak Için Visual Studio tasarım ortamı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9aae-116">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="a9aae-117">Bunları kodunuzda yaygın olarak kullanmayacak.</span><span class="sxs-lookup"><span data-stu-id="a9aae-117">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="a9aae-118">Atılmış olay</span><span class="sxs-lookup"><span data-stu-id="a9aae-118">The Disposed Event</span></span>  

 <span data-ttu-id="a9aae-119">`DataSet` , <xref:System.ComponentModel.MarshalByValueComponent> hem yöntemi hem de olayını sunan sınıfından türetilir <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> <xref:System.ComponentModel.MarshalByValueComponent.Disposed> .</span><span class="sxs-lookup"><span data-stu-id="a9aae-119">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="a9aae-120"><xref:System.ComponentModel.MarshalByValueComponent.Disposed>Olay, bileşen üzerinde atılmış olayı dinlemek için bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="a9aae-120">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="a9aae-121"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` Yöntemi çağrıldığında kodu yürütmek istiyorsanız, bir olayını kullanabilirsiniz <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="a9aae-121">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="a9aae-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> tarafından kullanılan kaynakları serbest bırakır <xref:System.ComponentModel.MarshalByValueComponent> .</span><span class="sxs-lookup"><span data-stu-id="a9aae-122"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9aae-123">`DataSet`Ve nesneleri, ' `DataTable` dan devralınır <xref:System.ComponentModel.MarshalByValueComponent> ve <xref:System.Runtime.Serialization.ISerializable> Uzaktan iletişim için arabirimi destekler.</span><span class="sxs-lookup"><span data-stu-id="a9aae-123">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="a9aae-124">Bunlar uzaktan kullanılabilecek tek ADO.NET nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="a9aae-124">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="a9aae-125">Daha fazla bilgi için bkz. [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a9aae-125">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="a9aae-126">İle çalışırken kullanılabilir diğer olaylar hakkında daha fazla bilgi için `DataSet` , bkz. [DataTable olaylarını Işleme](handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="a9aae-126">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9aae-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9aae-127">See also</span></span>

- [<span data-ttu-id="a9aae-128">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="a9aae-128">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="a9aae-129">[Veriler doğrulanıyor](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a9aae-129">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="a9aae-130">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a9aae-130">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="a9aae-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9aae-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
