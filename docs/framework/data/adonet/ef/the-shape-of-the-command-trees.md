---
title: Komut ağaçlarının şekli
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: aba5511b8baa395714bde315d9542932e854c98b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378554"
---
# <a name="the-shape-of-the-command-trees"></a>Komut ağaçlarının şekli

SQL üretimi modülü, belirli bir giriş sorgu komut ağacı ifadeye göre bir arka uç belirli SQL sorgusu oluşturmak için sorumludur. Bu bölüm, özellikleri, özellikler ve sorgu komut ağaçlarının yapısını açıklar.

## <a name="query-command-trees-overview"></a>Sorgu komut ağaçlarını genel bakış

Bir sorgu komut ağacı bir sorgu nesne modeli gösterimidir. Sorgu komut ağaçlarını iki amaca hizmet eder:

- Giriş sorgusu karşı belirtilen ifade [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].

- Bir sağlayıcıya verilen ve arka uç yönelik bir sorgu açıklayan bir çıkış sorgu ifade etmek için.

Komut ağaçlarını destekleyen SQL:1999 uyumlu sorguları, iç içe geçmiş koleksiyonlar ve bir varlığın belirli bir tür olup olmadığını denetlemeye veya kümeleri bir türüne göre filtreleme gibi tür işlemleri ile çalışmak için destek dahil olmak üzere daha zengin bir semantik sorgu.

Sorgu mantığı tanımlayan bir ifade ağacı kök DBQueryCommandTree.Query özelliğidir. DBQueryCommandTree.Parameters özelliği sorguda kullanılan parametrelerin listesini içerir. İfade ağacı Dbexpression'dan nesnelerden oluşur.

Dbexpression'dan nesne bazı hesaplama temsil eder. Çeşitli türlerde ifadeler tarafından sağlanan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sabitleri dahil olmak üzere, sorgu ifadeleri oluşturmak için değişkenler, İşlevler, Oluşturucular ve standart ilişkisel işleçler gibi filtre ve birleştirme. Her Dbexpression'dan nesnesi bu ifade tarafından üretilen sonuç türü temsil eden bir resulttype'ı özelliğine sahiptir. Bu tür bir typeusage değeri ifade edilir.

## <a name="shapes-of-the-output-query-command-tree"></a>Çıkış sorgu komut ağacı şekilleri

Çıkış sorgu komut ağaçlarını yakından ilişkisel (SQL) sorguları ve sorgu komutu ağaçlarına geçerli olandan çok daha sıkı kurallarına bağlı kalmanızı. Bunlar genellikle SQL'e kolayca çevrilir yapıları içerir.

Gezinti özellikleri, devralma ve varlıklar arasındaki ilişkileri destekler kavramsal modeline karşı giriş komut ağaçlarını cinsinden ifade edilir. Çıkış komut ağaçlarını depolama modelinde ifade edilir. Giriş komut ağaçlarını iç içe geçmiş koleksiyonlar proje olanak sağlar, ancak çıkış komut ağaçlarını yapın.

Çıkış sorgu komut ağaçlarını kullanılabilir Dbexpression'dan nesneler kümesini kullanarak oluşturulur ve bu alt bile bazı ifadeler sınırlı kullanımı.

Verilen ifade belirli bir tür olup olmadığını denetlemeye veya kümeleri bir türüne göre filtreleme gibi işlemleri türü, çıkış komut ağaçlarında mevcut değildir.

Çıkış komut ağaçlarında Boolean değerleri döndüren ifadeler projeksiyonlar ve yalnızca gerektiren bir filtre veya case ifadesi gibi bir koşul ifadeleri koşullarında kullanılır.

Bir çıkış sorgu komut ağaçlarını DbProjectExpression nesne köküdür.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>İfade türleri çıkış sorgu komutu ağaçlarında yok

Aşağıdaki ifade türleri içinde bir çıkış sorgu komut ağacı geçerli değil ve sağlayıcıları tarafından ele alınması gerekmez:

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>İfade kısıtlamalar ve notlar

Birçok ifadeleri yalnızca çıktı sorgu komut ağaçlarını sınırlı bir şekilde kullanılabilir:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Aşağıdaki işlev türleri geçirilebilir:

- Edm ad alanı tarafından tanınan kurallı işlevler.

- Yerleşik (Depolama) işlevler BuiltInAttribute tarafından tanınır.

- Kullanıcı tanımlı işlevler.

Kurallı işlevler (bkz [kurallı işlevler](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) daha fazla bilgi için) parçası olarak belirtilen [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], ve sağlayıcıları bu belirtimlerle uyarlanan kurallı işlevler için uygulamaları sağlamanız. Store işlevleri ilgili sağlayıcı bildirimi özelliklere dayanır. Kullanıcı tanımlı işlevleri SSDL teknik özelliklerine bağlıdır.

Ayrıca, NiladicFunction özniteliğine sahip işlevleri bağımsız değişken yoktur ve sonunda parantez olmadan çevrilmesi gerekir.  Diğer bir deyişle,  *\<functionName >* yerine  *\<functionName > ()*.

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

Dbnewınstanceexpression, yalnızca aşağıdaki iki durumlarda oluşabilir:

- Projeksiyon DbProjectExpression özelliği.  Bu şekilde kullanıldığında aşağıdaki kısıtlamalar uygulanır:

    - Sonuç türü satır türünde olmalıdır.

    - Her bağımsız değişkenlerinden biri, bir basit türü ile bir sonuç üretir bir ifadedir. Genellikle, her bağımsız değişken bir DbVariableReferenceExpression veya bir işlev çağrısını bir DbVariableReferenceExpression, bir işlev çağırma veya bir aritmetik hesaplaması DbPropertyExpression üzerinden bir PropertyExpression gibi skaler bir ifade. . Ancak, skaler bir sorgu temsil eden bir ifade bir Dbnewınstanceexpression için bağımsız değişken listesinde de oluşabilir. Skaler bir sorgu temsil eden bir ifade olan tam olarak bir satır ve tek sütunlu bir DbElementExpression nesne kök ile temel bir tür döndüren sorgu temsil eden bir ifade ağacı

- Bir koleksiyon dönüş türüyle bu durumda, yeni bir bağımsız değişken olarak sağlanan ifadeleri koleksiyonunu tanımlar.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

Bir DbVariableReferenceExpression DbPropertyExpression düğümün alt öğesi bulunmalıdır.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Bir DbGroupByExpression'ın toplamalar özelliği yalnızca DbFunctionAggregate türünde öğelere sahip olabilir. Başka bir toplama türü vardır.

#### <a name="dblimitexpression"></a>DbLimitExpression

Sınır özelliği yalnızca bir DbConstantExpression veya bir DbParameterReferenceExpression olabilir. Ayrıca WithTies her zaman false .NET Framework 3.5 sürümü itibarıyla özelliğidir.

#### <a name="dbscanexpression"></a>DbScanExpression

Çıkış komut ağaçlarında kullanıldığında DbScanExpression etkili bir şekilde bir tarama bir tablo, görünüm veya EntitySetBase::Target tarafından temsil edilen bir depo sorgu temsil eder.

Bir sorgu temsil eder hedefinin "sorgu tanımlama" meta veri özelliği null olmayan, ise, hangi sorgu metni meta veri deposu şeması tanımında belirtilen sağlayıcının belirli bir dil (veya diyalekti) özelliğinde sağlanır.

Aksi takdirde, hedef, bir tablo veya Görünüm temsil eder. Ya da "Şema" meta veri özelliği, şema ön ekidir değilse varlık kapsayıcı adı null; Aksi takdirde.  Tablo veya Görünüm adı ya da "Tablo" meta veri özelliği değilse varlık adı özniteliğinin temel ayarlayın, aksi halde null şeklindedir.

Tüm bu özellikler, depo şeması tanım dosyasında (SSDL) karşılık gelen Entityset'i tanımını kaynaklanan.

### <a name="using-primitive-types"></a>İlkel türler kullanma

İlkel türler çıkış komut ağaçlarında başvurulduğunda, bunlar genellikle kavramsal modelin ilkel türlerinde başvurulur. Ancak, belirli ifadeler için karşılık gelen depolama ilkel tür sağlayıcıları gerekir. Sağlayıcı null karşılık gelen türe dönüştürme gerekiyorsa DbCastExpression ve büyük olasılıkla DbNullExpression, bu tür ifadeleri örnekleri içerir. Bu gibi durumlarda sağlayıcıları, ilkel tür türü ve kendi modelleri göre sağlayıcı türü için eşleme yapmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
