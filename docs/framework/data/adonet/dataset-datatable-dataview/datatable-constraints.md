---
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 1224518a9a16f48f770b6839317b9787da97377b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153280"
---
# <a name="datatable-constraints"></a><span data-ttu-id="66d63-102">DataTable Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="66d63-102">DataTable Constraints</span></span>

<span data-ttu-id="66d63-103">Verilerin bütünlüğünü sağlamak için, bir içindeki veriler üzerinde kısıtlama zorlamak üzere kısıtlamaları kullanabilirsiniz <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="66d63-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="66d63-104">Kısıtlama bir sütuna veya ilgili sütunlara uygulanan bir otomatik kuraldır ve bir satırın değeri bir değer değiştiğinde eylem kursu belirler.</span><span class="sxs-lookup"><span data-stu-id="66d63-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="66d63-105">Özelliği true olduğunda kısıtlamalar uygulanır `System.Data.DataSet.EnforceConstraints` <xref:System.Data.DataSet> . **true**</span><span class="sxs-lookup"><span data-stu-id="66d63-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="66d63-106">Özelliği ayarlamayı gösteren bir kod örneği için `EnforceConstraints` bkz <xref:System.Data.DataSet.EnforceConstraints%2A> . başvuru konusu.</span><span class="sxs-lookup"><span data-stu-id="66d63-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="66d63-107">ADO.NET içinde iki tür kısıtlama vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> .</span><span class="sxs-lookup"><span data-stu-id="66d63-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="66d63-108">Varsayılan olarak, <xref:System.Data.DataRelation> **veri kümesine**bir ekleyerek iki veya daha fazla tablo arasında bir ilişki oluşturduğunuzda her iki kısıtlama otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66d63-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="66d63-109">Ancak, ilişki oluştururken yanlış **createkısıtlamalarını**belirterek bu davranışı devre dışı bırakabilirsiniz  =  **false** .</span><span class="sxs-lookup"><span data-stu-id="66d63-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="66d63-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="66d63-110">ForeignKeyConstraint</span></span>  

 <span data-ttu-id="66d63-111">Bir **ForeignKeyConstraint** , ilgili tablolarda güncelleştirmelerin ve silinme işlemlerinin nasıl yayıldığı hakkında kurallara zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d63-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="66d63-112">Örneğin, bir tablonun bir satırındaki bir değer güncellenir veya silinirse ve aynı değer aynı zamanda bir veya daha fazla ilişkili tabloda kullanılıyorsa, **ForeignKeyConstraint** ilişkili tablolarda ne olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="66d63-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="66d63-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>ForeignKeyConstraint ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> Özellikleri, Kullanıcı **ForeignKeyConstraint** ilgili tablodaki bir satırı silmeye veya güncelleştirmeye çalıştığında gerçekleştirilecek eylemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66d63-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="66d63-114">Aşağıdaki tabloda, **ForeignKeyConstraint**'In **DeleteRule** ve **UpdateRule** özellikleri için kullanılabilen farklı ayarlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66d63-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="66d63-115">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="66d63-115">Rule setting</span></span>|<span data-ttu-id="66d63-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66d63-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="66d63-117">**Seçilemez**</span><span class="sxs-lookup"><span data-stu-id="66d63-117">**Cascade**</span></span>|<span data-ttu-id="66d63-118">İlişkili satırları silin veya güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="66d63-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="66d63-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="66d63-119">**SetNull**</span></span>|<span data-ttu-id="66d63-120">İlgili satırlardaki değerleri **DBNull**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="66d63-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="66d63-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="66d63-121">**SetDefault**</span></span>|<span data-ttu-id="66d63-122">İlgili satırlardaki değerleri varsayılan değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="66d63-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="66d63-123">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="66d63-123">**None**</span></span>|<span data-ttu-id="66d63-124">İlgili satırlarda hiçbir işlem yapın.</span><span class="sxs-lookup"><span data-stu-id="66d63-124">Take no action on related rows.</span></span> <span data-ttu-id="66d63-125">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="66d63-125">This is the default.</span></span>|  
  
 <span data-ttu-id="66d63-126">Bir **ForeignKeyConstraint** , ilişkili sütunlardaki değişiklikleri kısıtlayabilir ve yayabilir.</span><span class="sxs-lookup"><span data-stu-id="66d63-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="66d63-127">Bir sütunun **ForeignKeyConstraint** için ayarlanan özelliklere bağlı olarak, **veri kümesinin** **enforcekısıtlamalar** özelliği **true**ise, üst satırda belirli işlemleri gerçekleştirmek bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="66d63-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="66d63-128">Örneğin, **ForeignKeyConstraint** 'In **DeleteRule** özelliği **none**ise, bir üst satır alt satırları varsa silinemez.</span><span class="sxs-lookup"><span data-stu-id="66d63-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="66d63-129">**ForeignKeyConstraint** oluşturucusunu kullanarak, tek sütunlar arasında veya bir sütun dizisi arasında yabancı anahtar kısıtlaması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="66d63-130">Elde edilen **ForeignKeyConstraint** nesnesini tablonun **kısıtlamalar** özelliğinin **Add** yöntemine geçirin, bu bir **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="66d63-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="66d63-131">Ayrıca, bir **ForeignKeyConstraint**oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="66d63-132">Bir **ForeignKeyConstraint**oluştururken, **DeleteRule** ve **UpdateRule** değerlerini bağımsız değişken olarak oluşturucuya geçirebilir ya da aşağıdaki örnekte olduğu gibi bunları özellikler olarak ayarlayabilirsiniz (burada **DeleteRule** değeri **none**olarak ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="66d63-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="66d63-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="66d63-133">AcceptRejectRule</span></span>  

 <span data-ttu-id="66d63-134">Satırlarda yapılan değişiklikler **AcceptChanges** yöntemi kullanılarak kabul edilebilir veya **DataSet**, **DataTable**veya **DataRow**' ın **RejectChanges** yöntemi kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="66d63-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="66d63-135">Bir **veri kümesi** **ForeignKeyConstraints**Içerdiğinde, **AcceptChanges** veya **RejectChanges** yöntemlerini çağırmak **AcceptRejectRule**'yi zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d63-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="66d63-136">**ForeignKeyConstraint** 'ın **AcceptRejectRule** özelliği, üst satırda **AcceptChanges** veya **RejectChanges** çağrıldığında alt satırlarda hangi eylemin alınacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="66d63-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="66d63-137">Aşağıdaki tabloda, **AcceptRejectRule**için kullanılabilir ayarlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="66d63-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="66d63-138">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="66d63-138">Rule setting</span></span>|<span data-ttu-id="66d63-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66d63-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="66d63-140">**Seçilemez**</span><span class="sxs-lookup"><span data-stu-id="66d63-140">**Cascade**</span></span>|<span data-ttu-id="66d63-141">Alt satırlardaki değişiklikleri kabul edin veya reddedin.</span><span class="sxs-lookup"><span data-stu-id="66d63-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="66d63-142">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="66d63-142">**None**</span></span>|<span data-ttu-id="66d63-143">Alt satırlarda hiçbir işlem yapın.</span><span class="sxs-lookup"><span data-stu-id="66d63-143">Take no action on child rows.</span></span> <span data-ttu-id="66d63-144">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="66d63-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="66d63-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="66d63-145">Example</span></span>  

 <span data-ttu-id="66d63-146">Aşağıdaki örnek bir oluşturur, ve <xref:System.Data.ForeignKeyConstraint> dahil olmak üzere bazı özelliklerini ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> ve <xref:System.Data.ConstraintCollection> bir nesnesinin öğesine ekler <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="66d63-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="66d63-147">UniqueConstraint kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="66d63-147">UniqueConstraint</span></span>  

 <span data-ttu-id="66d63-148">Tek bir sütuna veya bir **DataTable**içindeki bir sütun dizisine atanabilecek **UniqueConstraint** nesnesi, belirtilen sütundaki veya sütunlardaki tüm verilerin her satır için benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66d63-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="66d63-149">**UniqueConstraint** oluşturucuyu kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="66d63-150">Elde edilen **UniqueConstraint** nesnesini, **ConstraintCollection**olan tablonun **kısıtlamalar** özelliğinin **Add** metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="66d63-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="66d63-151">Ayrıca, bir **UniqueConstraint kısıtlaması**oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="66d63-152">Bir sütun veya sütun için bir **UniqueConstraint kısıtlaması** oluştururken, isteğe bağlı olarak sütun veya sütunların birincil anahtar olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="66d63-153">Ayrıca, sütunun **Unique** özelliğini **true**olarak ayarlayarak bir sütun için benzersiz bir kısıtlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d63-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="66d63-154">Alternatif olarak, tek bir sütunun **Unique** özelliğinin **false** olarak ayarlanması, var olabilecek herhangi bir benzersiz kısıtlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="66d63-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="66d63-155">Bir tablo için birincil anahtar olarak bir sütun veya sütun tanımlamak, belirtilen sütun veya sütunlar için otomatik olarak benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66d63-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="66d63-156">**DataTable**'ın **PrimaryKey** özelliğinden bir sütunu kaldırırsanız, **UniqueConstraint kısıtlaması** kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="66d63-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="66d63-157">Aşağıdaki örnek, bir **DataTable**'ın iki sütunu Için bir **UniqueConstraint kısıtlaması** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66d63-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66d63-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66d63-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="66d63-159">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="66d63-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="66d63-160">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="66d63-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="66d63-161">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="66d63-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
