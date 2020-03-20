---
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151292"
---
# <a name="datatable-constraints"></a><span data-ttu-id="72688-102">DataTable Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="72688-102">DataTable Constraints</span></span>
<span data-ttu-id="72688-103">Verilerin bütünlüğünü korumak için, bir 'deki <xref:System.Data.DataTable>veriler üzerindeki kısıtlamaları zorlamak için kısıtlamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="72688-104">Kısıtlama, bir satırın değeri bir şekilde değiştirildiğinde eylem seyrini belirleyen bir sütuna veya ilgili sütunlara uygulanan otomatik bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="72688-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="72688-105">Kısıtlamalar, `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> **doğru**olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="72688-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="72688-106">`EnforceConstraints` Özelliğin nasıl ayarlandığını gösteren bir kod <xref:System.Data.DataSet.EnforceConstraints%2A> örneği için başvuru konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="72688-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="72688-107">ADO.NET'da iki tür kısıtlama vardır: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>ve .</span><span class="sxs-lookup"><span data-stu-id="72688-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="72688-108">Varsayılan olarak, <xref:System.Data.DataRelation> **DataSet'e**bir tane ekleyerek iki veya daha fazla tablo arasında ilişki oluşturduğunuzda her iki kısıtlama da otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="72688-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="72688-109">Ancak, ilişki oluştururken **createConstraints** = **yanlış** belirterek bu davranışı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="72688-110">Foreignkeyconstraint</span><span class="sxs-lookup"><span data-stu-id="72688-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="72688-111">**ForeignKeyConstraint,** ilgili tablolara güncelleştirmelerin ve silmelerin nasıl yayLılacak olduğuna ilişkin kurallar uygular.</span><span class="sxs-lookup"><span data-stu-id="72688-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="72688-112">Örneğin, bir tablonun satırındaki bir değer güncelleştirilir veya silinirse ve aynı değer bir veya daha fazla ilgili tabloda da kullanılırsa, ilgili tablolarda neler olacağını **ForeignKeyConstraint** belirler.</span><span class="sxs-lookup"><span data-stu-id="72688-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="72688-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> **ForeignKeyConstraint'in** özellikleri ve özellikleri, kullanıcı ilgili tablodaki bir satırı silmeye veya güncelleştirmeye çalıştığında yapılacak eylemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72688-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="72688-114">Aşağıdaki tabloda **ForeignKeyConstraint'in** **DeleteRule** ve **UpdateRule** özellikleri için kullanılabilen farklı ayarlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72688-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="72688-115">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="72688-115">Rule setting</span></span>|<span data-ttu-id="72688-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72688-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="72688-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="72688-117">**Cascade**</span></span>|<span data-ttu-id="72688-118">İlgili satırları silin veya güncelleyin.</span><span class="sxs-lookup"><span data-stu-id="72688-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="72688-119">**Setnull**</span><span class="sxs-lookup"><span data-stu-id="72688-119">**SetNull**</span></span>|<span data-ttu-id="72688-120">İlgili satırlarda değerleri **DBNull'a**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72688-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="72688-121">**Setdefault**</span><span class="sxs-lookup"><span data-stu-id="72688-121">**SetDefault**</span></span>|<span data-ttu-id="72688-122">İlgili satırlarda değerleri varsayılan değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72688-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="72688-123">**Yok**</span><span class="sxs-lookup"><span data-stu-id="72688-123">**None**</span></span>|<span data-ttu-id="72688-124">İlgili satırlarda hiçbir işlem de bulunmayın.</span><span class="sxs-lookup"><span data-stu-id="72688-124">Take no action on related rows.</span></span> <span data-ttu-id="72688-125">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="72688-125">This is the default.</span></span>|  
  
 <span data-ttu-id="72688-126">**ForeignKeyConstraint,** ilgili sütundeğişiklikleri kısıtlamanın yanı sıra çoğaltabilir.</span><span class="sxs-lookup"><span data-stu-id="72688-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="72688-127">Bir sütunun **ForeignKeyConstraint** için ayarlanan özelliklerine bağlı olarak, **DataSet'in** **EnforceConstraints** özelliği **doğruysa,** ana satırda belirli işlemler gerçekleştirmek bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="72688-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="72688-128">Örneğin, **ForeignKeyConstraint'in** **DeleteRule** özelliği **Yok**ise, alt satırı varsa bir üst satır silinemez.</span><span class="sxs-lookup"><span data-stu-id="72688-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="72688-129">**ForeignKeyConstraint** oluşturucusunu kullanarak tek sütunlar arasında veya bir dizi sütun arasında yabancı anahtar kısıtlaması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="72688-130">Ortaya çıkan **ForeignKeyConstraint** nesnesini, bir **ConstraintCollection**olan tablonun **Kısıtlamalar** özelliğinin **Ekle** yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="72688-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="72688-131">Ayrıca, bir **ForeignKeyConstraint**oluşturmak için **constraintcollection'ın Ekle** yönteminin birkaç aşırı yüklemesine oluşturucu bağımsız değişkenler geçirebilirsiniz. **ConstraintCollection**</span><span class="sxs-lookup"><span data-stu-id="72688-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="72688-132">**ForeignKeyConstraint**oluştururken, **DeleteRule** ve **UpdateRule** değerlerini bağımsız değişken olarak oluşturucuya geçirebilir veya bunları aşağıdaki örnekte olduğu gibi **(DeleteRule** değerinin **None**olarak ayarlandığı) özellikleri olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="72688-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="72688-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="72688-134">Satırdeğişiklikleri **AcceptChanges** yöntemi kullanılarak kabul edilebilir veya **DataSet,** **DataTable**veya **DataRow'un** **Reddet** değişiklikleri yöntemi kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="72688-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="72688-135">Bir **DataSet** **ForeignKeyConstraints**içeriyorsa , **AcceptChanges** veya **RejectChanges** yöntemlerini çağırarak **AcceptRejectRule'i**zorlar.</span><span class="sxs-lookup"><span data-stu-id="72688-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="72688-136">**ForeignKeyConstraint'in** **AcceptRejectRule** özelliği, üst satırda **Değişiklikleri Kabul** veya **Reddet** çağrıldığında alt satırlarda hangi eylemin alınacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="72688-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="72688-137">Aşağıdaki tabloda **AcceptRejectRule**için kullanılabilir ayarlar listelenir.</span><span class="sxs-lookup"><span data-stu-id="72688-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="72688-138">Kural ayarı</span><span class="sxs-lookup"><span data-stu-id="72688-138">Rule setting</span></span>|<span data-ttu-id="72688-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72688-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="72688-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="72688-140">**Cascade**</span></span>|<span data-ttu-id="72688-141">Alt satırlarda yapılan değişiklikleri kabul edin veya reddedin.</span><span class="sxs-lookup"><span data-stu-id="72688-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="72688-142">**Yok**</span><span class="sxs-lookup"><span data-stu-id="72688-142">**None**</span></span>|<span data-ttu-id="72688-143">Alt satırlar üzerinde hiçbir işlem de bulunmayın.</span><span class="sxs-lookup"><span data-stu-id="72688-143">Take no action on child rows.</span></span> <span data-ttu-id="72688-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="72688-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="72688-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="72688-145">Example</span></span>  
 <span data-ttu-id="72688-146">Aşağıdaki örnek, bir <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, özellikleri, dahil olmak üzere birkaç tane <xref:System.Data.ConstraintCollection> ayarlar <xref:System.Data.DataTable> ve bir nesnenin ekler.</span><span class="sxs-lookup"><span data-stu-id="72688-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="72688-147">Uniqueconstraint</span><span class="sxs-lookup"><span data-stu-id="72688-147">UniqueConstraint</span></span>  
 <span data-ttu-id="72688-148">Tek bir sütuna veya **DataTable'daki**bir sütun dizisine atanabilen **Benzersiz Kısıtlama** nesnesi, belirtilen sütun veya sütunlarda bulunan tüm verilerin satır başına benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="72688-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="72688-149">**UniqueConstraint** oluşturucusunu kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="72688-150">Ortaya çıkan **UniqueConstraint** nesnesini, bir **ConstraintCollection**olan tablonun **Kısıtlamalar** özelliğinin **Ekle** yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="72688-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="72688-151">Ayrıca, **bir UniqueConstraint**oluşturmak için **constraintcollection'ın** **Ekle** yönteminin birkaç aşırı yüklemesine oluşturucu bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="72688-152">Bir sütun veya sütun için **Benzersiz Kısıtlama** oluştururken, isteğe bağlı olarak sütun veya sütunların birincil anahtar olup olmadığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="72688-153">Ayrıca, sütunun **Benzersiz** özelliğini **doğru**olarak ayarlayarak sütun için benzersiz bir kısıtlama da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72688-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="72688-154">Alternatif olarak, tek bir sütunun **Benzersiz** özelliğini **false** olarak ayarlamak, var olabilecek benzersiz kısıtlamaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="72688-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="72688-155">Bir sütun veya sütunu tabloiçin birincil anahtar olarak tanımlamak, belirtilen sütun veya sütunlar için otomatik olarak benzersiz bir kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72688-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="72688-156">**Bir sütunu DataTable'ın** **PrimaryKey** özelliğinden kaldırırsanız, **UniqueConstraint** kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="72688-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="72688-157">Aşağıdaki örnek, Bir **DataTable'ın**iki sütunu için **Benzersiz Kısıtlama** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72688-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72688-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72688-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="72688-159">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="72688-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="72688-160">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="72688-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="72688-161">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72688-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
