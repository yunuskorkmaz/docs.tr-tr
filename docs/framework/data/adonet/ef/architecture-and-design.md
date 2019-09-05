---
title: Mimari ve Tasarım
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 50fc643fecf4b188123c556d754b3cbfa529e5e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251713"
---
# <a name="architecture-and-design"></a>Mimari ve Tasarım

[Örnek sağlayıcıdaki](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) SQL oluşturma modülü, komut ağacını temsil eden ifade ağacında bir ziyaretçi olarak uygulanır. Oluşturma, ifade ağacının tek bir geçişinde yapılır.

Ağacın düğümleri aşağıdan yukarıya işlenir. İlk olarak, bir ara yapı üretilir: Her ikisi de ısıntefragment uygulayan Sqlselectdeyimin veya SqlBuilder. Ardından, dize SQL deyimleri Bu yapıdan üretilir. Ara yapının iki nedeni vardır:

- Mantıksal olarak, bir SQL SELECT deyimleri sıra dışında doldurulur. FROM yan tümcesine katılan düğümler WHERE, GROUP BY ve ORDER BY yan tümcesinde yer alan düğümlerden önce ziyaret edilir.

- Diğer adları yeniden adlandırmak için, yeniden adlandırma sırasında çarpışmalardan kaçınmak için kullanılan tüm diğer adları tanımlamalısınız. SqlBuilder 'daki yeniden adlandırma seçimlerini ertelemek için, yeniden adlandırma aday olan sütunları temsil etmek üzere sembol nesneleri kullanın.

![Diyagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")

İlk aşamada, ifade ağacını ziyaret ederken ifadeler Sqlselectdeyimlerine gruplanır, birleştirmeler düzleştirilir ve birleştirme diğer adları düzleştirilir. Bu geçiş sırasında, sembol nesneleri yeniden adlandırılabilir sütunları veya girdi diğer adlarını temsil eder.

İkinci aşamada, gerçek dizeyi üretirken diğer adlar yeniden adlandırılır.

## <a name="data-structures"></a>Veri yapıları

Bu bölümde, bir SQL açıklaması oluşturmak için kullandığınız [örnek sağlayıcıda](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) kullanılan türler açıklanmaktadır.

### <a name="isqlfragment"></a>Isqlfragment

Bu bölüm, iki amaca hizmet eden ısqlfragment arabirimini uygulayan sınıfları ele almaktadır:

- Tüm ziyaretçi yöntemleri için ortak bir dönüş türü.

- Son SQL dizesini yazmak için bir yöntem sağlar.

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a>SqlBuilder

SqlBuilder, StringBuilder 'a benzeyen son SQL dizesi için bir cihaz topluyor. Bu, son SQL oluşturan dizelerden oluşur ve dizelere dönüştürülebilen ısqlparçaların yanı da.

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a>Sqlselectdeyimin

Sqlselectdeyim, "SELECT..." şeklinin kurallı bir SQL SELECT ifadesini temsil eder. KAYNAK.. WHERE... GRUPLANDIRMA ÖLÇÜTÜ... SIRALAMA ÖLÇÜTÜ ".

Her SQL yan tümcesi bir StringBuilder tarafından temsil edilir. Ayrıca, DISTINCT 'in belirtildiğinden ve deyimin en üst olup olmadığını izler. Deyimi en üstte değilse, deyimin bir TOP yan tümcesi da yoksa ORDER BY yan tümcesi atlanır.

FromExtents, SELECT ifadesiyle ilgili girişlerin listesini içerir. Genellikle yalnızca bir öğe vardır. Birleşimler için SELECT deyimlerinin geçici olarak birden fazla öğesi olabilir.

SELECT deyimleri bir JOIN düğümü tarafından oluşturulduysa, Sqlselectdeyimde Alljoinpackages içinde birleşimde düzleştirilmiş tüm uzantıların bir listesini tutar. OuterExtents, Sqlselectdeyimin dış başvurularını temsil eder ve giriş diğer adı yeniden adlandırması için kullanılır.

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

#### <a name="topclause"></a>Topyan tümcesi

Topyan tümcesi bir Sqlselectdeyiminde ÜSTTEKI ifadeyi temsil eder. TopCount özelliği, kaç tane en fazla satırın seçilmesi gerektiğini gösterir.  WithTies true olduğunda, topyan tümcesi bir DbLimitExpression tarafından oluşturulmuştur.

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a>Simgeleri

Sembol ile ilgili sınıflar ve sembol tablosu, giriş diğer adı yeniden adlandırma, JOIN diğer adı düzleştirme ve sütun diğer adı yeniden adlandırma işlemleri gerçekleştirir.

Sembol sınıfı bir kapsamı, iç içe bir SELECT ifadesini veya bir sütunu temsil eder. Bu, oluşturulduktan sonra yeniden adlandırmaya izin vermek için gerçek bir diğer ad yerine kullanılır ve temsil ettiği Yapıt (tür gibi) için ek bilgiler de taşır.

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

Ad, temsil edilen kapsam, iç içe SELECT açıklaması veya bir sütun için özgün diğer adı depolar.

NewName, SQL SELECT ifadesinde kullanılacak diğer adı depolar. İlk olarak ad olarak ayarlanır ve yalnızca son dize sorgusu oluşturulurken gerekliyse yeniden adlandırılır.

Tür yalnızca kapsamları ve iç içe geçmiş SELECT deyimlerini temsil eden semboller için yararlıdır.

#### <a name="symbolpair"></a>SymbolPair

SymbolPair sınıfı, kayıt düzleştirmeyi adresleyen.

D (v, "J3. J2. J1. a. x"), burada v 'nin bir VarRef, J1, J2, J3 birleşmesi, bir uzantısı ve x bir sütun olduğu bir özellik ifadesi düşünün.

Bu, sonunda {j '} içine çevrilmelidir. {x '}. Kaynak alanı, bir JOIN ifadesini temsil eden en dıştaki SqlStatement 'yi temsil eder (J2); Bu her zaman bir JOIN simgedir. Sütun alanı, JOIN olmayan bir sembolünde durduruluncaya kadar bir JOIN simgesinden bir sonrakine gider. Bu, bir DbPropertyExpression ziyaret edildiğinde döndürülür, ancak bir SqlBuilder 'a hiçbir zaman eklenmez.

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a>JoinSymbol

Bir JOIN sembolü, bir JOIN veya JOIN girişi ile iç içe bir SELECT ifadesini temsil eden bir simgedir.

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

ColumnList, SELECT yan tümcesindeki sütunların listesini temsil eder ve bu sembol bir SQL SELECT ifadesini temsil eder. Extenlıst, SELECT yan tümcesindeki uzantıların listesidir. Birleşimin en üst düzeyde düzleştirilmiş birden çok uzantısı varsa FlattenedExtentList, uzantı diğer adlarının doğru şekilde yeniden adlandırıldığından emin olmak için kapsamları izler.

NameToExtent, Extenlıst içindeki tüm kapsamları sözlük olarak içerir. Bir JoinSymbol 'ın sıradan bir JOIN simgesi mi yoksa buna karşılık gelen bir Sqlselectdeyimmi olduğunu anlamak için ınestedjoın kullanılır.

Tüm listeler tam olarak bir kez ayarlanır ve ardından aramalar veya numaralandırma için kullanılır.

#### <a name="symboltable"></a>SymbolTable

SymbolTable, değişken adlarını simgelere çözümlemek için kullanılır. SymbolTable, her kapsam için yeni bir girdiye sahip bir yığın olarak uygulanır. Arama, bir giriş bulunana kadar yığının en üstünden en alta doğru arar.

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

SQL oluşturma modülünün bir örneği başına yalnızca bir SymbolTable vardır. Kapsamlar, her ilişkisel düğüm için girilir ve çıkış yaptı. Daha önceki kapsamlardaki tüm semboller, aynı ada sahip diğer semboller tarafından gizlenmediği takdirde daha sonraki kapsamlar tarafından görülebilir.

### <a name="global-state-for-the-visitor"></a>Ziyaretçi için genel durum

Diğer adların ve sütunların yeniden adlandırılmasına yardımcı olmak için, sorgu ağacının ilk geçişinde kullanılan tüm sütun adlarının (AllColumnNames) ve uzantı diğer adlarının (AllExtentNames) bir listesini saklayın.  Sembol tablosu, değişken adlarını semboller olarak çözümler. IsVarRefSingle yalnızca doğrulama amacıyla kullanılır, kesinlikle gerekli değildir.

Currentselectdeyimin ve ıparentajoın aracılığıyla kullanılan iki yığın, ziyaretçi deseninin parametreleri geçememize izin vermediğinden, "Parameters" öğesini üstten alt düğümlere geçirmek için kullanılır.

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

## <a name="common-scenarios"></a>Yaygın senaryolar

Bu bölümde, yaygın sağlayıcı senaryoları açıklanmaktadır.

### <a name="grouping-expression-nodes-into-sql-statements"></a>Ifade düğümlerini SQL deyimlerine gruplama

İlk ilişkisel düğüme rastlandığınızda bir Sqlselectdeyim oluşturulur (genellikle bir DbScanExpression uzantısı). Mümkün olduğunca çok sayıda iç içe sorgu içeren bir SQL SELECT açıklaması oluşturmak için, bu Sqlselectdeyimde mümkün olduğunca üst düğümlerinden birçoğu toplayın.

Belirli bir (ilişkisel) düğümün geçerli Sqlselectdeyimye eklenip eklenemeyeceğini (giriş ziyaret edildiğinde döndürülen) veya yeni bir deyimin başlatılması gerekiyorsa, yöntemin uyumlu olarak hesaplanmasının ve şu anda Verilen düğümün altında hangi düğümlerin altında olduğuna bağlı olarak Sqlselectdeyimin.

Genellikle, birleştirme için kabul edilen düğümlerin boş olmadığı yan tümcelerden sonra SQL ifade yan tümceleri değerlendiriliyorsa, düğüm geçerli ifadeye eklenemez. Örneğin, bir sonraki düğüm bir filtre ise, bu düğüm geçerli Sqlselectdeyimde yalnızca aşağıdakilerin doğru olması durumunda eklenebilir:

- SEÇIM listesi boş. SEÇIM listesi boş değilse, seçim listesi filtreden önceki bir düğüm tarafından üretildiyse ve koşul bu SEÇIM listesi tarafından üretilen sütunlara başvurabilir.

- GROUPBY boş. GROUPBY boş değilse, filtrenin eklenmesi, Gruplandırmadan önce filtrelemeye neden olur, bu doğru değildir.

- TOP yan tümcesi boş. TOP yan tümcesi boş değilse, filtrenin eklenmesi üst, doğru olmayan bir şekilde filtrelemeye neden olur.

Bu, her zaman var olan bir Sqlselectdeyimin parçası olarak eklendiğinden, bu, DbConstantExpression veya aritmetik ifadeler gibi ilişkisel olmayan düğümler için geçerli değildir.

Ayrıca, JOIN ağacının köküyle karşılaşıldığında (JOIN üst öğesi olmayan bir JOIN düğümü), yeni bir Sqlselectdeyimin başlatılır. Tüm sol sırt JOIN alt öğeleri, bu Sqlselectdeyimin içine toplanır.

Her yeni bir Sqlselectdeyimi başlatıldığında ve geçerli bir giriş girişe eklendiğinde, varsa, geçerli Sqlselectdeyimin İzdüşüm sütunları (bir SELECT yan tümcesi) eklenerek tamamlanması gerekebilir. Bu, Sqlselectdeyimin FromExtents ' na bakar ve FromExtents tarafından temsil edilen kapsam listesinin tüm sütunlarını, öngörülen sütunlar listesine getiren AddDefaultColumns yöntemi ile yapılır. Bu işlem yapılır çünkü bu noktada diğer düğümlerin hangi sütunlara başvurduğu bilinmiyor. Bu, yalnızca daha sonra kullanılabilecek sütunları Project için iyileştirilebilir.

### <a name="join-flattening"></a>Düzleştirme ile Birleştir

Isparentajoın özelliği, belirli bir birleştirmenin düzleştirilerek bulunup bulunmadığını belirlemenize yardımcı olur. Özellikle, isparentajoın yalnızca bir `true` birleşimin sol alt öğesi için ve bir birleşime anında giriş olan her DbScanExpression için geri döner ve bu durumda alt düğüm, üst öğenin daha sonra kullanacağı sqlselectdeyimin aynısını yeniden kullanır. Daha fazla bilgi için bkz. "Ifadeleri JOIN".

### <a name="input-alias-redirecting"></a>Giriş diğer adı yönlendirme

Giriş diğer adı, sembol tablosu ile gerçekleştirilir.

Giriş diğer adının yeniden yönlendirildiğini açıklamak için, [komut ağaçları-En Iyi UYGULAMALARDAN SQL oluşturma](generating-sql-from-command-trees-best-practices.md)bölümündeki ilk örneğe bakın.  "A", projeksiyonda "b" öğesine yönlendirilmek için gerekir.

Bir sqlselectdeyimnesnesi oluşturulduğunda, düğümün girişi olan uzantısı Sqlselectdeyimin from özelliğine konur. Bir sembol (\<symbol_b >), bu kapsamı temsil eden "as" + \<symbol_b > from yan tümcesine eklendiği şekilde giriş bağlama adı ("b") temel alınarak oluşturulur.  Sembol, FromExtents özelliğine de eklenir.

Sembol, giriş bağlama adını kendisine bağlamak için sembol tablosuna da eklenir ("b", \<symbol_b >).

Sonraki bir düğüm bu Sqlselectdeyimsini yeniden kullanıyorsa, giriş bağlama adını bu simgeye bağlamak için sembol tablosuna bir giriş ekler. Örneğimizde, "a" giriş bağlama adına sahip DbProjectExpression, sqlselectdeyimin yeniden kullanır ve tabloya ("a", \< symbol_b >) ekler.

İfadeler, Sqlselectdeyimi yeniden kullanan düğümün giriş bağlama adına başvuru yaparken, bu başvuru sembol tablosu doğru yeniden yönlendirilen simgeye kullanılarak çözümlenir. "A. x" öğesinden "a", "a", "a" DbVariableReferenceExpression, symbol_b > symbol simgesine \<çözümlenir.

### <a name="join-alias-flattening"></a>Diğer ad düzleştirmeyi Birleştir

DbPropertyExpression başlıklı bölümde açıklandığı gibi bir DbPropertyExpression ziyaret edildiğinde JOIN diğer adı düzleştirme elde edilir.

### <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantı diğer adı yeniden adlandırma

Sütun adı ve uzantı diğer adı yeniden adlandırma sorunu, SQL oluşturmanın Ikinci aşaması başlıklı bölümde açıklanan oluşturmanın ikinci aşamasında yalnızca diğer adlarla değiştirilen semboller kullanılarak ele alınır: String komutu oluşturuluyor.

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>SQL oluşturma 'nın ilk aşaması: Ifade ağacını ziyaret etme

Bu bölümde, sorguyu temsil eden ifade ziyaret edildiğinde ve bir ara yapı üretildiğinde, bir Sqlselectdeyimi veya bir SqlBuilder olduğunda SQL üretimi ilk aşaması açıklanmaktadır.

Bu bölümde, farklı ifade düğüm kategorilerini ziyaret eden ilkeler ve belirli ifade türlerini ziyaret eden Ayrıntılar açıklanmaktadır.

### <a name="relational-non-join-nodes"></a>İlişkisel (JOIN olmayan) düğümler

Aşağıdaki ifade türleri, JOIN olmayan düğümleri destekler:

- DbDistinctExpression

- DbFilterExpression

- DbGroupByExpression

- DbLimitExpression

- DbProjectExpression

- DbSkipExpression

- DbSortExpression

Bu düğümleri ziyaret eden aşağıdaki model aşağıdadır:

1. İlişkisel girişi ziyaret edin ve elde edilen Sqlselectdeyimden yararlanın. İlişkisel bir düğüme giriş, aşağıdakilerden biri olabilir:

    - Uzantı (örneğin, DbScanExpression) dahil olmak üzere ilişkisel bir düğüm. Bu tür bir düğüm ziyaret etmek bir Sqlselectdeyimin geri döndürür.

    - Set Operation ifadesi (örneğin UNıON ALL). Sonuç, köşeli ayraçlar içine sarmalanmış ve yeni bir Sqlselectdeyimin FROM yan tümcesine yerleştirilecek.

2. Geçerli düğümün giriş tarafından üretilen Sqlselectdeyimye eklenip eklenemeyeceğini denetleyin. Ifadeleri SQL deyimlerine gruplama başlıklı Bölüm bunu açıklar. Aksi takdirde,

    - Geçerli Sqlselectdeyimin nesnesini açılır.

    - Yeni bir sqlselectdeyimnesnesi oluşturun ve yeni Sqlselectdeyimin nesnesinden ÖĞESINDEN popomış Sqlselectdeyimin öğesini ekleyin.

    - Yeni nesneyi yığının üzerine yerleştirin.

3. Giriş ifadesi bağlamayı girdiden doğru simgeye yeniden yönlendirin. Bu bilgiler Sqlselectdeyimnesnesi içinde tutulur.

4. Yeni bir SymbolTable kapsamı ekleyin.

5. İfadenin giriş dışı bölümünü (örneğin, projeksiyon ve koşul) ziyaret edin.

6. Genel yığınlara eklenen tüm nesneleri açılır.

 DbSkipExpression SQL 'de doğrudan eşdeğer değildir. Mantıksal olarak, öğesine çevrilir:

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a>JOIN Ifadeleri

Aşağıdaki, JOIN ifadeleri olarak kabul edilir ve VisitJoinExpression yöntemi tarafından ortak bir şekilde işlenir:

- DbApplyExpression

- DbJoinExpression

- DbCrossJoinExpression

Aşağıda, ziyaret ettiğiniz adımlar verilmiştir:

İlk olarak, alt öğeleri ziyaret etmeden önce ıparentajoın, JOIN düğümünün bir sol sırt üzerinde bir birleşimin alt öğesi olup olmadığını denetlemek için çağrılır. False döndürürse, yeni bir Sqlselectdeyimin başlatılır. Bu anlamda, üst öğe (birleştirme düğümü), alt öğelerin büyük olasılıkla kullanması için Sqlselectdeyimlerini oluşturduğunda, birleşimler düğümlerin geri kalanından farklı şekilde ziyaret edilir.

İkinci olarak, girişleri tek seferde işleyin. Her giriş için:

1. Girişi ziyaret edin.

2. Post işlemi, bir JOIN ifadesinin alt öğesini ziyaret ettikten sonra, büyük olasılıkla alt öğe tarafından üretilen Sqlselectexpression 'ı tamamladıktan sonra, sembol tablosunun korunmasından sorumlu ProcessJoinInputResult öğesini çağırarak girişi ziyaret etme sonucudur Alt öğenin sonucu aşağıdakilerden biri olabilir:

    - Bir Sqlselectdeyimden üst öğenin ekleneceği öğeden farklı. Bu durumda, varsayılan sütunlar eklenerek tamamlanması gerekebilir. Giriş bir birleşimle olduysa, yeni bir JOIN simgesi oluşturmanız gerekir. Aksi takdirde, normal bir simge oluşturun.

    - Bir uzantı (örneğin, bir DbScanExpression), bu durumda yalnızca üst öğenin Sqlselectdeyiminin giriş listesine eklenir.

    - Bir Sqlselectdeyimin değil, bu durumda köşeli ayraç ile sarmalanır.

    - Üst öğenin eklendiği aynı Sqlselectdeyimdir. Bu durumda, FromExtents listesindeki simgelerin hepsini temsil eden tek bir yeni JoinSymbol ile değiştirilmeleri gerekir.

    - İlk üç durumda, AS yan tümcesini eklemek ve sembol tablosunu güncelleştirmek için AddFromSymbol çağırılır.

Üçüncü olarak, (varsa) JOIN koşulu ziyaret edilir.

### <a name="set-operations"></a>Ayarlama İşlemleri

Set Operations DbUnionAllExpression, DbExceptExpression ve DbIntersectExpression, VisitSetOpExpression yöntemi tarafından işlenir. Şeklin bir SqlBuilder 'ı oluşturur

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

Burada \<leftsqlselectdeyim > ve \<rightsqlselectdeyim > her bir girişin her birini ziyaret edilerek elde edilen sqlselectdeyimlerdir \<ve setop > karşılık gelen işlemdir (örneğin, UNION ALL).

### <a name="dbscanexpression"></a>DbScanExpression

Bir JOIN bağlamında ziyaret edildiğinde (başka bir birleşimin sol alt öğesi olan bir birleşime giriş olarak) DbScanExpression, bir sorgu, tablo veya görünüm olan karşılık gelen hedef için hedef SQL 'e sahip bir SqlBuilder döndürür. Aksi takdirde, FROM alanı ile karşılık gelen hedefe karşılık gelen yeni bir Sqlselectdeyimin oluşturulması gerekir.

### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Bir DbVariableReferenceExpression ziyaret edilmesi, sembol tablosunda bir aramaya bağlı olarak bu değişken başvuru ifadesine karşılık gelen simgeyi döndürür.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Bir DbPropertyExpression ziyaret edildiğinde JOIN diğer adının düzleştirilmesi tanımlanır ve işlenir.

Örnek özelliği ilk kez ziyaret edilir ve sonuç bir sembol, JoinSymbol veya bir SymbolPair olur. Bu üç durum şu şekilde işlenir:

- Bir JoinSymbol döndürülürse, NameToExtent özelliği, gerekli özellik için bir sembol içerir. JOIN sembolü iç içe bir birleştirmeyi temsil ediyorsa, örnek diğer ad olarak kullanılacak simgeyi izlemek için JOIN simgesiyle birlikte yeni bir sembol çifti döndürülür ve daha fazla çözüm için gerçek özelliği temsil eden simge.

- Bir SymbolPair döndürülürse ve sütun bölümü bir JOIN sembolsiyse, bir JOIN sembolü yeniden döndürülür, ancak artık Column özelliği geçerli özellik ifadesi tarafından temsil edilen özelliği işaret etmek üzere güncellenir. Aksi halde, diğer ad olarak SymbolPair kaynağı ve geçerli özelliğin simgesi sütun olarak bir SqlBuilder döndürülür.

- Bir sembol döndürülürse, ziyaret yöntemi bu örneğe sahip bir SqlBuilder yöntemini ve sütun adı olarak özellik adını döndürür.

### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbProjectExpression 'ın Projection özelliği olarak kullanıldığında, DbNewInstanceExpression oluşturamıyor, yansıtılan sütunları temsil eden bağımsız değişkenlerin virgülle ayrılmış bir listesini oluşturur.

DbNewInstanceExpression oluşturamıyor bir koleksiyon dönüş türüne sahip olduğunda ve bağımsız değişkenler olarak sunulan ifadelerin yeni bir koleksiyonunu tanımladığında, aşağıdaki üç durum ayrı olarak işlenir:

- DbNewInstanceExpression oluşturamıyor tek bağımsız değişken olarak DbElementExpression varsa, aşağıdaki gibi çevrilir:

    ```
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
    ```

DbNewInstanceExpression oluşturamıyor bağımsız değişken yoksa (boş bir tabloyu temsil ediyorsa), DbNewInstanceExpression oluşturamıyor öğesine çevrilir:

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

Aksi takdirde DbNewInstanceExpression oluşturamıyor, bağımsız değişkenlerin bir UNION-ALL merdiveni oluşturur:

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a>DbFunctionExpression

Kurallı ve yerleşik işlevler aynı şekilde işlenir: (örneğin, LTRIM (dize) için özel işleme (örneğin, düğüm) gerekiyorsa, uygun işleyici çağrılır. Aksi halde bunlar, fonksiyonadı (arg1, arg2,..., argN) olarak çevrilir.

Sözlükler, hangi işlevlerin özel işleme ve ilgili işleyicilerinin gerekli olduğunu izlemek için kullanılır.

Kullanıcı tanımlı işlevler NamespaceName. fonksiyonadı öğesine çevrilir (arg1, arg2,..., argN).

### <a name="dbelementexpression"></a>DbElementExpression

DbElementExpression 'ı ziyaret eden yöntem yalnızca bir skaler alt sorguyu temsil etmek için kullanıldığında DbElementExpression 'ı ziyaret etmek için çağrılır. Bu nedenle, DbElementExpression, tamamen bir Sqlselectdeyim halinde çeviri yapar ve çevresine köşeli ayraç ekler.

### <a name="dbquantifierexpression"></a>DbQuantifierExpression

İfade türüne (any veya tümü) bağlı olarak, Dbnicelik Erexpression şöyle çevrilir:

```
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a>DbNotExpression

Bazı durumlarda, DbNotExpression 'ın giriş ifadesiyle çevirisini daraltmak mümkündür. Örneğin:

```
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

İkinci daraltmasının neden olduğu nedeni, verimsizlikleri türünde Dbnicelik Erexpression çevrilirken sağlayıcı tarafından tanıtılmıştır. Bu nedenle Entity Framework basitleştirme işlemi yapılamadı.

### <a name="dbisemptyexpression"></a>DbIsEmptyExpression

DbIsEmptyExpression şu şekilde çevrilir:

```
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL üretimi ikinci aşaması: String komutunu oluşturma

Bir dize SQL komutu oluştururken, Sqlselectdeyimin sembolleri için gerçek diğer adları üretir, bu da sütun adı ve uzantı diğer adı yeniden adlandırma sorununa yöneliktir.

Uzantı diğer adının yeniden adlandırılması, Sqlselectdeyimnesnesi bir dizeye yazılırken oluşur. İlk olarak, dış kapsamlar tarafından kullanılan tüm diğer adların bir listesini oluşturun. FromExtents içindeki her sembol (ya da null olmayan), herhangi bir dış uzantı ile çakışıyorsa yeniden adlandırılır. Yeniden adlandırma gerekiyorsa, AllExtentNames ' de toplanan herhangi bir uzantı ile çakışmaz.

Bir dizeye sembol nesnesi yazılırken sütun yeniden adlandırması oluşur. İlk aşamadaki AddDefaultColumns, belirli bir sütun sembolünün yeniden adlandırılması gerektiğini tespit etti. İkinci aşamada yalnızca yeniden adlandırma işlemi, üretilen adın AllColumnNames içinde kullanılan adla çakışmamasını sağlamak için oluşur

Hem diğer adlar hem de sütunlar için benzersiz adlar oluşturmak üzere, existing_name \<> _N kullanın; burada n henüz kullanılmamış olan en küçük diğer addır. Tüm diğer adların genel listesi, basamaklı yeniden adlandırmaları gereksinimini artırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Sağlayıcısında SQL Oluşturma](sql-generation-in-the-sample-provider.md)
