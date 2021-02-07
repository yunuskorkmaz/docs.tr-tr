---
description: 'Daha fazla bilgi edinin: DataTable kısıtlamaları'
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 0c712115fd87fefae3578b2f3fc0adfc416f412e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724914"
---
# <a name="datatable-constraints"></a><span data-ttu-id="007ae-103">DataTable Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="007ae-103">DataTable Constraints</span></span>

<span data-ttu-id="007ae-104">Verilerin bütünlüğünü sağlamak için, bir içindeki veriler üzerinde kısıtlama zorlamak üzere kısıtlamaları kullanabilirsiniz <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="007ae-104">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="007ae-105">Kısıtlama bir sütuna veya ilgili sütunlara uygulanan bir otomatik kuraldır ve bir satırın değeri bir değer değiştiğinde eylem kursu belirler.</span><span class="sxs-lookup"><span data-stu-id="007ae-105">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="007ae-106">Özelliği true olduğunda kısıtlamalar uygulanır `System.Data.DataSet.EnforceConstraints` <xref:System.Data.DataSet> . </span><span class="sxs-lookup"><span data-stu-id="007ae-106">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="007ae-107">Özelliği ayarlamayı gösteren bir kod örneği için `EnforceConstraints` bkz <xref:System.Data.DataSet.EnforceConstraints%2A> . başvuru konusu.</span><span class="sxs-lookup"><span data-stu-id="007ae-107">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="007ae-108">ADO.NET içinde iki tür kısıtlama vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> .</span><span class="sxs-lookup"><span data-stu-id="007ae-108">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="007ae-109">Varsayılan olarak, <xref:System.Data.DataRelation> **veri kümesine** bir ekleyerek iki veya daha fazla tablo arasında bir ilişki oluşturduğunuzda her iki kısıtlama otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="007ae-109">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="007ae-110">Ancak, ilişki oluştururken yanlış **createkısıtlamalarını** belirterek bu davranışı devre dışı bırakabilirsiniz  =   .</span><span class="sxs-lookup"><span data-stu-id="007ae-110">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="007ae-111">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="007ae-111">ForeignKeyConstraint</span></span>  

 <span data-ttu-id="007ae-112">Bir **ForeignKeyConstraint** , ilgili tablolarda güncelleştirmelerin ve silinme işlemlerinin nasıl yayıldığı hakkında kurallara zorlar.</span><span class="sxs-lookup"><span data-stu-id="007ae-112">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="007ae-113">Örneğin, bir tablonun bir satırındaki bir değer güncellenir veya silinirse ve aynı değer aynı zamanda bir veya daha fazla ilişkili tabloda kullanılıyorsa, **ForeignKeyConstraint** ilişkili tablolarda ne olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="007ae-113">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="007ae-114"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>ForeignKeyConstraint ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> Özellikleri, Kullanıcı  ilgili tablodaki bir satırı silmeye veya güncelleştirmeye çalıştığında gerçekleştirilecek eylemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="007ae-114">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="007ae-115">Aşağıdaki tabloda, **ForeignKeyConstraint**'In **DeleteRule** ve **UpdateRule** özellikleri için kullanılabilen farklı ayarlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="007ae-115">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="007ae-116">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="007ae-116">Rule setting</span></span>|<span data-ttu-id="007ae-117">Description</span><span class="sxs-lookup"><span data-stu-id="007ae-117">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="007ae-118">**Seçilemez**</span><span class="sxs-lookup"><span data-stu-id="007ae-118">**Cascade**</span></span>|<span data-ttu-id="007ae-119">İlişkili satırları silin veya güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="007ae-119">Delete or update related rows.</span></span>|  
|<span data-ttu-id="007ae-120">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="007ae-120">**SetNull**</span></span>|<span data-ttu-id="007ae-121">İlgili satırlardaki değerleri **DBNull** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="007ae-121">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="007ae-122">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="007ae-122">**SetDefault**</span></span>|<span data-ttu-id="007ae-123">İlgili satırlardaki değerleri varsayılan değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="007ae-123">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="007ae-124">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="007ae-124">**None**</span></span>|<span data-ttu-id="007ae-125">İlgili satırlarda hiçbir işlem yapın.</span><span class="sxs-lookup"><span data-stu-id="007ae-125">Take no action on related rows.</span></span> <span data-ttu-id="007ae-126">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="007ae-126">This is the default.</span></span>|  
  
 <span data-ttu-id="007ae-127">Bir **ForeignKeyConstraint** , ilişkili sütunlardaki değişiklikleri kısıtlayabilir ve yayabilir.</span><span class="sxs-lookup"><span data-stu-id="007ae-127">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="007ae-128">Bir sütunun **ForeignKeyConstraint** için ayarlanan özelliklere bağlı olarak, **veri kümesinin** **enforcekısıtlamalar** özelliği **true** ise, üst satırda belirli işlemleri gerçekleştirmek bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="007ae-128">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="007ae-129">Örneğin, **ForeignKeyConstraint** 'In **DeleteRule** özelliği **none** ise, bir üst satır alt satırları varsa silinemez.</span><span class="sxs-lookup"><span data-stu-id="007ae-129">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="007ae-130">**ForeignKeyConstraint** oluşturucusunu kullanarak, tek sütunlar arasında veya bir sütun dizisi arasında yabancı anahtar kısıtlaması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-130">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="007ae-131">Elde edilen **ForeignKeyConstraint** nesnesini tablonun **kısıtlamalar** özelliğinin **Add** yöntemine geçirin, bu bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="007ae-131">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="007ae-132">Ayrıca, bir **ForeignKeyConstraint** oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-132">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="007ae-133">Bir **ForeignKeyConstraint** oluştururken, **DeleteRule** ve **UpdateRule** değerlerini bağımsız değişken olarak oluşturucuya geçirebilir ya da aşağıdaki örnekte olduğu gibi bunları özellikler olarak ayarlayabilirsiniz (burada **DeleteRule** değeri **none** olarak ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="007ae-133">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="007ae-134">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="007ae-134">AcceptRejectRule</span></span>  

 <span data-ttu-id="007ae-135">Satırlarda yapılan değişiklikler **AcceptChanges** yöntemi kullanılarak kabul edilebilir veya **DataSet**, **DataTable** veya **DataRow**' ın **RejectChanges** yöntemi kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="007ae-135">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="007ae-136">Bir **veri kümesi** **ForeignKeyConstraints** Içerdiğinde, **AcceptChanges** veya **RejectChanges** yöntemlerini çağırmak **AcceptRejectRule**'yi zorlar.</span><span class="sxs-lookup"><span data-stu-id="007ae-136">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="007ae-137">**ForeignKeyConstraint** 'ın **AcceptRejectRule** özelliği, üst satırda **AcceptChanges** veya **RejectChanges** çağrıldığında alt satırlarda hangi eylemin alınacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="007ae-137">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="007ae-138">Aşağıdaki tabloda, **AcceptRejectRule** için kullanılabilir ayarlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="007ae-138">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="007ae-139">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="007ae-139">Rule setting</span></span>|<span data-ttu-id="007ae-140">Description</span><span class="sxs-lookup"><span data-stu-id="007ae-140">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="007ae-141">**Seçilemez**</span><span class="sxs-lookup"><span data-stu-id="007ae-141">**Cascade**</span></span>|<span data-ttu-id="007ae-142">Alt satırlardaki değişiklikleri kabul edin veya reddedin.</span><span class="sxs-lookup"><span data-stu-id="007ae-142">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="007ae-143">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="007ae-143">**None**</span></span>|<span data-ttu-id="007ae-144">Alt satırlarda hiçbir işlem yapın.</span><span class="sxs-lookup"><span data-stu-id="007ae-144">Take no action on child rows.</span></span> <span data-ttu-id="007ae-145">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="007ae-145">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="007ae-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="007ae-146">Example</span></span>  

 <span data-ttu-id="007ae-147">Aşağıdaki örnek bir oluşturur, ve <xref:System.Data.ForeignKeyConstraint> dahil olmak üzere bazı özelliklerini ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> ve <xref:System.Data.ConstraintCollection> bir nesnesinin öğesine ekler <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="007ae-147">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="007ae-148">UniqueConstraint kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="007ae-148">UniqueConstraint</span></span>  

 <span data-ttu-id="007ae-149">Tek bir sütuna veya bir **DataTable** içindeki bir sütun dizisine atanabilecek **UniqueConstraint** nesnesi, belirtilen sütundaki veya sütunlardaki tüm verilerin her satır için benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="007ae-149">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="007ae-150">**UniqueConstraint** oluşturucuyu kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-150">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="007ae-151">Elde edilen **UniqueConstraint** nesnesini, **ConstraintCollection** olan tablonun **kısıtlamalar** özelliğinin **Add** metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="007ae-151">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="007ae-152">Ayrıca, bir **UniqueConstraint kısıtlaması** oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-152">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="007ae-153">Bir sütun veya sütun için bir **UniqueConstraint kısıtlaması** oluştururken, isteğe bağlı olarak sütun veya sütunların birincil anahtar olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-153">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="007ae-154">Ayrıca, sütunun **Unique** özelliğini **true** olarak ayarlayarak bir sütun için benzersiz bir kısıtlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007ae-154">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="007ae-155">Alternatif olarak, tek bir sütunun **Unique** özelliğinin **false** olarak ayarlanması, var olabilecek herhangi bir benzersiz kısıtlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="007ae-155">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="007ae-156">Bir tablo için birincil anahtar olarak bir sütun veya sütun tanımlamak, belirtilen sütun veya sütunlar için otomatik olarak benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="007ae-156">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="007ae-157">**DataTable**'ın **PrimaryKey** özelliğinden bir sütunu kaldırırsanız, **UniqueConstraint kısıtlaması** kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="007ae-157">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="007ae-158">Aşağıdaki örnek, bir **DataTable**'ın iki sütunu Için bir **UniqueConstraint kısıtlaması** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="007ae-158">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="007ae-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="007ae-159">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="007ae-160">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="007ae-160">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="007ae-161">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="007ae-161">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="007ae-162">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="007ae-162">ADO.NET Overview</span></span>](../ado-net-overview.md)
