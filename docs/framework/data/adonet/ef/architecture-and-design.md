---
title: Mimari ve Tasarım
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 35fbc39db23a2b08ab926e122d2f1eb1806a369b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040017"
---
# <a name="architecture-and-design"></a><span data-ttu-id="1bd70-102">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="1bd70-102">Architecture and Design</span></span>

<span data-ttu-id="1bd70-103">[Örnek sağlayıcıdaki](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) SQL oluşturma modülü, komut ağacını temsil eden ifade ağacında bir ziyaretçi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="1bd70-104">Oluşturma, ifade ağacının tek bir geçişinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-104">The generation is done in a single pass over the expression tree.</span></span>

<span data-ttu-id="1bd70-105">Ağacın düğümleri aşağıdan yukarıya işlenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="1bd70-106">İlk olarak, bir ara yapı oluşturulur: Sqlselectdeyimin veya SqlBuilder, her ikisi de ısqlfragment.</span><span class="sxs-lookup"><span data-stu-id="1bd70-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="1bd70-107">Ardından, dize SQL deyimleri Bu yapıdan üretilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="1bd70-108">Ara yapının iki nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="1bd70-108">There are two reasons for the intermediate structure:</span></span>

- <span data-ttu-id="1bd70-109">Mantıksal olarak, bir SQL SELECT deyimleri sıra dışında doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="1bd70-110">FROM yan tümcesine katılan düğümler WHERE, GROUP BY ve ORDER BY yan tümcesinde yer alan düğümlerden önce ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>

- <span data-ttu-id="1bd70-111">Diğer adları yeniden adlandırmak için, yeniden adlandırma sırasında çarpışmalardan kaçınmak için kullanılan tüm diğer adları tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1bd70-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="1bd70-112">SqlBuilder 'daki yeniden adlandırma seçimlerini ertelemek için, yeniden adlandırma aday olan sütunları temsil etmek üzere sembol nesneleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bd70-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>

<span data-ttu-id="1bd70-113">![Çizimindeki](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="1bd70-113">![Diagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>

<span data-ttu-id="1bd70-114">İlk aşamada, ifade ağacını ziyaret ederken ifadeler Sqlselectdeyimlerine gruplanır, birleştirmeler düzleştirilir ve birleştirme diğer adları düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="1bd70-115">Bu geçiş sırasında, sembol nesneleri yeniden adlandırılabilir sütunları veya girdi diğer adlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd70-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>

<span data-ttu-id="1bd70-116">İkinci aşamada, gerçek dizeyi üretirken diğer adlar yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>

## <a name="data-structures"></a><span data-ttu-id="1bd70-117">Veri yapıları</span><span class="sxs-lookup"><span data-stu-id="1bd70-117">Data Structures</span></span>

<span data-ttu-id="1bd70-118">Bu bölümde, bir SQL açıklaması oluşturmak için kullandığınız [örnek sağlayıcıda](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) kullanılan türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>

### <a name="isqlfragment"></a><span data-ttu-id="1bd70-119">Isqlfragment</span><span class="sxs-lookup"><span data-stu-id="1bd70-119">ISqlFragment</span></span>

<span data-ttu-id="1bd70-120">Bu bölüm, iki amaca hizmet eden ısqlfragment arabirimini uygulayan sınıfları ele almaktadır:</span><span class="sxs-lookup"><span data-stu-id="1bd70-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>

- <span data-ttu-id="1bd70-121">Tüm ziyaretçi yöntemleri için ortak bir dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="1bd70-121">A common return type for all the visitor methods.</span></span>

- <span data-ttu-id="1bd70-122">Son SQL dizesini yazmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-122">Gives a method to write the final SQL string.</span></span>

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a><span data-ttu-id="1bd70-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="1bd70-123">SqlBuilder</span></span>

<span data-ttu-id="1bd70-124">SqlBuilder, StringBuilder 'a benzeyen son SQL dizesi için bir cihaz topluyor.</span><span class="sxs-lookup"><span data-stu-id="1bd70-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="1bd70-125">Bu, son SQL oluşturan dizelerden oluşur ve dizelere dönüştürülebilen ısqlparçaların yanı da.</span><span class="sxs-lookup"><span data-stu-id="1bd70-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a><span data-ttu-id="1bd70-126">Sqlselectdeyimin</span><span class="sxs-lookup"><span data-stu-id="1bd70-126">SqlSelectStatement</span></span>

<span data-ttu-id="1bd70-127">Sqlselectdeyim, "SELECT..." şeklinin kurallı bir SQL SELECT ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd70-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="1bd70-128">Kaynak..</span><span class="sxs-lookup"><span data-stu-id="1bd70-128">FROM  ..</span></span> <span data-ttu-id="1bd70-129">WHERE...</span><span class="sxs-lookup"><span data-stu-id="1bd70-129">WHERE …</span></span> <span data-ttu-id="1bd70-130">GRUPLANDıRMA ÖLÇÜTÜ...</span><span class="sxs-lookup"><span data-stu-id="1bd70-130">GROUP BY …</span></span> <span data-ttu-id="1bd70-131">SıRALAMA ÖLÇÜTÜ ".</span><span class="sxs-lookup"><span data-stu-id="1bd70-131">ORDER BY".</span></span>

<span data-ttu-id="1bd70-132">Her SQL yan tümcesi bir StringBuilder tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="1bd70-133">Ayrıca, DISTINCT 'in belirtildiğinden ve deyimin en üst olup olmadığını izler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="1bd70-134">Deyimi en üstte değilse, deyimin bir TOP yan tümcesi da yoksa ORDER BY yan tümcesi atlanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>

<span data-ttu-id="1bd70-135">FromExtents, SELECT ifadesiyle ilgili girişlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="1bd70-136">Genellikle yalnızca bir öğe vardır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-136">There is usually just one element in this.</span></span> <span data-ttu-id="1bd70-137">Birleşimler için SELECT deyimlerinin geçici olarak birden fazla öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-137">SELECT statements for joins may temporarily have more than one element.</span></span>

<span data-ttu-id="1bd70-138">SELECT deyimleri bir JOIN düğümü tarafından oluşturulduysa, Sqlselectdeyimde Alljoinpackages içinde birleşimde düzleştirilmiş tüm uzantıların bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="1bd70-139">OuterExtents, Sqlselectdeyimin dış başvurularını temsil eder ve giriş diğer adı yeniden adlandırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>

```csharp
internal sealed class SqlSelectStatement : ISqlFragment {
   internal bool IsDistinct { get, set };
   internal bool IsTopMost

   internal List<Symbol> AllJoinExtents { get, set };
   internal List<Symbol> FromExtents { get};
   internal Dictionary<Symbol, bool> OuterExtents { get};

   internal TopClause Top { get, set };

   internal SqlBuilder Select {get};
   internal SqlBuilder From
   internal SqlBuilder Where
   internal SqlBuilder GroupBy
   public SqlBuilder OrderBy
}
```

#### <a name="topclause"></a><span data-ttu-id="1bd70-140">Topyan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1bd70-140">TopClause</span></span>

<span data-ttu-id="1bd70-141">Topyan tümcesi bir Sqlselectdeyiminde ÜSTTEKI ifadeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd70-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="1bd70-142">TopCount özelliği, kaç tane en fazla satırın seçilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="1bd70-143">WithTies true olduğunda, topyan tümcesi bir DbLimitExpression tarafından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-143">When WithTies is true, the TopClause was built from a DbLimitExpression.</span></span>

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a><span data-ttu-id="1bd70-144">Simgeleri</span><span class="sxs-lookup"><span data-stu-id="1bd70-144">Symbols</span></span>

<span data-ttu-id="1bd70-145">Sembol ile ilgili sınıflar ve sembol tablosu, giriş diğer adı yeniden adlandırma, JOIN diğer adı düzleştirme ve sütun diğer adı yeniden adlandırma işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>

<span data-ttu-id="1bd70-146">Sembol sınıfı bir kapsamı, iç içe bir SELECT ifadesini veya bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd70-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="1bd70-147">Bu, oluşturulduktan sonra yeniden adlandırmaya izin vermek için gerçek bir diğer ad yerine kullanılır ve temsil ettiği Yapıt (tür gibi) için ek bilgiler de taşır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>

```csharp
class Symbol : ISqlFragment {
   internal Dictionary<string, Symbol> Columns {get}
   internal bool NeedsRenaming {get, set}
   internal bool IsUnnest {get, set}   //not used

   public string Name{get}
   public string NewName {get,set}
   internal TypeUsage Type {get, set}

   public Symbol(string name, TypeUsage type)
}
```

<span data-ttu-id="1bd70-148">Ad, temsil edilen kapsam, iç içe SELECT açıklaması veya bir sütun için özgün diğer adı depolar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>

<span data-ttu-id="1bd70-149">NewName, SQL SELECT ifadesinde kullanılacak diğer adı depolar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="1bd70-150">İlk olarak ad olarak ayarlanır ve yalnızca son dize sorgusu oluşturulurken gerekliyse yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>

<span data-ttu-id="1bd70-151">Tür yalnızca kapsamları ve iç içe geçmiş SELECT deyimlerini temsil eden semboller için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>

#### <a name="symbolpair"></a><span data-ttu-id="1bd70-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="1bd70-152">SymbolPair</span></span>

<span data-ttu-id="1bd70-153">SymbolPair sınıfı, kayıt düzleştirmeyi adresleyen.</span><span class="sxs-lookup"><span data-stu-id="1bd70-153">The SymbolPair class addresses record flattening.</span></span>

<span data-ttu-id="1bd70-154">D (v, "J3. J2. J1. a. x"), burada v 'nin bir VarRef, J1, J2, J3 birleşmesi, bir uzantısı ve x bir sütun olduğu bir özellik ifadesi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1bd70-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>

<span data-ttu-id="1bd70-155">Bu, sonunda {j '} içine çevrilmelidir. {x '}.</span><span class="sxs-lookup"><span data-stu-id="1bd70-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="1bd70-156">Kaynak alanı, bir JOIN ifadesini temsil eden en dıştaki SqlStatement 'yi temsil eder (J2); Bu her zaman bir JOIN simgedir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="1bd70-157">Sütun alanı, JOIN olmayan bir sembolünde durduruluncaya kadar bir JOIN simgesinden bir sonrakine gider.</span><span class="sxs-lookup"><span data-stu-id="1bd70-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="1bd70-158">Bu, bir DbPropertyExpression ziyaret edildiğinde döndürülür, ancak bir SqlBuilder 'a hiçbir zaman eklenmez.</span><span class="sxs-lookup"><span data-stu-id="1bd70-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a><span data-ttu-id="1bd70-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="1bd70-159">JoinSymbol</span></span>

<span data-ttu-id="1bd70-160">Bir JOIN sembolü, bir JOIN veya JOIN girişi ile iç içe bir SELECT ifadesini temsil eden bir simgedir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>

```csharp
internal sealed class JoinSymbol : Symbol {
   internal List<Symbol> ColumnList {get, set}
   internal List<Symbol> ExtentList {get}
   internal List<Symbol> FlattenedExtentList {get, set}
   internal Dictionary<string, Symbol> NameToExtent {get}
   internal bool IsNestedJoin {get, set}

   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)
}
```

<span data-ttu-id="1bd70-161">ColumnList, SELECT yan tümcesindeki sütunların listesini temsil eder ve bu sembol bir SQL SELECT ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bd70-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="1bd70-162">Extenlıst, SELECT yan tümcesindeki uzantıların listesidir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="1bd70-163">Birleşimin en üst düzeyde düzleştirilmiş birden çok uzantısı varsa FlattenedExtentList, uzantı diğer adlarının doğru şekilde yeniden adlandırıldığından emin olmak için kapsamları izler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>

<span data-ttu-id="1bd70-164">NameToExtent, Extenlıst içindeki tüm kapsamları sözlük olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="1bd70-165">Bir JoinSymbol 'ın sıradan bir JOIN simgesi mi yoksa buna karşılık gelen bir Sqlselectdeyimmi olduğunu anlamak için ınestedjoın kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>

<span data-ttu-id="1bd70-166">Tüm listeler tam olarak bir kez ayarlanır ve ardından aramalar veya numaralandırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>

#### <a name="symboltable"></a><span data-ttu-id="1bd70-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="1bd70-167">SymbolTable</span></span>

<span data-ttu-id="1bd70-168">SymbolTable, değişken adlarını simgelere çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="1bd70-169">SymbolTable, her kapsam için yeni bir girdiye sahip bir yığın olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="1bd70-170">Arama, bir giriş bulunana kadar yığının en üstünden en alta doğru arar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

<span data-ttu-id="1bd70-171">SQL oluşturma modülünün bir örneği başına yalnızca bir SymbolTable vardır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="1bd70-172">Kapsamlar, her ilişkisel düğüm için girilir ve çıkış yaptı.</span><span class="sxs-lookup"><span data-stu-id="1bd70-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="1bd70-173">Daha önceki kapsamlardaki tüm semboller, aynı ada sahip diğer semboller tarafından gizlenmediği takdirde daha sonraki kapsamlar tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>

### <a name="global-state-for-the-visitor"></a><span data-ttu-id="1bd70-174">Ziyaretçi için genel durum</span><span class="sxs-lookup"><span data-stu-id="1bd70-174">Global State for the Visitor</span></span>

<span data-ttu-id="1bd70-175">Diğer adların ve sütunların yeniden adlandırılmasına yardımcı olmak için, sorgu ağacının ilk geçişinde kullanılan tüm sütun adlarının (AllColumnNames) ve uzantı diğer adlarının (AllExtentNames) bir listesini saklayın.</span><span class="sxs-lookup"><span data-stu-id="1bd70-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="1bd70-176">Sembol tablosu, değişken adlarını semboller olarak çözümler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="1bd70-177">IsVarRefSingle yalnızca doğrulama amacıyla kullanılır, kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>

<span data-ttu-id="1bd70-178">Currentselectdeyimin ve ıparentajoın aracılığıyla kullanılan iki yığın, ziyaretçi deseninin parametreleri geçememize izin vermediğinden, "Parameters" öğesini üstten alt düğümlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>

```csharp
internal Dictionary<string, int> AllExtentNames {get}
internal Dictionary<string, int> AllColumnNames {get}
SymbolTable symbolTable = new SymbolTable();
bool isVarRefSingle = false;

Stack<SqlSelectStatement> selectStatementStack;
private SqlSelectStatement CurrentSelectStatement{get}

Stack<bool> isParentAJoinStack;
private bool IsParentAJoin{get}
```

## <a name="common-scenarios"></a><span data-ttu-id="1bd70-179">Yaygın senaryolar</span><span class="sxs-lookup"><span data-stu-id="1bd70-179">Common Scenarios</span></span>

<span data-ttu-id="1bd70-180">Bu bölümde, yaygın sağlayıcı senaryoları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-180">This section discusses common provider scenarios.</span></span>

### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="1bd70-181">Ifade düğümlerini SQL deyimlerine gruplama</span><span class="sxs-lookup"><span data-stu-id="1bd70-181">Grouping Expression Nodes into SQL Statements</span></span>

<span data-ttu-id="1bd70-182">İlk ilişkisel düğüme rastlandığınızda bir Sqlselectdeyim oluşturulur (genellikle bir DbScanExpression uzantısı).</span><span class="sxs-lookup"><span data-stu-id="1bd70-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="1bd70-183">Mümkün olduğunca çok sayıda iç içe sorgu içeren bir SQL SELECT açıklaması oluşturmak için, bu Sqlselectdeyimde mümkün olduğunca üst düğümlerinden birçoğu toplayın.</span><span class="sxs-lookup"><span data-stu-id="1bd70-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>

<span data-ttu-id="1bd70-184">Belirli bir (ilişkisel) düğümün geçerli Sqlselectdeyimye eklenip eklenemeyeceğini (giriş ziyaret edildiğinde döndürülen) veya yeni bir deyimin başlatılması gerekiyorsa, yöntemin uyumlu olarak hesaplanmasının ve şu anda Verilen düğümün altında hangi düğümlerin altında olduğuna bağlı olarak Sqlselectdeyimin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>

<span data-ttu-id="1bd70-185">Genellikle, birleştirme için kabul edilen düğümlerin boş olmadığı yan tümcelerden sonra SQL ifade yan tümceleri değerlendiriliyorsa, düğüm geçerli ifadeye eklenemez.</span><span class="sxs-lookup"><span data-stu-id="1bd70-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="1bd70-186">Örneğin, bir sonraki düğüm bir filtre ise, bu düğüm geçerli Sqlselectdeyimde yalnızca aşağıdakilerin doğru olması durumunda eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>

- <span data-ttu-id="1bd70-187">SEÇIM listesi boş.</span><span class="sxs-lookup"><span data-stu-id="1bd70-187">The SELECT list is empty.</span></span> <span data-ttu-id="1bd70-188">SEÇIM listesi boş değilse, seçim listesi filtreden önceki bir düğüm tarafından üretildiyse ve koşul bu SEÇIM listesi tarafından üretilen sütunlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>

- <span data-ttu-id="1bd70-189">GROUPBY boş.</span><span class="sxs-lookup"><span data-stu-id="1bd70-189">The GROUPBY is empty.</span></span> <span data-ttu-id="1bd70-190">GROUPBY boş değilse, filtrenin eklenmesi, Gruplandırmadan önce filtrelemeye neden olur, bu doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>

- <span data-ttu-id="1bd70-191">TOP yan tümcesi boş.</span><span class="sxs-lookup"><span data-stu-id="1bd70-191">The TOP clause is empty.</span></span> <span data-ttu-id="1bd70-192">TOP yan tümcesi boş değilse, filtrenin eklenmesi üst, doğru olmayan bir şekilde filtrelemeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>

<span data-ttu-id="1bd70-193">Bu, her zaman var olan bir Sqlselectdeyimin parçası olarak eklendiğinden, bu, DbConstantExpression veya aritmetik ifadeler gibi ilişkisel olmayan düğümler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>

<span data-ttu-id="1bd70-194">Ayrıca, JOIN ağacının köküyle karşılaşıldığında (JOIN üst öğesi olmayan bir JOIN düğümü), yeni bir Sqlselectdeyimin başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="1bd70-195">Tüm sol sırt JOIN alt öğeleri, bu Sqlselectdeyimin içine toplanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>

<span data-ttu-id="1bd70-196">Her yeni bir Sqlselectdeyimi başlatıldığında ve geçerli bir giriş girişe eklendiğinde, varsa, geçerli Sqlselectdeyimin İzdüşüm sütunları (bir SELECT yan tümcesi) eklenerek tamamlanması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="1bd70-197">Bu, Sqlselectdeyimin FromExtents ' na bakar ve FromExtents tarafından temsil edilen kapsam listesinin tüm sütunlarını, öngörülen sütunlar listesine getiren AddDefaultColumns yöntemi ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="1bd70-198">Bu işlem yapılır çünkü bu noktada diğer düğümlerin hangi sütunlara başvurduğu bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="1bd70-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="1bd70-199">Bu, yalnızca daha sonra kullanılabilecek sütunları Project için iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-199">This can be optimized to only project the columns that can later be used.</span></span>

### <a name="join-flattening"></a><span data-ttu-id="1bd70-200">Düzleştirme ile Birleştir</span><span class="sxs-lookup"><span data-stu-id="1bd70-200">Join Flattening</span></span>

<span data-ttu-id="1bd70-201">Isparentajoın özelliği, belirli bir birleştirmenin düzleştirilerek bulunup bulunmadığını belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="1bd70-202">Özellikle, Isparentajoın yalnızca bir birleşimin sol alt öğesi için `true` ve bir birleşime anında giriş olan her DbScanExpression için döndürür ve bu durumda alt düğüm, üst öğenin daha sonra kullanacağı Sqlselectdeyimi yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="1bd70-203">Daha fazla bilgi için bkz. "Ifadeleri JOIN".</span><span class="sxs-lookup"><span data-stu-id="1bd70-203">For more information, see "Join Expressions".</span></span>

### <a name="input-alias-redirecting"></a><span data-ttu-id="1bd70-204">Giriş diğer adı yönlendirme</span><span class="sxs-lookup"><span data-stu-id="1bd70-204">Input Alias Redirecting</span></span>

<span data-ttu-id="1bd70-205">Giriş diğer adı, sembol tablosu ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-205">Input alias redirecting is accomplished with the symbol table.</span></span>

<span data-ttu-id="1bd70-206">Giriş diğer adının yeniden yönlendirildiğini açıklamak için, [komut ağaçları-En Iyi UYGULAMALARDAN SQL oluşturma](generating-sql-from-command-trees-best-practices.md)bölümündeki ilk örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="1bd70-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="1bd70-207">"A", projeksiyonda "b" öğesine yönlendirilmek için gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-207">There "a" needed to be redirected to "b" in the projection.</span></span>

<span data-ttu-id="1bd70-208">Bir sqlselectdeyimnesnesi oluşturulduğunda, düğümün girişi olan uzantısı Sqlselectdeyimin from özelliğine konur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="1bd70-209">Bir sembol (\<symbol_b >), bu kapsamı temsil eden "AS" + \<symbol_b > from yan tümcesine eklendiği şekilde giriş bağlama adına ("b") göre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-209">A Symbol (\<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " + \<symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="1bd70-210">Sembol, FromExtents özelliğine de eklenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-210">The symbol is also added to the FromExtents property.</span></span>

<span data-ttu-id="1bd70-211">Sembol, giriş bağlama adını kendisine bağlamak için sembol tablosuna de eklenir ("b", \<symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="1bd70-211">The symbol is also added to the symbol table to link the input binding name to it ("b", \<symbol_b>).</span></span>

<span data-ttu-id="1bd70-212">Sonraki bir düğüm bu Sqlselectdeyimsini yeniden kullanıyorsa, giriş bağlama adını bu simgeye bağlamak için sembol tablosuna bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="1bd70-213">Örneğimizde, "a" giriş bağlama adına sahip DbProjectExpression, Sqlselectdeyimin yeniden kullanır ve tabloya ("a", \< symbol_b >) ekler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>

<span data-ttu-id="1bd70-214">İfadeler, Sqlselectdeyimi yeniden kullanan düğümün giriş bağlama adına başvuru yaparken, bu başvuru sembol tablosu doğru yeniden yönlendirilen simgeye kullanılarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="1bd70-215">"A. x" öğesinden "a", "a", "a" DbVariableReferenceExpression, \<symbol_b > simgesine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol \<symbol_b>.</span></span>

### <a name="join-alias-flattening"></a><span data-ttu-id="1bd70-216">Diğer ad düzleştirmeyi Birleştir</span><span class="sxs-lookup"><span data-stu-id="1bd70-216">Join Alias Flattening</span></span>

<span data-ttu-id="1bd70-217">DbPropertyExpression başlıklı bölümde açıklandığı gibi bir DbPropertyExpression ziyaret edildiğinde JOIN diğer adı düzleştirme elde edilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>

### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="1bd70-218">Sütun adı ve uzantı diğer adı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="1bd70-218">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="1bd70-219">Sütun adı ve uzantı diğer adı yeniden adlandırma sorunu, SQL üretimi oluşturma: String komutunu oluşturma başlıklı bölümde açıklanan oluşturmanın ikinci aşamasında yalnızca diğer adlarla birlikte bulunan diğer adları kullanan semboller kullanılarak ele alınır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="1bd70-220">SQL oluşturma 'nın ilk aşaması: Ifade ağacını ziyaret etme</span><span class="sxs-lookup"><span data-stu-id="1bd70-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="1bd70-221">Bu bölümde, sorguyu temsil eden ifade ziyaret edildiğinde ve bir ara yapı üretildiğinde, bir Sqlselectdeyimi veya bir SqlBuilder olduğunda SQL üretimi ilk aşaması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>

<span data-ttu-id="1bd70-222">Bu bölümde, farklı ifade düğüm kategorilerini ziyaret eden ilkeler ve belirli ifade türlerini ziyaret eden Ayrıntılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>

### <a name="relational-non-join-nodes"></a><span data-ttu-id="1bd70-223">İlişkisel (JOIN olmayan) düğümler</span><span class="sxs-lookup"><span data-stu-id="1bd70-223">Relational (Non-Join) Nodes</span></span>

<span data-ttu-id="1bd70-224">Aşağıdaki ifade türleri, JOIN olmayan düğümleri destekler:</span><span class="sxs-lookup"><span data-stu-id="1bd70-224">The following expression types support non-join nodes:</span></span>

- <span data-ttu-id="1bd70-225">Dbdıstıntexpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-225">DbDistinctExpression</span></span>

- <span data-ttu-id="1bd70-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-226">DbFilterExpression</span></span>

- <span data-ttu-id="1bd70-227">Fazla</span><span class="sxs-lookup"><span data-stu-id="1bd70-227">DbGroupByExpression</span></span>

- <span data-ttu-id="1bd70-228">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-228">DbLimitExpression</span></span>

- <span data-ttu-id="1bd70-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-229">DbProjectExpression</span></span>

- <span data-ttu-id="1bd70-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-230">DbSkipExpression</span></span>

- <span data-ttu-id="1bd70-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-231">DbSortExpression</span></span>

<span data-ttu-id="1bd70-232">Bu düğümleri ziyaret eden aşağıdaki model aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="1bd70-232">Visiting these nodes follows the following pattern:</span></span>

1. <span data-ttu-id="1bd70-233">İlişkisel girişi ziyaret edin ve elde edilen Sqlselectdeyimden yararlanın.</span><span class="sxs-lookup"><span data-stu-id="1bd70-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="1bd70-234">İlişkisel bir düğüme giriş, aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-234">The input to a relational node could be one of the following:</span></span>

    - <span data-ttu-id="1bd70-235">Uzantı (örneğin, DbScanExpression) dahil olmak üzere ilişkisel bir düğüm.</span><span class="sxs-lookup"><span data-stu-id="1bd70-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="1bd70-236">Bu tür bir düğüm ziyaret etmek bir Sqlselectdeyimin geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-236">Visiting such a node returns a SqlSelectStatement.</span></span>

    - <span data-ttu-id="1bd70-237">Set Operation ifadesi (örneğin UNıON ALL).</span><span class="sxs-lookup"><span data-stu-id="1bd70-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="1bd70-238">Sonuç, köşeli ayraçlar içine sarmalanmış ve yeni bir Sqlselectdeyimin FROM yan tümcesine yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="1bd70-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>

2. <span data-ttu-id="1bd70-239">Geçerli düğümün giriş tarafından üretilen Sqlselectdeyimye eklenip eklenemeyeceğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="1bd70-240">Ifadeleri SQL deyimlerine gruplama başlıklı Bölüm bunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="1bd70-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="1bd70-241">Aksi takdirde,</span><span class="sxs-lookup"><span data-stu-id="1bd70-241">If not,</span></span>

    - <span data-ttu-id="1bd70-242">Geçerli Sqlselectdeyimin nesnesini açılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-242">Pop the current SqlSelectStatement object.</span></span>

    - <span data-ttu-id="1bd70-243">Yeni bir sqlselectdeyimnesnesi oluşturun ve yeni Sqlselectdeyimin nesnesinden ÖĞESINDEN popomış Sqlselectdeyimin öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>

    - <span data-ttu-id="1bd70-244">Yeni nesneyi yığının üzerine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-244">Put the new object on top of the stack.</span></span>

3. <span data-ttu-id="1bd70-245">Giriş ifadesi bağlamayı girdiden doğru simgeye yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="1bd70-246">Bu bilgiler Sqlselectdeyimnesnesi içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-246">This information is maintained in the SqlSelectStatement object.</span></span>

4. <span data-ttu-id="1bd70-247">Yeni bir SymbolTable kapsamı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-247">Add a new SymbolTable scope.</span></span>

5. <span data-ttu-id="1bd70-248">İfadenin giriş dışı bölümünü (örneğin, projeksiyon ve koşul) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>

6. <span data-ttu-id="1bd70-249">Genel yığınlara eklenen tüm nesneleri açılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-249">Pop all the objects added to the global stacks.</span></span>

 <span data-ttu-id="1bd70-250">DbSkipExpression SQL 'de doğrudan eşdeğer değildir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="1bd70-251">Mantıksal olarak, öğesine çevrilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-251">Logically, it is translated into:</span></span>

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a><span data-ttu-id="1bd70-252">JOIN Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1bd70-252">Join Expressions</span></span>

<span data-ttu-id="1bd70-253">Aşağıdaki, JOIN ifadeleri olarak kabul edilir ve VisitJoinExpression yöntemi tarafından ortak bir şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>

- <span data-ttu-id="1bd70-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-254">DbApplyExpression</span></span>

- <span data-ttu-id="1bd70-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-255">DbJoinExpression</span></span>

- <span data-ttu-id="1bd70-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-256">DbCrossJoinExpression</span></span>

<span data-ttu-id="1bd70-257">Aşağıda, ziyaret ettiğiniz adımlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-257">The following are the visit steps:</span></span>

<span data-ttu-id="1bd70-258">İlk olarak, alt öğeleri ziyaret etmeden önce ıparentajoın, JOIN düğümünün bir sol sırt üzerinde bir birleşimin alt öğesi olup olmadığını denetlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="1bd70-259">False döndürürse, yeni bir Sqlselectdeyimin başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="1bd70-260">Bu anlamda, üst öğe (birleştirme düğümü), alt öğelerin büyük olasılıkla kullanması için Sqlselectdeyimlerini oluşturduğunda, birleşimler düğümlerin geri kalanından farklı şekilde ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>

<span data-ttu-id="1bd70-261">İkinci olarak, girişleri tek seferde işleyin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="1bd70-262">Her giriş için:</span><span class="sxs-lookup"><span data-stu-id="1bd70-262">For each input:</span></span>

1. <span data-ttu-id="1bd70-263">Girişi ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="1bd70-263">Visit the input.</span></span>

2. <span data-ttu-id="1bd70-264">Post işlemi, bir JOIN ifadesinin alt öğesini ziyaret ettikten sonra, büyük olasılıkla alt öğe tarafından üretilen Sqlselectexpression 'ı tamamladıktan sonra, sembol tablosunun korunmasından sorumlu ProcessJoinInputResult öğesini çağırarak girişi ziyaret etme sonucudur</span><span class="sxs-lookup"><span data-stu-id="1bd70-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="1bd70-265">Alt öğenin sonucu aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-265">The child's result could be one of the following:</span></span>

    - <span data-ttu-id="1bd70-266">Bir Sqlselectdeyimden üst öğenin ekleneceği öğeden farklı.</span><span class="sxs-lookup"><span data-stu-id="1bd70-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="1bd70-267">Bu durumda, varsayılan sütunlar eklenerek tamamlanması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="1bd70-268">Giriş bir birleşimle olduysa, yeni bir JOIN simgesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="1bd70-269">Aksi takdirde, normal bir simge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bd70-269">Otherwise, create a normal symbol.</span></span>

    - <span data-ttu-id="1bd70-270">Bir uzantı (örneğin, bir DbScanExpression), bu durumda yalnızca üst öğenin Sqlselectdeyiminin giriş listesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>

    - <span data-ttu-id="1bd70-271">Bir Sqlselectdeyimin değil, bu durumda köşeli ayraç ile sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>

    - <span data-ttu-id="1bd70-272">Üst öğenin eklendiği aynı Sqlselectdeyimdir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="1bd70-273">Bu durumda, FromExtents listesindeki simgelerin hepsini temsil eden tek bir yeni JoinSymbol ile değiştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>

    - <span data-ttu-id="1bd70-274">İlk üç durumda, AS yan tümcesini eklemek ve sembol tablosunu güncelleştirmek için AddFromSymbol çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>

<span data-ttu-id="1bd70-275">Üçüncü olarak, (varsa) JOIN koşulu ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-275">Third, the join condition (if any) is visited.</span></span>

### <a name="set-operations"></a><span data-ttu-id="1bd70-276">Ayarlama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1bd70-276">Set Operations</span></span>

<span data-ttu-id="1bd70-277">Set Operations DbUnionAllExpression, DbExceptExpression ve DbIntersectExpression, VisitSetOpExpression yöntemi tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="1bd70-278">Şeklin bir SqlBuilder 'ı oluşturur</span><span class="sxs-lookup"><span data-stu-id="1bd70-278">It creates a SqlBuilder of the shape</span></span>

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

<span data-ttu-id="1bd70-279">\<Leftsqlselectdeyim > ve \<Rightsqlselectdeyim > her bir girişin her birini ziyaret edilerek elde edilen sqlselectdeyimlerdir ve \<setOp > karşılık gelen işlemdir (örneğin, UNıON ALL).</span><span class="sxs-lookup"><span data-stu-id="1bd70-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>

### <a name="dbscanexpression"></a><span data-ttu-id="1bd70-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-280">DbScanExpression</span></span>

<span data-ttu-id="1bd70-281">Bir JOIN bağlamında ziyaret edildiğinde (başka bir birleşimin sol alt öğesi olan bir birleşime giriş olarak) DbScanExpression, bir sorgu, tablo veya görünüm olan karşılık gelen hedef için hedef SQL 'e sahip bir SqlBuilder döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="1bd70-282">Aksi takdirde, FROM alanı ile karşılık gelen hedefe karşılık gelen yeni bir Sqlselectdeyimin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>

### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="1bd70-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-283">DbVariableReferenceExpression</span></span>

<span data-ttu-id="1bd70-284">Bir DbVariableReferenceExpression ziyaret edilmesi, sembol tablosunda bir aramaya bağlı olarak bu değişken başvuru ifadesine karşılık gelen simgeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="1bd70-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-285">DbPropertyExpression</span></span>

<span data-ttu-id="1bd70-286">Bir DbPropertyExpression ziyaret edildiğinde JOIN diğer adının düzleştirilmesi tanımlanır ve işlenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>

<span data-ttu-id="1bd70-287">Örnek özelliği ilk kez ziyaret edilir ve sonuç bir sembol, JoinSymbol veya bir SymbolPair olur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="1bd70-288">Bu üç durum şu şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-288">Here is how these three cases are handled:</span></span>

- <span data-ttu-id="1bd70-289">Bir JoinSymbol döndürülürse, NameToExtent özelliği, gerekli özellik için bir sembol içerir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="1bd70-290">JOIN sembolü iç içe bir birleştirmeyi temsil ediyorsa, örnek diğer ad olarak kullanılacak simgeyi izlemek için JOIN simgesiyle birlikte yeni bir sembol çifti döndürülür ve daha fazla çözüm için gerçek özelliği temsil eden simge.</span><span class="sxs-lookup"><span data-stu-id="1bd70-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>

- <span data-ttu-id="1bd70-291">Bir SymbolPair döndürülürse ve sütun bölümü bir JOIN sembolsiyse, bir JOIN sembolü yeniden döndürülür, ancak artık Column özelliği geçerli özellik ifadesi tarafından temsil edilen özelliği işaret etmek üzere güncellenir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="1bd70-292">Aksi halde, diğer ad olarak SymbolPair kaynağı ve geçerli özelliğin simgesi sütun olarak bir SqlBuilder döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>

- <span data-ttu-id="1bd70-293">Bir sembol döndürülürse, ziyaret yöntemi bu örneğe sahip bir SqlBuilder yöntemini ve sütun adı olarak özellik adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>

### <a name="dbnewinstanceexpression"></a><span data-ttu-id="1bd70-294">DbNewInstanceExpression oluşturamıyor</span><span class="sxs-lookup"><span data-stu-id="1bd70-294">DbNewInstanceExpression</span></span>

<span data-ttu-id="1bd70-295">DbProjectExpression 'ın Projection özelliği olarak kullanıldığında, DbNewInstanceExpression oluşturamıyor, yansıtılan sütunları temsil eden bağımsız değişkenlerin virgülle ayrılmış bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>

<span data-ttu-id="1bd70-296">DbNewInstanceExpression oluşturamıyor bir koleksiyon dönüş türüne sahip olduğunda ve bağımsız değişkenler olarak sunulan ifadelerin yeni bir koleksiyonunu tanımladığında, aşağıdaki üç durum ayrı olarak işlenir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>

- <span data-ttu-id="1bd70-297">DbNewInstanceExpression oluşturamıyor tek bağımsız değişken olarak DbElementExpression varsa, aşağıdaki gibi çevrilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>

```sql
NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
```

<span data-ttu-id="1bd70-298">DbNewInstanceExpression oluşturamıyor bağımsız değişken yoksa (boş bir tabloyu temsil ediyorsa), DbNewInstanceExpression oluşturamıyor öğesine çevrilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

<span data-ttu-id="1bd70-299">Aksi takdirde DbNewInstanceExpression oluşturamıyor, bağımsız değişkenlerin bir UNION-ALL merdiveni oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1bd70-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a><span data-ttu-id="1bd70-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-300">DbFunctionExpression</span></span>

<span data-ttu-id="1bd70-301">Kurallı ve yerleşik işlevler aynı şekilde işlenir: (örneğin, LTRIM (dize) için özel işleme (örneğin, düğüm) gerekiyorsa, uygun işleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="1bd70-302">Aksi halde bunlar, fonksiyonadı (arg1, arg2,..., argN) olarak çevrilir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>

<span data-ttu-id="1bd70-303">Sözlükler, hangi işlevlerin özel işleme ve ilgili işleyicilerinin gerekli olduğunu izlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>

<span data-ttu-id="1bd70-304">Kullanıcı tanımlı işlevler NamespaceName. fonksiyonadı öğesine çevrilir (arg1, arg2,..., argN).</span><span class="sxs-lookup"><span data-stu-id="1bd70-304">User-defined functions are translated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>

### <a name="dbelementexpression"></a><span data-ttu-id="1bd70-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-305">DbElementExpression</span></span>

<span data-ttu-id="1bd70-306">DbElementExpression 'ı ziyaret eden yöntem yalnızca bir skaler alt sorguyu temsil etmek için kullanıldığında DbElementExpression 'ı ziyaret etmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="1bd70-307">Bu nedenle, DbElementExpression, tamamen bir Sqlselectdeyim halinde çeviri yapar ve çevresine köşeli ayraç ekler.</span><span class="sxs-lookup"><span data-stu-id="1bd70-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>

### <a name="dbquantifierexpression"></a><span data-ttu-id="1bd70-308">Dbnicelik Erexpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-308">DbQuantifierExpression</span></span>

<span data-ttu-id="1bd70-309">İfade türüne (any veya tümü) bağlı olarak, Dbnicelik Erexpression şöyle çevrilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated as:</span></span>

```sql
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a><span data-ttu-id="1bd70-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-310">DbNotExpression</span></span>

<span data-ttu-id="1bd70-311">Bazı durumlarda, DbNotExpression 'ın giriş ifadesiyle çevirisini daraltmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1bd70-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="1bd70-312">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1bd70-312">For example:</span></span>

```sql
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

<span data-ttu-id="1bd70-313">İkinci daraltmasının neden olduğu nedeni, verimsizlikleri türünde Dbnicelik Erexpression çevrilirken sağlayıcı tarafından tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="1bd70-314">Bu nedenle Entity Framework basitleştirme işlemi yapılamadı.</span><span class="sxs-lookup"><span data-stu-id="1bd70-314">Thus the Entity Framework could not have done the simplification.</span></span>

### <a name="dbisemptyexpression"></a><span data-ttu-id="1bd70-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="1bd70-315">DbIsEmptyExpression</span></span>

<span data-ttu-id="1bd70-316">DbIsEmptyExpression şu şekilde çevrilir:</span><span class="sxs-lookup"><span data-stu-id="1bd70-316">DbIsEmptyExpression is translated as:</span></span>

```sql
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="1bd70-317">SQL üretimi ikinci aşaması: String komutunu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bd70-317">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="1bd70-318">Bir dize SQL komutu oluştururken, Sqlselectdeyimin sembolleri için gerçek diğer adları üretir, bu da sütun adı ve uzantı diğer adı yeniden adlandırma sorununa yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1bd70-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>

<span data-ttu-id="1bd70-319">Uzantı diğer adının yeniden adlandırılması, Sqlselectdeyimnesnesi bir dizeye yazılırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="1bd70-320">İlk olarak, dış kapsamlar tarafından kullanılan tüm diğer adların bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bd70-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="1bd70-321">FromExtents içindeki her sembol (ya da null olmayan), herhangi bir dış uzantı ile çakışıyorsa yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="1bd70-322">Yeniden adlandırma gerekiyorsa, AllExtentNames ' de toplanan herhangi bir uzantı ile çakışmaz.</span><span class="sxs-lookup"><span data-stu-id="1bd70-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>

<span data-ttu-id="1bd70-323">Bir dizeye sembol nesnesi yazılırken sütun yeniden adlandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="1bd70-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="1bd70-324">İlk aşamadaki AddDefaultColumns, belirli bir sütun sembolünün yeniden adlandırılması gerektiğini tespit etti.</span><span class="sxs-lookup"><span data-stu-id="1bd70-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="1bd70-325">İkinci aşamada yalnızca yeniden adlandırma işlemi, üretilen adın AllColumnNames içinde kullanılan adla çakışmamasını sağlamak için oluşur</span><span class="sxs-lookup"><span data-stu-id="1bd70-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>

<span data-ttu-id="1bd70-326">Her ikisi de diğer adlar ve sütunlar için benzersiz adlar oluşturmak üzere \<existing_name > _N kullanın; burada n henüz kullanılmamış olan en küçük diğer addır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-326">To produce unique names both for extent aliases and for columns, use \<existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="1bd70-327">Tüm diğer adların genel listesi, basamaklı yeniden adlandırmaları gereksinimini artırır.</span><span class="sxs-lookup"><span data-stu-id="1bd70-327">The global list of all aliases increases the need for cascading renames.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd70-328">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bd70-328">See also</span></span>

- [<span data-ttu-id="1bd70-329">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bd70-329">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
