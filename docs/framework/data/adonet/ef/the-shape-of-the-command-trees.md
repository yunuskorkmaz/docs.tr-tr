---
title: Komut ağaçlarını şekli
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 9084e2616ac4ea540bdf755afd011d67a5c991fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766042"
---
# <a name="the-shape-of-the-command-trees"></a>Komut ağaçlarını şekli
SQL oluşturma modülü, belirtilen giriş sorgu komut ağacı ifadesi temelinde bir arka uç belirli SQL sorgusu oluşturmak için sorumludur. Bu bölüm, özellikleri, özellikleri ve sorgu komut ağaçlarını yapısını anlatılmaktadır.  
  
## <a name="query-command-trees-overview"></a>Sorgu komut ağaçlarını genel bakış  
 Bir sorgu komut ağacındaki bir sorguda nesne modeli gösterimidir. Sorgu komut ağaçlarını iki amaca hizmet eder:  
  
-   Karşı belirtilen bir giriş sorgu ifade etmek için [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Bir sağlayıcıya verilen ve arka uç yönelik bir sorgu açıklayan bir çıktı sorgu ifade etmek için.  
  
 Query ağaçları SQL:1999 uyumlu sorgular, iç içe geçmiş koleksiyonlar ve türü işlemleri, bir varlığın belirli bir tür olup olmadığını denetleme veya kümeleri türüne göre filtreleme gibi ile çalışmak için destek dahil olmak üzere daha zengin semantiğini desteklemek komutu.  
  
 Sorgu mantığını tanımlayan ifade ağacına kökündeki DBQueryCommandTree.Query özelliğidir. DBQueryCommandTree.Parameters özelliği sorguda kullanılan parametrelerin listesini içerir. İfade ağacına DbExpression nesnelerin oluşur.  
  
 DbExpression nesnesi bazı hesaplama temsil eder. Çeşitli türlerde ifadeleri tarafından sağlanan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sabitleri dahil olmak üzere sorgu ifadeleri oluşturmak için değişkenler, İşlevler, Oluşturucular ve standart ilişkisel işleçler gibi filtre ve birleştirme. Her DbExpression nesnesi bu deyim tarafından üretilen sonuç türü gösteren bir ResultType özelliğine sahiptir. Bu tür bir TypeUsage ifade edilir.  
  
## <a name="shapes-of-the-output-query-command-tree"></a>Çıktı sorgu komut ağacı şekilleri  
 Çıktı sorgu komut ağaçlarını yakından ilişkili (SQL) sorguları temsil eder ve sorgu komut ağaçlarını geçerli olandan çok daha sıkı kurallar uygun. Bunlar genellikle SQL kolayca çevrilir yapılar içerir.  
  
 Giriş komut ağaçlarını Gezinti özellikleri, varlıkların ve devralma arasındaki ilişkileri destekler kavramsal model karşı ifade edilir. Çıkış komut ağaçlarını depolama modeline göre belirtilmiştir. Giriş komut ağaçlarını proje iç içe geçmiş koleksiyonları olanak sağlar, ancak çıktı komut ağaçlarını desteklemez.  
  
 Çıktı sorgu komut ağaçlarını kullanılabilir DbExpression nesneler kümesini kullanılarak oluşturulur ve bu alt bile bazı ifadelerinde sınırlı kullanımı.  
  
 Verilen ifade belirli bir tür olup olmadığını denetleme veya kümeleri türüne göre filtreleme gibi türü işlemler, çıktı komut ağaçlarında yok.  
  
 Çıkış komutu ağaçlarında Boole değerleri döndüren ifadeler tahminleri ve yalnızca bir filtre veya case deyimi gibi bir koşul gerektiren ifadeleri koşullarında için kullanılır.  
  
 Bir çıkış sorgu komut ağaçlarını kökündeki DbProjectExpression nesnesidir.  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a>İfade türleri çıkış sorgu komutu ağaçlarında yok  
 Aşağıdaki ifade türleri bir çıktı sorgu komutu ağacında geçerli değildir ve sağlayıcıları tarafından yapılması gerekmez:  
  
 DbDerefExpression  
  
 DbEntityRefExpression  
  
 DbRefKeyExpression  
  
 DbIsOfExpression  
  
 DbOfTypeExpression  
  
 DbRefExpression  
  
 DbRelationshipNavigationExpression  
  
 DbTreatExpression  
  
### <a name="expression-restrictions-and-notes"></a>İfade kısıtlamaları ve notlar  
 Birçok ifadeleri yalnızca çıktı sorgu komut ağaçlarını sınırlı bir şekilde kullanılabilir:  
  
#### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Aşağıdaki işlev türleri geçirilebilir:  
  
-   Edm ad alanı tarafından tanınan kurallı işlevleri.  
  
-   BuiltInAttribute tarafından tanınan yerleşik (Depolama) çalışır.  
  
-   Kullanıcı tanımlı işlevler.  
  
 Kurallı işlevleri (bkz [kurallı işlevleri](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) daha fazla bilgi için) parçası olarak belirtilen [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], ve sağlayıcıları bu belirtimlerle uyarlanan kurallı işlevleri için uygulamaları sağlamanız. Depo işlevleri karşılık gelen sağlayıcı bildiriminde belirtimlerini temel alır. Kullanıcı tanımlı işlevler SSDL belirtimlerini temel alır.  
  
 Ayrıca, işlevleri NiladicFunction özniteliğine sahip bağımsız değişken yoktur ve sonunda parantez olmadan çevrilmesi gerekir.  Diğer bir deyişle,  *\<functionName >* yerine  *\<functionName > ()*.  
  
#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 Dbnewınstanceexpression, yalnızca aşağıdaki iki durumlarda oluşabilir:  
  
-   DbProjectExpression projeksiyon özelliği olarak.  Bu nedenle kullanıldığında aşağıdaki kısıtlamalar geçerlidir:  
  
    -   Sonuç türü bir satır türü olmalıdır.  
  
    -   Bağımsız değişkenlerinin her birini bir ilkel tür bir sonuçla üreten bir ifadedir. Genellikle, her bir bağımsız değişkeni bir DbVariableReferenceExpression veya bir işlev çağrısını bir DbVariableReferenceExpression, bir işlev çağrısını ya da bir aritmetik hesaplaması DbPropertyExpression üzerinden PropertyExpression gibi skaler bir ifade. . Ancak, skaler bir alt sorgu temsil eden bir ifade da bir Dbnewınstanceexpression için bağımsız değişkenlerin listesini ortaya çıkabilir. Tam olarak bir satır ve DbElementExperession nesne kök ile temel bir türünde bir sütun döndüren bir alt sorgu temsil eden bir ifade ağacına skaler bir alt sorgu temsil eden bir ifade değil  
  
-   Bir koleksiyon dönüş türüyle bu durumda, yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonunu tanımlar.  
  
#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Bir DbVariableReferenceExpression DbPropertyExpression düğümün alt öğesi olması gerekir.  
  
#### <a name="dbgroupbyexpression"></a>DbGroupByExpression  
 Bir dbgroupbyexpression toplamalar özelliği yalnızca DbFunctionAggregate türündeki öğeler olabilir. Başka bir toplama türü vardır.  
  
#### <a name="dblimitexpression"></a>DbLimitExpression  
 Sınır özelliği yalnızca bir DbConstantExpression veya DbParameterReferenceExpression olabilir. Ayrıca WithTies her zaman, .NET Framework 3.5 sürümünü itibariyle false özelliğidir.  
  
#### <a name="dbscanexpression"></a>DbScanExpression  
 Çıkış komutu ağaçlarında kullanıldığında, DbScanExpression etkili bir şekilde bir tarama bir tablo, bir görünüm veya EnitySetBase::Target tarafından temsil edilen bir deposu sorgusu üzerinden temsil eder.  
  
 Bir sorgu temsil eden hedef "sorgu tanımlama" meta veri özelliği boş ise, hangi sorgu metnini depo şeması tanım belirtildiği gibi sağlayıcının belirli bir dil (veya dialect) bu meta veri özelliği sağlanmalıdır.  
  
 Aksi takdirde, hedef bir tablo veya Görünüm temsil eder. Kendi şema önekini ya da "Şema" meta veri özelliği, olmasa bile kapsayıcı adı boş, aksi takdirde.  Tablo veya Görünüm adı ya da "Tablo" meta veri özelliği değilse varlığı adını temel ayarlayın, aksi halde null ' dir.  
  
 Bu özellikleri depo şeması tanım dosyasındaki (SSDL) karşılık gelen EntitySet tanımını kaynaklanır.  
  
### <a name="using-primitive-types"></a>İlkel türler kullanma  
 İlkel türler çıkış komut ağaçlarında başvurulduğunda genellikle kavramsal modelin ilkel türlerinde başvurulur. Ancak, belirli ifadeleri için karşılık gelen deposu ilkel tür sağlayıcıları gerekir. Sağlayıcı null değerine karşılık gelen tür cast gerekiyorsa, bu tür örnekleri DbCastExpression ve büyük olasılıkla DbNullExpression, içerir. Bu durumlarda, sağlayıcıları, ilkel türü türü ve onun modelleri göre sağlayıcı türü için eşleme yapmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
