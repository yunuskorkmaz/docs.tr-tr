---
title: "Mimari ve tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 48b80856242730a5412cd9d5d8dd2c7f857304ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="architecture-and-design"></a>Mimari ve tasarım
SQL nesil modülünde [örnek sağlayıcı](http://go.microsoft.com/fwlink/?LinkId=180616) ziyaretçisi komut ağacı temsil eden ifade ağaç olarak uygulanır. Nesil tek geçişte ifade ağacına yapılır.  
  
 Ağaç düğümleri aşağıdan yukarı işlenir. İlk olarak, bir ara yapısı üretilen: SqlSelectStatement veya SqlBuilder, hem uygulama ISqlFragment. Ardından, SQL deyimini dize bu yapısından oluşturulur. Ara yapısı iki nedeni vardır:  
  
-   Mantıksal olarak, SQL SELECT deyimine bozuk doldurulur. FROM yan tümcesinde katılmak düğümleri, WHERE, GROUP BY ve ORDER BY yan tümcesi içinde katılmak düğümleri önce ziyaret edilen.  
  
-   Diğer adlar yeniden adlandırmak için yeniden adlandırma sırasında çakışmaları önlemek için tüm kullanılan diğer adlarını tanımlamanız gerekir. SqlBuilder içinde yeniden adlandırma seçenekler erteleme simgenin nesneleri yeniden adlandırmak için adaylar sütunları göstermek için kullanın.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 İfade ağacına ziyaret sırasında ilk aşamasında, ifadeleri SqlSelectStatements gruplandırılır, birleştirmeler düzleştirilmiş ve birleştirme diğer adlar düzleştirilmiş. Bu geçişi sırasında simgesi nesneleri, sütunları veya adlandırılabilir giriş diğer adı temsil eder.  
  
 Gerçek dize oluşturan sırasında ikinci aşamasında, diğer adlar yeniden adlandırılmıştır.  
  
## <a name="data-structures"></a>Veri yapıları  
 Bu bölümde kullanılan türleri açıklanmaktadır [örnek sağlayıcı](http://go.microsoft.com/fwlink/?LinkId=180616) bir SQL deyimi oluşturmak için kullanın.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 Bu bölüm iki amaca hizmet eder ISqlFragment arabirimini uygulayan sınıflar kapsar:  
  
-   Tüm ziyaretçi yöntemleri için ortak bir dönüş türü.  
  
-   Son SQL dizesi yazmak için bir yöntem sağlar.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder son SQL dizesi için StringBuilder için benzer bir toplama aygıttır. Dizeleri dönüştürülebilir ISqlFragments birlikte en son SQL oluşturan dizeleri oluşur.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 Kurallı SQL SELECT deyimine "seçin... şeklin SqlSelectStatement temsil eder KAYNAK.. WHERE... GRUPLANDIRMA ÖLÇÜTÜ... SIRALAMA ÖLÇÜTÜ".  
  
 Her SQL yan tümceleri StringBuilder temsil edilir. Ayrıca, DISTINCT belirtilen olup olmadığını ve deyim en üstteki olup olmadığını izler. Deyim en üstteki değilse, deyim de TOP yan tümcesinde bulunmadığı sürece ORDER BY yan tümcesi atlanır.  
  
 FromExtents SELECT deyimi girdileri listesini içerir. Yoktur genellikle yalnızca tek bir öğede bu. SELECT deyimleri birleştirmelerde geçici olarak birden fazla öğe olabilir.  
  
 SELECT deyimi bir birleşim düğümü tarafından oluşturduysanız, SqlSelectStatement AllJoinExtents birleştirmeye düzleştirilmiş tüm uzantıların listesini tutar. OuterExtents SqlSelectStatement dış başvuruları temsil eder ve giriş diğer adı yeniden adlandırmak için kullanılır.  
  
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
  
#### <a name="topclause"></a>TopClause  
 TopClause bir SqlSelectStatement üst ifadesinde temsil eder. TopCount özelliği üst satır sayısını seçilmelidir gösterir.  WithTies true olduğunda, TopClause DbLimitExpession üretilmiştir.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Simgeleri  
 Simge ile ilgili sınıflar ve simge tablosunu giriş diğer adı yeniden adlandırma, diğer ad JOIN düzleştirme ve sütun diğer adı yeniden adlandırma gerçekleştirin.  
  
 Sembol sınıfı bir kapsam, iç içe geçmiş bir SELECT deyimi veya bir sütunu temsil eder. Gerçek bir diğer ad yerine kullanılmış ve ayrıca (türü gibi) temsil eden yapı için ek bilgi taşıyan sonra yeniden adlandırma işlemi için izin vermek için kullanılır.  
  
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
  
 Gösterilen azami ölçüde, iç içe geçmiş SELECT deyimi veya bir sütun özgün diğer adını depolar.  
  
 NewName kullanılacak olan diğer SQL SELECT deyiminde depolar. Bu özgün adına ayarlayın ve yalnızca son dizede sorgu oluşturulurken gerektiğinde yeniden adlandırıldı.  
  
 Türü yalnızca kapsam ve iç içe geçmiş SELECT deyimi temsil eden simgelerini yararlıdır.  
  
#### <a name="symbolpair"></a>SymbolPair  
 SymbolPair sınıfı kayıt düzleştirme giderir.  
  
 Bir özellik ifadesi (v, "j3.j2.j1.a.x") D VarRef, j1, j2 v olduğu düşünün, j3 birleştirme, bir bir kapsam, x ise bir sütun.  
  
 Bu içine süre sonra çevrilmesi gerekiyor {j'}. {x'}. Kaynak alanı birleştirme ifadesi (deyin j2); temsil eden dıştaki SqlStatement temsil eder her zaman bir birleşim simge budur. Bir birleştirme dışı simgeyi durduruluncaya kadar sütun alanı bir birleşim simgesini diğerine taşır. Bu bir DbPropertyExpression ziyaret eden döndürülür, ancak hiçbir zaman bir SqlBuilder eklendi.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 Bir birleştirme simge bir birleşim veya Giriş birleşim iç içe geçmiş SELECT deyimiyle temsil eden bir simge ' dir.  
  
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
  
 SQL SELECT deyimine bu simgeyi temsil ediyorsa ColumnList SELECT yan tümcesinde sütun listesini temsil eder. ExtentList SELECT yan tümcesinde uzantıların listesi verilmiştir. Birleşim en üst düzeyinde düzleştirilmiş birden çok kapsam varsa, diğer adlar doğru olarak adlandırılır, uzantı emin olmak için kapsam FlattenedExtentList izler.  
  
 NameToExtent ExtentList tüm uzantıda bir sözlük olarak sahiptir. IsNestedJoin bir JoinSymbol bir sıradan birleştirme simge veya karşılık gelen SqlSelectStatement içeren olup olmadığını belirlemek için kullanılır.  
  
 Tüm listeleri tam olarak bir kez ayarlayın ve sonra arama veya numaralandırma için kullanılır.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable simgeleri değişken adları çözmek için kullanılır. SymbolTable her kapsam için yeni bir giriş yığın olarak uygulanır. Bir giriş bulunana kadar aramaları yığının üst kısmından altına arayın.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Sql üretimi modülü bir örneği başına yalnızca bir SymbolTable yoktur. Kapsamları girilen ve ilişkisel her düğüm için çıkıldı. Önceki kapsamlar tüm sembolleri aynı ada sahip başka sembollerin tarafından gizli sürece sonraki kapsamlar için görünür durumdadır.  
  
### <a name="global-state-for-the-visitor"></a>Ziyaretçi için genel durum  
 Diğer adlar ve sütunları yeniden adlandırma yardımcı olmak üzere tüm sütun adlarının (AllColumnNames) listesini korumak ve ilk kullanılan ölçüde diğer adlarını (AllExtentNames) sorgu ağaç geçirin.  Sembol tablosuna değişken adları simgeleri çözümler. IsVarRefSingle yalnızca kullanılan doğrulama amacıyla kesinlikle gerekli değildir.  
  
 CurrentSelectStatement ve IsParentAJoin aracılığıyla kullanılan iki yığınları ziyaretçi düzeni bize parametreleri izin vermiyor bu yana "parametreleri" alt düğümleri için üst öğeden geçirmek için kullanılır.  
  
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
  
## <a name="common-scenarios"></a>Yaygın senaryolar  
 Bu bölümde, yaygın sağlayıcısı senaryolar açıklanmaktadır.  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>SQL deyimleri ifade düğümleri gruplandırma  
 İlk ilişkisel düğümü karşılaşıldığında bir SqlSelectStatement oluşturulur (genellikle DbScanExpression ölçüde) ağacında yukarı Alttan ziyaret ederken. Bir SQL SELECT deyimiyle az olarak üretmek için olabildiğince, üst düğümlerinden bu SqlSelectStatement mümkün olduğunca çoğunu olarak toplama sorguları iç içe geçmiş.  
  
 Verilen (ilişkisel) düğüm geçerli SqlSelectStatement (giriş ziyaret eden döndürülen bir) eklenebilmesi için veya yeni bir sistem başlatılması gerekip gerekmediğine karar IsCompatible yöntemi tarafından hesaplanır ve hangi zaten içinde olduğuna bağlıdır SqlSelectStatement ne düğümleri verilen düğüm olan üzerinde bağlıdır.  
  
 Genellikle, SQL deyimini yan tümceleri burada birleştirme için kabul düğümleri boş olmayan yan tümceleri sonra değerlendirildiğinde düğüm geçerli ifadesine eklenemez. Bir sonraki düğüme bir filtre ise, yalnızca aşağıdaki doğruysa, örneğin, o düğümü geçerli SqlSelectStatement birleştirilebilir:  
  
-   Seçim listesi boş. Seçim listesi boş değilse seçim listesi filtre önceki bir düğüm tarafından üretilen ve koşul bu seçim listesi tarafından üretilen sütunlara başvurabilir.  
  
-   GROUPBY boştur. Filtre ekleme, GROUPBY boş değilse, doğru değil gruplandırma önce filtreleme anlamına gelir.  
  
-   TOP yan tümcesi boştur. Filtre ekleme, TOP yan tümcesinde boş değilse, doğru değil üst yapmadan önce filtreleme anlamına gelir.  
  
 Bunlar her zaman mevcut bir SqlSelectStatement bir parçası olarak dahil olduğu için bu DbConstantExpression veya aritmetik ifadeler gibi ilişkisel olmayan düğümleri için geçerli değildir.  
  
 Ayrıca, (bir birleşim üst öğesi yok bir birleşim düğümü) katılma ağacının kökü karşılaşıldığında, yeni SqlSelectStatement başlatılır. Tüm sol Sırt birleştirme alt o SqlSelectStatement toplanır.  
  
 Yeni SqlSelectStatement başlatıldığından ve geçerli bir giriş eklenen her geçerli SqlSelectStatement biri yoksa, projeksiyon sütunlar (bir SELECT yan tümcesi) ekleyerek tamamlanması gerekir. Bu yöntem, SqlSelectStatement FromExtents arar ve tahmini sütunlar listesine kapsamdaki FromExtents tarafından temsil edilen uzantıların listesini getirir tüm sütunları ekleyen AddDefaultColumns gerçekleştirilir. Bu noktada, hangi sütunların diğer düğümleri tarafından başvurulan bilinmeyen olduğundan bu, gerçekleştirilir. Bu, daha sonra kullanılabilir sütunlar yalnızca projeye iyileştirilebilir.  
  
### <a name="join-flattening"></a>Düzleştirme katılma  
 IsParentAJoin özelliği, verilen bir birleştirme düzleştirilmiş olup olmadığını belirlemenize yardımcı olur. Özellikle, IsParentAJoin döndürür `true` yalnızca bir birleştirme ve hemen her DbScanExpression için sol alt durumda bir birleştirme için o alt düğüm giriş için üst daha sonra kullanacağınız aynı SqlSelectStatement yeniden kullanır. Daha fazla bilgi için "Katılma ifadeleri" konusuna bakın.  
  
### <a name="input-alias-redirecting"></a>Diğer ad yönlendirme giriş  
 Giriş diğer adı yeniden yönlendirme sembol tablosu gerçekleştirilir.  
  
 İlk örnekte başvurmak giriş diğer adı yeniden yönlendirme açıklamak için [komut ağaçlarını - en iyi uygulamaları oluşturma SQL'den](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Yok "a" gerekli "b" projeksiyon yönlendirilmesi.  
  
 Bir SqlSelectStatement nesnesi oluşturulduğunda, giriş düğüme ölçüde SqlSelectStatement From özelliğinde yerleştirilir. Bir simge (< symbol_b >) o uzantı temsil etmek için giriş bağlaması adı ("b") ve "AS" temel alınarak oluşturulur + < symbol_b > From yan tümcesi için eklenir.  Simgenin FromExtents özelliğine de eklenir.  
  
 Simgenin de giriş bağlaması adı ("b", < symbol_b >) bağlamak üzere sembol tablosuna eklenir.  
  
 Bir sonraki düğüme bu SqlSelectStatement yeniden kullanır, bir giriş için bu simgeyi giriş bağlaması adını bağlamak için Sembol tablosuna ekler. Bizim örneğimizde, giriş bağlaması adı "a" ile DbProjectExpression SqlSelectStatement yeniden kullanmak ve Ekle ("a", \< symbol_b >) tablosu.  
  
 İfadeleri SqlSelectStatement yeniden düğümünün giriş bağlaması adı başvurduğunuzda, bu başvuruyu doğru yeniden yönlendirilen simgesine sembol tablosunu kullanarak çözümlenir. "A.x" den "a" DbVariableReferenceExpression temsil eden ziyaret ederken çözümlendiğinde "a" BT < symbol_b > simgenin çözümleyin.  
  
### <a name="join-alias-flattening"></a>Diğer ad düzleştirme katılma  
 DbPropertyExpression başlıklı bölümde açıklandığı gibi bir DbPropertyExpression ziyaret zaman diğer birleştirme düzleştirme elde edilir.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantı Alias yeniden adlandırma  
 İkinci aşama, SQL üretimi başlıklı bölümde açıklanan nesil ikinci aşamasında diğer adları ile yalnızca değiştirilen simgeleri kullanarak sütun adı ve diğer ad uzantısı yeniden adlandırma sorunu ele: dize komutu oluşturuluyor.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>Birinci aşama SQL oluşturma: ifade ağacına ziyaret edin  
 Bu bölümde SQL oluşturma, ne zaman ifade sorgu ziyaret edilen temsil eden ve Ara yapısı üretileceğini, ilk aşaması ya da bir SqlSelectStatement veya bir SqlBuilder açıklanmaktadır.  
  
 Bu bölümde, ziyaret farklı ifade düğümü kategorileri ilkeleri ve belirli ifade türleri ziyaret Ayrıntılar açıklanmaktadır.  
  
### <a name="relational-non-join-nodes"></a>İlişkisel (birleştirme olmayan) düğümler  
 Aşağıdaki ifade türleri birleştirme olmayan düğümler destekler:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   Bir DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Bu düğümler ziyaret şu deseni izler:  
  
1.  İlişkisel giriş sayfasını ziyaret edin ve sonuçta elde edilen SqlSelectStatement alın. İlişkisel bir düğüme giriş aşağıdakilerden biri olabilir:  
  
    -   Bir uzantı (örneğin, bir DbScanExpression) dahil olmak üzere bir ilişkisel düğüm. Bu tür bir düğüm ziyaret eden bir SqlSelectStatement döndürür.  
  
    -   Küme işlemi ifadesi (UNION ALL, örneğin). Parantez içine alınmış ve yeni SqlSelectStatement FROM yan tümcesinde put sonuç vardır.  
  
2.  Geçerli düğüm giriş tarafından üretilen SqlSelectStatement eklenebilir olup olmadığını denetleyin. SQL deyimleri gruplandırma ifadeleri başlıklı bölümde bu açıklanmaktadır. Aksi durumda,  
  
    -   Geçerli SqlSelectStatement nesne açılır.  
  
    -   Yeni bir SqlSelectStatement nesnesi oluşturun ve yeni SqlSelectStatement nesnenin FROM popped SqlSelectStatement ekleyin.  
  
    -   Yeni nesne yığının en üstünde yerleştirin.  
  
3.  Giriş ifadesi bağlama doğru simge girdisinden yönlendirin. Bu bilgiler SqlSelectStatement nesnesinde korunur.  
  
4.  Yeni bir SymbolTable kapsamı ekleyin.  
  
5.  İfade (örneğin, yansıtma ve koşulu) giriş olmayan parçası ziyaret edin.  
  
6.  Genel yığınları eklenen tüm nesneler açılır.  
  
 DbSkipExpression SQL doğrudan bir eşdeğer yok. Mantıksal olarak, veri dönüştürülür:  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>İfadeler katılma  
 Aşağıdaki birleşim ifadeleri olarak kabul edilir ve ortak bir biçimde VisitJoinExpression yöntemi tarafından işlenir:  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 Ziyaret adımları şunlardır:  
  
 İlk olarak, alt öğelerini ziyaret önce IsParentAJoin birleştirme düğümü bir birleştirme sol Sırt boyunca alt olup olmadığını denetlemek için çağrılır. False değeri döndürülürse, yeni SqlSelectStatement başlatılır. (Birleştirme düğümü) üst SqlSelectStatement büyük olasılıkla kullanılacak çocuklar için oluştururken bu anlamda birleştirmeler farklı düğümlerin geri kalanından ziyaret edilen.  
  
 İkinci olarak, bir girdi bir kerede işleme. Her giriş için:  
  
1.  Giriş sayfasını ziyaret edin.  
  
2.  POST işlemi JOIN ifadesinin bir alt ziyaret ve büyük olasılıkla alt tarafından üretilen SqlSelectStatement bittikten sonra simge tablosunun bakımı için sorumlu olduğu ProcessJoinInputResult, çağırarak giriş ziyaret sonucu. Çocuğunuzun sonucu aşağıdakilerden biri olabilir:  
  
    -   Üst eklenecek sunucudan farklı bir SqlSelectStatement. Böyle bir durumda, varsayılan sütunları ekleyerek tamamlanmış olması gerekebilir. Giriş bir birleştirme olduysa, yeni bir birleşim sembol oluşturmanız gerekir. Aksi takdirde, normal bir simge oluşturun.  
  
    -   Yalnızca üst girişleri listesine eklenen durum SqlSelectStatement kullanıcının bir uzantı (bir DbScanExpression, örneğin).  
  
    -   Servis talebi ile sarılır ayraçlar içinde olmayan bir SqlSelectStatement.  
  
    -   Üst ekleneceği aynı SqlSelectStatement. Böyle bir durumda FromExtents listesinde simgelerin tümünü temsil eden tek yeni bir JoinSymbol değiştirilmesi gerekir.  
  
    -   İlk üç durumlarda, AddFromSymbol AS yan tümcesi ekleyin ve sembol tablosunu güncelleştirmek için çağrılır.  
  
 Üçüncü (varsa) birleştirme koşulunun ziyaret edilen.  
  
### <a name="set-operations"></a>Ayarlama İşlemleri  
 Ayarlama işlemleri DbUnionAllExpression, DbExceptExpression ve DbIntersectExpression VisitSetOpExpression yöntemi tarafından işlenir. Şeklin SqlBuilder oluşturur  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Burada \<leftSqlSelectStatement > ve \<rightSqlSelectStatement > olan her girdi ziyaret ederek elde SqlSelectStatements ve \<setOp > karşılık gelen (UNION ALL örneğin) bir işlemdir.  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 (Başka bir birleştirme sol alt bir birleştirme girdi) olarak bir birleşim bağlamında ziyaret ettiğinde DbScanExpression SqlBuilder tanımlayan bir sorgu, tablo veya Görünüm karşılık gelen hedef hedef SQL ile döndürür. Aksi takdirde, yeni SqlSelectStatement Kimden alanı karşılık gelen hedef karşılık gelecek şekilde ayarlanmış oluşturulur.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Bir DbVariableReferenceExpression ziyaret simgesi tablosundaki Ara temel Bu değişken başvuru ifade ile eşleşen simgesini döndürür.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Diğer ad JOIN düzleştirme tanımlanmış ve bir DbPropertyExpression ziyaret eden işlenen.  
  
 Örnek özelliği ilk kez ziyaret ve bir sembol, bir JoinSymbol ya da bir SymbolPair sonucudur. Bu üç durumda işlenme aşağıda verilmiştir:  
  
-   Bir JoinSymbol döndürülürse, kendi NameToExtent özelliği gerekli bir özellik için bir simge içerir. İç içe geçmiş bir birleşim birleştirme simgenin temsil ediyorsa, yeni bir simge çifti örneği diğer ad olarak kullanılan simge izlemek için birleştirme simgesi ile daha fazla çözümleme için gerçek özelliğini temsil eden simgesi ile döndürülür.  
  
-   Bir SymbolPair döndürülür ve bir birleşim simge sütun parçası ise, bir birleşim simge tekrar döndürülür, ancak column özelliği için geçerli özellik ifade tarafından temsil edilen özelliği işaret edecek şekilde güncelleştirilmiştir. Aksi takdirde bir SqlBuilder diğer adını ve sütun olarak geçerli bir özellik için simge olarak SymbolPair kaynağıyla döndürülür.  
  
-   Bir simge döndürülürse, ziyaret yöntemi SqlBuilder yöntemi bu örneği diğer ad olarak ve sütun adı olarak özellik adını döndürür.  
  
### <a name="dbnewinstanceexpression"></a>Dbnewınstanceexpression  
 DbProjectExpression projeksiyon özelliği olarak kullanıldığında, Dbnewınstanceexpression tahmini sütunları temsil etmek için bağımsız değişkenlerin virgülle ayrılmış bir liste oluşturur.  
  
 Dbnewınstanceexpression koleksiyonu dönüş türü olan ve yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonunu tanımlar, aşağıdaki üç durumda ayrı olarak ele alınmıştır:  
  
-   Dbnewınstanceexpression tek bağımsız değişken olarak DbElementExpression varsa, aşağıdaki gibi çevrilir:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Dbnewınstanceexpression bağımsız değişkenler varsa (boş bir tablo gösterir) Dbnewınstanceexpression çevrilir:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 Aksi takdirde Dbnewınstanceexpression UNION all basamaklardan bağımsız değişkenlerden biri oluşturur:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Kurallı ve yerleşik işlevler aynı şekilde işlenir: özel işleme (örneğin LTRIM(RTRIM(string) için TRIM(string)) ihtiyacınız varsa, uygun işleyiciyi çağrılır. Aksi halde bunlar (arg1, arg2,..., argn) FunctionName çevrilir.  
  
 Sözlük, hangi işlevleri özel işleme ve bunların uygun işleyicileri gereksinim izlemek için kullanılır.  
  
 Kullanıcı tanımlı işlevler (arg1, arg2,..., argn) NamespaceName.FunctionName tanslated içindedir.  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 DbElementExpression ziyaret yöntemi yalnızca bir skaler alt sorgu temsil etmek üzere kullanıldığında DbElementExpression ziyaret için çağrılır. Bu nedenle, DbElementExpression tam SqlSelectStatement dönüşür ve köşeli ayraç içine ekler.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 İfade türüne bağlı olarak (veya tamamını), DbQuantifierExpression çevrilir olarak:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>DbNotExpression  
 Bazı durumlarda DbNotExpression çeviri ile giriş ifadesi daraltmak mümkündür. Örneğin:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 İkinci Daralt gerçekleştirilen nedeni, DbQuantifierExpression çevirme yazdığınızda, tüm verimsiz sağlayıcı tarafından sunulan nedeni. Bu nedenle Entity Framework basitleştirme yapmadıysanız.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression olarak çevrilir:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL üretimi ikinci aşaması: dize komutu oluşturuluyor  
 Bir dize SQL komutu oluştururken SqlSelectStatement hangi sütun adı ve diğer ad uzantısı yeniden adlandırma sorunu giderir sembolleri için gerçek diğer adlar üretir.  
  
 Diğer ad uzantısı yeniden adlandırma bir dizeye SqlSelectStatement nesne yazılırken oluşur. İlk dış kapsam tarafından kullanılan tüm diğer adları listesini oluşturun. Her simge FromExtents (veya null olmayan ise AllJoinExtents) herhangi bir dış kapsam ile çakışırsa adı. Yeniden adlandırma gerekirse AllExtentNames içinde toplanan kapsam biriyle çakışmamasını.  
  
 Sütun yeniden adlandırma, bir dizeyi bir sembol nesnesi yazılırken oluşur. İlk aşamada AddDefaultColumns belirli bir sütun simge yeniden adlandırılacak olup olmadığını belirledi. İkinci aşamasında, üretilen adı AllColumnNames içinde kullanılan herhangi bir ad ile çakışmadığından emin yalnızca yeniden adlandırma ortaya çıkar  
  
 Uzantı diğer adlar ve sütunlar için benzersiz adlar oluşturmak için n henüz kullanılmamış küçük diğer adı olduğu < existing_name > _n kullanın. Tüm diğer adları genel listesini basamaklı yeniden adlandırır gereksinimini artırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
