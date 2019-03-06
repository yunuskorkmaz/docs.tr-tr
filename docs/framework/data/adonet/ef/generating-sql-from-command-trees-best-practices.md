---
title: SQL komut ağaçlarından - en iyi uygulamalar oluşturma
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 6ac46b577f071bca6c79e23b8b77f9b267ac879b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369675"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="8c851-102">SQL komut ağaçlarından - en iyi uygulamalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c851-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="8c851-103">Çıkış sorgu komut ağaçlarını yakından sorguları SQL ifade model.</span><span class="sxs-lookup"><span data-stu-id="8c851-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="8c851-104">Ancak, SQL bir çıkış komut ağacından oluşturulurken bazı sık karşılaşılan zorluklar sağlayıcısı yazıcılar için vardır.</span><span class="sxs-lookup"><span data-stu-id="8c851-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="8c851-105">Bu konuda, bu sorunları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="8c851-105">This topic discusses these challenges.</span></span> <span data-ttu-id="8c851-106">Sonraki konu başlığında örnek sağlayıcısı bu sorunları gidermek üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c851-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="8c851-107">Bir SQL SELECT deyimi içinde Dbexpression'dan düğümleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="8c851-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="8c851-108">Aşağıdaki şekil, iç içe bir yapı normal bir SQL deyimi vardır:</span><span class="sxs-lookup"><span data-stu-id="8c851-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="8c851-109">Bir veya daha fazla yan tümceleri boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="8c851-110">İç içe geçmiş bir SELECT deyimi, tüm satırların oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="8c851-111">Bir SQL SELECT deyimi sorgu komut ağacı, olası bir çevirisini her ilişkisel işleç için bir alt sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c851-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="8c851-112">Ancak, okunması zor olabilecek gereksiz iç içe geçmiş alt sorgulara neden.</span><span class="sxs-lookup"><span data-stu-id="8c851-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="8c851-113">Bazı veri depoları sorgu sonlanmayacağından.</span><span class="sxs-lookup"><span data-stu-id="8c851-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="8c851-114">Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8c851-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="8c851-115">Verimsiz bir çeviri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8c851-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="8c851-116">Her ilişkisel ifade düğüme yeni bir SQL SELECT deyimi olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8c851-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="8c851-117">Bu nedenle, doğruluk korurken tek bir SQL SELECT deyimi içinde mümkün olduğunca çok ifade düğümleri toplamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8c851-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="8c851-118">Yukarıda verilen örneği için bu tür bir toplama sonucu şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="8c851-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="8c851-119">Bir SQL SELECT deyimi birleşimlerde düzleştirme</span><span class="sxs-lookup"><span data-stu-id="8c851-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="8c851-120">Tek bir SQL SELECT deyimi içinde birden çok düğüm toplayarak bir kullanım durumu, tek bir SQL SELECT deyimi birden fazla birleştirme ifadelere yeniden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="8c851-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="8c851-121">İki girdi arasında tek bir birleştirme DbJoinExpression'temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8c851-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="8c851-122">Ancak, tek bir SQL SELECT deyimi bir parçası olarak, birden fazla birleştirme belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="8c851-123">Bu durumda birleştirmeler belirtilen sıraya göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="8c851-124">Omurgası birleştirmeler sol, (başka bir birleşimin sol alt olarak görünen JOIN), daha kolay tek bir SQL SELECT deyimi içinde düzleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="8c851-125">Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8c851-125">For example, consider the following query command tree:</span></span>

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="8c851-126">Bu doğru içine çevrilebilir:</span><span class="sxs-lookup"><span data-stu-id="8c851-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="8c851-127">Ancak, sol olmayan Sırt birleştirmeler kolayca düzleştirilmiş kullanılamaz ve bunları düzleştirilecek denememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8c851-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="8c851-128">Örneğin, aşağıdaki sorguyu birleşimlerde ağaç komut:</span><span class="sxs-lookup"><span data-stu-id="8c851-128">For example, the joins in the following query command tree:</span></span>

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="8c851-129">Bir alt sorgusu ile SQL SELECT deyimi çevrilmesi.</span><span class="sxs-lookup"><span data-stu-id="8c851-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="8c851-130">Giriş diğer adı yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="8c851-130">Input Alias Redirecting</span></span>

<span data-ttu-id="8c851-131">Giriş diğer adı yeniden yönlendirme açıklamak için DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, ilişkisel ifadelerin yapısı göz önünde bulundurun ve DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="8c851-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="8c851-132">Bu tür her bir giriş koleksiyonu tanımlayan bir veya daha fazla giriş özelliği vardır ve her bir girişe karşılık gelen bir bağlama değişken her giriş öğesinin bir koleksiyon geçişi sırasında temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c851-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="8c851-133">Bağlama değişkeni girişi öğesinde, örneğin bir DbFilterExpression koşul özelliğini ya da projeksiyon özelliği bir DbProjectExpression söz konusu olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c851-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="8c851-134">Daha fazla ilişkisel ifade düğümleri tek bir SQL SELECT deyimi içinde toplama ve onu kullanan bağlama değişkeni bir ilişkisel ifade kullanıldı (örneğin bir DbProjectExpression yansıtma özelliğinin bir parçası) parçası olan bir ifade değerlendirme zaman olabilir birden fazla ifade bağlamaları tek bir ölçüde yönlendirilmesi yaptığınız gibi giriş diğer adı ile aynı olmaması.</span><span class="sxs-lookup"><span data-stu-id="8c851-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="8c851-135">Bu sorun, diğer adını yeniden adlandırma adı verilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="8c851-136">Bu konudaki ilk örnek göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8c851-136">Consider the first example in this topic.</span></span> <span data-ttu-id="8c851-137">Naïve çeviri yapılması ve projeksiyon a.x (DbPropertyExpression (bir, bir x)) çevirme, bunun içine çevirmek doğru olup olmadığını `a.x` çünkü diğer adlı giriş bağlama değişkeni eşleştirmek için "a" olarak sahip olabiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="8c851-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="8c851-138">Ancak, her iki düğüm ile tek bir SQL SELECT deyimi toplanırken içine aynı DbPropertyExpression çevirmek ihtiyacınız `b.x`, "b" ile diğer adlı giriş süredir.</span><span class="sxs-lookup"><span data-stu-id="8c851-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="8c851-139">Diğer ad düzleştirme katılın</span><span class="sxs-lookup"><span data-stu-id="8c851-139">Join Alias Flattening</span></span>

<span data-ttu-id="8c851-140">Diğer ilişkisel içindeki herhangi bir ifade bir çıktı komut ağacı, her biri girişleri birine karşılık gelen iki sütunlardan oluşan bir satır olduğundan bir sonuç türü DbJoinExpression çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8c851-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="8c851-141">Birleştirme sonucu kaynaklanan bir skaler özelliğe erişmek için yerleşik bir DbPropertyExpression başka bir DbPropertyExpression olur.</span><span class="sxs-lookup"><span data-stu-id="8c851-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="8c851-142">Örnek 2 ve 3. örnek "b.c.y" içinde "a.b.y" örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="8c851-143">Ancak karşılık gelen SQL deyimlerinde bunlar "b.y" adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8c851-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="8c851-144">Bu yeniden yumuşatma, diğer ad birleştirme düzleştirme çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8c851-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="8c851-145">Sütun adı ve uzantısı diğer adını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="8c851-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="8c851-146">Girişleri katılan tüm sütunları bir ad çakışması oluşabilir, listelenirken bir projeksiyon ile tamamlanması bir birleşimi olan bir SQL SELECT sorgu varsa, bir giriş olarak birden fazla aynı sütun adı sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="8c851-147">Çakışma önlemek için sütun için farklı bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c851-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="8c851-148">Ayrıca, birleşimler düzleştirme, tablo (veya alt sorgular) adlandırılması gerek bu durum çakışan diğer adlar, olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="8c851-149">SELECT önlemek \*</span><span class="sxs-lookup"><span data-stu-id="8c851-149">Avoid SELECT \*</span></span>

<span data-ttu-id="8c851-150">Kullanmayın `SELECT *` temel tabloları seçin.</span><span class="sxs-lookup"><span data-stu-id="8c851-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="8c851-151">Depolama modelinde bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama yalnızca veritabanı tablodaki sütunların bir alt kümesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="8c851-152">Bu durumda, `SELECT *` hatalı bir sonuç üretebilir.</span><span class="sxs-lookup"><span data-stu-id="8c851-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="8c851-153">Bunun yerine, bir katılımcı ifadenin sonuç türü sütun adları kullanarak katılan tüm sütunları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c851-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="8c851-154">Yeniden ifade</span><span class="sxs-lookup"><span data-stu-id="8c851-154">Reuse of Expressions</span></span>

<span data-ttu-id="8c851-155">İfadeleri yeniden geçirilen sorgu komut ağacı [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c851-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8c851-156">Her bir ifade yalnızca bir kez sorgu komutu ağaçta görünür varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="8c851-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="8c851-157">Eşleme ilkel türler</span><span class="sxs-lookup"><span data-stu-id="8c851-157">Mapping Primitive Types</span></span>

<span data-ttu-id="8c851-158">Tüm olası değerler uyacak şekilde, kavramsal (EDM) tür sağlayıcısı türleri eşlerken geniş türü (Int32) eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c851-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="8c851-159">Ayrıca, BLOB türleri gibi birçok işlem için kullanılamaz türleriyle eşleme önlemek (örneğin, `ntext` SQL Server).</span><span class="sxs-lookup"><span data-stu-id="8c851-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c851-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c851-160">See also</span></span>

- [<span data-ttu-id="8c851-161">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="8c851-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
