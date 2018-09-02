---
title: Mimari ve tasarım
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 5a0d8aac401a3485bc5f158bcda893ad9ab424e8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419610"
---
# <a name="architecture-and-design"></a>Mimari ve tasarım
SQL üretimi modülünde [örnek sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=180616) komut ağacı temsil eden ifade ağacında bir ziyaretçi olarak uygulanır. Oluşturma, tek bir geçişinde ifade ağacı gerçekleştirilir.  
  
 Ağaç düğümleri aşağıdan yukarı işlenir. İlk olarak, bir ara yapı üretilir: SqlSelectStatement veya SqlBuilder, her iki uygulama ISqlFragment. Ardından, dize SQL deyimi, yapısından oluşturulur. Ara yapı için iki nedeni vardır:  
  
-   Mantıksal olarak bir SQL SELECT deyimi sıralamaya doldurulur. FROM yan tümcesinde katılan düğümleri, WHERE, GROUP BY ve ORDER BY yan tümcesi içinde katılan düğümleri önce ziyaret.  
  
-   Diğer adlar yeniden adlandırmak için yeniden adlandırma sırasında çarpışmalardan kaçınmak için kullanılan tüm diğer adlarını tanımlamanız gerekir. Yeniden adlandırma seçenekleri SqlBuilder erteleneceği sütunları yeniden adlandırma için aday niteliği temsil etmek için Sembol nesneleri kullanır.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 İfade ağacı ziyaret sırasında ilk aşamada ifadeleri SqlSelectStatements gruplandırılır ve birleşimler düzleştirilmiş birleştirme diğer adlar düzleştirilir. Bu geçişi sırasında sembol nesneleri, sütunları veya yeniden adlandırılabilir giriş diğer adları temsil eder.  
  
 Gerçek dize üretme sırasında İkinci aşamada, diğer adlar yeniden adlandırılır.  
  
## <a name="data-structures"></a>Veri yapıları  
 Bu bölümde kullanılan türleri ele alınmaktadır [örnek sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=180616) bir SQL deyimi oluşturmak için kullanın.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 Bu bölüm iki amaca hizmet eder ISqlFragment arabirimi uygulayan sınıflar kapsamaktadır:  
  
-   Ziyaretçi yöntemleri için ortak bir dönüş türü.  
  
-   Son SQL dizesi yazmak için bir yöntem sağlar.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder son SQL dizesi, StringBuilder için benzer bir toplama cihazdır. Dizelere dönüştürülebileceği ISqlFragments birlikte en son SQL oluşturan dizeleri oluşur.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 Kurallı bir SQL SELECT deyimi "seçin... şeklin SqlSelectStatement temsil eder KAYNAK.. WHERE... GRUPLANDIRMA ÖLÇÜTÜ... ORDER BY".  
  
 Her SQL maddeleri uygulamasının, çünkü StringBuilder tarafından temsil edilir. Ayrıca, farklı belirtilmiş olup olmadığını ve deyim üstteki olup olmadığını izler. Deyim üstteki değilse, deyim bir TOP yan tümcesini olmadıkça ORDER BY yan tümcesi atlanır.  
  
 SELECT deyimi için giriş listesinin FromExtents içerir. Olur ve genellikle tek öğe bu. SELECT deyimleri birleştirmeler için geçici olarak birden fazla öğe olabilir.  
  
 SELECT deyimi bir birleşim düğümü tarafından oluşturduysanız SqlSelectStatement AllJoinExtents içinde birleştirme düzleştirilmiş tüm uzantıların listesini tutar. OuterExtents SqlSelectStatement dış başvuruları temsil eder ve giriş diğer adı yeniden adlandırmak için kullanılır.  
  
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
 TopClause üst ifadede bir SqlSelectStatement temsil eder. ÜST satırları seçilmelidir TopCount özelliği belirtir.  WithTies true olduğunda, bir DbLimitExpession TopClause oluşturulmuştur.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Simgeleri  
 Sembol ile ilgili sınıflar ve sembol tablosuna sütun diğer adı yeniden adlandırma giriş diğer adı yeniden adlandırma ve diğer ad birleştirme düzleştirme gerçekleştirin.  
  
 Sembol sınıfı, bir uzantı, iç içe geçmiş bir SELECT deyimi veya bir sütunu temsil eder. Gerçek bir diğer ad yerine kullanılmış ve ayrıca daha fazla bilgi için (türü gibi) temsil ettiği yapıt taşır, sonra yeniden adlandırmak için izin vermek için kullanılır.  
  
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
  
 Gösterilen ölçüde, iç içe geçmiş bir SELECT deyimi veya bir sütun özgün diğer adını depolar.  
  
 NewName SQL SELECT deyimi kullanılacak diğer depolar. Bu özgün adına ayarlayın ve yalnızca son dizede sorgu oluşturma sırasında gerekirse yeniden adlandırıldı.  
  
 Türü yalnızca kapsamları ve iç içe geçmiş bir SELECT deyimi temsil eden simge için kullanışlıdır.  
  
#### <a name="symbolpair"></a>SymbolPair  
 Kayıt düzleştirme SymbolPair sınıfı ele alır.  
  
 Bir özellik ifadesi VarRef, j1, j2 v olduğu D (v, "j3.j2.j1.a.x") göz önünde bulundurun, j3 birleşimler, bir uzantı ve x ise bir sütun.  
  
 Bu oturum sonunda çevrilmesi gerekir {j'}. {x'}. Kaynak alanı (örneğin j2); bir birleştirme ifadeyi temsil eden, en dıştaki sqldeyimi temsil eder. Bu her zaman bir birleşim semboldür. Bir birleştirme dışı simgeyi durduruluncaya kadar sütun alanı bir birleşim sembolünden diğerine taşır. Bu bir DbPropertyExpression ziyaret döndürülür, ancak hiçbir zaman bir SqlBuilder için eklendi.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 İç içe geçmiş bir SELECT deyimi bir birleşim veya Giriş bir birleşim ile temsil eden bir simge bir birleşim semboldür.  
  
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
  
 Bir SQL SELECT deyimi bu simgeyi temsil ediyorsa ColumnList SELECT yan tümcesindeki sütun listesini temsil eder. ExtentList kapsamlarını SELECT yan tümcesinde listesidir. Birleşim en üst düzeyinde düzleştirilmiş birden çok kapsam varsa, bu uzantı diğer adları doğru şekilde adlandırılır emin olmak için kapsam FlattenedExtentList izler.  
  
 NameToExtent ExtentList içindeki tüm kapsamları bir sözlük olarak sahiptir. IsNestedJoin bir JoinSymbol sıradan birleştirme sembol veya karşılık gelen SqlSelectStatement içeren olup olmadığını belirlemek için kullanılır.  
  
 Tüm listeleri tam olarak ayarlamalı ve sonra aramaları veya numaralandırma için kullanılır.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable sembollere değişken adlarını çözmek için kullanılır. SymbolTable yığını ile her kapsam için yeni bir giriş olarak uygulanır. Bir giriş bulunana kadar aramaları yığının en üstünden en altına arayın.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Sql oluşturma modülü bir örneği başına yalnızca bir SymbolTable yoktur. Kapsamları girilen ve ilişkisel her düğüm için çıkıldı. Önceki kapsamlardaki tüm sembolleri aynı ada sahip diğer simgeler tarafından gizlenmiş sürece sonraki kapsamlar için görünür değildir.  
  
### <a name="global-state-for-the-visitor"></a>Ziyaretçi için genel durum  
 Diğer adlar ve sütunları yeniden adlandırma yardımcı olmak için tüm sütun adlarının (AllColumnNames) listesini korumak ve sorgu ağacına ilk kullanılan uzantı diğer adları (AllExtentNames) geçirin.  Sembol tablosuna değişken adları için semboller çözümleniyor. IsVarRefSingle yalnızca kullanılan doğrulama amacıyla kesinlikle gerekli değildir.  
  
 CurrentSelectStatement ve IsParentAJoin kullanılan iki yığınları ziyaretçi deseni parametreleri geçirmek bize izin vermediği "parameters" alt düğümleri için üst öğeden geçirmek için kullanılır.  
  
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
 Bu bölümde, sağlayıcı senaryoları ele alınmaktadır.  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>SQL Açıklamaalarını ifade düğümleri gruplandırma  
 İlk ilişkisel düğümü ile karşılaşıldığında bir SqlSelectStatement oluşturulur (genellikle DbScanExpression ölçüde) yedekleme alt ağacı ziyaret edildiğinde. Bir SQL SELECT deyimi ile birkaç olarak üretmek için olabildiğince, üst düğümlerinden bu SqlSelectStatement olabildiğince fazla sayıda toplama sorguları iç içe geçmiş.  
  
 Verilen (ilişkisel) bir düğüm geçerli SqlSelectStatement (giriş ziyaret döndürülen bir) eklenebilmesi için veya yeni bir deyim başlatılması gerekip gerekmediğine karar IsCompatible yöntemiyle hesaplanır ve hangi zaten kullanımda olduğuna bağlıdır SqlSelectStatement hangi düğümleri verilen düğüm olan üzerinde bağlıdır.  
  
 Genellikle, SQL deyimi yan tümceleri burada birleştirmesi için dikkate düğümleri boş olmayan yan tümcelerinden sonra değerlendirilir, düğüm için geçerli deyim eklenemez. Bir filtre sonraki düğümü ise yalnızca aşağıdaki true ise örneğin, o düğümde geçerli SqlSelectStatement dahil edilebilir:  
  
-   Seçim listesi boş. Seçim listesi boş değilse seçim listesine filtre önceki bir düğüm tarafından oluşturulan ve koşul bu seçim listesi tarafından üretilen sütunlarına başvurabilir.  
  
-   GROUPBY boştur. Filtre ekleme, GROUPBY boş değilse, doğru değil gruplandırma önce filtreleme anlamına gelir.  
  
-   TOP yan tümcesini boştur. Filtre ekleme, TOP yan tümcesini boş değilse, doğru olmayan üst gerçekleştirmeden önce filtreleme anlamına gelir.  
  
 Bunlar her zaman mevcut bir SqlSelectStatement bir parçası olarak dahil edilir çünkü bu DbConstantExpression veya aritmetik ifadeler gibi ilişkisel olmayan düğümleri için geçerli değildir.  
  
 Ayrıca, (bir birleşim üst öğesi yok bir birleşim düğümü) birleştirme ağacının kökü ile karşılaşıldığında, yeni SqlSelectStatement başlatılır. Tüm alt sol Sırt birleştirme öğelerini bu SqlSelectStatement toplanır.  
  
 Yeni bir SqlSelectStatement başlatıldığından ve geçerli bir giriş eklendiğinde her geçerli SqlSelectStatement yoksa bir projeksiyon sütunları (SELECT yan) ekleyerek tamamlanmış olması gerekebilir. Bu, SqlSelectStatement FromExtents görünümünü ve öngörülen sütun listesi için kapsamda FromExtents tarafından temsil edilen uzantıların listesini getirir. tüm sütunları ekler, AddDefaultColumns yöntemiyle gerçekleştirilir. Bu noktada, hangi sütunların diğer düğümler tarafından başvurulan bilinmeyen olduğundan bu, gerçekleştirilir. Bu, yalnızca daha sonra kullanılabilir sütunlar projeye iyileştirilebilir.  
  
### <a name="join-flattening"></a>Düzleştirme katılın  
 IsParentAJoin özelliği belirli bir birleştirme düzleştirilmiş olup olmadığını belirler. Özellikle, IsParentAJoin döndürür `true` üst daha sonra kullanacağınız aynı SqlSelectStatement yalnızca bir anlıktır her DbScanExpression ve bir birleşimin sol alt durumda bir birleştirme için o alt düğüm girişi için kullanır. Daha fazla bilgi için "Expressions birleştirme" bakın.  
  
### <a name="input-alias-redirecting"></a>Giriş diğer adı yeniden yönlendirme  
 Giriş diğer adı yeniden yönlendirme, sembol tablosu ile gerçekleştirilir.  
  
 Giriş diğer adı yeniden yönlendirme açıklamak için ilk örnekte bakın [SQL oluşturma - komut ağaçlarından en iyi](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Burada "a" gerekli "b" yansıtma yönlendirilecek.  
  
 SqlSelectStatement nesne oluşturulduğunda, giriş düğümüne ölçüde SqlSelectStatement Kimden özelliğinde konur. Bir simge (< symbol_b >) Bu uzantı temsil etmek için giriş bağlamasına adı ("b") ve "AS" dayanarak oluşturulan + < symbol_b > From yan tümcesi için eklenir.  Simgenin FromExtents özelliğini de eklenir.  
  
 Sembolü sembol tablosuna giriş bağlaması adı ("b", < symbol_b >) bağlamak üzere de eklenir.  
  
 Bir sonraki düğümü bu SqlSelectStatement kullanır, bu sembole giriş bağlama adını bağlamak için Sembol tablosuna bir giriş ekler. Bizim örneğimizde, giriş bağlaması adı "a" ile DbProjectExpression SqlSelectStatement yeniden ve ekleyin ("a", \< symbol_b >) tablo.  
  
 İfadeleri SqlSelectStatement yeniden düğümünün giriş bağlaması adı başvurduğunuzda, bu başvuruyu kullanarak doğru yeniden yönlendirilen sembolü sembol tablosuna çözümlenir. "A.x" öğesinden "a" DbVariableReferenceExpression temsil eden ziyaret ederken çözümlendiğinde "a" BT < symbol_b > Sembole çözülecektir.  
  
### <a name="join-alias-flattening"></a>Diğer ad düzleştirme katılın  
 DbPropertyExpression başlıklı bölümde açıklanan şekilde bir DbPropertyExpression ziyaret, diğer ad birleştirme düzleştirme elde edilir.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantısı diğer adını yeniden adlandırma  
 İkinci aşamada ikinci aşaması, SQL Oluşturma başlıklı bölümde açıklanan oluşturma diğer adları ile yalnızca değiştirilen simgeler kullanarak sütun adı ve diğer ad uzantısı yeniden adlandırma sorunu ele: dize komutu oluşturuluyor.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>SQL üretimi ilk aşaması: ifade ağacı ziyaret edin  
 Bu bölümde, sorgu ziyaret edilen ifade gösteren ve bir ara yapı oluşturulur, SQL oluşturma, ilk aşaması ya da bir SqlSelectStatement veya bir SqlBuilder açıklanmaktadır.  
  
 Bu bölümde, ilkeler ziyaret farklı ifade düğüm kategoriler ve belirli bir ifade türleri ziyaret ayrıntılarını açıklar.  
  
### <a name="relational-non-join-nodes"></a>İlişkisel (birleştirme olmayan) düğümler  
 Aşağıdaki ifade türleri birleştirme olmayan düğümleri destekler:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Bu düğümler ziyaret şu deseni izler:  
  
1.  İlişkisel giriş sayfasını ziyaret edin ve sonuçta elde edilen SqlSelectStatement alın. İlişkisel bir düğüme giriş aşağıdakilerden biri olabilir:  
  
    -   Bir uzantı (örneğin, bir DbScanExpression) dahil olmak üzere bir ilişkisel düğümü. Bu tür bir düğüm ziyaret bir SqlSelectStatement döndürür.  
  
    -   Küme işlemi ifadesi (UNION ALL, örneğin). Köşeli ayraç içinde sarmalanmış ve yeni SqlSelectStatement FROM yan tümcesinde put sonucu vardır.  
  
2.  Geçerli düğüm giriş tarafından üretilen SqlSelectStatement eklenebilir olup olmadığını denetleyin. Bu gruplandırma ifadeleri bölümüne SQL Açıklamaalarını açıklar. Aksi halde  
  
    -   Geçerli SqlSelectStatement nesne açılır.  
  
    -   Yeni bir SqlSelectStatement nesnesi oluşturun ve yeni SqlSelectStatement nesnenin başlangıç popped SqlSelectStatement ekleyin.  
  
    -   Yeni nesne yığının en üstünde yerleştirin.  
  
3.  Giriş ifadesini bağlama doğru sembole girdiden yönlendirin. Bu bilgiler SqlSelectStatement nesnesinde korunur.  
  
4.  Yeni bir SymbolTable kapsam ekleyin.  
  
5.  İfade (örneğin, yansıtma ve koşul) olmayan giriş bölümünü ziyaret edin.  
  
6.  Genel yığınları için eklenen her nesne açılır.  
  
 DbSkipExpression SQL'de doğrudan bir eşdeğer yok. Mantıksal olarak veri dönüştürülür:  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>İfadeleri katılın  
 Aşağıdaki birleştirme ifadeler değerlendirilir ve yaygın bir şekilde VisitJoinExpression yöntemi tarafından işlenir:  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 Ziyaret uygulamanız gereken adımlar şunlardır:  
  
 İlk olarak, alt gitmeden önce IsParentAJoin birleştirme düğümün bir alt bir birleşimin sol Sırt boyunca olup olmadığını denetlemek için çağrılır. False döndürürse, yeni SqlSelectStatement başlatılır. Üst (birleştirme düğüm) için büyük olasılıkla kullanılacak alt SqlSelectStatement oluşturduğundan bu anlamda birleştirmeler farklı düğümlerin geri kalanından ziyaret.  
  
 İkinci olarak, bir giriş teker teker işler. Her giriş için:  
  
1.  Giriş sayfasını ziyaret edin.  
  
2.  POST işlemi ProcessJoinInputResult, sembol tablosuna bir JOIN ifadesinin bir alt ziyaret ve büyük olasılıkla alt tarafından üretilen SqlSelectStatement bittikten sonra bakımından sorumlu olduğu çağırarak giriş ziyaret sonucu. Alt sonuç aşağıdakilerden biri olabilir:  
  
    -   Bir üst eklenecek farklı SqlSelectStatement. Böyle bir durumda, varsayılan sütunlar ekleyerek tamamlanmış olması gerekebilir. Bir birleştirme giriş ise, yeni bir birleştirme sembol oluşturmanız gerekir. Aksi takdirde, normal bir sembol oluşturun.  
  
    -   Uzantı, yalnızca üst girişleri listesine eklenmiş SqlSelectStatement kullanıcının (bir DbScanExpression, örneğin).  
  
    -   İle kaydırılan çalışması, köşeli ayraçlar değil bir SqlSelectStatement.  
  
    -   Üst ekleneceği aynı SqlSelectStatement. Böyle bir durumda FromExtents listesinde simgelerin tümünü temsil eden tek yeni bir JoinSymbol değiştirilmesi gerekir.  
  
    -   İlk üç durumlarda AddFromSymbol, AS yan tümcesi ekleyin ve sembol tablosunu güncelleştirmek için çağrılır.  
  
 Birleştirme koşulunun (varsa) üçüncü ziyaret.  
  
### <a name="set-operations"></a>Ayarlama İşlemleri  
 Ayarlama işlemleri DbUnionAllExpression DbExceptExpression ve DbIntersectExpression VisitSetOpExpression yöntemi tarafından işlenir. Bir şeklin SqlBuilder oluşturur  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Burada \<leftSqlSelectStatement > ve \<rightSqlSelectStatement > SqlSelectStatements elde ederek, girişlerin her biri olan ve \<setOp > karşılık gelen (UNION ALL örneğin) bir işlemdir.  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 (Başka bir birleşimin sol alt bir birleştirme için giriş) olarak bir birleştirme bağlamında ziyaret ederse, ' % s'hedef SQL tanımlayan bir sorgu, tablo veya Görünüm karşılık gelen hedefi için bir SqlBuilder DbScanExpression döndürür. Aksi takdirde, yeni SqlSelectStatement FROM alanı karşılık gelen hedefine karşılık olarak ayarlanmış oluşturulur.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Bir DbVariableReferenceExpression ziyareti bir ara sembol tablosuna göre bu değişken başvurusu ifadesi ile eşleşen sembol döndürür.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Diğer ad birleştirme düzleştirme tanımlandığı ve bir DbPropertyExpression ziyaret işlenir.  
  
 Örnek özelliği ilk kez ziyaret edilen ve bir sembol, bir JoinSymbol veya bir SymbolPair sonucudur. Bu üç durumların nasıl işleneceğini aşağıda verilmiştir:  
  
-   Bir JoinSymbol döndürülürse, kendi NameToExtent özelliği gerekli bir özellik için bir simge içerir. İç içe birleşim birleştirme sembol temsil ediyorsa, yeni bir simge çifti örnek diğer ad olarak kullanılan sembol izlemek için birleştirme sembol ve daha fazla çözümleme için gerçek özelliğini temsil eden bir simge ile döndürülür.  
  
-   Bir SymbolPair döndürülür ve birleştirme sembol sütun parçası ise, bir birleştirme sembol yeniden döndürülür, ancak şimdi column özelliği geçerli bir özellik ifadesi tarafından temsil edilen özelliğin işaret edecek şekilde güncelleştirildi. Aksi takdirde bir SqlBuilder SymbolPair kaynak diğer adı ve sütun olarak geçerli bir özellik için simge olarak döndürülür.  
  
-   Bir sembol döndürülürse, ziyaret yöntemi bu örnek diğer ad olarak ve sütun adı olarak özellik adı ile bir SqlBuilder yöntemi döndürür.  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 DbProjectExpression projeksiyon özellik olarak kullanıldığında, Dbnewınstanceexpression öngörülen sütunları temsil etmek için bağımsız değişkenlerin virgülle ayrılmış bir liste oluşturur.  
  
 Dbnewınstanceexpression, koleksiyon dönüş türüne sahip ve yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonu tanımlar, aşağıdaki üç durumda ayrı olarak ele alınmıştır:  
  
-   Dbnewınstanceexpression DbElementExpression tek bağımsız değişken olarak varsa, aşağıdaki gibi çevrilir:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Dbnewınstanceexpression, bağımsız değişkenleri yoksa (boş bir tablo gösterir) Dbnewınstanceexpression çevrilir:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 Aksi takdirde Dbnewınstanceexpression bağımsız değişkenlerin bir birleşimi tüm Merdiveni oluşturur:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Canonical ve yerleşik işlevler, aynı şekilde işlenir: Bunlar özel işleme (örneğin, LTRIM(RTRIM(string) için TRIM(string)) gerekiyorsa, uygun işleyicisi çağrılır. Aksi takdirde bunlar (arg1, arg2,..., argn) FunctionName çevrilir.  
  
 Sözlük, hangi işlevleri ve özel işleme uygun işleyicilerini gereksinim izlemek için kullanılır.  
  
 Kullanıcı tanımlı işlevleri tanslated NamespaceName.FunctionName (arg1, arg2,..., argn) için ' dir.  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 DbElementExpression ziyaret yöntemi yalnızca skaler bir sorgu temsil etmek için kullanılan bir DbElementExpression ziyaret için çağrılır. Bu nedenle, DbElementExpression içinde tam bir SqlSelectStatement çevirir ve köşeli ayraç içine ekler.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 İfade türüne (veya tamamını) DbQuantifierExpression çevrilir olarak:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>DbNotExpression  
 Bazı durumlarda DbNotExpression çevirisi, bir giriş ifadesi ile daraltmak mümkündür. Örneğin:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 DbQuantifierExpression, çevirme yazdığınızda tüm verimsizlikleri sağlayıcı tarafından sunulan ikinci Daralt gerçekleştirilen neden olmasıdır. Bu nedenle Entity Framework basitleştirme tamamlayabilirdik değil.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression olarak çevrilir:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>SQL üretimi ikinci aşaması: dize komutu oluşturma  
 Bir SQL komut dizesi oluştururken SqlSelectStatement olan sütun adı ve diğer ad uzantısı yeniden adlandırma sorunu giderir sembolleri için gerçek diğer adlar üretir.  
  
 Diğer ad uzantısı yeniden adlandırma, bir dizeye SqlSelectStatement nesne yazarken gerçekleşir. İlk dış kapsam tarafından kullanılan tüm diğer adları listesi oluşturun. Her simge FromExtents (veya null olmayan ise AllJoinExtents), herhangi bir dış kapsam ile çakışırsa adı. Yeniden adlandırma gerekirse tüm AllExtentNames içinde toplanan yerleşimi çakışmayacağı.  
  
 Sütun yeniden adlandırma, bir dizeye bir sembol nesnesi yazılırken gerçekleşir. İlk aşamada AddDefaultColumns, belirli bir sütun sembol yeniden adlandırılacak olup olmadığını belirledi. İkinci aşamasında üretilen adı AllColumnNames içinde kullanılan herhangi bir ad ile çakışmadığından emin olmak yalnızca yeniden adlandırma gerçekleşir.  
  
 Uzantı diğer adlar için hem de sütunlar için benzersiz adlar oluşturmak için burada n, henüz kullanılmamış en küçük bir diğer ad, < existing_name > _n kullanın. Genel liste tüm adlar, basamaklı yeniden adlandırmaya gerek artırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
