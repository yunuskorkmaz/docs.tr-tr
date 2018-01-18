---
title: "Veri kaynakları ile DataAdapters güncelleştiriliyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e99ff801894149a2324638bfacbc1d32ee937e0a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="cfe6e-102">Veri kaynakları ile DataAdapters güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="cfe6e-102">Updating Data Sources with DataAdapters</span></span>
<span data-ttu-id="cfe6e-103">`Update` Yöntemi <xref:System.Data.Common.DataAdapter> değişikliklerden çözümlemek için çağrılan bir <xref:System.Data.DataSet> veri kaynağına geri.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="cfe6e-104">`Update` Yöntemi gibi `Fill` yöntemi örneği bağımsız değişken olarak alan bir `DataSet`ve isteğe bağlı bir <xref:System.Data.DataTable> nesne veya `DataTable` adı.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="cfe6e-105">`DataSet` Örneği `DataSet` yapıldı, değişiklikler içeriyor ve `DataTable` değişiklikleri alınacağı tabloyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="cfe6e-106">Öyle değilse `DataTable` belirtilirse, ilk `DataTable` içinde `DataSet` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>  
  
 <span data-ttu-id="cfe6e-107">Çağırdığınızda `Update` yöntemi, `DataAdapter` yapmış olduğunuz değişiklikleri analiz eder ve uygun komutu (INSERT, UPDATE veya DELETE) yürütür.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="cfe6e-108">Zaman `DataAdapter` bir değişiklik karşılaştığı bir <xref:System.Data.DataRow>, kullanır <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, veya <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> değişiklik işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="cfe6e-109">Bu tasarım zamanında komut sözdizimi belirterek ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak tanır ve mümkün olduğunda, saklı yordamlar yalıtılacaktır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="cfe6e-110">Komutları çağırmadan önce açık olarak ayarlamalısınız `Update`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="cfe6e-111">Varsa `Update` olarak adlandırılır ve uygun komutu için belirli bir güncelleştirme yok (örneğin, Hayır `DeleteCommand` silinen satır), bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfe6e-112">Düzenlemek veya kullanarak verileri silmek için SQL Server saklı yordamları kullanıyorsanız, bir `DataAdapter`, saklı yordam tanımı'nda SET NOCOUNT ON kullanmadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="cfe6e-113">Bu sıfır olarak döndürülen etkilenen satırların sayısı neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="cfe6e-114">Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
 <span data-ttu-id="cfe6e-115">Komut parametreleri, bir SQL deyimi için girdi ve çıktı değerler veya değiştirilen her satır için saklı yordam belirtmek için kullanılabilir bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="cfe6e-116">Daha fazla bilgi için bkz: [DataAdapter parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-116">For more information, see [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfe6e-117">Bir satırın silinmesi arasındaki farkı anlamak önemlidir bir <xref:System.Data.DataTable> ve satır kaldırma.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="cfe6e-118">Çağırdığınızda `Remove` veya `RemoveAt` yöntemi, satır hemen kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="cfe6e-119">Ardından başarılı olursa arka uç veri kaynağına karşılık gelen satırları etkilenmez `DataTable` veya `DataSet` için bir `DataAdapter` ve arama `Update`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="cfe6e-120">Kullandığınızda `Delete` yöntemi, satır içinde kalır `DataTable` ve silinmek üzere işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="cfe6e-121">Ardından geçirirseniz `DataTable` veya `DataSet` için bir `DataAdapter` ve arama `Update`, arka uç veri kaynağına karşılık gelen satır silindi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>  
  
 <span data-ttu-id="cfe6e-122">Varsa, `DataTable` eşlendiği veya oluşturulan tek veritabanı tablosundan özelliklerden yararlanabilirsiniz <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesne `DeleteCommand`, `InsertCommand`, ve `UpdateCommand` için nesneleri `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="cfe6e-123">Daha fazla bilgi için bkz: [CommandBuilders oluşturma komutlarıyla](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-123">For more information, see [Generating Commands with CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span></span>  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="cfe6e-124">Bir veri kümesine değerlerini eşlemek için UpdatedRowSource kullanma</span><span class="sxs-lookup"><span data-stu-id="cfe6e-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>  
 <span data-ttu-id="cfe6e-125">Veri kaynağından döndürülen değerler geri nasıl eşlendiğini denetleyebilir `DataTable` güncelleştirme yöntemini çağrısından bir `DataAdapter`, kullanarak <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliği bir <xref:System.Data.Common.DbCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="cfe6e-126">Ayarlayarak `UpdatedRowSource` özelliğini birine <xref:System.Data.UpdateRowSource> numaralandırma değerlerinin çıkış parametreleri tarafından döndürülen olup olmadığını denetleyebilir `DataAdapter` komutlar göz ardı veya değiştirilen satırda uygulanan `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="cfe6e-127">İlk (varsa) satır değiştirilen satırda uygulanan döndürülen olup olmadığını belirtebilirsiniz `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>  
  
 <span data-ttu-id="cfe6e-128">Farklı değerleri aşağıdaki tabloda açıklanmaktadır `UpdateRowSource` numaralandırma ve ile kullanılan bir komut davranışını nasıl etkilediklerini bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>  
  
|<span data-ttu-id="cfe6e-129">UpdatedRowSource numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cfe6e-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="cfe6e-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfe6e-130">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="cfe6e-131">Değiştirilen satır çıkış parametreleri ve döndürülen sonuç kümesi ilk satır eşlenebilir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="cfe6e-132">Döndürülen sonuç kümesi ilk satır verileri yalnızca değiştirilen satıra eşlenebilir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="cfe6e-133">Herhangi bir çıktı parametreleri veya döndürülen sonuç kümesinin satırlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-133">Any output parameters or rows of a returned result set are ignored.</span></span>|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="cfe6e-134">Çıkış parametreleri yalnızca değiştirilen satıra eşlenebilir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|  
  
 <span data-ttu-id="cfe6e-135">`Update` Metodu çözümler değişikliklerinizi geri veri kaynağına; ancak diğer istemciler değiştirilen verileri veri kaynağında doldurduğunuz son zaman `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="cfe6e-136">Yenilemek için `DataSet` geçerli verilerle kullanmak `DataAdapter` ve `Fill` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="cfe6e-137">Yeni satırlar tabloya eklenir ve güncelleştirilmiş bilgileri varolan satırlara birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="cfe6e-138">`Fill` Yöntemi yeni bir satır eklenir ya da var olan bir satır satır birincil anahtar değerlerinin inceleyerek güncelleştirileceği belirler `DataSet` ve tarafından döndürülen satır `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="cfe6e-139">Varsa `Fill` yöntemi karşılaştığı bir satır için bir birincil anahtar değeri `DataSet` tarafından döndürülen sonuçlar numaralı satırdaki bir birincil anahtar değeri ile eşleşen `SelectCommand`, varolan bir satır tarafındandöndürülensatırbilgileriylegüncelleştirir`SelectCommand`ve ayarlar <xref:System.Data.DataRow.RowState%2A> mevcut satırın `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="cfe6e-140">Tarafından döndürülen bir satır varsa `SelectCommand` satırları birincil anahtar değerleriyle eşleşmeyen birincil anahtar değerine sahip `DataSet`, `Fill` yöntemi ile yeni bir satır ekler bir `RowState` , `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfe6e-141">Varsa `SelectCommand` bir dış birleşim, sonuçlarını döndürür `DataAdapter` ayarlanmamış bir `PrimaryKey` elde edilen değer `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="cfe6e-142">Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün olarak çözülen emin olun.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="cfe6e-143">Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-143">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="cfe6e-144">Çağırma sırasında meydana gelebilecek özel durumları işleme `Update` yöntemini kullanabilirsiniz `RowUpdated` göründüklerinde satır güncelleştirme hataları yanıtlamasını olay (bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), veya ayarlayabilirsiniz `DataAdapter.ContinueUpdateOnError` için`true` çağırmadan önce `Update`ve depolanan hata bilgilerini yanıtlar `RowError` güncelleştirme tamamlandığında, belirli bir satır özelliği (bkz [satır hata bilgilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span></span>  
  
 <span data-ttu-id="cfe6e-145">**Not** çağırma `AcceptChanges` üzerinde `DataSet`, `DataTable`, veya `DataRow` tüm neden olacak `Original` değerleri bir `DataRow` ile üzerine yazılmasını `Current` değerleri `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-145">**Note** Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="cfe6e-146">Çağrıldıktan sonra satırı benzersiz olarak tanımlayan alan değerlerini değiştirilmişse, `AcceptChanges` `Original` değerleri artık değerleri veri kaynağında eşleşmeyen.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="cfe6e-147">`AcceptChanges`Her satır için güncelleştirme yöntemine bir çağrı sırasında otomatik olarak çağrılır bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="cfe6e-148">İlk ayarlayarak güncelleştirme yöntemine bir çağrı sırasında orijinal değerleri koruyabilir `AcceptChangesDuringUpdate` özelliği `DataAdapter` false ya da bir olay işleyicisi oluşturarak `RowUpdated` olay ve ayarı <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="cfe6e-149">Daha fazla bilgi için bkz: [birleştirme DataSet içeriği](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) ve [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-149">For more information, see [Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfe6e-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfe6e-150">Example</span></span>  
 <span data-ttu-id="cfe6e-151">Aşağıdaki örnekler açıkça ayarlayarak değiştirilmiş satırlara güncelleştirmeleri gerçekleştirmek nasıl göstermektedir `UpdateCommand` , bir `DataAdapter` ve çağırma kendi `Update` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="cfe6e-152">Parametre güncelleştirme WHERE yan tümcesinde deyimi kullanmak üzere ayarlanmış belirtilen bildirimi `Original` değerini `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="cfe6e-153">Bu önemlidir çünkü `Current` değeri değiştirilmiş olabilir ve veri kaynağındaki değer eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="cfe6e-154">`Original` Değerdir doldurmak için kullanılan değer `DataTable` veri kaynağından.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a><span data-ttu-id="cfe6e-155">AutoIncrement sütunları</span><span class="sxs-lookup"><span data-stu-id="cfe6e-155">AutoIncrement Columns</span></span>  
 <span data-ttu-id="cfe6e-156">Veri kaynağınızı tablolardan otomatik artırma sütunları varsa, sütunları doldurabilirsiniz, `DataSet` da otomatik artım değeri döndüren bir saklı yordam bir output parametresi olarak ve, bir tablodaki bir sütun eşlemesi, göre döndürme bir sonuç kümesi bir saklı yordam veya SQL deyimi veya kullanarak döndürülen ilk satırında otomatik artım değeri `RowUpdated` olayı `DataAdapter` ek bir SELECT deyimi yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="cfe6e-157">Daha fazla bilgi ve bir örnek için bkz: [alma kimliği veya sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-157">For more information and an example, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="cfe6e-158">Ekler, güncelleştirmeleri ve silme sıralama</span><span class="sxs-lookup"><span data-stu-id="cfe6e-158">Ordering of Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="cfe6e-159">Birçok durumlarda aracılığıyla hangi değişikliklerinin sırayla `DataSet` gönderilen veri kaynağı önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="cfe6e-160">Örneğin, bir birincil anahtar değeri olan bir satır için güncelleştirilir ve yabancı anahtar olarak yeni birincil anahtar değerine sahip yeni bir satır eklenir, güncelleştirmeden önce Ekle işlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>  
  
 <span data-ttu-id="cfe6e-161">Kullanabileceğiniz `Select` yöntemi `DataTable` döndürmek için bir `DataRow` yalnızca belirli bir satırlarla başvuran dizi `RowState`.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="cfe6e-162">Ardından döndürülen geçirebilirsiniz `DataRow` için dizi `Update` yöntemi `DataAdapter` değiştirilen satırları işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="cfe6e-163">Güncelleştirilecek satırların alt kümesini belirterek ekler, güncelleştirmeleri ve silme işlenen siparişi kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfe6e-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfe6e-164">Example</span></span>  
 <span data-ttu-id="cfe6e-165">Örneğin, aşağıdaki kodu tablonun silinen satırları işlenen ilk sonra güncelleştirilen satırları ve eklenen satırlar olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Added))  
```  
  
```csharp  
DataTable table = dataSet.Tables["Customers"];  
  
// First process deletes.  
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));  
  
// Next process updates.  
adapter.Update(table.Select(null, null,   
  DataViewRowState.ModifiedCurrent));  
  
// Finally, process inserts.  
adapter.Update(table.Select(null, null, DataViewRowState.Added));  
```  
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="cfe6e-166">DataAdapter almak ve verileri güncelleştirmek için kullanın</span><span class="sxs-lookup"><span data-stu-id="cfe6e-166">Use a DataAdapter to Retrieve and Update Data</span></span>  
 <span data-ttu-id="cfe6e-167">DataAdapter alabilir ve verileri güncelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-167">You can use a DataAdapter to retrieve and update the data.</span></span>  
  
-   <span data-ttu-id="cfe6e-168">Örnek DataAdapter.AcceptChangesDuringFill veritabanındaki verileri kopyalamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="cfe6e-169">Özelliği false olarak ayarlarsanız, AcceptChanges tablo doldururken çağrılmaz ve yeni eklenen satır ekli satırlar olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="cfe6e-170">Bu nedenle, örnek veritabanına yeni satır eklemek için bu satırı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-170">So, the sample uses these rows to insert the new rows into the database.</span></span>  
  
-   <span data-ttu-id="cfe6e-171">Örnekler DataAdapter.TableMappings kaynak tablosu ile DataTable arasında eşleme tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>  
  
-   <span data-ttu-id="cfe6e-172">Örnek DataAdapter.FillLoadOption nasıl bağdaştırıcısı DataTable DbDataReader nesnesinden doldurur belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="cfe6e-173">DataTable oluşturduğunuzda, yalnızca verileri veritabanından geçerli sürümü veya özgün sürümü LoadOption.Upsert veya LoadOption.PreserveChanges olarak özelliği ayarlanarak yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>  
  
-   <span data-ttu-id="cfe6e-174">Toplu işlemleri gerçekleştirmek için DbDataAdapter.UpdateBatchSize kullanarak örnek da tabloyu güncelleştir.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>  
  
 <span data-ttu-id="cfe6e-175">Derleme ve örneği çalıştırmadan önce örnek veritabanı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cfe6e-175">Before you compile and run the sample, you need to create the sample database:</span></span>  
  
```  
USE [master]  
GO  
  
CREATE DATABASE [MySchool]   
  
GO  
  
USE [MySchool]  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,  
[Year] [smallint] NOT NULL,  
[Title] [nvarchar](100) NOT NULL,  
[Credits] [int] NOT NULL,  
[DepartmentID] [int] NOT NULL,  
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED  
(  
[CourseID] ASC,  
[Year] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,  
[Name] [nvarchar](50) NOT NULL,  
[Budget] [money] NOT NULL,  
[StartDate] [datetime] NOT NULL,  
[Administrator] [int] NULL,  
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED  
(  
[DepartmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)  
  
SET IDENTITY_INSERT [dbo].[Department] ON   
  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)  
SET IDENTITY_INSERT [dbo].[Department] OFF  
  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
```  
  
 <span data-ttu-id="cfe6e-176">Bu kod örneği ile C# ve Visual Basic projeleri bulunabilir [Geliştirici kod örnekleri](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="cfe6e-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Linq;  
using CSDataAdapterOperations.Properties;  
  
namespace CSDataAdapterOperations.Properties {  
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {  
  
      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));  
  
      public static Settings Default {  
         get {  
            return defaultInstance;  
         }  
      }  
  
      [global::System.Configuration.ApplicationScopedSettingAttribute()]  
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]  
      public string MySchoolConnectionString {  
         get {  
            return ((string)(this["MySchoolConnectionString"]));  
         }  
      }  
   }  
}  
  
class Program {  
   static void Main(string[] args) {  
      Settings settings = new Settings();  
  
      // Copy the data from the database.  Get the table Department and Course from the database.  
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]  
                                     FROM [MySchool].[dbo].[Department];  
  
                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],  
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]  
                                   FROM [MySchool].[dbo].[Course]  
                                   Group by [CourseID]";  
  
      DataSet mySchool = new DataSet();  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);  
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);  
  
      // Use DataTableMapping to map the source tables and the destination tables.  
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};  
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);  
  
      Console.WriteLine("The following tables are from the database.");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      // Roll back the changes  
      DataTable department = mySchool.Tables["Department"];  
      DataTable course = mySchool.Tables["Course"];  
  
      department.Rows[0]["Name"] = "New" + department.Rows[0][1];  
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];  
      course.Rows[0]["Credits"] = 10;  
  
      Console.WriteLine("After we changed the tables:");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      department.RejectChanges();  
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");  
      ShowDataTable(department);  
  
      DataColumn[] primaryColumns = { course.Columns["CourseID"] };  
      DataColumn[] resetColumns = { course.Columns["Title"] };  
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);  
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");  
      ShowDataTable(course);  
  
      // Batch update the table.  
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],   
                                   [Credits],[DepartmentID])   
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";  
      SqlCommand insertCommand = new SqlCommand(insertString);  
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");  
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");  
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");  
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");  
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");  
  
      const Int32 batchSize = 10;  
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);  
   }  
  
   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);  
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a   
            // DataRow after it is added to the DataTable during any of the Fill operations.  
            adapter.AcceptChangesDuringFill = false;  
  
            adapter.Fill(dataSet);  
         }  
      }  
   }  
  
   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.  
   private static void ResetCourse(DataTable table, String connectionString,  
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {  
      table.PrimaryKey = primaryColumns;  
  
      // Build the query string  
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));  
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
  
      ResetDataTable(table, connectionString, selectCommand);  
   }  
  
   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges   
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges  
   // The ResetDataTable method rolls back one or more columns of data.  
   private static void ResetDataTable(DataTable table, String connectionString,  
       SqlCommand selectCommand) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {  
            // The incoming values for this row will be written to the current version of each   
            // column. The original version of each column's data will not be changed.  
            adapter.FillLoadOption = LoadOption.Upsert;  
  
            adapter.Fill(table);  
         }  
      }  
   }  
  
   private static void BatchInsertUpdate(DataTable table, String connectionString,  
       SqlCommand insertCommand, Int32 batchSize) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         insertCommand.Connection = connection;  
         // When setting UpdateBatchSize to a value other than 1, all the commands   
         // associated with the SqlDataAdapter have to have their UpdatedRowSource   
         // property set to None or OutputParameters. An exception is thrown otherwise.  
         insertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter()) {  
            adapter.InsertCommand = insertCommand;  
            // Gets or sets the number of rows that are processed in each round-trip to the server.  
            // Setting it to 1 disables batch updates, as rows are sent one at a time.  
            adapter.UpdateBatchSize = batchSize;  
  
            adapter.Update(table);  
  
            Console.WriteLine("Successfully to update the table.");  
         }  
      }  
   }  
  
   private static void ShowDataTable(DataTable table) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-14}", col.ColumnName);  
      }  
      Console.WriteLine("{0,-14}", "RowState");  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-14:d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))  
               Console.Write("{0,-14:C}", row[col]);  
            else  
               Console.Write("{0,-14}", row[col]);  
         }  
         Console.WriteLine("{0,-14}", row.RowState);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfe6e-177">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfe6e-177">See Also</span></span>  
 [<span data-ttu-id="cfe6e-178">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="cfe6e-178">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="cfe6e-179">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="cfe6e-179">Row States and Row Versions</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="cfe6e-180">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="cfe6e-180">AcceptChanges and RejectChanges</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [<span data-ttu-id="cfe6e-181">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="cfe6e-181">Merging DataSet Contents</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [<span data-ttu-id="cfe6e-182">Kimliği veya Otomatik Sayı Değerlerini Alma</span><span class="sxs-lookup"><span data-stu-id="cfe6e-182">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [<span data-ttu-id="cfe6e-183">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="cfe6e-183">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
