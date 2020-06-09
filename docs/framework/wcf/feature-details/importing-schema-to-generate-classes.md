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
ms.openlocfilehash: 01f5162727a213fa5dcdf8a70e4e8e4c3627f086
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596909"
---
# <a name="importing-schema-to-generate-classes"></a>Sınıf Oluşturmak için Şemayı İçe Aktarma
Windows Communication Foundation (WCF) ile kullanılabilen şemalardan sınıflar oluşturmak için, <xref:System.Runtime.Serialization.XsdDataContractImporter> sınıfını kullanın. Bu konuda işlem ve Çeşitlemeler açıklanmaktadır.  
  
## <a name="the-import-process"></a>Içeri aktarma Işlemi
 Şema içeri aktarma işlemi bir ile başlar <xref:System.Xml.Schema.XmlSchemaSet> ve bir oluşturur <xref:System.CodeDom.CodeCompileUnit> .  
  
 , `XmlSchemaSet` BIR XML şeması tanım dili (xsd) şema belgelerinin bir kümesini temsil eden .NET Framework şema nesne modeli 'nin (som) bir parçasıdır. `XmlSchemaSet`BIR xsd belgeleri kümesinden bir nesne oluşturmak için, her bir belgeyi bir nesne içine serisini kaldırma <xref:System.Xml.Schema.XmlSchema> (kullanarak <xref:System.Xml.Serialization.XmlSerializer> ) ve bu nesneleri yeni bir öğesine ekleyin `XmlSchemaSet` .  
  
 , `CodeCompileUnit` Bir soyut şekilde .NET Framework kodunu temsil eden .NET Framework kod belge nesne modeli (CodeDom) parçasıdır. İçindeki gerçek kodu oluşturmak için, `CodeCompileUnit` veya sınıfı gibi sınıfının bir alt sınıfını kullanın <xref:System.CodeDom.Compiler.CodeDomProvider> <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> .  
  
### <a name="to-import-a-schema"></a>Bir şemayı içeri aktarmak için  
  
1. <xref:System.Runtime.Serialization.XsdDataContractImporter> nesnesinin bir örneğini oluşturun.  
  
2. İsteğe bağlı. Oluşturucuda bir geçirin `CodeCompileUnit` . Şema içeri aktarma sırasında oluşturulan türler, `CodeCompileUnit` boş olarak başlamak yerine bu örneğe eklenir `CodeCompileUnit` .  
  
3. İsteğe bağlı. Yöntemlerden birini çağırın <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> . Yöntemi, verilen şemanın geçerli bir veri anlaşması şeması olup olmadığını ve içeri aktarılabileceğini belirler. `CanImport`Yöntemi ile aynı aşırı yüklemeleri (bir `Import` sonraki adımla) içerir.  
  
4. Daha fazla yüklenmiş `Import` metotlardan birini çağırın, örneğin, <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> yöntemi.  
  
     En basit aşırı yükleme bir alır `XmlSchemaSet` ve bu şema kümesinde bulunan anonim türler dahil olmak üzere tüm türleri içeri aktarır. Diğer aşırı yüklemeler XSD türünü veya alınacak türlerin bir listesini belirtmenize izin verir (bir <xref:System.Xml.XmlQualifiedName> veya bir nesne koleksiyonu biçiminde `XmlQualifiedName` ). Bu durumda, yalnızca belirtilen türler içeri aktarılır. Aşırı yükleme <xref:System.Xml.Schema.XmlSchemaElement> , belirli bir öğeyi öğesinden ve `XmlSchemaSet` ilişkili türünü (anonim olup olmadığı) içeri aktaran bir ' ı alır. Bu aşırı yükleme `XmlQualifiedName` , bu öğe için oluşturulan türün veri sözleşmesi adını temsil eden bir döndürür.  
  
     Metodun birden çok çağrısı `Import` , aynı birden çok öğe eklenmesine neden olacak `CodeCompileUnit` . Bir tür, zaten varsa öğesine oluşturulmaz `CodeCompileUnit` . `Import` `XsdDataContractImporter` Birden çok nesne kullanmak yerine aynı şekilde birden çok kez çağırın `XsdDataContractImporter` . Bu, oluşturulmuş yinelenen türlerin oluşmaması için önerilen yoldur.  
  
    > [!NOTE]
    > İçeri aktarma işlemi sırasında bir hata oluşursa, `CodeCompileUnit` öngörülemeyen bir durumda olur. `CodeCompileUnit`Başarısız bir içeri aktarma işleminden kaynaklanan bir işlemin kullanılması sizi güvenlik açıklarına maruz bırakabilir.  
  
5. `CodeCompileUnit`Özelliği aracılığıyla öğesine erişin <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> .  
  
### <a name="import-options-customizing-the-generated-types"></a>İçeri aktarma seçenekleri: oluşturulan türleri özelleştirme  
 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>Öğesinin özelliğini, <xref:System.Runtime.Serialization.XsdDataContractImporter> <xref:System.Runtime.Serialization.ImportOptions> içe aktarma işleminin çeşitli yönlerini denetlemek için sınıfının bir örneğine ayarlayabilirsiniz. Bir dizi seçenek, oluşturulan türleri doğrudan etkiler.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Erişim düzeyini denetleme (GenerateInternal veya/Internal anahtarı)  
 Bu, [ServiceModel meta veri yardımcı programı aracında (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) **/Internal** anahtarına karşılık gelir.  
  
 Genel türler normalde şemadan, özel alanlarla ve ortak veri üyesi özellikleriyle eşleşen şemadan oluşturulur. Bunun yerine iç türler oluşturmak için <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliğini olarak ayarlayın `true` .  
  
 Aşağıdaki örnek, <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> özelliği olarak ayarlandığında bir iç sınıfa dönüştürülmüş bir şemayı gösterir`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Ad alanlarını denetleme (ad alanları veya/Namespace anahtarı)  
 Bu, aracındaki **/Namespace** anahtarına karşılık gelir `Svcutil.exe` .  
  
 Normalde şemadan oluşturulan türler, [veri sözleşmesi şema başvurusunda](data-contract-schema-reference.md)açıklanan bir eşlemeye göre belirli bir .NET Framework ad alanına karşılık gelen her XSD ad alanı ile .NET Framework ad alanları içinde oluşturulur. Bu eşlemeyi özelliği ile özelleştirebilirsiniz <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> <xref:System.Collections.Generic.Dictionary%602> . Belirli bir XSD ad alanı sözlükte bulunursa, eşleşen .NET Framework ad alanı sözlüğünüze de alınır.  
  
 Örneğin, aşağıdaki şemayı göz önünde bulundurun.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Aşağıdaki örnek, `Namespaces` `http://schemas.contoso.com/carSchema` "contoso. araba" ad alanını eşlemek için özelliğini kullanır.  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>SerializableAttribute (GenerateSerializable veya/Serializable anahtar) ekleniyor  
 Bu, aracındaki **/Serializable** anahtarına karşılık gelir `Svcutil.exe` .  
  
 Bazen şemadan oluşturulan türlerin .NET Framework çalışma zamanı serileştirme altyapılarıyla (örneğin, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> ve sınıfları) kullanılabilir olması önemlidir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Bu, .NET Framework uzaktan iletişim için türler kullanılırken kullanışlıdır. Bunu etkinleştirmek için, <xref:System.SerializableAttribute> normal özniteliğe ek olarak oluşturulan türlere özniteliği uygulamanız gerekir <xref:System.Runtime.Serialization.DataContractAttribute> . İçeri aktarma seçeneği olarak ayarlandıysa öznitelik otomatik olarak oluşturulur `GenerateSerializable` `true` .  
  
 Aşağıdaki örnek, `Vehicle` `GenerateSerializable` olarak ayarlanmış içeri aktarma seçeneği ile oluşturulan sınıfı gösterir `true` .  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Veri bağlama desteği ekleme (EnableDataBinding veya/enableDataBinding anahtarı)  
 Bu, Svcutil. exe aracındaki **/EnableDataBinding** anahtarına karşılık gelir.  
  
 Bazen, bu türlerin örneklerine yönelik tüm güncelleştirmeler Kullanıcı arabirimini otomatik olarak güncelleştirecek şekilde şemadan oluşturulan türleri grafik kullanıcı arabirimi bileşenlerine bağlamak isteyebilirsiniz. , `XsdDataContractImporter` <xref:System.ComponentModel.INotifyPropertyChanged> Herhangi bir özellik değişikliğinin bir olayı tetiklediği şekilde arabirimi uygulayan türler oluşturabilir. Bu arabirimi (örneğin, Windows Presentation Foundation (WPF)) destekleyen bir istemci kullanıcı arabirimi programlama ortamıyla kullanılmak üzere tür oluşturuyorsanız, <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> Bu özelliği etkinleştirmek için özelliğini olarak ayarlayın `true` .  
  
 Aşağıdaki örnek, `Vehicle` olarak kümesiyle oluşturulan sınıfı gösterir <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> `true` .  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>İçeri aktarma seçenekleri: koleksiyon türlerini seçme  
 XML 'deki iki özel desen öğe koleksiyonlarını temsil eder: bir öğe ve diğeri arasındaki öğe ve ilişkilerin listeleri. Aşağıda dizeler listesinin bir örneği verilmiştir.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Aşağıda, bir dize ve bir tamsayı (ve) arasındaki ilişkilendirmenin bir örneği verilmiştir `city name` `population` .  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
> Herhangi bir ilişkilendirme de bir liste olarak kabul edilebilir. Örneğin, önceki ilişkilendirmeyi, `city` iki alanı (bir dize alanı ve bir tamsayı alanı) olan karmaşık nesneler listesi olarak görüntüleyebilirsiniz. Her iki desen de XSD şemasında temsili vardır. Bir liste ile bir ilişki arasındaki farkı ayırt etmenin bir yolu yoktur. bu nedenle, şemada WCF 'ye özgü özel bir ek açıklama varsa, bu tür desenler her zaman liste olarak değerlendirilir. Ek açıklama, belirli bir düzenin bir ilişkilendirmeyi temsil ettiğini belirtir. Daha fazla bilgi için bkz. [veri sözleşmesi şema başvurusu](data-contract-schema-reference.md).  
  
 Normalde, bir liste, şemanın standart adlandırma deseninin takip edilip edilmeyeceğini bağlı olarak, genel bir listeden veya .NET Framework dizi olarak türetilen koleksiyon veri anlaşması olarak içeri aktarılır. Bu, [veri sözleşmeleri Içindeki koleksiyon türlerinde](collection-types-in-data-contracts.md)daha ayrıntılı olarak açıklanmıştır. İlişkilendirmeler normalde <xref:System.Collections.Generic.Dictionary%602> Sözlük nesnesinden türetilen bir veya koleksiyon veri anlaşması olarak içeri aktarılır. Örneğin, aşağıdaki şemayı göz önünde bulundurun.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Bu, aşağıdaki gibi içeri aktarılır (okunabilirlik için özellikler yerine alanlar gösterilir).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Bu tür şema desenleri için oluşturulan koleksiyon türlerini özelleştirmek mümkündür. Örneğin, <xref:System.ComponentModel.BindingList%601> <xref:System.Collections.Generic.List%601> türü bir liste kutusuna bağlamak ve koleksiyonun içerikleri değiştiğinde otomatik olarak güncelleştirilmesini sağlamak için sınıfı yerine sınıfından türetilen Koleksiyonlar oluşturmak isteyebilirsiniz. Bunu yapmak için, <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> <xref:System.Runtime.Serialization.ImportOptions> sınıfının özelliğini kullanılacak koleksiyon türleri listesine ayarlayın (bundan sonra başvurulan türler olarak bilinirdi). Herhangi bir koleksiyon içeri aktarılırken, başvurulan koleksiyon türlerinin bu listesi taranır ve bir tane bulunursa en iyi eşleşen koleksiyon kullanılır. İlişkilendirmeler yalnızca genel veya genel olmayan arabirimi uygulayan türlerle eşleştirilir <xref:System.Collections.IDictionary> , ancak listeler desteklenen herhangi bir koleksiyon türüyle eşleştirilir.  
  
 Örneğin, <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği bir olarak ayarlandıysa <xref:System.ComponentModel.BindingList%601> , `people` Yukarıdaki örnekteki tür aşağıdaki gibi oluşturulur.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Kapalı bir genel, en iyi eşleşme olarak değerlendirilir. Örneğin, türleri `BindingList(Of Integer)` ve <xref:System.Collections.ArrayList> başvurulan türlerin koleksiyonuna geçirilirse, şemada bulunan tüm tamsayılar listesi bir olarak içeri aktarılır `BindingList(Of Integer)` . Diğer tüm listeler (örneğin,) `List(Of String)` bir olarak içeri aktarılır `ArrayList` .  
  
 Genel arabirimi uygulayan bir tür `IDictionary` başvurulan türler koleksiyonuna eklenirse, tür parametreleri tamamen açık ya da tam kapalı olmalıdır.  
  
 Yinelemelere izin verilmez. Örneğin, başvurulan türlere hem a hem de ekleyemezsiniz `List(Of Integer)` `Collection(Of Integer)` . Bu, şemada bir tamsayılar listesi bulunduğunda kullanılması gereken belirlenmesi olanaksız hale getirir. Yinelemeler yalnızca, bir şemada yinelenen sorunları ortaya çıkaran bir tür varsa tespit edilir. Örneğin, içeri aktarılan şema tamsayılar listesi içermiyorsa, başvurulan türler koleksiyonunda hem hem de öğesine sahip olmasına izin verilir `List(Of Integer)` `Collection(Of Integer)` , ancak hiçbir etkiye sahip olmaz.  
  
 Başvurulan koleksiyon türleri mekanizması, karmaşık türlerin koleksiyonları (diğer koleksiyonların koleksiyonları dahil) için eşit derecede iyi bir şekilde çalışarak, yalnızca temel elemanlar koleksiyonları için değildir.  
  
 `ReferencedCollectionTypes`Özelliği, SvcUtil. exe aracında **/CollectionType** anahtarına karşılık gelir. Birden çok koleksiyon türüne başvurmak için, **/CollectionType** anahtarının birden çok kez belirtilmesi gerektiğini unutmayın. Tür MsCorLib. dll içinde değilse, derleme için **/Reference** anahtarı kullanılarak da başvurulmalıdır.  
  
#### <a name="import-options-referencing-existing-types"></a>İçeri aktarma seçenekleri: Varolan türlere başvurma  
 Bazen, şemadaki türler var olan .NET Framework türlerine karşılık gelir ve bu türleri sıfırdan oluşturmanız gerekmez. (Bu bölüm yalnızca koleksiyon olmayan türler için geçerlidir. Koleksiyon türleri için önceki bölüme bakın.)  
  
 Örneğin, bir kişiyi temsil eden her zaman kullanmak istediğiniz standart bir şirket genelinde "kişi" veri sözleşmesi türü olabilir. Bazı hizmetler bu türü her kullandığında ve şeması hizmet meta verilerinde göründüğünde, `Person` her hizmet için yeni bir tane oluşturmak yerine, bu şemayı içeri aktarırken var olan türü yeniden kullanmak isteyebilirsiniz.  
  
 Bunu yapmak için, özelliği sınıfında döndüren koleksiyona yeniden kullanmak istediğiniz .NET Framework türlerinin bir listesini geçirin <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> <xref:System.Runtime.Serialization.ImportOptions> . Bu türlerden birinde, bir şema türünün adı ve ad alanıyla eşleşen bir veri anlaşması adı ve ad alanı varsa, yapısal bir karşılaştırma gerçekleştirilir. Türlerin hem eşleşen adları hem de eşleşen yapıları olduğunu tespit ederseniz, yeni bir tane oluşturmak yerine var olan .NET Framework türü yeniden kullanılır. Yalnızca ad, yapıyla eşleşiyorsa, bir özel durum oluşturulur. Türler (örneğin, yeni isteğe bağlı veri üyeleri ekleme) olduğunda sürüm oluşturma için bir kesinti olmadığını unutmayın. Yapıların tam olarak eşleşmesi gerekir.  
  
 Bu ad ve ad alanı ile hiçbir şema türü içeri aktarılmadığı sürece, başvurulan türler koleksiyonuna aynı veri anlaşması adına ve ad alanına sahip birden çok tür eklemek geçerlidir. Bu, şemada aslında olmayan türler için yinelemeler hakkında endişelenmenize gerek kalmadan bir derlemedeki tüm türleri koleksiyona kolayca eklemenizi sağlar.  
  
 `ReferencedTypes`Özelliği, Svcutil. exe aracının belirli modundaki çalışma modlarında **/Reference** anahtarına karşılık gelir.  
  
> [!NOTE]
> Svcutil. exe veya (Visual Studio 'da) **hizmet başvurusu Ekle** araçları kullanılırken, mscorlib. dll ' deki tüm türlere otomatik olarak başvurulur.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>İçeri aktarma seçenekleri: DataContract olmayan şemayı IXmlSerializable türleri olarak Içeri aktarma  
 , <xref:System.Runtime.Serialization.XsdDataContractImporter> Şemanın sınırlı bir alt kümesini destekler. Desteklenmeyen şema yapıları varsa (örneğin, XML öznitelikleri), içeri aktarma girişimi bir özel durumla başarısız olur. Ancak, <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> özelliği olarak ayarlamak, `true` Desteklenen şema aralığını genişletir. Olarak ayarlandığında `true` , <xref:System.Runtime.Serialization.XsdDataContractImporter> arabirimini uygulayan türler oluşturulur <xref:System.Xml.Serialization.IXmlSerializable> . Bu, bu türlerin XML gösterimine doğrudan erişim sağlar.  
  
##### <a name="design-considerations"></a>Tasarımda Dikkat Edilmesi Gerekenler  
  
- Doğrudan yazılmış XML temsili ile çalışmak zor olabilir. <xref:System.Xml.Serialization.XmlSerializer>Şema ile, veri sözleşmeleri için kesin olarak belirlenmiş bir şekilde uyumlu olmayan bir şekilde çalışmak için alternatif bir serileştirme altyapısı kullanmayı düşünün. Daha fazla bilgi için, bkz. [XmlSerializer sınıfını kullanma](using-the-xmlserializer-class.md).  
  
- Bazı şema yapıları, <xref:System.Runtime.Serialization.XsdDataContractImporter> özelliği olarak ayarlandığında bile tarafından içeri aktarılamaz <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> `true` . <xref:System.Xml.Serialization.XmlSerializer>Bu durumda, bu gibi durumlarda kullanmayı düşünün.  
  
- Her ikisi de <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> `true` veya `false` [veri sözleşmesi şema başvurusunda](data-contract-schema-reference.md)açıklananlar tarafından desteklenen tam şema yapıları.  
  
- Oluşturulan türler için şema <xref:System.Xml.Serialization.IXmlSerializable> içeri aktarıldığında ve verildiğinde uygunluğu korumaz. Diğer bir deyişle, şemayı oluşturulan türlerden dışa aktarma ve sınıflar olarak içeri aktarma özgün şemayı döndürmez.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>Seçeneği, <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> daha önce açıklanan seçenekle birleştirmek mümkündür. Uygulamalar olarak oluşturulması gereken türler için <xref:System.Xml.Serialization.IXmlSerializable> , özelliği kullanılırken yapısal denetim atlanır <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> .  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>Seçeneği, Svcutil. exe aracında **/ImportXmlTypes** anahtarına karşılık gelir.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Oluşturulan IXmlSerializable türleriyle çalışma  
 Oluşturulan `IXmlSerializable` türler, bir nesne dizisi döndüren "nodesField" adlı bir özel alan içerir <xref:System.Xml.XmlNode> . Böyle bir türün bir örneğinin serisini kaldırırken, XML verilerine doğrudan bu alan aracılığıyla XML Belge Nesne Modeli erişebilirsiniz. Bu türün bir örneğini serileştirilirken, bu alanı istenen XML verilerine ayarlayabilirsiniz ve seri hale gelir.  
  
 Bu, uygulama aracılığıyla yapılır `IXmlSerializable` . Oluşturulan `IXmlSerializable` türde <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> uygulama, <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> sınıfının yöntemini çağırır <xref:System.Runtime.Serialization.XmlSerializableServices> . Yöntemi, tarafından bir nesne dizisi aracılığıyla sağlanmış XML 'i dönüştüren bir yardımcı yöntemdir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlNode> . <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Uygulama tersini yapar ve `XmlNode` nesne dizisini bir çağrı dizisine dönüştürür <xref:System.Xml.XmlWriter> . Bu, yöntemi kullanılarak gerçekleştirilir <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> .  
  
 Şema dışa aktarma işlemini üretilen sınıflarda çalıştırmak mümkündür `IXmlSerializable` . Daha önce belirtildiği gibi, özgün şemayı geri almanız gerekir. Bunun yerine, herhangi bir XSD türü için bir joker karakter olan "anyType" standart XSD türü alırsınız.  
  
 Bu, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği oluşturulan `IXmlSerializable` sınıflara uygulanarak ve <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> "anyType" türünü oluşturmak için yöntemini çağıran bir yöntemi belirterek gerçekleştirilir.  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.XmlSerializableServices>Tür yalnızca söz konusu özelliği desteklemek için vardır. Herhangi bir amaçla kullanılması önerilmez.  
  
#### <a name="import-options-advanced-options"></a>İçeri aktarma seçenekleri: Gelişmiş Seçenekler  
 Aşağıda gelişmiş içeri aktarma seçenekleri verilmiştir:  
  
- <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>özelliði. <xref:System.CodeDom.Compiler.CodeDomProvider>Oluşturulan sınıfların kodunu oluşturmak için kullanılacak öğesini belirtin. İçeri aktarma mekanizması, tarafından desteklenmeyen özelliklerden kaçınmaya çalışır <xref:System.CodeDom.Compiler.CodeDomProvider> . <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>Ayarlanmamışsa, .NET Framework özelliklerinin tam kümesi hiçbir kısıtlama olmadan kullanılır.  
  
- <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>özelliði. <xref:System.Runtime.Serialization.IDataContractSurrogate>Bu özellikle bir uygulama belirtilebilir. <xref:System.Runtime.Serialization.IDataContractSurrogate>İçeri aktarma işlemini özelleştirir. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../extending/data-contract-surrogates.md). Varsayılan olarak, hiçbir yedek kullanılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Veri Sözleşmesi Şema Başvurusu](data-contract-schema-reference.md)
- [Veri Anlaşması Yedekleri](../extending/data-contract-surrogates.md)
- [Şema İçeri ve Dışarı Aktarma](schema-import-and-export.md)
- [Sınıflardan Şemaları Dışarı Aktarma](exporting-schemas-from-classes.md)
- [Veri Sözleşmesi Şema Başvurusu](data-contract-schema-reference.md)
