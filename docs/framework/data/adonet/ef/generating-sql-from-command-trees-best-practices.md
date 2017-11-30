---
title: "SQL komut ağaçlarını - en iyi uygulamaları oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06d2711d9dac203645c127fa86581a9888db3cb1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="832e4-102">SQL komut ağaçlarını - en iyi uygulamaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="832e4-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="832e4-103">Çıktı sorgu komut ağaçlarını yakından sorguları SQL'de ifade model.</span><span class="sxs-lookup"><span data-stu-id="832e4-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="832e4-104">Ancak, SQL bir çıkış komut ağacından oluştururken sağlayıcısı yazıcılarına ilişkin ortak bazı zorluklar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="832e4-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="832e4-105">Bu konuda bu zorluklar anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="832e4-105">This topic discusses these challenges.</span></span> <span data-ttu-id="832e4-106">Sonraki konusundaki örnek sağlayıcısı bu güçlükleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="832e4-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="832e4-107">Grup DbExpression düğümlerini SQL SELECT deyimi</span><span class="sxs-lookup"><span data-stu-id="832e4-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="832e4-108">Tipik bir SQL deyimi aşağıdaki şeklin iç içe geçmiş bir yapı vardır:</span><span class="sxs-lookup"><span data-stu-id="832e4-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="832e4-109">Bir veya daha fazla yan tümceleri boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="832e4-110">İç içe geçmiş bir SELECT deyimi satırları hiçbirinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="832e4-111">Olası bir sorgu komut ağacı çeviri SQL SELECT deyimi içinde her ilişkisel işleci için bir alt sorgu üretir.</span><span class="sxs-lookup"><span data-stu-id="832e4-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="832e4-112">Ancak, okunması zor olacaktır gereksiz iç içe alt sorgulara yol açar.</span><span class="sxs-lookup"><span data-stu-id="832e4-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="832e4-113">Bazı veri depoları sorgu kötü gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="832e4-114">Örnek olarak, aşağıdaki sorgu komut ağacı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="832e4-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="832e4-115">Bir verimsiz çevirisini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="832e4-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="832e4-116">Her ilişkisel ifadesi düğüm yeni bir SQL SELECT deyimi olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="832e4-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="832e4-117">Bu nedenle, doğruluk korurken tek bir SQL SELECT deyimi içinde mümkün olduğu kadar ifade düğümleri toplamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="832e4-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="832e4-118">Yukarıda gösterilen örnek için bu tür bir toplama sonucu olacaktır:</span><span class="sxs-lookup"><span data-stu-id="832e4-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="832e4-119">Bir SQL SELECT deyimi içinde birleştirmeler düzleştirme</span><span class="sxs-lookup"><span data-stu-id="832e4-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="832e4-120">Tek bir SQL SELECT deyimine birden çok düğüm toplayarak, bir durumda, tek bir SQL SELECT deyimine birden fazla birleşim ifadelere toplama.</span><span class="sxs-lookup"><span data-stu-id="832e4-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="832e4-121">DbJoinExpression iki girdi arasında tek bir birleşim temsil eder.</span><span class="sxs-lookup"><span data-stu-id="832e4-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="832e4-122">Ancak, tek bir SQL SELECT deyimi bir parçası olarak, birden fazla birleşim belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="832e4-123">Bu durumda birleştirmeler belirtilen sırayla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="832e4-124">Sırt birleştirmeler sol, (başka bir birleştirme sol alt olarak görünür birleştirmeler) daha kolay tek bir SQL SELECT deyimine düzleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="832e4-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="832e4-125">Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="832e4-125">For example, consider the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="832e4-126">Bu doğru içine çevrilebilir:</span><span class="sxs-lookup"><span data-stu-id="832e4-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="832e4-127">Ancak, sol olmayan Sırt birleştirmeler kolayca düzleştirilmiş olamaz ve değil bunları düzleştirmek denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="832e4-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="832e4-128">Örneğin, aşağıdaki sorguyu birleşimlerde ağaç komut:</span><span class="sxs-lookup"><span data-stu-id="832e4-128">For example, the joins in the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="832e4-129">Bir alt sorgu ile SQL SELECT deyimi çevrilmesi.</span><span class="sxs-lookup"><span data-stu-id="832e4-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="832e4-130">Diğer ad yönlendirme giriş</span><span class="sxs-lookup"><span data-stu-id="832e4-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="832e4-131">Giriş diğer adı yeniden yönlendirme açıklamak için DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, toplama, DbApplyExpression, gibi ilişkisel ifadeleri yapısını göz önünde bulundurun ve DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="832e4-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="832e4-132">Bu türlerinin her biri bir giriş koleksiyonu açıklayan bir veya daha fazla giriş özellikleri vardır ve her giriş için karşılık gelen bir bağlama değişken her öğe bu giriş, koleksiyon geçişi sırasında temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="832e4-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="832e4-133">Bağlama değişkeni girişi öğesinde, örneğin bir DbFilterExpression koşulu özelliğinin ya da bir DbProjectExpression projeksiyon özelliği için söz konusu olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="832e4-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="832e4-134">Daha fazla ilişkisel ifade düğümleri tek bir SQL SELECT deyimine toplayarak ve kullandığı bağlama değişkeni ilişkisel ifade (örneğin bir DbProjectExpression projeksiyon özelliğinin bir parçası) parçası olan bir ifade değerlendirme zaman olabilir birden çok ifade bağlamaları tek bir kapsam için yeniden yönlendirilmesi yaptığınız gibi giriş diğer adı ile aynı olması.</span><span class="sxs-lookup"><span data-stu-id="832e4-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="832e4-135">Bu sorun, diğer yeniden adlandırma adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="832e4-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="832e4-136">Bu konudaki ilk örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="832e4-136">Consider the first example in this topic.</span></span> <span data-ttu-id="832e4-137">Naïve çeviri yapılması ve projeksiyon a.x (DbPropertyExpression (x)) çevirme, onu içine çevirmek doğru olup olmadığını `a.x` biz diğer giriş bağlama değişkeni eşleştirmek için "a" olarak olduğundan.</span><span class="sxs-lookup"><span data-stu-id="832e4-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="832e4-138">Bununla birlikte, her iki düğüm tek bir SQL SELECT deyimine toplanırken içine aynı DbPropertyExpression çevirmek ihtiyacınız `b.x`giriş diğer adı "b" bırakıldı gibi.</span><span class="sxs-lookup"><span data-stu-id="832e4-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="832e4-139">Diğer ad düzleştirme katılma</span><span class="sxs-lookup"><span data-stu-id="832e4-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="832e4-140">Diğer ilişkisel içindeki herhangi bir ifade farklı olarak bir çıkış komut ağacı, her biri girişleri birine karşılık gelen iki sütunlarının oluşan bir satır, bir sonuç türü DbJoinExpression çıkarır.</span><span class="sxs-lookup"><span data-stu-id="832e4-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="832e4-141">Bir birleştirme sonucu kaynaklanan skaler bir özelliğe erişmek için bir DbPropertyExpresssion yerleşik başka bir DbPropertyExpresssion olur.</span><span class="sxs-lookup"><span data-stu-id="832e4-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="832e4-142">Örnek 2 ve 3 örnekte "b.c.y" "a.b.y" örnek verilebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="832e4-143">Ancak karşılık gelen SQL deyimlerinde bunlar "b.y" adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="832e4-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="832e4-144">Bu yeniden yumuşatma diğer birleştirme düzleştirme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="832e4-145">Sütun adı ve uzantı Alias yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="832e4-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="832e4-146">Birden fazla olarak girişleri katılan tüm sütunları bir ad çakışması ortaya çıkabilir, numaralandırılırken bir yansıtma ile tamamlanacak bir birleşimi olan bir SQL SELECT sorgu varsa, bir giriş aynı sütun adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="832e4-147">Çakışma önlemek için sütun için farklı bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="832e4-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="832e4-148">Ayrıca, birleştirmeler düzleştirme, katılımcı tabloları (veya alt sorgular) yeniden adlandırılması gerek bu durumda yazılımlarla çakışma diğer adlar, olabilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="832e4-149">SELECT kaçının *</span><span class="sxs-lookup"><span data-stu-id="832e4-149">Avoid SELECT *</span></span>  
 <span data-ttu-id="832e4-150">Kullanmayın `SELECT *` temel tablolardan seçin.</span><span class="sxs-lookup"><span data-stu-id="832e4-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="832e4-151">Depolama modelinde bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama veritabanı tabloda yer alan bir sütun alt kümesini yalnızca içerebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="832e4-152">Bu durumda, `SELECT *` hatalı bir sonuç üretebilir.</span><span class="sxs-lookup"><span data-stu-id="832e4-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="832e4-153">Bunun yerine, katılımcı ifadeler sonuç türü sütun adlarından kullanarak tüm katılımcı sütunları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="832e4-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="832e4-154">İfadeler kullanılmasını</span><span class="sxs-lookup"><span data-stu-id="832e4-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="832e4-155">İfadeler yeniden kullanılabilir geçirilen sorgu komut ağacındaki [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="832e4-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="832e4-156">Her bir ifadenin yalnızca bir kez sorgu komutu ağacında görünür varsayalım değil.</span><span class="sxs-lookup"><span data-stu-id="832e4-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="832e4-157">İlkel türler eşleme</span><span class="sxs-lookup"><span data-stu-id="832e4-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="832e4-158">Tüm olası değerler uyacak şekilde, kavramsal (EDM) türleri sağlayıcısı türlerinin eşlerken, geniş türü (Int32) eşlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="832e4-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="832e4-159">Ayrıca, BLOB türleri gibi birçok işlem için kullanılamaz türler için eşleme kaçının (örneğin, `ntext` içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="832e4-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832e4-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="832e4-160">See Also</span></span>  
 [<span data-ttu-id="832e4-161">SQL oluşturma</span><span class="sxs-lookup"><span data-stu-id="832e4-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
