---
title: Komut Ağaçlarının Şekli
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248218"
---
# <a name="the-shape-of-the-command-trees"></a>Komut Ağaçlarının Şekli

SQL oluşturma modülü, belirli bir giriş sorgusu komut ağacı ifadesine göre arka uca özel SQL sorgusu oluşturmaktan sorumludur. Bu bölümde sorgu komut ağaçlarının özellikleri, özellikleri ve yapısı açıklanmaktadır.

## <a name="query-command-trees-overview"></a>Sorgu komut ağaçlarına genel bakış

Sorgu komut ağacı bir sorgunun nesne modeli gösterimidir. Sorgu komut ağaçları iki amaca hizmet eder:

- Öğesine göre [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]belirtilen bir giriş sorgusunu ifade etmek için.

- Bir sağlayıcıya verilen bir çıkış sorgusunu ifade etmek ve arka uca yönelik bir sorgu tanımlar.

Sorgu komut ağaçları, iç içe geçmiş Koleksiyonlar ve tür işlemleriyle çalışma desteği de dahil olmak üzere, bir varlığın belirli bir türde olup olmadığını kontrol etme ya da bir türe göre filtreleme kümeleri gibi SQL: 1999 uyumlu sorgulardan daha zengin semantiğini destekler.

DBQueryCommandTree. Query özelliği, sorgu mantığını tanımlayan ifade ağacının köküdür. DBQueryCommandTree. Parameters özelliği, sorguda kullanılan parametrelerin bir listesini içerir. İfade ağacı DbExpression nesnelerinden oluşur.

DbExpression nesnesi bazı hesaplamayı temsil eder. Birçok ifade türü, sabitleri, değişkenleri, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] işlevleri, oluşturucuları ve Filter ve JOIN gibi standart İlişkisel işleçleri içeren sorgu ifadeleri oluşturmak için tarafından sağlanır. Her DbExpression nesnesinin, bu ifade tarafından üretilen sonucun türünü temsil eden bir ResultType özelliği vardır. Bu tür bir TypeUsage olarak ifade edilir.

## <a name="shapes-of-the-output-query-command-tree"></a>Çıkış sorgusu komut ağacının şekilleri

Çıkış sorgusu komut ağaçları, ilişkisel (SQL) sorgularını yakından temsil eder ve sorgu komut ağaçları için uygulananlardan daha sıkı kurallara uyar. Genellikle SQL 'e kolayca çevrilmiş yapılar içerir.

Giriş komut ağaçları, gezinti özelliklerini, varlıklar arasındaki ilişkilendirmeleri ve devralmayı destekleyen kavramsal modele göre ifade edilir. Çıkış komut ağaçları, depolama modeline göre ifade edilir. Giriş komut ağaçları, iç içe geçmiş koleksiyonları proje yapmanıza izin verir, ancak çıkış komut ağaçları değildir.

Çıkış sorgusu komut ağaçları, kullanılabilir DbExpression nesnelerinin bir alt kümesi kullanılarak oluşturulur ve hatta söz konusu alt kümedeki bazı ifadelerin kısıtlı kullanımı vardır.

Belirli bir ifadenin belirli bir türde olup olmadığını veya bir türe göre filtreleme kümelerini denetlemek gibi tür işlemleri çıkış komut ağaçlarında mevcut değildir.

Çıkış komut ağaçlarında, yalnızca bir filtre veya bir Case deyimi gibi bir koşul gerektiren deyimlerdeki koşullara göre yalnızca Boole değerleri döndüren ifadeler kullanılır.

Çıkış sorgusu komut ağaçlarının kökü bir DbProjectExpression nesnesidir.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Çıkış sorgusunda ifade türleri yok komut ağaçları

Aşağıdaki ifade türleri bir çıkış sorgusu komut ağacında geçerli değildir ve sağlayıcılar tarafından işlenmemelidir:

- DbDerefExpression başvuru türünde

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>İfade kısıtlamaları ve notları

Birçok ifade yalnızca çıkış sorgusu komut ağaçlarında kısıtlı bir şekilde kullanılabilir:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Aşağıdaki işlev türleri geçirilebilir:

- EDM ad alanı tarafından tanınan kurallı işlevler.

- Buıltedattribute tarafından tanınan yerleşik (mağaza) işlevler.

- Kullanıcı tanımlı işlevler.

Kurallı işlevler (daha fazla bilgi için [kurallı işlevlere](./language-reference/canonical-functions.md) bakın), [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]öğesinin bir parçası olarak belirtilir ve sağlayıcılar bu belirtimlere göre kurallı işlevlere yönelik uygulamalar sağlamalıdır. Mağaza işlevleri, karşılık gelen sağlayıcı bildiriminde yer alan belirtimlere göre yapılır. Kullanıcı tanımlı işlevler SSDL içindeki belirtimlere dayanır.

Ayrıca, NiladicFunction özniteliğine sahip işlevlerin bağımsız değişkeni yoktur ve sonda parantez olmadan çevrilmelidir.  Diğer bir deyişle,  *\<* fonksiyonadı  *\<> ()* yerine fonksiyonadı >.

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbNewInstanceExpression oluşturamıyor yalnızca aşağıdaki iki durumda bulunabilir:

- DbProjectExpression 'ın Projection özelliği olarak.  Bu şekilde kullanıldığında, aşağıdaki kısıtlamalar geçerlidir:

  - Sonuç türü bir satır türü olmalıdır.

  - Bağımsız değişkenlerinin her biri, temel bir türle bir sonuç üreten bir ifadedir. Genellikle, her bağımsız değişken bir DbVariableReferenceExpression üzerinde bir PropertyExpression, bir işlev çağırma veya bir DbVariableReferenceExpression ya da işlev çağırma üzerinden DbPropertyExpression 'ın aritmetik bir hesaplaması gibi bir skaler ifadedir . Ancak, bir DbNewInstanceExpression oluşturamıyor için bağımsız değişkenler listesinde skaler bir alt sorguyu temsil eden bir ifade da oluşabilir. Skaler bir alt sorguyu temsil eden bir ifade, tam olarak bir satır ve bir basit türün bir sütununu DbElementExpression nesne köküyle döndüren bir alt sorguyu temsil eden bir ifade ağacıdır

- Koleksiyon dönüş türü ile, bu durumda bağımsız değişkenler olarak sunulan ifadelerin yeni bir koleksiyonunu tanımlar.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Bir DbVariableReferenceExpression, DbPropertyExpression düğümünün bir alt öğesi olmalıdır.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Bir DbGroupByExpression 'ın toplamalar özelliği yalnızca DbFunctionAggregate türünde öğelere sahip olabilir. Başka bir toplama türü yok.

#### <a name="dblimitexpression"></a>DbLimitExpression

Özellik sınırı yalnızca bir DbConstantExpression veya DbParameterReferenceExpression olabilir. Ayrıca özellik özellikleri, .NET Framework sürüm 3,5 itibariyle her zaman false 'tur.

#### <a name="dbscanexpression"></a>DbScanExpression

Çıkış komut ağaçlarında kullanıldığında, DbScanExpression bir tablo, görünüm veya bir depolama sorgusu üzerinde EntitySetBase:: Target ile temsil edilen bir taramayı etkin bir şekilde temsil eder.

Hedefin "sorgu tanımlama" meta veri özelliği null değilse, bir sorguyu temsil eder ve bu meta veri özelliğinde, depo şeması tanımında belirtilen dilde (veya diyalekt) belirtilen sorgu metni.

Aksi takdirde, hedef bir tabloyu veya görünümü temsil eder. Şema ön eki, null değilse "Schema" meta veri özelliğinde bulunur, aksi takdirde varlık kapsayıcısı adıdır.  Tablo veya Görünüm adı, null değilse "Table" meta veri özelliğidir, aksi takdirde varlık kümesi tabanının Name özelliği olur.

Tüm bu özellikler, depo şeması tanım dosyasındaki (SSDL) karşılık gelen EntitySet 'in tanımından kaynaklanacak.

### <a name="using-primitive-types"></a>Temel türleri kullanma

Çıkış komut ağaçlarında temel türlere başvurulduklarında, bunlara genellikle kavramsal modelin ilkel türlerinde başvurulur. Ancak, bazı ifadelerde sağlayıcılara karşılık gelen depo temel türü gerekir. Bu tür ifadelere örnek olarak, sağlayıcının null değeri karşılık gelen türe ataması gerekiyorsa DbCastExpression ve muhtemelen Dbsnullexpression sayılabilir. Bu durumlarda, sağlayıcılar temel tür türü ve onun modellerini temel alan sağlayıcı türüyle eşlemeyi yapılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Üretimi](sql-generation.md)
