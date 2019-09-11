---
title: Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 9859c7df941ae6681c991001e0d1e5a50c7ffc60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855009"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="a02a7-102">Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a02a7-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="a02a7-103">Çıktı sorgu komut ağaçları SQL 'de ifade edilecek şekilde daha yakından model sorguları.</span><span class="sxs-lookup"><span data-stu-id="a02a7-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="a02a7-104">Ancak, bir çıkış komut ağacından SQL oluştururken sağlayıcı yazıcılarında ilgili bazı yaygın sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="a02a7-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="a02a7-105">Bu konuda bu sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a02a7-105">This topic discusses these challenges.</span></span> <span data-ttu-id="a02a7-106">Bir sonraki konu başlığında, örnek sağlayıcı bu güçlükleri nasıl ele alınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="a02a7-107">SQL SELECT deyiminde DbExpression düğümlerini gruplandırma</span><span class="sxs-lookup"><span data-stu-id="a02a7-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="a02a7-108">Tipik bir SQL ifadesinin aşağıdaki şekle ait iç içe bir yapısı vardır:</span><span class="sxs-lookup"><span data-stu-id="a02a7-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="a02a7-109">Bir veya daha fazla yan tümce boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="a02a7-110">İç içe bir SELECT ifadesinin herhangi bir satırda oluşması olabilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="a02a7-111">Bir SQL SELECT ifadesine sorgu komut ağacının olası bir çevirisi, her ilişkisel operatör için bir alt sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a02a7-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="a02a7-112">Bununla birlikte, okunması zor olan, gereksiz iç sorgulara yol açacaktı.</span><span class="sxs-lookup"><span data-stu-id="a02a7-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="a02a7-113">Bazı veri depolarında sorgu kötü bir şekilde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="a02a7-114">Örnek olarak, aşağıdaki sorgu komut ağacını göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="a02a7-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="a02a7-115">Verimsiz bir çeviri şunları üretir:</span><span class="sxs-lookup"><span data-stu-id="a02a7-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="a02a7-116">Her ilişkisel ifade düğümünün yeni bir SQL SELECT deyimi haline geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a02a7-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="a02a7-117">Bu nedenle, doğruluğu korurken çok sayıda ifade düğümünü tek bir SQL SELECT deyimine mümkün olduğunca toplamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="a02a7-118">Yukarıda sunulan örnek için bu tür toplamın sonucu şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a02a7-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="a02a7-119">SQL SELECT deyimindeki birleştirmeleri düzleştirme</span><span class="sxs-lookup"><span data-stu-id="a02a7-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="a02a7-120">Birden çok düğümü tek bir SQL SELECT deyimi içinde birleştiren bir durum, birden çok JOIN ifadesini tek bir SQL SELECT deyimi içine toplayarak.</span><span class="sxs-lookup"><span data-stu-id="a02a7-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="a02a7-121">DbJoinExpression iki giriş arasındaki tek bir birleştirmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a02a7-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="a02a7-122">Ancak, tek bir SQL SELECT ifadesinin parçası olarak birden fazla JOIN belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="a02a7-123">Bu durumda, birleştirmeler belirtilen sırada gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="a02a7-124">Sol sırt birleşimleri (başka bir birleşimin sol alt öğesi olarak görünen birleşimler), tek bir SQL SELECT ifadesinde daha kolay bir şekilde düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="a02a7-125">Örneğin, aşağıdaki sorgu komut ağacını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a02a7-125">For example, consider the following query command tree:</span></span>

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

<span data-ttu-id="a02a7-126">Bu, öğesine doğru şekilde çevrilebilir:</span><span class="sxs-lookup"><span data-stu-id="a02a7-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="a02a7-127">Ancak, sol olmayan sırtı birleştirmeleri kolayca düzleştirilmez ve bunları düzleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a02a7-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="a02a7-128">Örneğin, aşağıdaki sorgu komut ağacındaki birleşimler:</span><span class="sxs-lookup"><span data-stu-id="a02a7-128">For example, the joins in the following query command tree:</span></span>

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

<span data-ttu-id="a02a7-129">Alt sorgu ile bir SQL SELECT ifadesine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="a02a7-130">Giriş diğer adı yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a02a7-130">Input Alias Redirecting</span></span>

<span data-ttu-id="a02a7-131">Girdi diğer adını yeniden yönlendirmeyi açıklamak için, DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression gibi ilişkisel ifadelerin yapısını göz önünde bulundurun. DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="a02a7-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="a02a7-132">Bu türlerin her birinde, bir giriş koleksiyonu tanımlayan bir veya daha fazla giriş özelliği bulunur ve her girişe karşılık gelen bir bağlama değişkeni, bu girişin her bir öğesini bir koleksiyon çapraz geçişi sırasında temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a02a7-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="a02a7-133">Bağlama değişkeni, giriş öğesine başvururken, örneğin bir DbFilterExpression 'ın koşul özelliğindeki veya bir DbProjectExpression 'ın Projection özelliğinin kullanıldığı durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a02a7-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="a02a7-134">Birden fazla ilişkisel ifade düğümünü tek bir SQL SELECT deyimine toplayarak ve ilişkisel bir ifadenin parçası olan bir ifadeyi değerlendirirken (örneğin, bir DbProjectExpression 'ın Projection özelliğinin bir parçası olarak), kullandığı bağlama değişkeni birden çok ifade bağlaması tek bir ölçüde yönlendirilmek zorunda olacağından, girişin diğer adıyla aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="a02a7-135">Bu soruna yeniden adlandırma adı verilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="a02a7-136">Bu konudaki ilk örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a02a7-136">Consider the first example in this topic.</span></span> <span data-ttu-id="a02a7-137">Naïve çevirisini yapar ve projeksiyonu bir. x (DbPropertyExpression (a, x)) çeviriyorsa, bağlama değişkeni ile eşleşmesi için girişin "a `a.x` " olarak başka bir ad alanı olduğu için ' a çevirmek doğru olur.</span><span class="sxs-lookup"><span data-stu-id="a02a7-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="a02a7-138">Ancak, hem düğümleri tek bir SQL SELECT deyimi içinde toplayarak, girişin "b" ile başka bir ad alanı olduğu için aynı `b.x`DbPropertyExpression ' a çevirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="a02a7-139">Diğer ad düzleştirmeyi Birleştir</span><span class="sxs-lookup"><span data-stu-id="a02a7-139">Join Alias Flattening</span></span>

<span data-ttu-id="a02a7-140">Bir çıkış komut ağacındaki diğer tüm ilişkisel deyimlerden farklı olarak, DbJoinExpression, her biri girdilerden birine karşılık gelen iki sütundan oluşan bir satır olan sonuç türünü çıktı.</span><span class="sxs-lookup"><span data-stu-id="a02a7-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="a02a7-141">Bir DbPropertyExpression, bir birleşimden kaynaklanan skaler bir özelliğe erişmek üzere yapılandırıldığında, başka bir DbPropertyExpression üzerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a02a7-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="a02a7-142">Örnek 2 ' de "a. b. y" ve örnek 3 ' te "b. c. y" verilebilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="a02a7-143">Bununla birlikte, bunlara karşılık gelen SQL deyimlerine "b. y" olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="a02a7-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="a02a7-144">Bu yeniden takma ad, JOIN diğer adı düzleştirme olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a02a7-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="a02a7-145">Sütun adı ve uzantı diğer adı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="a02a7-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="a02a7-146">Bir birleşime sahip bir SQL SELECT sorgusunun projeksiyon ile tamamlanması gerekiyorsa, tüm katılan sütunları girdilerden Numaralandırırken, birden fazla girişin aynı sütun adına sahip olabileceğinden bir ad çakışması meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="a02a7-147">Çarpışmadan kaçınmak için sütun için farklı bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="a02a7-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="a02a7-148">Ayrıca, birleştirmeleri düzleştirme sırasında, katılım tabloları (veya alt sorgular), bu durumda yeniden adlandırılması gereken diğer adları çarpışmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="a02a7-149">SELECT \* kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a02a7-149">Avoid SELECT \*</span></span>

<span data-ttu-id="a02a7-150">Temel tablolardan seçim `SELECT *` yapmak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a02a7-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="a02a7-151">Bir Entity Framework uygulamasındaki depolama modeli yalnızca veritabanı tablosundaki sütunların bir alt kümesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-151">The storage model in an Entity Framework application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="a02a7-152">Bu durumda, `SELECT *` yanlış sonuç verebilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="a02a7-153">Bunun yerine, katılan ifadelerin sonuç türünden sütun adlarını kullanarak tüm katılan sütunları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="a02a7-154">Ifadelerin yeniden kullanılması</span><span class="sxs-lookup"><span data-stu-id="a02a7-154">Reuse of Expressions</span></span>

<span data-ttu-id="a02a7-155">İfadeler, Entity Framework geçirilen sorgu komut ağacında yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-155">Expressions may be reused in the query command tree passed by the Entity Framework.</span></span> <span data-ttu-id="a02a7-156">Sorgu komut ağacında her bir ifadenin yalnızca bir kez göründüğünü varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="a02a7-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="a02a7-157">Temel türleri eşleme</span><span class="sxs-lookup"><span data-stu-id="a02a7-157">Mapping Primitive Types</span></span>

<span data-ttu-id="a02a7-158">Kavramsal (EDM) türlerini sağlayıcı türlerine eşlerken, tüm olası değerlerin sığması için en geniş türe (Int32) eşleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a02a7-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="a02a7-159">Ayrıca, blob türleri gibi çok sayıda işlem için kullanılamayan türlere eşlemektan kaçının (örneğin, `ntext` SQL Server).</span><span class="sxs-lookup"><span data-stu-id="a02a7-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="a02a7-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a02a7-160">See also</span></span>

- [<span data-ttu-id="a02a7-161">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="a02a7-161">SQL Generation</span></span>](sql-generation.md)
