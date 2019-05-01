---
title: Sınıf Oluşturmak için Şemayı İçe Aktarma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: 68890a5d86d2781e3c8079c86e941144e3796ea6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972672"
---
# <a name="importing-schema-to-generate-classes"></a>Sınıf Oluşturmak için Şemayı İçe Aktarma
Windows Communication Foundation (WCF) ile kullanılabilir şemaları gelen sınıflar oluşturmak için <xref:System.Runtime.Serialization.XsdDataContractImporter> sınıfı. Bu konu, işlem ve farklılıkları açıklar.  
  
## <a name="the-import-process"></a>İçeri aktarma işlemi
 Şema içeri aktarma işlemi ile başlayan bir <xref:System.Xml.Schema.XmlSchemaSet> ve üreten bir <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Bir parçası olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ait XML Şeması Tanım Dili (XSD) şeması belgeleri kümesini temsil eder şema nesne modeli (SOM). Oluşturmak için bir `XmlSchemaSet` XSD belgelerinin kümesinden nesnesi, her bir belgeye seri durumdan bir <xref:System.Xml.Schema.XmlSchema> nesne (kullanarak <xref:System.Xml.Serialization.XmlSerializer>) ve bu nesneler, yeni bir ekleme `XmlSchemaSet`.  
  
 `CodeCompileUnit` Parçasıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ait kod belge nesne modeli (CodeDOM) temsil eden [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] soyut bir şekilde kod. Gerçek kod oluşturmak için bir `CodeCompileUnit`, öğesinin kullanın <xref:System.CodeDom.Compiler.CodeDomProvider> gibi sınıf <xref:Microsoft.CSharp.CSharpCodeProvider> veya <xref:Microsoft.VisualBasic.VBCodeProvider> sınıfı.  
  
### <a name="to-import-a-schema"></a>Bir şemayı içeri aktarmak için  
  
1. Bir örneğini oluşturmak <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. İsteğe bağlı. Başarılı bir `CodeCompileUnit` oluşturucuda. Şema içeri aktarma sırasında oluşturulan türler için eklenen `CodeCompileUnit` örneği yerine boş bir ile başlayan `CodeCompileUnit`.  
  
3. İsteğe bağlı. Birini çağırın <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> yöntemleri. Yöntemi, belirtilen şema geçerli veri sözleşmesi şema ve aktarılabilir belirler. `CanImport` Yöntemi olarak aynı aşırı sahip `Import` (sonraki adım).  
  
4. Aşırı yüklenen birini çağırın `Import` yöntemleri, örneğin, <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> yöntemi.  
  
     En basit aşırı yüklemesi gereken bir `XmlSchemaSet` ve bu şema kümesinde bulunamadı, anonim türleri dahil olmak üzere tüm türleri içeri aktarır. Diğer aşırı yüklemeler, içeri aktarmak için XSD türü veya türlerinin bir listesini belirtmenizi sağlar (biçiminde bir <xref:System.Xml.XmlQualifiedName> veya koleksiyonu `XmlQualifiedName` nesneleri). Bu durumda, yalnızca belirtilen türlere içeri aktarılır. Aşırı alır bir <xref:System.Xml.Schema.XmlSchemaElement> / belirli bir öğeyle aktaran `XmlSchemaSet`, ilişkili türünü (veya anonim olup) yanı sıra. Bu aşırı yükleme döndürür bir `XmlQualifiedName`, bu öğe için oluşturulan türü veri anlaşması adına temsil eder.  
  
     Birden çok çağıran `Import` yöntemi sonucu birden çok öğe aynı eklenen `CodeCompileUnit`. Bir tür içinde oluşturulmaz `CodeCompileUnit` zaten var olup olmadığını. Çağrı `Import` üzerinde birden çok kez aynı `XsdDataContractImporter` birden çok kullanmak yerine `XsdDataContractImporter` nesneleri. Yinelenen tür oluşturulmasını önlemek için önerilen yöntem budur.  
  
    > [!NOTE]
    > İçeri aktarma sırasında bir hata varsa `CodeCompileUnit` öngörülemeyen durumda olacaktır. Kullanarak bir `CodeCompileUnit` başarısız bir alma işleminden kaynaklanan görülebilmesine neden olabilir, güvenlik açıklarını.  
  
5. Erişim `CodeCompileUnit` aracılığıyla <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> özelliği.  
  
### <a name="import-options-customizing-the-generated-types"></a>İçeri aktarma seçenekleri: Oluşturulan türler özelleştirme  
 Ayarlayabileceğiniz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği <xref:System.Runtime.Serialization.XsdDataContractImporter> örneğine <xref:System.Runtime.Serialization.ImportOptions> içeri aktarma işlemi çeşitli yönlerini denetlemek için sınıf. Bir dizi seçenek oluşturulan türler doğrudan etkiler.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Erişim düzeyi denetleme (GenerateInternal veya / iç geçiş)  
 Bu karşılık gelir **/ iç** açın [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalde, genel türler, özel alanlar ve eşleşen ortak veri üyesi özellikleri ile şemasından oluşturulur. Bunun yerine iç türleri üretmek için ayarlanmış <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliğini `true`.  
  
 Aşağıdaki örnek, bir iç dönüştürülen bir şema gösterir sınıfı <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliği `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Ad alanları (ad alanları veya geçiş/namespace) denetleme  
 Bu karşılık gelir **/namespace** açın `Svcutil.exe` aracı.  
  
 Normalde, içine şemadan oluşturulan türler üretilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ad alanları, belirli bir karşılık gelen her XSD ad alanı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ad alanı içinde tanımlanan bir eşleme göre [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu eşleme tarafından özelleştirebilirsiniz <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> özelliğini bir <xref:System.Collections.Generic.Dictionary%602>. Belirtilen bir XSD ad alanı eşleme sözlüğünde bulunursa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ad alanı, sözlükten de alınır.  
  
 Örneğin, aşağıdaki şema düşünün.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Aşağıdaki örnekte `Namespaces` eşlemek için özellik `http://schemas.contoso.com/carSchema` "Contoso.Cars" için ad alanı.  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>SerializableAttribute ekleme (GenerateSerializable veya / seri hale getirilebilir geçiş)  
 Bu karşılık gelir **/ seri hale getirilebilir** açın `Svcutil.exe` aracı.  
  
 Bazen ile kullanılabilir şemadan oluşturulan türler için önemli olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] çalışma zamanı serileştirme altyapıları (örneğin, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sınıfları). Türleri için kullanırken bu kullanışlıdır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uzaktan iletişim. Bunu etkinleştirmek için uygulamanız gerekir <xref:System.SerializableAttribute> normal ek olarak oluşturulan türler için öznitelik <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Öznitelik, otomatik olarak oluşturulan `GenerateSerializable` içeri aktarma seçeneği `true`.  
  
 Aşağıdaki örnekte gösterildiği `Vehicle` ile oluşturulan sınıf `GenerateSerializable` içeri aktarma seçeneği ayarlanmış `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Veri bağlama desteği (EnableDataBinding ya da /enableDataBinding anahtar) ekleme  
 Bu karşılık gelir **/enableDataBinding** Svcutil.exe aracını geçin.  
  
 Bazı durumlarda, böylece bu tür örnekleri için herhangi bir güncelleştirme kullanıcı Arabirimi otomatik olarak güncelleştirecektir grafik kullanıcı arabirimi bileşenlerine şemadan oluşturulan türler bağlamak isteyebilirsiniz. `XsdDataContractImporter` Uygulayan türler oluşturabilir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi şekilde herhangi bir özellik değişikliği bir olayı tetikler. Bu arabirim (gibi Windows Presentation Foundation (WPF)) destekleyen istemci kullanıcı Arabirimi programlama ortamı ile kullanmak için türleri oluşturuyorsanız ayarlayın <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> özelliğini `true` bu özelliği etkinleştirmek için.  
  
 Aşağıdaki örnekte gösterildiği `Vehicle` ile oluşturulan sınıf <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> kümesine `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>İçeri aktarma seçenekleri: Koleksiyon türleri seçme  
 İki özel düzen XML öğe koleksiyonunu temsil eder: öğeleri ve başka bir öğe arasındaki ilişkilendirmeleri ve listeler. Bir dize listesi örneği verilmiştir.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Bir dize ve tamsayı arasında bir ilişki örneği aşağıda verilmiştir (`city name` ve `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Herhangi bir ilişki listesini de değerlendirilebilir. Örneğin, karmaşık bir liste olarak önceki ilişkisini görüntüleyebileceğiniz `city` (bir dize alanı ve tamsayı alan) iki alan bilgisine nesneleri. Her iki gösterimi XSD şemasında sahiptir. WCF için belirli bir özel açıklama şemada olmadıkça desenler her zaman listeler olarak kabul edilir şekilde listesini arasında bir ilişkilendirme ayırt etmek için hiçbir yolu yoktur. Ek açıklama, belirli bir desen bir ilişkiyi temsil ettiğini gösterir. Daha fazla bilgi için [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Normalde, bir liste olarak veya bir genel liste türetilen bir koleksiyon veri anlaşması olarak içeri aktarılır bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] olup olmadığını şema koleksiyonları için standart adlandırma deseni izleyen bağlı olarak, dizi. Bu daha ayrıntılı olarak açıklanan [veri anlaşmalarında koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). İlişkileri olarak normal olarak içeri aktarılan bir <xref:System.Collections.Generic.Dictionary%602> veya sözlük nesneden türetilen bir koleksiyon veri anlaşması. Örneğin, aşağıdaki şema düşünün.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 (Alanları yerine özellikleri okunabilirlik için gösterilir) aşağıdaki gibi alınır.  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Şema desenler için oluşturulan koleksiyon türlerini özelleştirmek mümkündür. Örneğin, türetilen koleksiyonları oluşturmak isteyebilirsiniz <xref:System.ComponentModel.BindingList%601> yerine <xref:System.Collections.Generic.List%601> sınıf türüne bir liste kutusuna bağlamak ve bu sahip için koleksiyonun içeriğini değiştiğinde otomatik olarak güncelleştirilecektir. Bunu yapmak için ayarlanmış <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> (bundan böyle başvurulan türleri olarak bilinen) kullanılacak koleksiyon türlerinin bir listesi için sınıf. Bu başvuru yapılan koleksiyon türlerinin listesi herhangi bir koleksiyonu içeri aktarma sırasında taranır ve en iyi eşleşen koleksiyon bulunması durumunda kullanılır. İlişkilendirmeleri, yalnızca genel veya nongeneric uygulayan türler karşı eşleştirilir <xref:System.Collections.IDictionary> listeleri herhangi bir desteklenen koleksiyon türü karşı eşleştirilir sırada arabirim.  
  
 Örneğin, varsa <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği bir <xref:System.ComponentModel.BindingList%601>, `people` önceki örnekte türü şu şekilde oluşturulur.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Kapalı genel en iyi eşleşme olarak değerlendirilir. Örneğin, varsa türleri `BindingList(Of Integer)` ve <xref:System.Collections.ArrayList> geçirilen başvurulan türleri koleksiyonu için tüm listeleri şemasında bulunan tamsayı olarak içeri aktarılan bir `BindingList(Of Integer)`. Diğer listelerinde, örneğin, bir `List(Of String)`, olarak içeri aktarılan bir `ArrayList`.  
  
 Genel uygulayan bir tür ise `IDictionary` arabirimi başvurulan türlerin koleksiyonuna eklendiğinde, kendi tür parametreleri ya da tamamen açık ya da tamamen kapalı olmalıdır.  
  
 Tekrarlara izin verilmez. Örneğin, her ikisi de eklenemiyor bir `List(Of Integer)` ve `Collection(Of Integer)` başvurulan türleri için. Bu şemada tamsayı listesi bulunduğunda, kullanılması gerektiğini belirlemek olanaksız hale. Yinelenen sorun ortaya koyan şemasında bir tür varsa yinelenenleri algılanır. İçeri aktarılan şema tamsayı listesi içermiyorsa, örneğin, her ikisi de izin verilmez `List(Of Integer)` ve `Collection(Of Integer)` başvurulan türleri koleksiyonu, ancak bunların hiçbiri hiçbir etkisi olmaz.  
  
 Mekanizması eşit çalışır başvuru yapılan koleksiyon türlerinin yanı sıra karmaşık türleri (diğer koleksiyonları koleksiyonları dahil) için koleksiyonları ve temel elemanlar koleksiyonlar için tam değil.  
  
 `ReferencedCollectionTypes` Karşılık gelen özellik **/collectionType** SvcUtil.exe aracını geçin. Birden çok koleksiyon türleri başvurmak için unutmayın **/collectionType** anahtarı birden çok kez belirtilmesi gerekir. Türü MsCorLib.dll içinde değilse, kendi derlemesi de kullanarak başvurulmalıdır **/reference** geçin.  
  
#### <a name="import-options-referencing-existing-types"></a>İçeri aktarma seçenekleri: Mevcut türlerine başvurma  
 Bazen, türler, varolan karşılık gelen [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve bu tür sıfırdan oluşturmaya gerek yoktur. (Bu bölüm yalnızca noncollection türleri için geçerlidir. Koleksiyon türleri için önceki bölüme bakın.)  
  
 Örneğin, bir kişiyi temsil eden çağrılırken istediğiniz her zaman bir standart şirket çapında "Kişi" veri anlaşması türü olabilir. Bazı hizmet yaptığında bu tür ve şeması görünür hizmet meta verileri içinde varolan yeniden kullanmak isteyebileceğiniz `Person` her hizmet için yeni bir tane oluşturmak yerine bu şemayı içeri aktarılırken yazın.  
  
 Bunu yapmak için bir listesini geçirmek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] koleksiyonuna yeniden kullanmak istediğiniz türleri <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> özelliği döndürür üzerinde <xref:System.Runtime.Serialization.ImportOptions> sınıfı. Bu tür herhangi bir veri anlaşması adına ve adıyla eşleşen bir ad alanı ve ad alanı şema türü varsa, Yapısal karşılaştırma gerçekleştirilir. Türleri eşleşen adları hem eşleşen yapıları, mevcut olduğunu belirlenirse [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü yeniden kullanılabilir yeni birini üretmek yerine. Yalnızca değil yapı adıyla eşleşen bir özel durum oluşturulur. Başvuru türleri (örneğin, ekleyerek yeni isteğe bağlı veri üyeleri), sürüm oluşturma için hiçbir izin olduğunu unutmayın. Yapıları tam olarak eşleşmelidir.  
  
 Hiçbir şema türü, ad ve ad alanı ile aktarılır sürece aynı veri anlaşması adına ve ad alanı birden çok tür başvurulan türlerin koleksiyonuna ekleme uygundur. Bu, kolayca tüm türlerin koleksiyonuna bir derlemede gerçekten şemasında gerçekleşmez türleri çoğaltmaları hakkında endişelenmeden eklemenize olanak sağlar.  
  
 `ReferencedTypes` Karşılık gelen özellik **/reference** Svcutil.exe aracını işleyişini belirli modlarında geçin.  
  
> [!NOTE]
>  Svcutil.exe kullanırken veya (Visual Studio'da) **hizmet Başvurusu Ekle** araçları, tüm MsCorLib.dll türlerini otomatik olarak başvurulur.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>İçeri aktarma seçenekleri: DataContract olmayan şemayı IXmlSerializable türü olarak içeri aktarma  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Şemasının sınırlı bir alt kümesini destekler. Desteklenmeyen şema yapıları (örneğin, XML özniteliği) varsa, içeri aktarma denemesi bir özel durum ile başarısız olur. Ancak, ayarı <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> özelliğini `true` desteklenen şema aralığını genişletir. Ayarlandığında `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> uygulayan türler oluşturur <xref:System.Xml.Serialization.IXmlSerializable> arabirimi. Bu, bu tür XML gösterimini doğrudan erişim sağlar.  
  
##### <a name="design-considerations"></a>Tasarım konuları  
  
- Zayıf yazılmış bir XML gösterimi ile doğrudan çalışmak zor olabilir. Bir alternatif serileştirme motoruna gibi kullanmayı göz önünde bulundurun <xref:System.Xml.Serialization.XmlSerializer>, şema verilerle uyumlu değil sözleşme türü kesin belirlenmiş bir şekilde çalışmak için. Daha fazla bilgi için [XmlSerializer sınıfını kullanarak](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
- Bazı şema yapıları tarafından içeri aktarılamaz <xref:System.Runtime.Serialization.XsdDataContractImporter> bile <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> özelliği `true`. Yeniden kullanmayı <xref:System.Xml.Serialization.XmlSerializer> böyle durumlar için.  
  
- Tam şema yapıları desteklenen zaman <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> olduğu `true` veya `false` açıklanan [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
- Şeması için üretilen <xref:System.Xml.Serialization.IXmlSerializable> türleri içe ve dışa aktarılan kalitesini korumak değil. Diğer bir deyişle, oluşturulan türlerinden şemasını dışarı aktarıp sınıfları içeri aktarma özgün şema döndürmez.  
  
 Birleştirmek mümkündür <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> seçeneğini <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> daha önce açıklanan seçeneği. Sahip olarak oluşturulacak türleri <xref:System.Xml.Serialization.IXmlSerializable> kullanırken uygulamaları yapısal onay atlandı <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> özelliği.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Seçeneği karşılık gelen **/importXmlTypes** Svcutil.exe aracını geçin.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Oluşturulan IXmlSerializable türleri ile çalışma  
 Oluşturulan `IXmlSerializable` türleri "nodesField," adlı özel bir alan içeren bir dizi döndüren <xref:System.Xml.XmlNode> nesneleri. Böyle bir türü örneği işlenirken XML belge nesne modeli kullanarak XML verilerini bu alana doğrudan erişebilirsiniz. Bu türün örneğini serileştirilirken Bu alan için istenen XML verileri ayarlayabilirsiniz ve bu seri hale.  
  
 Bu aracılığıyla gerçekleştirilir `IXmlSerializable` uygulaması. İçinde oluşturulan `IXmlSerializable` türü <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> uygulama çağrıları <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> yöntemi <xref:System.Runtime.Serialization.XmlSerializableServices> sınıfı. Yöntemi sağlanan XML dönüştüren bir yardımcı yöntemdir bir <xref:System.Xml.XmlReader> dizisi olarak <xref:System.Xml.XmlNode> nesneleri. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama tersi yok ve bir dizi dönüştürür `XmlNode` nesneleri dizisini <xref:System.Xml.XmlWriter> çağırır. Kullanılarak elde edilir <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> yöntemi.  
  
 Oluşturulan şema dışarı aktarma işlemi çalıştırmak mümkün `IXmlSerializable` sınıfları. Daha önce belirtildiği gibi özgün şema geri alamayacaksınız. Bunun yerine, herhangi bir XSD türü için joker karakter olan "anyType" standart XSD türü, alırsınız.  
  
 Bu uygulama tarafından gerçekleştirilir <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği oluşturulmuş `IXmlSerializable` sınıfları ve belirten bir yöntem çağrılarının <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> "anyType" türü oluşturmak için yöntemi.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Türü var. yalnızca bu belirli özelliğini desteklemek için. Başka bir amaçla kullanım için önerilmez.  
  
#### <a name="import-options-advanced-options"></a>İçeri aktarma seçenekleri: Gelişmiş Seçenekleri  
 Aşağıdaki içeri aktarma Gelişmiş Seçenekler:  
  
- <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> özellik. Belirtin <xref:System.CodeDom.Compiler.CodeDomProvider> oluşturulan sınıflar için kod oluşturmak için kullanılacak. İçeri aktarma mekanizması girişimleri önlemek için Özellikler <xref:System.CodeDom.Compiler.CodeDomProvider> desteklemez. Varsa <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> ayarlı değil, tam kümesini [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] özellikleri, kısıtlama olmadan kullanılır.  
  
- <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> özellik. Bir <xref:System.Runtime.Serialization.IDataContractSurrogate> uygulaması, bu özellik ile belirtilebilir. <xref:System.Runtime.Serialization.IDataContractSurrogate> İçeri aktarma işlemi özelleştirir. Daha fazla bilgi için [veri anlaşması yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir vekil kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [Veri Anlaşması Yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [Şema İçeri ve Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Sınıflardan Şemaları Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
