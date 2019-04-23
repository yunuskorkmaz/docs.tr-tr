---
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 254f486fa19d8af30759d9a9fd6642a1a40e82a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165184"
---
# <a name="datatable-constraints"></a><span data-ttu-id="3a15c-102">DataTable Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3a15c-102">DataTable Constraints</span></span>
<span data-ttu-id="3a15c-103">Kısıtlamaları verileri kısıtlamalarını uygulamak için kullanabileceğiniz bir <xref:System.Data.DataTable>, veri bütünlüğünü korumak için.</span><span class="sxs-lookup"><span data-stu-id="3a15c-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="3a15c-104">Bir sınırlamadır uygulanan otomatik bir kural, bir sütun veya ilgili sütunlar için belirleyen kursu eyleminin bir satırın değerini şekilde değiştirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="3a15c-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="3a15c-105">Kısıtlamaları zorunlu olduğunda `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> olduğu **true**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="3a15c-106">Nasıl ayarlanacağı gösteren kod örneği için `EnforceConstraints` özelliği bkz <xref:System.Data.DataSet.EnforceConstraints%2A> başvuru konusu.</span><span class="sxs-lookup"><span data-stu-id="3a15c-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="3a15c-107">ADO.NET'te kısıtlamaları iki tür vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="3a15c-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="3a15c-108">Ekleyerek en az iki tablo arasında bir ilişki oluşturduğunuzda varsayılan olarak, her iki kısıtlamalar otomatik olarak oluşturulan bir <xref:System.Data.DataRelation> için **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="3a15c-109">Ancak, bu davranışı belirtilerek devre dışı bırakabilirsiniz **createConstraints** = **false** ilişki oluştururken.</span><span class="sxs-lookup"><span data-stu-id="3a15c-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="3a15c-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="3a15c-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="3a15c-111">A **ForeignKeyConstraint** hakkında güncelleştirme ve silme ilişkili tablolar için nasıl yayılır kuralları zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="3a15c-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="3a15c-112">Örneğin, bir değer, bir tablonun satır güncelleştirilemiyor veya silinemiyor ve aynı değeri de birinde kullanılır veya tabloları, ilgili daha fazla bir **ForeignKeyConstraint** ilişkili tabloların ne olacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="3a15c-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="3a15c-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> özelliklerini **ForeignKeyConstraint** silin veya ilgili bir tabloda bir satırı güncelleştirmek kullanıcının çalışır olduğunda gerçekleştirilecek eylem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3a15c-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="3a15c-114">Aşağıdaki tablo kullanılabilecek farklı ayarlar açıklanır **DeleteRule** ve **UpdateRule** özelliklerini **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="3a15c-115">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="3a15c-115">Rule setting</span></span>|<span data-ttu-id="3a15c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a15c-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3a15c-117">**Basamakla**</span><span class="sxs-lookup"><span data-stu-id="3a15c-117">**Cascade**</span></span>|<span data-ttu-id="3a15c-118">Silin veya ilişkili satırları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3a15c-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="3a15c-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="3a15c-119">**SetNull**</span></span>|<span data-ttu-id="3a15c-120">İlişkili satırların değerleri ayarlayın **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="3a15c-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="3a15c-121">**SetDefault**</span></span>|<span data-ttu-id="3a15c-122">Değerleri ilişkili satırları için varsayılan değer olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3a15c-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="3a15c-123">**Yok.**</span><span class="sxs-lookup"><span data-stu-id="3a15c-123">**None**</span></span>|<span data-ttu-id="3a15c-124">İlgili satır eylem yok.</span><span class="sxs-lookup"><span data-stu-id="3a15c-124">Take no action on related rows.</span></span> <span data-ttu-id="3a15c-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3a15c-125">This is the default.</span></span>|  
  
 <span data-ttu-id="3a15c-126">A **ForeignKeyConstraint** yaymak olarak değişiklikleriyle ilgili sütunları, kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a15c-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="3a15c-127">Özellikleri için bağlı olarak **ForeignKeyConstraint** bir sütunun varsa **EnforceConstraints** özelliği **veri kümesi** olduğu **true**, belirli işlemleri üst satırda bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a15c-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="3a15c-128">Örneğin, varsa **DeleteRule** özelliği **ForeignKeyConstraint** olduğu **hiçbiri**, herhangi bir alt satır varsa, bir üst satır silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="3a15c-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="3a15c-129">Bir yabancı anahtar kısıtlaması bir dizi kullanarak sütunları arasında veya tek bir sütun oluşturabilirsiniz **ForeignKeyConstraint** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3a15c-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="3a15c-130">Ortaya çıkan geçirmek **ForeignKeyConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** özelliğinin bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3a15c-131">Oluşturucu bağımsız ilişkin çeşitli aşırı yükler için de geçirebilirsiniz **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="3a15c-132">Oluştururken bir **ForeignKeyConstraint**, geçirebilirsiniz **DeleteRule** ve **UpdateRule** değerleri oluşturucusu için bağımsız değişkenler veya olarak ayarlayabilirsiniz gibi özellikleri Örnek (burada **DeleteRule** değeri ayarı **hiçbiri**).</span><span class="sxs-lookup"><span data-stu-id="3a15c-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="3a15c-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="3a15c-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="3a15c-134">Satırlara değişiklikler kullanarak kabul edilen **AcceptChanges** yöntemi veya iptal edilmiş kullanarak **RejectChanges** yöntemi **veri kümesi**, **DataTable**, veya **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="3a15c-135">Olduğunda bir **veri kümesi** içeren **sağlayan**, çağrılıyor **AcceptChanges** veya **RejectChanges** yöntemleriniuygular **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="3a15c-136">**AcceptRejectRule** özelliği **ForeignKeyConstraint** alt gerçekleştirilecek eylemi belirler ne zaman satırları **AcceptChanges** veya  **RejectChanges** üst satırda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a15c-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="3a15c-137">Aşağıdaki tabloda kullanılabilir ayarlarını listeler **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="3a15c-138">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="3a15c-138">Rule setting</span></span>|<span data-ttu-id="3a15c-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a15c-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3a15c-140">**Basamakla**</span><span class="sxs-lookup"><span data-stu-id="3a15c-140">**Cascade**</span></span>|<span data-ttu-id="3a15c-141">Veya alt satırlara değişiklikler reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a15c-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="3a15c-142">**Yok.**</span><span class="sxs-lookup"><span data-stu-id="3a15c-142">**None**</span></span>|<span data-ttu-id="3a15c-143">Alt satırlar üzerinde eylem yok.</span><span class="sxs-lookup"><span data-stu-id="3a15c-143">Take no action on child rows.</span></span> <span data-ttu-id="3a15c-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3a15c-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="3a15c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a15c-145">Example</span></span>  
 <span data-ttu-id="3a15c-146">Aşağıdaki örnek, oluşturur bir <xref:System.Data.ForeignKeyConstraint>, birkaç dahil olmak üzere özellikleri ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>ve bu gruba ekler <xref:System.Data.ConstraintCollection> , bir <xref:System.Data.DataTable> nesne.</span><span class="sxs-lookup"><span data-stu-id="3a15c-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="3a15c-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="3a15c-147">UniqueConstraint</span></span>  
 <span data-ttu-id="3a15c-148">**UniqueConstraint** tek bir sütun veya sütun bir dizi atanan nesne, bir **DataTable**, tüm verilerini belirtilen sütun veya sütunlar satır benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a15c-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="3a15c-149">Bir sütun veya sütun dizisi için benzersiz bir Kısıt kullanarak oluşturabileceğiniz **UniqueConstraint** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3a15c-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="3a15c-150">Ortaya çıkan geçirmek **UniqueConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** özelliğinin bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3a15c-151">Oluşturucu bağımsız ilişkin çeşitli aşırı yükler için de geçirebilirsiniz **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="3a15c-152">Oluştururken bir **UniqueConstraint** bir sütun veya sütunlar için isteğe bağlı olarak bir birincil anahtar sütun veya sütunlar olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a15c-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="3a15c-153">Ayarlayarak bir sütun için benzersiz bir Kısıt oluşturabilirsiniz **benzersiz** sütununun özellik **true**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="3a15c-154">Alternatif olarak, ayarı **benzersiz** özelliğini tek bir sütuna **false** oluşabilecek herhangi bir benzersiz kısıtlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3a15c-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="3a15c-155">Bir sütun veya sütunlar bir tablo için birincil anahtar olarak tanımlayan benzersiz bir kısıtlaması belirtilen sütun veya sütunlar için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a15c-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="3a15c-156">Bir sütun kaldırırsanız **PrimaryKey** özelliği bir **DataTable**, **UniqueConstraint** kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3a15c-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="3a15c-157">Aşağıdaki örnek, oluşturur bir **UniqueConstraint** iki sütunu için bir **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3a15c-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a15c-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a15c-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="3a15c-159">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="3a15c-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="3a15c-160">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="3a15c-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="3a15c-161">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3a15c-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
