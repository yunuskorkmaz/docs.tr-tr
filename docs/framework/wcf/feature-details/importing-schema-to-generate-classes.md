---
title: Sınıf Oluşturmak için Şemayı İçe Aktarma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43eaa4ffe562cf1dde5abd7e7540125dcf383732
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="importing-schema-to-generate-classes"></a>Sınıf Oluşturmak için Şemayı İçe Aktarma
İle kullanılabilen şemaları sınıfları oluşturmak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kullanın <xref:System.Runtime.Serialization.XsdDataContractImporter> sınıfı. Bu konu işlemini ve farklılıkları açıklar.  
  
## <a name="the-import-process"></a>İçeri aktarma işlemi  
 Şema alma işlemi ile başlayan bir <xref:System.Xml.Schema.XmlSchemaSet> ve üreten bir <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Bir parçası olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ait XML Şeması Tanım Dili (XSD) şema belgeleri kümesini temsil eder şema nesne modeli (SOM). Oluşturmak için bir `XmlSchemaSet` nesne bir dizi XSD belgeler, her belgeye seri durumdan bir <xref:System.Xml.Schema.XmlSchema> nesne (kullanarak <xref:System.Xml.Serialization.XmlSerializer>) ve bu nesnelerin yeni bir ekleme `XmlSchemaSet`.  
  
 `CodeCompileUnit` Parçası olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]'s kod belge nesne modeli (CodeDOM) temsil eden [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] soyut bir şekilde kod. Gerçek kodu oluşturmak için bir `CodeCompileUnit`, öğesinin bir alt kümesi kullanmak <xref:System.CodeDom.Compiler.CodeDomProvider> gibi sınıfı <xref:Microsoft.CSharp.CSharpCodeProvider> veya <xref:Microsoft.VisualBasic.VBCodeProvider> sınıfı.  
  
#### <a name="to-import-a-schema"></a>Bir şemayı içeri aktarmak için  
  
1.  Bir örneğini oluşturmak <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2.  İsteğe bağlı. Geçirmek bir `CodeCompileUnit` oluşturucuda. Şema alma işlemi sırasında oluşturulan türleri için eklenen `CodeCompileUnit` örneği yerine boş bir ile başlayan `CodeCompileUnit`.  
  
3.  İsteğe bağlı. Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> yöntemleri. Yöntemi, belirtilen şema geçerli bir veri sözleşmesi şema ve aktarılabilir olup olmadığını belirler. `CanImport` Yöntemi olarak aynı aşırı sahip `Import` (sonraki adım).  
  
4.  Aşırı yüklenmiş birini çağırın `Import` yöntemleri, örneğin, <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> yöntemi.  
  
     En basit aşırı geçen bir `XmlSchemaSet` ve bu şema kümesinde bulunan anonim türleri dahil olmak üzere tüm türü alır. Diğer aşırı yüklemeler XSD türü veya türlerinin bir listesini almak için belirtmenizi sağlar (biçiminde bir <xref:System.Xml.XmlQualifiedName> veya koleksiyonu `XmlQualifiedName` nesneleri). Bu durumda, yalnızca belirtilen türleri içeri aktarılır. Bir aşırı geçen bir <xref:System.Xml.Schema.XmlSchemaElement> dışı belirli bir öğe alır `XmlSchemaSet`, ilişkili türünü (veya anonim olup) yanı sıra. Bu aşırı döndüren bir `XmlQualifiedName`, bu öğe için oluşturulan türünün veri sözleşmesi adını temsil eder.  
  
     Birden çok çağıran `Import` aynı eklenmekte olan birden çok öğe yöntemi sonucunda `CodeCompileUnit`. Bir tür halinde oluşturulmaz `CodeCompileUnit` , zaten varsa. Çağrı `Import` birden çok kez üzerinde aynı `XsdDataContractImporter` birden çok kullanmak yerine `XsdDataContractImporter` nesneleri. Yinelenen türleri oluşturulmasını önlemek için önerilen yöntem budur.  
  
    > [!NOTE]
    >  İçeri aktarma sırasında bir hata olduğunda `CodeCompileUnit` öngörülemeyen durumda olacaktır. Kullanarak bir `CodeCompileUnit` başarısız alma işleminden kaynaklanan kullanıma, güvenlik açıkları için.  
  
5.  Erişim `CodeCompileUnit` aracılığıyla <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> özelliği.  
  
### <a name="import-options-customizing-the-generated-types"></a>İçeri aktarma seçenekleri: oluşturulan türleri özelleştirme  
 Ayarlayabileceğiniz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği <xref:System.Runtime.Serialization.XsdDataContractImporter> örneğine <xref:System.Runtime.Serialization.ImportOptions> içeri aktarma işlemi çeşitli yönlerini denetlemek için sınıf. Bir dizi seçenek oluşturulan türleri doğrudan etkiler.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Erişim düzeyini denetleme (GenerateInternal veya / iç geçiş)  
 Bu karşılık **/ iç** anahtarının [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalde, genel türleri özel alanlar ve eşleşen ortak veri üye özellikleri ile şemasından üretilir. Bunun yerine iç türleri oluşturmak üzere <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliğine `true`.  
  
 Aşağıdaki örnek, bir iç dönüştürülen bir şema gösterir sınıfı <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliği ayarlanmış `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Ad alanları (ad alanları veya geçiş/namespace) denetleme  
 Bu karşılık **/namespace** anahtarının `Svcutil.exe` aracı.  
  
 Şemayı oluşturulan türleri içine normalde, oluşturulan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ad alanları, belirli bir karşılık gelen her XSD ad alanı ile [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] açıklandığı bir eşleme göre ad alanı [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu eşleme tarafından özelleştirebilirsiniz <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> özelliğine bir <xref:System.Collections.Generic.Dictionary%602>. Belirli bir XSD ad eşleştirme sözlüğünde bulunursa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ad alanı, sözlükten de alınır.  
  
 Örneğin, aşağıdaki şema göz önünde bulundurun.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Aşağıdaki örnek kullanır `Namespaces` eşlemek için özellik "http://schemas.contoso.com/carSchema" ad "Contoso.Cars" alanına.  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>SerializableAttribute ekleme (GenerateSerializable veya / seri hale getirilebilir geçiş)  
 Bu karşılık **/ seri hale getirilebilir** anahtarının `Svcutil.exe` aracı.  
  
 Bazen şemadan oluşturulan türleri ile kullanılabilmesi önemli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] çalışma zamanı seri hale getirme altyapısı (örneğin, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıfları). Türleri için kullanırken bu yararlıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting. Bu ayarı etkinleştirmek için uygulamanız gerekir <xref:System.SerializableAttribute> oluşturulan türlerine normal ek özniteliğini <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Öznitelik, otomatik olarak oluşturulan `GenerateSerializable` alma seçeneği ayarlanmış `true`.  
  
 Aşağıdaki örnekte gösterildiği `Vehicle` ile oluşturulan sınıf `GenerateSerializable` alma seçeneği ayarlanmış `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Veri bağlama desteği (EnableDataBinding ya da /enableDataBinding anahtar) ekleme  
 Bu karşılık **/enableDataBinding** Svcutil.exe aracını kullanarak geçiş yapın.  
  
 Bazı durumlarda, böylece bu tür örnekleri için herhangi bir güncelleştirme kullanıcı Arabirimi otomatik olarak güncelleştirilecek şemadan grafik kullanıcı arabirimi bileşenlerini oluşturulan türlerini bağlamak isteyebilirsiniz. `XsdDataContractImporter` Uygulama türleri oluşturabilir <xref:System.ComponentModel.INotifyPropertyChanged> herhangi bir özellik değişikliği bir olay tetikler şekilde arabirimi. Bu arabirim (gibi Windows Presentation Foundation (WPF)) destekleyen bir istemci kullanıcı Arabirimi bir programlama ortamı ile kullanılmak üzere türleri oluşturmak istiyorsanız, ayarlayın <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> özelliğine `true` bu özelliği etkinleştirmek için.  
  
 Aşağıdaki örnekte gösterildiği `Vehicle` ile oluşturulan sınıf <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> kümesine `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>İçeri aktarma seçenekleri: Koleksiyon türleri seçme  
 İki özel desenleri XML öğe koleksiyonunu temsil eder: öğeleri ve arasındaki ilişkilendirmeleri bir öğe başka bir listesi. Dizeleri listesini bir örnek verilmiştir.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Bir dizeyi bir tamsayı arasında bir ilişki örneği aşağıda verilmiştir (`city name` ve `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Herhangi bir ilişkisi de listesini değerlendirilebilir. Örneğin, karmaşık bir liste olarak önceki ilişkilendirmesini görüntüleyebilirsiniz `city` (bir dize alanı ve tamsayı alan) iki alan sahipse nesneleri. İki desen gösterimi XSD şemasına sahip. Bir liste arasında bir ilişki sürece desenler her zaman listeleri davranılır şekilde ayırt etmek için bir yolu yoktur bir özel ek açıklama özgü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] şemada mevcuttur. Ek açıklamanın belirli bir desen bir ilişkiyi temsil ettiğini gösterir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Genel bir listeden veya olarak türetilen bir koleksiyon veri sözleşmesi olarak listesini normalde, alınan bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] olsun veya olmasın koleksiyonlar için standart adlandırma deseni bir şemayı izlediğinden bağlı olarak, dizi. Bu daha ayrıntılı olarak açıklanmıştır [veri sözleşmelerinde koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). İlişkilendirmeleri ya da normal olarak içeri aktarılan bir <xref:System.Collections.Generic.Dictionary%602> veya sözlük nesnesinden türer bir koleksiyonu veri sözleşme. Örneğin, aşağıdaki şema göz önünde bulundurun.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Bu (alanları okunabilirlik için özellikleri yerine gösterilir) şekilde alınır.  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Şema desenler için oluşturulan koleksiyon türleri özelleştirmek kullanılabilir. Örneğin, türetme koleksiyonlar oluşturmak isteyebilirsiniz <xref:System.ComponentModel.BindingList%601> yerine <xref:System.Collections.Generic.List%601> türü bir liste kutusunu bağlamak ve bu sahip için sınıf koleksiyonunun içeriğini değiştirdiğinizde otomatik olarak güncelleştirilecektir. Bunu yapmak için ayarlayın <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> (bundan böyle başvurulan türleri olarak bilinir) kullanılacak koleksiyon türleri listesine sınıfı. Başvurulan koleksiyon türleri bu listesi herhangi bir koleksiyonu içeri aktarırken taranır ve en iyi eşleşen koleksiyon bulunması durumunda kullanılır. İlişkilendirmeleri genel ya da nongeneric uygulayan türler karşı eşleşen <xref:System.Collections.IDictionary> listeleri karşı herhangi bir desteklenen koleksiyon türü eşleştirilir sırada arabirim.  
  
 Örneğin, varsa <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği ayarlanmış bir <xref:System.ComponentModel.BindingList%601>, `people` önceki örnekte türü şu şekilde oluşturulur.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Kapalı bir genel en iyi eşleşme olarak kabul edilir. Örneğin, varsa türleri `BindingList(Of Integer)` ve <xref:System.Collections.ArrayList> geçirilen başvurulan tür koleksiyona şemada bulunan tamsayıların tüm listeleri olarak içe aktarılan bir `BindingList(Of Integer)`. Diğer listelerinde, örneğin, bir `List(Of String)`, olarak alınan bir `ArrayList`.  
  
 Genel uygulayan bir tür ise `IDictionary` arabirimi başvurulan türleri koleksiyonunu eklenir, kendi tür parametreleri ya da tam olarak açık veya tam olarak kapalı olması gerekir.  
  
 Tekrarlara izin verilmez. Örneğin, her ikisi de ekleyemezsiniz bir `List(Of Integer)` ve `Collection(Of Integer)` başvurulan türleri için. Tamsayı listesi şemada bulunduğunda, kullanılması gerektiğini belirlemek mümkün anlaması. Yalnızca yinelenen sorun gösteren şemada bir türü varsa yinelenenleri algılanır. İçeri aktarılan şema tamsayılar listesi içermiyorsa, örneğin, bu hem de izin veriliyor `List(Of Integer)` ve `Collection(Of Integer)` başvurulan türler koleksiyonu, ancak ne hiçbir etkisi olmaz.  
  
 Mekanizması eşit çalışır başvurulan koleksiyon türleri karmaşık türler (diğer koleksiyonları koleksiyonları dahil) koleksiyonlar için yanı sıra ve temelleri koleksiyonlar için tam değil.  
  
 `ReferencedCollectionTypes` Özelliğine karşılık gelen **/collectionType** SvcUtil.exe aracını kullanarak geçiş yapın. Birden çok koleksiyon türleri başvurmak için unutmayın **/collectionType** anahtar birden fazla kez belirtilmesi gerekir. Türü mscrlib.dll değilse, kendi derleme de kullanılarak başvurulmalıdır **/reference** geçin.  
  
#### <a name="import-options-referencing-existing-types"></a>İçeri aktarma seçenekleri: Varolan türlerine başvurma  
 Bazen, varolan şema türlerinde karşılık [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve bu tür sıfırdan oluşturmaya gerek yoktur. (Bu bölüm, yalnızca noncollection türleri için geçerlidir. Koleksiyon türleri için kısmına bakın.)  
  
 Örneğin, bir kişinin temsil eden çağrılırken istediğiniz her zaman bir standart şirket çapında "Kişi" veri sözleşmesi türü olabilir. Bazı hizmet yaptığında bu tür ve şemasına kullanımını hizmeti meta verilerde görünür, varolan yeniden isteyebilirsiniz `Person` her hizmet için yeni bir tane oluşturmak yerine bu şemayı içe aktarırken yazın.  
  
 Bunu yapmak için listesini geçirmek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] koleksiyona yeniden kullanmak istediğiniz türleri <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> özelliği döndürür <xref:System.Runtime.Serialization.ImportOptions> sınıfı. Bu tür bir veri sözleşme adına ve adıyla eşleşen bir ad alanı ve ad alanı bir şema türü varsa, yapısal bir karşılaştırma gerçekleştirilir. Türleri eşleşen adları hem eşleşen yapıları, mevcut olduğunu belirlenirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü yeniden kullanılabilir yeni bir tane oluşturmak yerine. Yalnızca değil yapısı adıyla eşleşen bir özel durum oluşur. Türleri (örneğin, ekleme yeni isteğe bağlı veri üyeleri) başvururken sürüm oluşturma için hiç indirimi olduğunu unutmayın. Yapıları tam olarak eşleşmelidir.  
  
 Hiçbir şema türü, adı ve ad alanı içe sürece aynı veri sözleşme adına ve ad alanını birden çok tür başvurulan tür koleksiyona eklemek için uygundur. Bu kolayca tüm türleri koleksiyonuna derlemedeki gerçekte şemada gerçekleşmez türleri çoğaltmaları hakkında endişelenmeden eklemenize olanak sağlar.  
  
 `ReferencedTypes` Özelliğine karşılık gelen **/reference** geçiş işlemi Svcutil.exe aracının belirli modlarında.  
  
> [!NOTE]
>  Svcutil.exe kullanırken veya (Visual Studio) **hizmet Başvurusu Ekle** araçları, tüm MsCorLib.dll türlerini otomatik olarak başvurulan.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>İçeri aktarma seçenekleri: Olmayan DataContract şema IXmlSerializable türleri olarak alma  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Şemasının sınırlı bir alt kümesini destekler. Desteklenmeyen şema yapıları (örneğin, XML öznitelikleri) varsa, içe aktarma girişimi bir özel durum ile başarısız olur. Ancak, ayarı <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> özelliğine `true` desteklenen şema aralığını genişletir. Ayarlandığında `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> uygulama türleri oluşturur <xref:System.Xml.Serialization.IXmlSerializable> arabirimi. Bu, bu tür XML gösterimini doğrudan erişim sağlar.  
  
##### <a name="design-considerations"></a>Tasarım konuları  
  
-   Zayıf yazılmış XML gösterimi ile doğrudan çalışmak zor olabilir. Bir alternatif serileştirme motoruna gibi kullanmayı <xref:System.Xml.Serialization.XmlSerializer>, şema verilerle uyumlu olmayan sözleşmeleri kesin türü belirtilmiş şekilde çalışmak için. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Bazı şema yapıları tarafından aktarılamaz <xref:System.Runtime.Serialization.XsdDataContractImporter> bile <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> özelliği ayarlanmış `true`. Yeniden kullanmayı <xref:System.Xml.Serialization.XmlSerializer> bu gibi durumlarda için.  
  
-   Her ikisi de olan tam şema yapıları desteklenen zaman <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> olan `true` veya `false` açıklanan [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Şema için oluşturulan <xref:System.Xml.Serialization.IXmlSerializable> türleri içe ve dışa aktarılan uygunluğunu korumak değil. Diğer bir deyişle, şema oluşturulan türlerinden verme ve sınıfları olarak alma özgün şema döndürmez.  
  
 Birleştirmek olasıdır <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> seçeneğini <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> daha önce açıklanan seçeneği. Olarak oluşturulacak türleri için <xref:System.Xml.Serialization.IXmlSerializable> uygulamaları, yapısal onay kullanırken atlandı <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> özelliği.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Seçeneği karşılık gelen **/importXmlTypes** Svcutil.exe aracını kullanarak geçiş yapın.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Oluşturulan IXmlSerializable türleri ile çalışma  
 Oluşturulan `IXmlSerializable` türlerini "nodesField," adlı özel bir alan içeren bir dizi döndürür <xref:System.Xml.XmlNode> nesneleri. Bu tür bir türünün bir örneği çıkarılırken XML belge nesnesi modeli kullanarak XML veri aracılığıyla doğrudan bu alana erişebilirsiniz. Seri hale getirilir ve bu türünün bir örneğini serileştirirken Bu alan için istenen XML verileri ayarlayabilirsiniz.  
  
 Bu aracılığıyla gerçekleştirilir `IXmlSerializable` uygulaması. Oluşturulan içinde `IXmlSerializable` türü, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> uygulama çağrıları <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> yöntemi <xref:System.Runtime.Serialization.XmlSerializableServices> sınıfı. Yöntem aracılığıyla sağlanan XML dönüştüren bir yardımcı yöntemdir bir <xref:System.Xml.XmlReader> dizisi olarak <xref:System.Xml.XmlNode> nesneleri. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama karşıtı yapar ve dizisine dönüştürür `XmlNode` bir dizi nesnelere <xref:System.Xml.XmlWriter> çağrıları. Bu kullanılarak gerçekleştirilir <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> yöntemi.  
  
 Şema verme işlemi oluşturulan üzerinde çalıştırmak mümkündür `IXmlSerializable` sınıfları. Daha önce belirtildiği gibi özgün şema geri alamayacaksınız. Bunun yerine, herhangi bir XSD türü için bir joker karakter "anyType" standart XSD türü olan, alırsınız.  
  
 Bu uygulama tarafından gerçekleştirilir <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği oluşturulmuş `IXmlSerializable` sınıfları ve bir yöntem belirterek çağırır <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> yöntemi "anyType" türü.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Türü var. yalnızca belirli bu özelliği desteklemek için. Başka bir amaç için kullanım için önerilmez.  
  
#### <a name="import-options-advanced-options"></a>İçeri aktarma seçenekleri: Gelişmiş Seçenekleri  
 Aşağıdaki içeri aktarma Gelişmiş Seçenekler:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> özellik. Belirtin <xref:System.CodeDom.Compiler.CodeDomProvider> oluşturulan sınıflar için kod oluşturmak için kullanılacak. Alma mekanizması girişimleri önlemek için özellikleri <xref:System.CodeDom.Compiler.CodeDomProvider> desteklemiyor. Varsa <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> ayarlı değil, tam kümesi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] özellikleri ile herhangi bir kısıtlama kullanılır.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> özellik. Bir <xref:System.Runtime.Serialization.IDataContractSurrogate> uygulaması bu özellik ile belirtilebilir. <xref:System.Runtime.Serialization.IDataContractSurrogate> İçeri aktarma işlemi özelleştirir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir yedek kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [Veri Anlaşması Yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)  
 [Şema İçeri ve Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Sınıflardan Şemaları Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
