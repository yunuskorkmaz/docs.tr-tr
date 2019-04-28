---
title: Mimari ve Tasarım
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: a4b597c8a62c661ace4485959589823094b9a08f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606856"
---
# <a name="architecture-and-design"></a><span data-ttu-id="ecf98-102">Mimari ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="ecf98-102">Architecture and Design</span></span>
<span data-ttu-id="ecf98-103">SQL üretimi modülünde [örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) komut ağacı temsil eden ifade ağacında bir ziyaretçi olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="ecf98-104">Oluşturma, tek bir geçişinde ifade ağacı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-104">The generation is done in a single pass over the expression tree.</span></span>  
  
 <span data-ttu-id="ecf98-105">Ağaç düğümleri aşağıdan yukarı işlenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="ecf98-106">İlk olarak, bir ara yapı üretilir: SqlSelectStatement veya SqlBuilder, her iki uygulama ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="ecf98-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="ecf98-107">Ardından, dize SQL deyimi, yapısından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="ecf98-108">Ara yapı için iki nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="ecf98-108">There are two reasons for the intermediate structure:</span></span>  
  
- <span data-ttu-id="ecf98-109">Mantıksal olarak bir SQL SELECT deyimi sıralamaya doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="ecf98-110">FROM yan tümcesinde katılan düğümleri, WHERE, GROUP BY ve ORDER BY yan tümcesi içinde katılan düğümleri önce ziyaret.</span><span class="sxs-lookup"><span data-stu-id="ecf98-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>  
  
- <span data-ttu-id="ecf98-111">Diğer adlar yeniden adlandırmak için yeniden adlandırma sırasında çarpışmalardan kaçınmak için kullanılan tüm diğer adlarını tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="ecf98-112">Yeniden adlandırma seçenekleri SqlBuilder erteleneceği sütunları yeniden adlandırma için aday niteliği temsil etmek için Sembol nesneleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>  
  
 <span data-ttu-id="ecf98-113">![Diyagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="ecf98-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>  
  
 <span data-ttu-id="ecf98-114">İfade ağacı ziyaret sırasında ilk aşamada ifadeleri SqlSelectStatements gruplandırılır ve birleşimler düzleştirilmiş birleştirme diğer adlar düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="ecf98-115">Bu geçişi sırasında sembol nesneleri, sütunları veya yeniden adlandırılabilir giriş diğer adları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecf98-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>  
  
 <span data-ttu-id="ecf98-116">Gerçek dize üretme sırasında İkinci aşamada, diğer adlar yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>  
  
## <a name="data-structures"></a><span data-ttu-id="ecf98-117">Veri yapıları</span><span class="sxs-lookup"><span data-stu-id="ecf98-117">Data Structures</span></span>  
 <span data-ttu-id="ecf98-118">Bu bölümde kullanılan türleri ele alınmaktadır [örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) bir SQL deyimi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ecf98-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>  
  
### <a name="isqlfragment"></a><span data-ttu-id="ecf98-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="ecf98-119">ISqlFragment</span></span>  
 <span data-ttu-id="ecf98-120">Bu bölüm iki amaca hizmet eder ISqlFragment arabirimi uygulayan sınıflar kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="ecf98-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>  
  
- <span data-ttu-id="ecf98-121">Ziyaretçi yöntemleri için ortak bir dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="ecf98-121">A common return type for all the visitor methods.</span></span>  
  
- <span data-ttu-id="ecf98-122">Son SQL dizesi yazmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-122">Gives a method to write the final SQL string.</span></span>  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a><span data-ttu-id="ecf98-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="ecf98-123">SqlBuilder</span></span>  
 <span data-ttu-id="ecf98-124">SqlBuilder son SQL dizesi, StringBuilder için benzer bir toplama cihazdır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="ecf98-125">Dizelere dönüştürülebileceği ISqlFragments birlikte en son SQL oluşturan dizeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a><span data-ttu-id="ecf98-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="ecf98-126">SqlSelectStatement</span></span>  
 <span data-ttu-id="ecf98-127">Kurallı bir SQL SELECT deyimi "seçin... şeklin SqlSelectStatement temsil eder</span><span class="sxs-lookup"><span data-stu-id="ecf98-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="ecf98-128">KAYNAK..</span><span class="sxs-lookup"><span data-stu-id="ecf98-128">FROM  ..</span></span> <span data-ttu-id="ecf98-129">WHERE...</span><span class="sxs-lookup"><span data-stu-id="ecf98-129">WHERE …</span></span> <span data-ttu-id="ecf98-130">GRUPLANDIRMA ÖLÇÜTÜ...</span><span class="sxs-lookup"><span data-stu-id="ecf98-130">GROUP BY …</span></span> <span data-ttu-id="ecf98-131">ORDER BY".</span><span class="sxs-lookup"><span data-stu-id="ecf98-131">ORDER BY".</span></span>  
  
 <span data-ttu-id="ecf98-132">Her SQL maddeleri uygulamasının, çünkü StringBuilder tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="ecf98-133">Ayrıca, farklı belirtilmiş olup olmadığını ve deyim üstteki olup olmadığını izler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="ecf98-134">Deyim üstteki değilse, deyim bir TOP yan tümcesini olmadıkça ORDER BY yan tümcesi atlanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>  
  
 <span data-ttu-id="ecf98-135">SELECT deyimi için giriş listesinin FromExtents içerir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="ecf98-136">Olur ve genellikle tek öğe bu.</span><span class="sxs-lookup"><span data-stu-id="ecf98-136">There is usually just one element in this.</span></span> <span data-ttu-id="ecf98-137">SELECT deyimleri birleştirmeler için geçici olarak birden fazla öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-137">SELECT statements for joins may temporarily have more than one element.</span></span>  
  
 <span data-ttu-id="ecf98-138">SELECT deyimi bir birleşim düğümü tarafından oluşturduysanız SqlSelectStatement AllJoinExtents içinde birleştirme düzleştirilmiş tüm uzantıların listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="ecf98-139">OuterExtents SqlSelectStatement dış başvuruları temsil eder ve giriş diğer adı yeniden adlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>  
  
```  
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
  
#### <a name="topclause"></a><span data-ttu-id="ecf98-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="ecf98-140">TopClause</span></span>  
 <span data-ttu-id="ecf98-141">TopClause üst ifadede bir SqlSelectStatement temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecf98-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="ecf98-142">ÜST satırları seçilmelidir TopCount özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="ecf98-143">WithTies true olduğunda, bir DbLimitExpession TopClause oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-143">When WithTies is true, the TopClause was built from a DbLimitExpession.</span></span>  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a><span data-ttu-id="ecf98-144">Simgeleri</span><span class="sxs-lookup"><span data-stu-id="ecf98-144">Symbols</span></span>  
 <span data-ttu-id="ecf98-145">Sembol ile ilgili sınıflar ve sembol tablosuna sütun diğer adı yeniden adlandırma giriş diğer adı yeniden adlandırma ve diğer ad birleştirme düzleştirme gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>  
  
 <span data-ttu-id="ecf98-146">Sembol sınıfı, bir uzantı, iç içe geçmiş bir SELECT deyimi veya bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecf98-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="ecf98-147">Gerçek bir diğer ad yerine kullanılmış ve ayrıca daha fazla bilgi için (türü gibi) temsil ettiği yapıt taşır, sonra yeniden adlandırmak için izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>  
  
```  
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
  
 <span data-ttu-id="ecf98-148">Gösterilen ölçüde, iç içe geçmiş bir SELECT deyimi veya bir sütun özgün diğer adını depolar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>  
  
 <span data-ttu-id="ecf98-149">NewName SQL SELECT deyimi kullanılacak diğer depolar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="ecf98-150">Bu özgün adına ayarlayın ve yalnızca son dizede sorgu oluşturma sırasında gerekirse yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="ecf98-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>  
  
 <span data-ttu-id="ecf98-151">Türü yalnızca kapsamları ve iç içe geçmiş bir SELECT deyimi temsil eden simge için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>  
  
#### <a name="symbolpair"></a><span data-ttu-id="ecf98-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="ecf98-152">SymbolPair</span></span>  
 <span data-ttu-id="ecf98-153">Kayıt düzleştirme SymbolPair sınıfı ele alır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-153">The SymbolPair class addresses record flattening.</span></span>  
  
 <span data-ttu-id="ecf98-154">Bir özellik ifadesi VarRef, j1, j2 v olduğu D (v, "j3.j2.j1.a.x") göz önünde bulundurun, j3 birleşimler, bir uzantı ve x ise bir sütun.</span><span class="sxs-lookup"><span data-stu-id="ecf98-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>  
  
 <span data-ttu-id="ecf98-155">Bu oturum sonunda çevrilmesi gerekir {j'}. {x'}.</span><span class="sxs-lookup"><span data-stu-id="ecf98-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="ecf98-156">Kaynak alanı (örneğin j2); bir birleştirme ifadeyi temsil eden, en dıştaki sqldeyimi temsil eder. Bu her zaman bir birleşim semboldür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="ecf98-157">Bir birleştirme dışı simgeyi durduruluncaya kadar sütun alanı bir birleşim sembolünden diğerine taşır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="ecf98-158">Bu bir DbPropertyExpression ziyaret döndürülür, ancak hiçbir zaman bir SqlBuilder için eklendi.</span><span class="sxs-lookup"><span data-stu-id="ecf98-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a><span data-ttu-id="ecf98-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="ecf98-159">JoinSymbol</span></span>  
 <span data-ttu-id="ecf98-160">İç içe geçmiş bir SELECT deyimi bir birleşim veya Giriş bir birleşim ile temsil eden bir simge bir birleşim semboldür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>  
  
```  
internal sealed class JoinSymbol : Symbol {  
   internal List<Symbol> ColumnList {get, set}  
   internal List<Symbol> ExtentList {get}  
   internal List<Symbol> FlattenedExtentList {get, set}  
   internal Dictionary<string, Symbol> NameToExtent {get}  
   internal bool IsNestedJoin {get, set}  
  
   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)  
}  
```  
  
 <span data-ttu-id="ecf98-161">Bir SQL SELECT deyimi bu simgeyi temsil ediyorsa ColumnList SELECT yan tümcesindeki sütun listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecf98-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="ecf98-162">ExtentList kapsamlarını SELECT yan tümcesinde listesidir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="ecf98-163">Birleşim en üst düzeyinde düzleştirilmiş birden çok kapsam varsa, bu uzantı diğer adları doğru şekilde adlandırılır emin olmak için kapsam FlattenedExtentList izler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>  
  
 <span data-ttu-id="ecf98-164">NameToExtent ExtentList içindeki tüm kapsamları bir sözlük olarak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="ecf98-165">IsNestedJoin bir JoinSymbol sıradan birleştirme sembol veya karşılık gelen SqlSelectStatement içeren olup olmadığını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="ecf98-166">Tüm listeleri tam olarak ayarlamalı ve sonra aramaları veya numaralandırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>  
  
#### <a name="symboltable"></a><span data-ttu-id="ecf98-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="ecf98-167">SymbolTable</span></span>  
 <span data-ttu-id="ecf98-168">SymbolTable sembollere değişken adlarını çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="ecf98-169">SymbolTable yığını ile her kapsam için yeni bir giriş olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="ecf98-170">Bir giriş bulunana kadar aramaları yığının en üstünden en altına arayın.</span><span class="sxs-lookup"><span data-stu-id="ecf98-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 <span data-ttu-id="ecf98-171">Sql oluşturma modülü bir örneği başına yalnızca bir SymbolTable yoktur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="ecf98-172">Kapsamları girilen ve ilişkisel her düğüm için çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="ecf98-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="ecf98-173">Önceki kapsamlardaki tüm sembolleri aynı ada sahip diğer simgeler tarafından gizlenmiş sürece sonraki kapsamlar için görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>  
  
### <a name="global-state-for-the-visitor"></a><span data-ttu-id="ecf98-174">Ziyaretçi için genel durum</span><span class="sxs-lookup"><span data-stu-id="ecf98-174">Global State for the Visitor</span></span>  
 <span data-ttu-id="ecf98-175">Diğer adlar ve sütunları yeniden adlandırma yardımcı olmak için tüm sütun adlarının (AllColumnNames) listesini korumak ve sorgu ağacına ilk kullanılan uzantı diğer adları (AllExtentNames) geçirin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="ecf98-176">Sembol tablosuna değişken adları için semboller çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="ecf98-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="ecf98-177">IsVarRefSingle yalnızca kullanılan doğrulama amacıyla kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>  
  
 <span data-ttu-id="ecf98-178">CurrentSelectStatement ve IsParentAJoin kullanılan iki yığınları ziyaretçi deseni parametreleri geçirmek bize izin vermediği "parameters" alt düğümleri için üst öğeden geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>  
  
```  
internal Dictionary<string, int> AllExtentNames {get}  
internal Dictionary<string, int> AllColumnNames {get}  
SymbolTable symbolTable = new SymbolTable();  
bool isVarRefSingle = false;  
  
Stack<SqlSelectStatement> selectStatementStack;  
private SqlSelectStatement CurrentSelectStatement{get}  
  
Stack<bool> isParentAJoinStack;  
private bool IsParentAJoin{get}  
```  
  
## <a name="common-scenarios"></a><span data-ttu-id="ecf98-179">Yaygın senaryolar</span><span class="sxs-lookup"><span data-stu-id="ecf98-179">Common Scenarios</span></span>  
 <span data-ttu-id="ecf98-180">Bu bölümde, sağlayıcı senaryoları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-180">This section discusses common provider scenarios.</span></span>  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="ecf98-181">SQL Açıklamaalarını ifade düğümleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="ecf98-181">Grouping Expression Nodes into SQL Statements</span></span>  
 <span data-ttu-id="ecf98-182">İlk ilişkisel düğümü ile karşılaşıldığında bir SqlSelectStatement oluşturulur (genellikle DbScanExpression ölçüde) yedekleme alt ağacı ziyaret edildiğinde.</span><span class="sxs-lookup"><span data-stu-id="ecf98-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="ecf98-183">Bir SQL SELECT deyimi ile birkaç olarak üretmek için olabildiğince, üst düğümlerinden bu SqlSelectStatement olabildiğince fazla sayıda toplama sorguları iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="ecf98-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="ecf98-184">Verilen (ilişkisel) bir düğüm geçerli SqlSelectStatement (giriş ziyaret döndürülen bir) eklenebilmesi için veya yeni bir deyim başlatılması gerekip gerekmediğine karar IsCompatible yöntemiyle hesaplanır ve hangi zaten kullanımda olduğuna bağlıdır SqlSelectStatement hangi düğümleri verilen düğüm olan üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>  
  
 <span data-ttu-id="ecf98-185">Genellikle, SQL deyimi yan tümceleri burada birleştirmesi için dikkate düğümleri boş olmayan yan tümcelerinden sonra değerlendirilir, düğüm için geçerli deyim eklenemez.</span><span class="sxs-lookup"><span data-stu-id="ecf98-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="ecf98-186">Bir filtre sonraki düğümü ise yalnızca aşağıdaki true ise örneğin, o düğümde geçerli SqlSelectStatement dahil edilebilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>  
  
- <span data-ttu-id="ecf98-187">Seçim listesi boş.</span><span class="sxs-lookup"><span data-stu-id="ecf98-187">The SELECT list is empty.</span></span> <span data-ttu-id="ecf98-188">Seçim listesi boş değilse seçim listesine filtre önceki bir düğüm tarafından oluşturulan ve koşul bu seçim listesi tarafından üretilen sütunlarına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>  
  
- <span data-ttu-id="ecf98-189">GROUPBY boştur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-189">The GROUPBY is empty.</span></span> <span data-ttu-id="ecf98-190">Filtre ekleme, GROUPBY boş değilse, doğru değil gruplandırma önce filtreleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>  
  
- <span data-ttu-id="ecf98-191">TOP yan tümcesini boştur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-191">The TOP clause is empty.</span></span> <span data-ttu-id="ecf98-192">Filtre ekleme, TOP yan tümcesini boş değilse, doğru olmayan üst gerçekleştirmeden önce filtreleme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>  
  
 <span data-ttu-id="ecf98-193">Bunlar her zaman mevcut bir SqlSelectStatement bir parçası olarak dahil edilir çünkü bu DbConstantExpression veya aritmetik ifadeler gibi ilişkisel olmayan düğümleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="ecf98-194">Ayrıca, (bir birleşim üst öğesi yok bir birleşim düğümü) birleştirme ağacının kökü ile karşılaşıldığında, yeni SqlSelectStatement başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="ecf98-195">Tüm alt sol Sırt birleştirme öğelerini bu SqlSelectStatement toplanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="ecf98-196">Yeni bir SqlSelectStatement başlatıldığından ve geçerli bir giriş eklendiğinde her geçerli SqlSelectStatement yoksa bir projeksiyon sütunları (SELECT yan) ekleyerek tamamlanmış olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="ecf98-197">Bu, SqlSelectStatement FromExtents görünümünü ve öngörülen sütun listesi için kapsamda FromExtents tarafından temsil edilen uzantıların listesini getirir. tüm sütunları ekler, AddDefaultColumns yöntemiyle gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="ecf98-198">Bu noktada, hangi sütunların diğer düğümler tarafından başvurulan bilinmeyen olduğundan bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="ecf98-199">Bu, yalnızca daha sonra kullanılabilir sütunlar projeye iyileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-199">This can be optimized to only project the columns that can later be used.</span></span>  
  
### <a name="join-flattening"></a><span data-ttu-id="ecf98-200">Düzleştirme katılın</span><span class="sxs-lookup"><span data-stu-id="ecf98-200">Join Flattening</span></span>  
 <span data-ttu-id="ecf98-201">IsParentAJoin özelliği belirli bir birleştirme düzleştirilmiş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="ecf98-202">Özellikle, IsParentAJoin döndürür `true` üst daha sonra kullanacağınız aynı SqlSelectStatement yalnızca bir anlıktır her DbScanExpression ve bir birleşimin sol alt durumda bir birleştirme için o alt düğüm girişi için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="ecf98-203">Daha fazla bilgi için "Expressions birleştirme" bakın.</span><span class="sxs-lookup"><span data-stu-id="ecf98-203">For more information, see "Join Expressions".</span></span>  
  
### <a name="input-alias-redirecting"></a><span data-ttu-id="ecf98-204">Giriş diğer adı yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="ecf98-204">Input Alias Redirecting</span></span>  
 <span data-ttu-id="ecf98-205">Giriş diğer adı yeniden yönlendirme, sembol tablosu ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-205">Input alias redirecting is accomplished with the symbol table.</span></span>  
  
 <span data-ttu-id="ecf98-206">Giriş diğer adı yeniden yönlendirme açıklamak için ilk örnekte bakın [SQL oluşturma - komut ağaçlarından en iyi](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="ecf98-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="ecf98-207">Burada "a" gerekli "b" yansıtma yönlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="ecf98-207">There "a" needed to be redirected to "b" in the projection.</span></span>  
  
 <span data-ttu-id="ecf98-208">SqlSelectStatement nesne oluşturulduğunda, giriş düğümüne ölçüde SqlSelectStatement Kimden özelliğinde konur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="ecf98-209">Bir simge (< symbol_b >) Bu uzantı temsil etmek için giriş bağlamasına adı ("b") ve "AS" dayanarak oluşturulan + < symbol_b > From yan tümcesi için eklenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-209">A Symbol (<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " +  <symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="ecf98-210">Simgenin FromExtents özelliğini de eklenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-210">The symbol is also added to the FromExtents property.</span></span>  
  
 <span data-ttu-id="ecf98-211">Sembolü sembol tablosuna giriş bağlaması adı ("b", < symbol_b >) bağlamak üzere de eklenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-211">The symbol is also added to the symbol table to link the input binding name to it ("b", <symbol_b>).</span></span>  
  
 <span data-ttu-id="ecf98-212">Bir sonraki düğümü bu SqlSelectStatement kullanır, bu sembole giriş bağlama adını bağlamak için Sembol tablosuna bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="ecf98-213">Bizim örneğimizde, giriş bağlaması adı "a" ile DbProjectExpression SqlSelectStatement yeniden ve ekleyin ("a", \< symbol_b >) tablo.</span><span class="sxs-lookup"><span data-stu-id="ecf98-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>  
  
 <span data-ttu-id="ecf98-214">İfadeleri SqlSelectStatement yeniden düğümünün giriş bağlaması adı başvurduğunuzda, bu başvuruyu kullanarak doğru yeniden yönlendirilen sembolü sembol tablosuna çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="ecf98-215">"A.x" öğesinden "a" DbVariableReferenceExpression temsil eden ziyaret ederken çözümlendiğinde "a" BT < symbol_b > Sembole çözülecektir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol <symbol_b>.</span></span>  
  
### <a name="join-alias-flattening"></a><span data-ttu-id="ecf98-216">Diğer ad düzleştirme katılın</span><span class="sxs-lookup"><span data-stu-id="ecf98-216">Join Alias Flattening</span></span>  
 <span data-ttu-id="ecf98-217">DbPropertyExpression başlıklı bölümde açıklanan şekilde bir DbPropertyExpression ziyaret, diğer ad birleştirme düzleştirme elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>  
  
### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="ecf98-218">Sütun adı ve uzantısı diğer adını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="ecf98-218">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="ecf98-219">İkinci aşamada ikinci aşaması, SQL Oluşturma başlıklı bölümde açıklanan oluşturma diğer adları ile yalnızca değiştirilen simgeler kullanarak sorunu sütun adı ve diğer ad uzantısı yeniden adlandırma gönderilir: STRING komutu oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ecf98-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="ecf98-220">Birinci aşama SQL oluşturma: İfade ağacı ziyaret edin</span><span class="sxs-lookup"><span data-stu-id="ecf98-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="ecf98-221">Bu bölümde, sorgu ziyaret edilen ifade gösteren ve bir ara yapı oluşturulur, SQL oluşturma, ilk aşaması ya da bir SqlSelectStatement veya bir SqlBuilder açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>  
  
 <span data-ttu-id="ecf98-222">Bu bölümde, ilkeler ziyaret farklı ifade düğüm kategoriler ve belirli bir ifade türleri ziyaret ayrıntılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>  
  
### <a name="relational-non-join-nodes"></a><span data-ttu-id="ecf98-223">İlişkisel (birleştirme olmayan) düğümler</span><span class="sxs-lookup"><span data-stu-id="ecf98-223">Relational (Non-Join) Nodes</span></span>  
 <span data-ttu-id="ecf98-224">Aşağıdaki ifade türleri birleştirme olmayan düğümleri destekler:</span><span class="sxs-lookup"><span data-stu-id="ecf98-224">The following expression types support non-join nodes:</span></span>  
  
- <span data-ttu-id="ecf98-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-225">DbDistinctExpression</span></span>  
  
- <span data-ttu-id="ecf98-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-226">DbFilterExpression</span></span>  
  
- <span data-ttu-id="ecf98-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-227">DbGroupByExpression</span></span>  
  
- <span data-ttu-id="ecf98-228">DbLimitExpession</span><span class="sxs-lookup"><span data-stu-id="ecf98-228">DbLimitExpession</span></span>  
  
- <span data-ttu-id="ecf98-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-229">DbProjectExpression</span></span>  
  
- <span data-ttu-id="ecf98-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-230">DbSkipExpression</span></span>  
  
- <span data-ttu-id="ecf98-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-231">DbSortExpression</span></span>  
  
 <span data-ttu-id="ecf98-232">Bu düğümler ziyaret şu deseni izler:</span><span class="sxs-lookup"><span data-stu-id="ecf98-232">Visiting these nodes follows the following pattern:</span></span>  
  
1. <span data-ttu-id="ecf98-233">İlişkisel giriş sayfasını ziyaret edin ve sonuçta elde edilen SqlSelectStatement alın.</span><span class="sxs-lookup"><span data-stu-id="ecf98-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="ecf98-234">İlişkisel bir düğüme giriş aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-234">The input to a relational node could be one of the following:</span></span>  
  
    - <span data-ttu-id="ecf98-235">Bir uzantı (örneğin, bir DbScanExpression) dahil olmak üzere bir ilişkisel düğümü.</span><span class="sxs-lookup"><span data-stu-id="ecf98-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="ecf98-236">Bu tür bir düğüm ziyaret bir SqlSelectStatement döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-236">Visiting such a node returns a SqlSelectStatement.</span></span>  
  
    - <span data-ttu-id="ecf98-237">Küme işlemi ifadesi (UNION ALL, örneğin).</span><span class="sxs-lookup"><span data-stu-id="ecf98-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="ecf98-238">Köşeli ayraç içinde sarmalanmış ve yeni SqlSelectStatement FROM yan tümcesinde put sonucu vardır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>  
  
2. <span data-ttu-id="ecf98-239">Geçerli düğüm giriş tarafından üretilen SqlSelectStatement eklenebilir olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="ecf98-240">Bu gruplandırma ifadeleri bölümüne SQL Açıklamaalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecf98-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="ecf98-241">Aksi halde</span><span class="sxs-lookup"><span data-stu-id="ecf98-241">If not,</span></span>  
  
    - <span data-ttu-id="ecf98-242">Geçerli SqlSelectStatement nesne açılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-242">Pop the current SqlSelectStatement object.</span></span>  
  
    - <span data-ttu-id="ecf98-243">Yeni bir SqlSelectStatement nesnesi oluşturun ve yeni SqlSelectStatement nesnenin başlangıç popped SqlSelectStatement ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>  
  
    - <span data-ttu-id="ecf98-244">Yeni nesne yığının en üstünde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-244">Put the new object on top of the stack.</span></span>  
  
3. <span data-ttu-id="ecf98-245">Giriş ifadesini bağlama doğru sembole girdiden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="ecf98-246">Bu bilgiler SqlSelectStatement nesnesinde korunur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-246">This information is maintained in the SqlSelectStatement object.</span></span>  
  
4. <span data-ttu-id="ecf98-247">Yeni bir SymbolTable kapsam ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-247">Add a new SymbolTable scope.</span></span>  
  
5. <span data-ttu-id="ecf98-248">İfade (örneğin, yansıtma ve koşul) olmayan giriş bölümünü ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>  
  
6. <span data-ttu-id="ecf98-249">Genel yığınları için eklenen her nesne açılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-249">Pop all the objects added to the global stacks.</span></span>  
  
 <span data-ttu-id="ecf98-250">DbSkipExpression SQL'de doğrudan bir eşdeğer yok.</span><span class="sxs-lookup"><span data-stu-id="ecf98-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="ecf98-251">Mantıksal olarak veri dönüştürülür:</span><span class="sxs-lookup"><span data-stu-id="ecf98-251">Logically, it is translated into:</span></span>  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a><span data-ttu-id="ecf98-252">İfadeleri katılın</span><span class="sxs-lookup"><span data-stu-id="ecf98-252">Join Expressions</span></span>  
 <span data-ttu-id="ecf98-253">Aşağıdaki birleştirme ifadeler değerlendirilir ve yaygın bir şekilde VisitJoinExpression yöntemi tarafından işlenir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>  
  
- <span data-ttu-id="ecf98-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-254">DbApplyExpression</span></span>  
  
- <span data-ttu-id="ecf98-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-255">DbJoinExpression</span></span>  
  
- <span data-ttu-id="ecf98-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-256">DbCrossJoinExpression</span></span>  
  
 <span data-ttu-id="ecf98-257">Ziyaret uygulamanız gereken adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ecf98-257">The following are the visit steps:</span></span>  
  
 <span data-ttu-id="ecf98-258">İlk olarak, alt gitmeden önce IsParentAJoin birleştirme düğümün bir alt bir birleşimin sol Sırt boyunca olup olmadığını denetlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="ecf98-259">False döndürürse, yeni SqlSelectStatement başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="ecf98-260">Üst (birleştirme düğüm) için büyük olasılıkla kullanılacak alt SqlSelectStatement oluşturduğundan bu anlamda birleştirmeler farklı düğümlerin geri kalanından ziyaret.</span><span class="sxs-lookup"><span data-stu-id="ecf98-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>  
  
 <span data-ttu-id="ecf98-261">İkinci olarak, bir giriş teker teker işler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="ecf98-262">Her giriş için:</span><span class="sxs-lookup"><span data-stu-id="ecf98-262">For each input:</span></span>  
  
1. <span data-ttu-id="ecf98-263">Giriş sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="ecf98-263">Visit the input.</span></span>  
  
2. <span data-ttu-id="ecf98-264">POST işlemi ProcessJoinInputResult, sembol tablosuna bir JOIN ifadesinin bir alt ziyaret ve büyük olasılıkla alt tarafından üretilen SqlSelectStatement bittikten sonra bakımından sorumlu olduğu çağırarak giriş ziyaret sonucu.</span><span class="sxs-lookup"><span data-stu-id="ecf98-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="ecf98-265">Alt sonuç aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-265">The child's result could be one of the following:</span></span>  
  
    - <span data-ttu-id="ecf98-266">Bir üst eklenecek farklı SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="ecf98-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="ecf98-267">Böyle bir durumda, varsayılan sütunlar ekleyerek tamamlanmış olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="ecf98-268">Bir birleştirme giriş ise, yeni bir birleştirme sembol oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="ecf98-269">Aksi takdirde, normal bir sembol oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ecf98-269">Otherwise, create a normal symbol.</span></span>  
  
    - <span data-ttu-id="ecf98-270">Uzantı, yalnızca üst girişleri listesine eklenmiş SqlSelectStatement kullanıcının (bir DbScanExpression, örneğin).</span><span class="sxs-lookup"><span data-stu-id="ecf98-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>  
  
    - <span data-ttu-id="ecf98-271">İle kaydırılan çalışması, köşeli ayraçlar değil bir SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="ecf98-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>  
  
    - <span data-ttu-id="ecf98-272">Üst ekleneceği aynı SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="ecf98-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="ecf98-273">Böyle bir durumda FromExtents listesinde simgelerin tümünü temsil eden tek yeni bir JoinSymbol değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>  
  
    - <span data-ttu-id="ecf98-274">İlk üç durumlarda AddFromSymbol, AS yan tümcesi ekleyin ve sembol tablosunu güncelleştirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>  
  
 <span data-ttu-id="ecf98-275">Birleştirme koşulunun (varsa) üçüncü ziyaret.</span><span class="sxs-lookup"><span data-stu-id="ecf98-275">Third, the join condition (if any) is visited.</span></span>  
  
### <a name="set-operations"></a><span data-ttu-id="ecf98-276">Ayarlama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="ecf98-276">Set Operations</span></span>  
 <span data-ttu-id="ecf98-277">Ayarlama işlemleri DbUnionAllExpression DbExceptExpression ve DbIntersectExpression VisitSetOpExpression yöntemi tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="ecf98-278">Bir şeklin SqlBuilder oluşturur</span><span class="sxs-lookup"><span data-stu-id="ecf98-278">It creates a SqlBuilder of the shape</span></span>  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 <span data-ttu-id="ecf98-279">Burada \<leftSqlSelectStatement > ve \<rightSqlSelectStatement > SqlSelectStatements elde ederek, girişlerin her biri olan ve \<setOp > karşılık gelen (UNION ALL örneğin) bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>  
  
### <a name="dbscanexpression"></a><span data-ttu-id="ecf98-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-280">DbScanExpression</span></span>  
 <span data-ttu-id="ecf98-281">(Başka bir birleşimin sol alt bir birleştirme için giriş) olarak bir birleştirme bağlamında ziyaret ederse, ' % s'hedef SQL tanımlayan bir sorgu, tablo veya Görünüm karşılık gelen hedefi için bir SqlBuilder DbScanExpression döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="ecf98-282">Aksi takdirde, yeni SqlSelectStatement FROM alanı karşılık gelen hedefine karşılık olarak ayarlanmış oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>  
  
### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="ecf98-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-283">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="ecf98-284">Bir DbVariableReferenceExpression ziyareti bir ara sembol tablosuna göre bu değişken başvurusu ifadesi ile eşleşen sembol döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="ecf98-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-285">DbPropertyExpression</span></span>  
 <span data-ttu-id="ecf98-286">Diğer ad birleştirme düzleştirme tanımlandığı ve bir DbPropertyExpression ziyaret işlenir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>  
  
 <span data-ttu-id="ecf98-287">Örnek özelliği ilk kez ziyaret edilen ve bir sembol, bir JoinSymbol veya bir SymbolPair sonucudur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="ecf98-288">Bu üç durumların nasıl işleneceğini aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-288">Here is how these three cases are handled:</span></span>  
  
- <span data-ttu-id="ecf98-289">Bir JoinSymbol döndürülürse, kendi NameToExtent özelliği gerekli bir özellik için bir simge içerir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="ecf98-290">İç içe birleşim birleştirme sembol temsil ediyorsa, yeni bir simge çifti örnek diğer ad olarak kullanılan sembol izlemek için birleştirme sembol ve daha fazla çözümleme için gerçek özelliğini temsil eden bir simge ile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>  
  
- <span data-ttu-id="ecf98-291">Bir SymbolPair döndürülür ve birleştirme sembol sütun parçası ise, bir birleştirme sembol yeniden döndürülür, ancak şimdi column özelliği geçerli bir özellik ifadesi tarafından temsil edilen özelliğin işaret edecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="ecf98-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="ecf98-292">Aksi takdirde bir SqlBuilder SymbolPair kaynak diğer adı ve sütun olarak geçerli bir özellik için simge olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>  
  
- <span data-ttu-id="ecf98-293">Bir sembol döndürülürse, ziyaret yöntemi bu örnek diğer ad olarak ve sütun adı olarak özellik adı ile bir SqlBuilder yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>  
  
### <a name="dbnewinstanceexpression"></a><span data-ttu-id="ecf98-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-294">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="ecf98-295">DbProjectExpression projeksiyon özellik olarak kullanıldığında, Dbnewınstanceexpression öngörülen sütunları temsil etmek için bağımsız değişkenlerin virgülle ayrılmış bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecf98-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>  
  
 <span data-ttu-id="ecf98-296">Dbnewınstanceexpression, koleksiyon dönüş türüne sahip ve yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonu tanımlar, aşağıdaki üç durumda ayrı olarak ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="ecf98-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>  
  
- <span data-ttu-id="ecf98-297">Dbnewınstanceexpression DbElementExpression tek bağımsız değişken olarak varsa, aşağıdaki gibi çevrilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 <span data-ttu-id="ecf98-298">Dbnewınstanceexpression, bağımsız değişkenleri yoksa (boş bir tablo gösterir) Dbnewınstanceexpression çevrilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 <span data-ttu-id="ecf98-299">Aksi takdirde Dbnewınstanceexpression bağımsız değişkenlerin bir birleşimi tüm Merdiveni oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ecf98-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a><span data-ttu-id="ecf98-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-300">DbFunctionExpression</span></span>  
 <span data-ttu-id="ecf98-301">Canonical ve yerleşik işlevler, aynı şekilde işlenir: Bunlar özel işleme (örneğin, LTRIM(RTRIM(string) için TRIM(string)) gerekiyorsa, uygun işleyicisi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="ecf98-302">Aksi takdirde bunlar (arg1, arg2,..., argn) FunctionName çevrilir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>  
  
 <span data-ttu-id="ecf98-303">Sözlük, hangi işlevleri ve özel işleme uygun işleyicilerini gereksinim izlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>  
  
 <span data-ttu-id="ecf98-304">Kullanıcı tanımlı işlevleri tanslated NamespaceName.FunctionName (arg1, arg2,..., argn) için ' dir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-304">User-defined functions are tanslated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>  
  
### <a name="dbelementexpression"></a><span data-ttu-id="ecf98-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-305">DbElementExpression</span></span>  
 <span data-ttu-id="ecf98-306">DbElementExpression ziyaret yöntemi yalnızca skaler bir sorgu temsil etmek için kullanılan bir DbElementExpression ziyaret için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="ecf98-307">Bu nedenle, DbElementExpression içinde tam bir SqlSelectStatement çevirir ve köşeli ayraç içine ekler.</span><span class="sxs-lookup"><span data-stu-id="ecf98-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>  
  
### <a name="dbquantifierexpression"></a><span data-ttu-id="ecf98-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-308">DbQuantifierExpression</span></span>  
 <span data-ttu-id="ecf98-309">İfade türüne (veya tamamını) DbQuantifierExpression çevrilir olarak:</span><span class="sxs-lookup"><span data-stu-id="ecf98-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a><span data-ttu-id="ecf98-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-310">DbNotExpression</span></span>  
 <span data-ttu-id="ecf98-311">Bazı durumlarda DbNotExpression çevirisi, bir giriş ifadesi ile daraltmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ecf98-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="ecf98-312">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ecf98-312">For example:</span></span>  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 <span data-ttu-id="ecf98-313">DbQuantifierExpression, çevirme yazdığınızda tüm verimsizlikleri sağlayıcı tarafından sunulan ikinci Daralt gerçekleştirilen neden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="ecf98-314">Bu nedenle Entity Framework basitleştirme tamamlayabilirdik değil.</span><span class="sxs-lookup"><span data-stu-id="ecf98-314">Thus the Entity Framework could not have done the simplification.</span></span>  
  
### <a name="dbisemptyexpression"></a><span data-ttu-id="ecf98-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="ecf98-315">DbIsEmptyExpression</span></span>  
 <span data-ttu-id="ecf98-316">DbIsEmptyExpression olarak çevrilir:</span><span class="sxs-lookup"><span data-stu-id="ecf98-316">DbIsEmptyExpression is translated as:</span></span>  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="ecf98-317">İkinci aşama SQL oluşturma: STRING komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecf98-317">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="ecf98-318">Bir SQL komut dizesi oluştururken SqlSelectStatement olan sütun adı ve diğer ad uzantısı yeniden adlandırma sorunu giderir sembolleri için gerçek diğer adlar üretir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>  
  
 <span data-ttu-id="ecf98-319">Diğer ad uzantısı yeniden adlandırma, bir dizeye SqlSelectStatement nesne yazarken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="ecf98-320">İlk dış kapsam tarafından kullanılan tüm diğer adları listesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ecf98-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="ecf98-321">Her simge FromExtents (veya null olmayan ise AllJoinExtents), herhangi bir dış kapsam ile çakışırsa adı.</span><span class="sxs-lookup"><span data-stu-id="ecf98-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="ecf98-322">Yeniden adlandırma gerekirse tüm AllExtentNames içinde toplanan yerleşimi çakışmayacağı.</span><span class="sxs-lookup"><span data-stu-id="ecf98-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>  
  
 <span data-ttu-id="ecf98-323">Sütun yeniden adlandırma, bir dizeye bir sembol nesnesi yazılırken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="ecf98-324">İlk aşamada AddDefaultColumns, belirli bir sütun sembol yeniden adlandırılacak olup olmadığını belirledi.</span><span class="sxs-lookup"><span data-stu-id="ecf98-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="ecf98-325">İkinci aşamasında üretilen adı AllColumnNames içinde kullanılan herhangi bir ad ile çakışmadığından emin olmak yalnızca yeniden adlandırma gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ecf98-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>  
  
 <span data-ttu-id="ecf98-326">Uzantı diğer adlar için hem de sütunlar için benzersiz adlar oluşturmak için burada n, henüz kullanılmamış en küçük bir diğer ad, < existing_name > _n kullanın.</span><span class="sxs-lookup"><span data-stu-id="ecf98-326">To produce unique names both for extent aliases and for columns, use <existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="ecf98-327">Genel liste tüm adlar, basamaklı yeniden adlandırmaya gerek artırır.</span><span class="sxs-lookup"><span data-stu-id="ecf98-327">The global list of all aliases increases the need for cascading renames.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf98-328">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecf98-328">See also</span></span>

- [<span data-ttu-id="ecf98-329">Örnek Sağlayıcısında SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ecf98-329">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
