---
title: Veri Kaynaklarını DataAdapters ile Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 4a6e22352a309f9d624c6922abc531cb31a5baf1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736695"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="356e7-102">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="356e7-102">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="356e7-103"><xref:System.Data.Common.DataAdapter> `Update` yöntemi, bir <xref:System.Data.DataSet> değişiklikleri veri kaynağına geri çözümlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="356e7-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="356e7-104">`Fill` yöntemi gibi `Update` yöntemi, bir `DataSet`örneği ve isteğe bağlı bir <xref:System.Data.DataTable> nesnesi ya da `DataTable` adı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="356e7-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="356e7-105">`DataSet` örnek, yapılmış olan değişiklikleri içeren `DataSet` ve `DataTable` değişikliklerin alınacağı tabloyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="356e7-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="356e7-106">`DataTable` belirtilmemişse, `DataSet` ilk `DataTable` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="356e7-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="356e7-107">`Update` yöntemini çağırdığınızda, `DataAdapter` yapılan değişiklikleri analiz eder ve uygun komutu yürütür (INSERT, UPDATE veya DELETE).</span><span class="sxs-lookup"><span data-stu-id="356e7-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="356e7-108">`DataAdapter` bir <xref:System.Data.DataRow>değişikliği karşılaştığında, değişikliği işlemek için <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>veya <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="356e7-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="356e7-109">Bu, tasarım zamanında komut sözdizimini belirterek ve mümkün olduğunda saklı yordamların kullanımı aracılığıyla ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="356e7-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="356e7-110">`Update`çağrılmadan önce komutları açıkça ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="356e7-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="356e7-111">`Update` çağrılırsa ve belirli bir güncelleştirme için uygun komut yoksa (örneğin, silinen satırlar için `DeleteCommand` yoksa) bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="356e7-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="356e7-112">`DataAdapter`kullanarak verileri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız, saklı yordam tanımında SET NOCOUNT kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="356e7-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="356e7-113">Bu, etkilenen satır sayısı sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="356e7-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="356e7-114">Bu olayda bir <xref:System.Data.DBConcurrencyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="356e7-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="356e7-115">Komut parametreleri, bir SQL deyimin giriş ve çıkış değerlerini veya bir `DataSet`değiştirilen her satır için saklı yordamı belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="356e7-116">Daha fazla bilgi için bkz. [DataAdapter Parameters](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="356e7-116">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="356e7-117"><xref:System.Data.DataTable> bir satırı silme ve satırı kaldırma arasındaki farkı anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="356e7-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="356e7-118">`Remove` veya `RemoveAt` yöntemini çağırdığınızda, satır hemen kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="356e7-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="356e7-119">Daha sonra `DataTable` veya `DataSet` bir `DataAdapter` geçirirseniz ve `Update`çağırırsanız, arka uç veri kaynağındaki karşılık gelen tüm satırlar etkilenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="356e7-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="356e7-120">`Delete` yöntemini kullandığınızda, satır `DataTable` kalır ve silinmek üzere işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="356e7-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="356e7-121">Daha sonra `DataTable` veya `DataSet` bir `DataAdapter` geçirirseniz ve `Update`çağırırsanız, arka uç veri kaynağındaki karşılık gelen satır silinir.</span><span class="sxs-lookup"><span data-stu-id="356e7-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="356e7-122">`DataTable` tek bir veritabanı tablosundan eşlenir veya oluşturulduysa, `UpdateCommand` için `DeleteCommand`, `InsertCommand`ve `DataAdapter`nesnelerini otomatik olarak oluşturmak üzere <xref:System.Data.Common.DbCommandBuilder> nesnesinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="356e7-123">Daha fazla bilgi için bkz. [CommandBuilder 'lar Ile komut oluşturma](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="356e7-123">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="356e7-124">Değerleri bir veri kümesiyle eşlemek için UpdatedRowSource kullanma</span><span class="sxs-lookup"><span data-stu-id="356e7-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="356e7-125">Bir <xref:System.Data.Common.DbCommand> nesnesinin <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliğini kullanarak, veri kaynağından döndürülen değerlerin bir `DataAdapter`Update metoduna yapılan çağrıdan `DataTable` nasıl geri eşlendiğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="356e7-126">`UpdatedRowSource` özelliğini <xref:System.Data.UpdateRowSource> sabit listesi değerlerinden birine ayarlayarak, `DataAdapter` komutlarıyla döndürülen çıkış parametrelerinin yok sayıldığını veya `DataSet`değiştirilen satıra uygulanıp uygulanmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="356e7-127">Ayrıca, ilk döndürülen satırın (varsa) `DataTable`değiştirilen satıra uygulanıp uygulanmayacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="356e7-128">Aşağıdaki tabloda `UpdateRowSource` numaralandırmanın farklı değerleri ve `DataAdapter`ile kullanılan bir komutun davranışını nasıl etkilediği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="356e7-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="356e7-129">UpdatedRowSource numaralandırması</span><span class="sxs-lookup"><span data-stu-id="356e7-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="356e7-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="356e7-130">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="356e7-131">Döndürülen sonuç kümesinin çıkış parametreleri ve ilk satırı, `DataSet`değiştirilen satırıyla eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="356e7-132">Yalnızca döndürülen sonuç kümesinin ilk satırındaki veriler `DataSet`değiştirilen satırla eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="356e7-133">Döndürülen sonuç kümesinin herhangi bir çıkış parametresi veya satırı yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="356e7-133">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="356e7-134">`DataSet`değiştirilen satırına yalnızca çıkış parametreleri eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="356e7-135">`Update` yöntemi, değişikliklerinizi veri kaynağına geri çözümler; Ancak, `DataSet`son kez doldurduktan sonra diğer istemciler veri kaynağındaki verileri değiştirmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="356e7-136">`DataSet` geçerli verilerle yenilemek için `DataAdapter` ve `Fill` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="356e7-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="356e7-137">Tabloya yeni satırlar eklenecek ve güncel bilgiler mevcut satırlara dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="356e7-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="356e7-138">`Fill` yöntemi, yeni bir satırın eklenip eklenmeyeceğini veya var olan bir satırın, `DataSet` ve `SelectCommand`tarafından döndürülen satırlardaki birincil anahtar değerlerini inceleyerek güncelleştirileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="356e7-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="356e7-139">`Fill` yöntemi, `SelectCommand`tarafından döndürülen sonuçlardaki bir satırdaki birincil anahtar değeriyle eşleşen `DataSet` bir satır için birincil anahtar değeriyle karşılaştığında, var olan satırı `SelectCommand` tarafından döndürülen satırdaki bilgilerle güncelleştirir ve var olan satırın <xref:System.Data.DataRow.RowState%2A> `Unchanged`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="356e7-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="356e7-140">`SelectCommand` tarafından döndürülen bir satır, `DataSet`satırların birincil anahtar değerleriyle eşleşmeyen bir birincil anahtar değeri içeriyorsa, `Fill` yöntemi `Unchanged``RowState` yeni bir satır ekler.</span><span class="sxs-lookup"><span data-stu-id="356e7-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="356e7-141">`SelectCommand` bir dış BIRLEŞTIRMENIN sonuçlarını döndürürse, `DataAdapter` elde edilen `DataTable`için bir `PrimaryKey` değeri ayarlayamaz.</span><span class="sxs-lookup"><span data-stu-id="356e7-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="356e7-142">Yinelenen satırların doğru bir şekilde çözümlendiğinden emin olmak için `PrimaryKey` kendiniz tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="356e7-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="356e7-143">Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="356e7-143">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="356e7-144">`Update` yöntemi çağrılırken oluşabilecek özel durumları işlemek için `RowUpdated` olayını kullanarak, ortaya çıkan satır güncelleştirme hatalarına yanıt verebilirsiniz (bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md)) veya `Update`çağrılmadan önce `true` `DataAdapter.ContinueUpdateOnError` ayarlayabilir ve güncelleştirme tamamlandığında belirli bir satırın `RowError` özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz (bkz. [satır hata bilgileri](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="356e7-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="356e7-145">`DataSet`, `DataTable`veya `DataRow` `AcceptChanges` çağırmak, `Original` `DataRow` değerlerinin üzerine yazılmasına neden olur.`Current``DataRow`</span><span class="sxs-lookup"><span data-stu-id="356e7-145">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="356e7-146">Satırı benzersiz olarak tanımlayan alan değerleri değiştirilmişse `AcceptChanges` çağrıldıktan sonra `Original` değerler artık veri kaynağındaki değerlerle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="356e7-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="356e7-147">`AcceptChanges`, bir `DataAdapter`Update metoduna yapılan çağrı sırasında her satır için otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="356e7-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="356e7-148">Önce `DataAdapter` `AcceptChangesDuringUpdate` özelliğini false olarak ayarlayarak veya `RowUpdated` olayı için bir olay işleyicisi oluşturarak ve <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow>ayarlayarak, Update yöntemine yapılan bir çağrı sırasında özgün değerleri koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="356e7-149">Daha fazla bilgi için bkz. [DataSet Içeriğini birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md) ve [DataAdapter olaylarını işleme](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="356e7-149">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="356e7-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="356e7-150">Example</span></span>

<span data-ttu-id="356e7-151">Aşağıdaki örneklerde, bir `DataAdapter` `UpdateCommand` ve `Update` metodunu çağırarak, değiştirilen satırlara yapılan güncelleştirmelerin nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="356e7-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="356e7-152">UPDATE ifadesinin WHERE yan tümcesinde belirtilen parametrenin `SourceColumn``Original` değerini kullanacak şekilde ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="356e7-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="356e7-153">Bu önemlidir çünkü `Current` değer değiştirilmiş olabilir ve veri kaynağındaki değerle eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="356e7-154">`Original` değeri, `DataTable` veri kaynağından doldurmak için kullanılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="356e7-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="356e7-155">AutoIncrement sütunları</span><span class="sxs-lookup"><span data-stu-id="356e7-155">AutoIncrement Columns</span></span>

<span data-ttu-id="356e7-156">Veri kaynağınızdaki tabloların sütunları otomatik olarak artırdıysanız, otomatik artış değerini bir saklı yordamın çıkış parametresi olarak döndürerek ve bir tablodaki bir sütuna eşleyerek, bir saklı yordam veya SQL ifadesiyle döndürülen sonuç kümesinin ilk satırına otomatik artış değerini döndürerek veya ek bir SELECT ifadesini yürütmek için `DataAdapter` `RowUpdated` olayını kullanarak `DataSet` sütunları doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="356e7-157">Daha fazla bilgi ve örnek için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="356e7-157">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="356e7-158">Ekleme, güncelleştirme ve silme sıralaması</span><span class="sxs-lookup"><span data-stu-id="356e7-158">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="356e7-159">Birçok durumda, `DataSet` üzerinde yapılan değişikliklerin veri kaynağına gönderildiği sıra önemlidir.</span><span class="sxs-lookup"><span data-stu-id="356e7-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="356e7-160">Örneğin, var olan bir satır için birincil anahtar değeri güncellenir ve yeni birincil anahtar değeriyle yabancı anahtar olarak yeni bir satır eklendiyse, bu güncelleştirmeyi INSERT öncesinde işlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="356e7-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="356e7-161">Yalnızca belirli bir `RowState`olan satırlara başvuran bir `DataRow` dizisi döndürmek için `DataTable` `Select` yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="356e7-162">Daha sonra, değiştirilen satırları işlemek için döndürülen `DataRow` dizisini `DataAdapter` `Update` yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="356e7-163">Görüntülenecek satırların bir alt kümesini belirterek, ekleme, güncelleştirme ve silme işleme sırasını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="356e7-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="356e7-164">Example</span></span>

<span data-ttu-id="356e7-165">Örneğin, aşağıdaki kod, tablonun silinen satırlarının önce işlenmesini, ardından güncelleştirilmiş satırları ve eklenen satırları sağlar.</span><span class="sxs-lookup"><span data-stu-id="356e7-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
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

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="356e7-166">Verileri almak ve güncelleştirmek için bir DataAdapter kullanın</span><span class="sxs-lookup"><span data-stu-id="356e7-166">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="356e7-167">Verileri almak ve güncelleştirmek için bir DataAdapter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-167">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="356e7-168">Örnek, veritabanındaki verileri kopyalamak için DataAdapter. AcceptChangesDuringFill ' i kullanır.</span><span class="sxs-lookup"><span data-stu-id="356e7-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="356e7-169">Özellik false olarak ayarlandıysa, tablo doldurulurken AcceptChanges çağrılmaz ve yeni eklenen satırlar eklenen satırlar olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="356e7-170">Bu nedenle örnek, yeni satırları veritabanına eklemek için bu satırları kullanır.</span><span class="sxs-lookup"><span data-stu-id="356e7-170">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="356e7-171">Örnekler, kaynak tablo ve DataTable arasındaki eşlemeyi tanımlamak için DataAdapter. TableMappings kullanır.</span><span class="sxs-lookup"><span data-stu-id="356e7-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="356e7-172">Örnek, bağdaştırıcının DataTable nesnesini DbDataReader 'dan nasıl doldurduğunu anlamak için DataAdapter. FillLoadOption kullanır.</span><span class="sxs-lookup"><span data-stu-id="356e7-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="356e7-173">Bir DataTable oluşturduğunuzda, özelliği LoadOption. upsert veya LoadOption. PreserveChanges olarak ayarlayarak veritabanını yalnızca geçerli sürüme veya özgün sürüme yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="356e7-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="356e7-174">Örnek, toplu işlemleri gerçekleştirmek için DbDataAdapter. UpdateBatchSize kullanarak tabloyu da güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="356e7-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="356e7-175">Örneği derleyip çalıştırmadan önce örnek veritabanını oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="356e7-175">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
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

<span data-ttu-id="356e7-176">C#ve bu kod örneğine sahip Visual Basic projeler [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)üzerinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="356e7-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
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
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

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

## <a name="see-also"></a><span data-ttu-id="356e7-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="356e7-177">See also</span></span>

- [<span data-ttu-id="356e7-178">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="356e7-178">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="356e7-179">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="356e7-179">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="356e7-180">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="356e7-180">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="356e7-181">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="356e7-181">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="356e7-182">Kimliği veya Otomatik Sayı Değerlerini Alma</span><span class="sxs-lookup"><span data-stu-id="356e7-182">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="356e7-183">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="356e7-183">ADO.NET Overview</span></span>](ado-net-overview.md)
