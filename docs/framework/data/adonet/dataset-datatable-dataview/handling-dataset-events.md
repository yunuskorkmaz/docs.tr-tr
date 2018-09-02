---
title: DataSet olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: ff684adcb4e23b91b3e59476299d277c90c22c51
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394261"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="ce0a8-102">DataSet olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="ce0a8-102">Handling DataSet Events</span></span>
<span data-ttu-id="ce0a8-103"><xref:System.Data.DataSet> Nesnesi, üç olay sağlar: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, ve <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="ce0a8-104">MergeFailed olay</span><span class="sxs-lookup"><span data-stu-id="ce0a8-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="ce0a8-105">Olayı'en sık kullanılan `DataSet` nesnedir `MergeFailed`, ne zaman tetiklenir şemasını `DataSet` birleştirilen çakışma nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="ce0a8-106">Bu, bir hedef ve kaynak ortaya çıkar <xref:System.Data.DataRow> aynı birincil anahtar değere sahip ve <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="ce0a8-107">Örneğin, bir tablonun birincil anahtar sütunlarını birleştirilen, iki tablo arasında aynıdır `DataSet` nesneler, bir özel durum harekete geçirilir ve `MergeFailed` olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="ce0a8-108"><xref:System.Data.MergeFailedEventArgs> Geçirilen nesne `MergeFailed` etkinliğiniz bir <xref:System.Data.MergeFailedEventArgs.Conflict%2A> şema ikisi arasındaki çakışmayı tanımlayan özellik `DataSet` nesneleri ve <xref:System.Data.MergeFailedEventArgs.Table%2A> çakışan tablonun adını tanımlayan özellik.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="ce0a8-109">Aşağıdaki kod parçası, bir olay işleyicisi eklemek gösterilmiştir `MergeFailed` olay.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="ce0a8-110">Başlatılmış bir olaya</span><span class="sxs-lookup"><span data-stu-id="ce0a8-110">The Initialized Event</span></span>  
 <span data-ttu-id="ce0a8-111"><xref:System.Data.DataSet.Initialized> Olaylarının sonra `DataSet` Oluşturucusu yeni bir örneğini başlatır `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="ce0a8-112"><xref:System.Data.DataSet.IsInitialized%2A> Özelliği döndürür `true` varsa `DataSet` başlatma; tamamlandı Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="ce0a8-113"><xref:System.Data.DataSet.BeginInit%2A> Başlatma başlatan yöntem bir `DataSet`, ayarlar <xref:System.Data.DataSet.IsInitialized%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="ce0a8-114"><xref:System.Data.DataSet.EndInit%2A> Başlatma biten yöntemi `DataSet`, ayarlar `true`.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="ce0a8-115">Bu yöntemler başlatmak için Visual Studio tasarım ortamı tarafından kullanılan bir `DataSet` başka bir bileşen tarafından kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="ce0a8-116">Yaygın olarak bunları kodunuzda kullanacağınız değil.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="ce0a8-117">Silinen olayı</span><span class="sxs-lookup"><span data-stu-id="ce0a8-117">The Disposed Event</span></span>  
 <span data-ttu-id="ce0a8-118">`DataSet` türetilen <xref:System.ComponentModel.MarshalByValueComponent> hem de sunan sınıfı <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi ve <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olay.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="ce0a8-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Olay bileşende bırakılmış olay dinlemek için bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="ce0a8-120">Kullanabileceğiniz <xref:System.ComponentModel.MarshalByValueComponent.Disposed> olayı bir `DataSet` çalıştırmak istiyorsanız ne zaman kod <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="ce0a8-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> tarafından kullanılan kaynakları serbest <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce0a8-122">`DataSet` Ve `DataTable` nesneleri devralmanız <xref:System.ComponentModel.MarshalByValueComponent> ve Destek <xref:System.Runtime.Serialization.ISerializable> uzaktan iletişim için arabirim.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="ce0a8-123">Bunlar, düğümlerde yalnızca ADO.NET nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="ce0a8-124">Daha fazla bilgi için [uzak nesneleri](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="ce0a8-124">For more information, see [Remote Objects](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="ce0a8-125">Diğer olaylar ile çalışırken kullanılabilir hakkında daha fazla bilgi için bir `DataSet`, bkz: [DataTable olaylarını işleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) ve [DataAdapter olaylarını işleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="ce0a8-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0a8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce0a8-126">See Also</span></span>  
 [<span data-ttu-id="ce0a8-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="ce0a8-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ce0a8-128">Verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="ce0a8-128">Validating Data</span></span>](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="ce0a8-129">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ce0a8-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ce0a8-130">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ce0a8-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
