---
title: "DataTable kısıtlamaları"
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb1fd2c7aa057fcc83c82ab9d72129db2cac680e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-constraints"></a><span data-ttu-id="3cc51-102">DataTable kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3cc51-102">DataTable Constraints</span></span>
<span data-ttu-id="3cc51-103">Kısıtlamaları verileri kısıtlamalar uygulamak için kullanabileceğiniz bir <xref:System.Data.DataTable>, veri bütünlüğünü korumak için.</span><span class="sxs-lookup"><span data-stu-id="3cc51-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="3cc51-104">Uygulanan bir otomatik kuralı bir kısıtlamadır bir sütun veya ilgili sütunları için belirleyen eylem seyri bir satır değerinin şekilde değiştirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="3cc51-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="3cc51-105">Kısıtlamaları zorlanmaz zaman `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> olan **doğru**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="3cc51-106">Nasıl ayarlanacağı gösteren kod örneği için `EnforceConstraints` özelliği, bkz: <xref:System.Data.DataSet.EnforceConstraints%2A> başvuru konusu.</span><span class="sxs-lookup"><span data-stu-id="3cc51-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="3cc51-107">ADO.NET kısıtlamalarını iki tür vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="3cc51-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="3cc51-108">Ekleyerek en az iki tablo arasında bir ilişki oluşturduğunuzda varsayılan olarak, her iki kısıtlamaları otomatik olarak oluşturulmuş bir <xref:System.Data.DataRelation> için **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="3cc51-109">Ancak, bu davranış belirterek devre dışı bırakabilirsiniz **createConstraints** = **false** ilişki oluştururken.</span><span class="sxs-lookup"><span data-stu-id="3cc51-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="3cc51-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="3cc51-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="3cc51-111">A **ForeignKeyConstraint** kuralları güncelleştirmeleri ve silme ilişkili tablolar için nasıl yayılır hakkında zorlar.</span><span class="sxs-lookup"><span data-stu-id="3cc51-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="3cc51-112">Bir tablo satırının değerinde güncelleştirilmiş ya da silinmiş, aynı değeri de birinde kullanılır ve tablolar, ilgili daha fazla örneğin, bir **ForeignKeyConstraint** ne ilişkili tabloları olacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="3cc51-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="3cc51-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> özelliklerini **ForeignKeyConstraint** kullanıcı silin veya ilişkili bir tabloda bir satırı güncelleştirme girişiminde olduğunda gerçekleştirilecek eylem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3cc51-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="3cc51-114">Aşağıdaki tabloda kullanılabilir için farklı ayarlar açıklanır **DeleteRule** ve **UpdateRule** özelliklerini **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="3cc51-115">Kuralı ayarı</span><span class="sxs-lookup"><span data-stu-id="3cc51-115">Rule setting</span></span>|<span data-ttu-id="3cc51-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cc51-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3cc51-117">**CASCADE**</span><span class="sxs-lookup"><span data-stu-id="3cc51-117">**Cascade**</span></span>|<span data-ttu-id="3cc51-118">Silin veya ilişkili satırları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3cc51-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="3cc51-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="3cc51-119">**SetNull**</span></span>|<span data-ttu-id="3cc51-120">İlişkili satırların değerlerini ayarlayabilirsiniz **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="3cc51-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="3cc51-121">**SetDefault**</span></span>|<span data-ttu-id="3cc51-122">Varsayılan değer ilişkili satırların değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3cc51-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="3cc51-123">**Yok**</span><span class="sxs-lookup"><span data-stu-id="3cc51-123">**None**</span></span>|<span data-ttu-id="3cc51-124">İlgili satırlarda eylem yok.</span><span class="sxs-lookup"><span data-stu-id="3cc51-124">Take no action on related rows.</span></span> <span data-ttu-id="3cc51-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3cc51-125">This is the default.</span></span>|  
  
 <span data-ttu-id="3cc51-126">A **ForeignKeyConstraint** kısıtlayabilirsiniz, yanı sıra yayılması, değişiklikler ilgili sütun.</span><span class="sxs-lookup"><span data-stu-id="3cc51-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="3cc51-127">Özellikleri için ayarlanmış bağlı olarak **ForeignKeyConstraint** bir sütunun varsa **EnforceConstraints** özelliği **DataSet** olan **true**, belirli işlemleri üst satırda bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="3cc51-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="3cc51-128">Örneğin, varsa **DeleteRule** özelliği **ForeignKeyConstraint** olan **hiçbiri**, herhangi bir alt satır varsa, bir üst satır silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="3cc51-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="3cc51-129">Bir yabancı anahtar kısıtlaması tek sütun veya sütunlar kullanarak bir dizi arasında oluşturabilirsiniz **ForeignKeyConstraint** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3cc51-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="3cc51-130">Elde edilen geçirmek **ForeignKeyConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** olan özellik bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3cc51-131">Oluşturucu bağımsız değişkenleri için birkaç aşırı geçebilen **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="3cc51-132">Oluştururken bir **ForeignKeyConstraint**, geçirebilirsiniz **DeleteRule** ve **UpdateRule** oluşturucuya değerleri bağımsız değişken veya olarak ayarlayabilirsiniz özellikleri olarak olarak Örnek (burada **DeleteRule** değeri ayarı **hiçbiri**).</span><span class="sxs-lookup"><span data-stu-id="3cc51-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="3cc51-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="3cc51-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="3cc51-134">Satır değişiklikleri kullanarak kabul edilen **AcceptChanges** yöntemi veya iptal edilen kullanarak **RejectChanges** yöntemi **DataSet**, **DataTable**, veya **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="3cc51-135">Zaman bir **DataSet** içeren **sağlayan**, çağıran **AcceptChanges** veya **RejectChanges** yöntemleri zorlar **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="3cc51-136">**AcceptRejectRule** özelliği **ForeignKeyConstraint** alt gerçekleştirilecek eylemi belirler ne zaman satırları **AcceptChanges** veya  **RejectChanges** üst satırındaki adı verilir.</span><span class="sxs-lookup"><span data-stu-id="3cc51-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="3cc51-137">Aşağıdaki tabloda kullanılabilir ayarlarını listeler **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="3cc51-138">Kuralı ayarı</span><span class="sxs-lookup"><span data-stu-id="3cc51-138">Rule setting</span></span>|<span data-ttu-id="3cc51-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cc51-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3cc51-140">**CASCADE**</span><span class="sxs-lookup"><span data-stu-id="3cc51-140">**Cascade**</span></span>|<span data-ttu-id="3cc51-141">Kabul edin veya alt satır reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cc51-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="3cc51-142">**Yok**</span><span class="sxs-lookup"><span data-stu-id="3cc51-142">**None**</span></span>|<span data-ttu-id="3cc51-143">Alt satırlarda eylem yok.</span><span class="sxs-lookup"><span data-stu-id="3cc51-143">Take no action on child rows.</span></span> <span data-ttu-id="3cc51-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3cc51-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="3cc51-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cc51-145">Example</span></span>  
 <span data-ttu-id="3cc51-146">Aşağıdaki örnekte bir <xref:System.Data.ForeignKeyConstraint>, özelliklerini de dahil olmak üzere çeşitli ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>ve ona ekler <xref:System.Data.ConstraintCollection> , bir <xref:System.Data.DataTable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3cc51-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="3cc51-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="3cc51-147">UniqueConstraint</span></span>  
 <span data-ttu-id="3cc51-148">**UniqueConstraint** tek bir sütun veya sütun bir dizi atanabilir nesnesi bir **DataTable**, belirtilen sütun veya sütunlar tüm verileri satır benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cc51-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="3cc51-149">Kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz **UniqueConstraint** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3cc51-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="3cc51-150">Elde edilen geçirmek **UniqueConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** olan özellik bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3cc51-151">Oluşturucu bağımsız değişkenleri için birkaç aşırı geçebilen **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="3cc51-152">Oluştururken bir **UniqueConstraint** bir sütun veya sütunlar için isteğe bağlı olarak sütun veya sütunlar birincil bir anahtar olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cc51-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="3cc51-153">Ayarlayarak bir sütun için benzersiz bir kısıtlama oluşturabilirsiniz **benzersiz** sütuna özelliğinin **doğru**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="3cc51-154">Alternatif olarak, ayarı **benzersiz** tek bir sütun özelliğinin **false** bulunabilecek herhangi benzersiz kısıtlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3cc51-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="3cc51-155">Bir tablonun birincil anahtarı olarak bir sütun veya sütunlar tanımlama belirtilen sütun veya sütunlar için benzersiz bir kısıtlama otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3cc51-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="3cc51-156">Bir sütun kaldırırsanız **PrimaryKey** özelliği bir **DataTable**, **UniqueConstraint** kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3cc51-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="3cc51-157">Aşağıdaki örnekte bir **UniqueConstraint** iki sütunu için bir **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3cc51-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cc51-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cc51-158">See Also</span></span>  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [<span data-ttu-id="3cc51-159">DataTable şema tanımı</span><span class="sxs-lookup"><span data-stu-id="3cc51-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="3cc51-160">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="3cc51-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3cc51-161">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3cc51-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
