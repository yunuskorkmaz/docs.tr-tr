---
title: XmlSerializer Sınıfını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 18674a5410cd411ff78e2d3f768b02687cd13f6d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637349"
---
# <a name="using-the-xmlserializer-class"></a>XmlSerializer Sınıfını Kullanma
Windows Communication Foundation (WCF), istemciler ve hizmetler, serileştirme adlı bir işlem arasında aktarılır XML içinde uygulamanızda veri kapatmak için iki farklı bir seri hale getirme teknolojilerini kullanabilirsiniz.  
  
## <a name="datacontractserializer-as-the-default"></a>Varsayılan olarak DataContractSerializer  
 Varsayılan olarak WCF kullanan <xref:System.Runtime.Serialization.DataContractSerializer> veri türleri serileştirmek için sınıfı. Bu serileştiricinin aşağıdaki türlerini destekler:  
  
- Temel (örnek, tamsayı, dize ve bayt dizileri için), aşağıdakiler gibi bazı özel türleri yanı sıra türler <xref:System.Xml.XmlElement> ve <xref:System.DateTime>, hangi temel olarak kabul edilir.  
  
- Veri anlaşması türleri (türleri ile işaretlenen <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği).  
  
- Türleri ile işaretlenen <xref:System.SerializableAttribute> içeren öznitelik türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
- Türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi.  
  
- Birçok genel koleksiyon türleri dahil birçok ortak koleksiyon türleri.  
  
 Birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ikinci iki kategoriye ayrılır ve bu nedenle seri hale getirilebilir. Diziler seri hale getirilebilir türlerin seri hale getirilebilir. Tam bir listesi için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Sözleşmesi türleri veri ile birlikte kullanılan, yeni WCF hizmetleri yazmak için önerilen yoldur. Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>XmlSerializer sınıfını kullanma zamanı  
 WCF da destekler <xref:System.Xml.Serialization.XmlSerializer> sınıfı. <xref:System.Xml.Serialization.XmlSerializer> Sınıf WCF'ye benzersiz değil. Aynı seri hale getirme altyapısı olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri kullanın. <xref:System.Xml.Serialization.XmlSerializer> Sınıf türleri çok dar kümesini destekler <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı, ancak daha fazla denetim elde edilen XML üzerinden sağlar ve XML Şeması Tanım Dili (XSD) standart fazlasını destekler. Ayrıca serializable türler üzerinde herhangi bir bildirim temelli özniteliği gerektirmez. XML seri hale getirme konusunda daha fazla bilgi için bkz. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] belgeleri. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı veri anlaşması türleri desteklemez.  
  
 Svcutil.exe kullanırken veya **hizmet Başvurusu Ekle** üçüncü taraf bir hizmet için istemci kodu oluşturma veya üçüncü taraf şema, uygun bir seri hale getirici erişmek için Visual Studio özelliği otomatik olarak seçilir. Şema ile uyumlu değilse <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> seçilir.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>XmlSerializer için el ile geçiş  
 Bazen, el ile geçiş gerekebilir <xref:System.Xml.Serialization.XmlSerializer>. Bu, örneğin, aşağıdaki durumlarda gerçekleşir:  
  
- Bir uygulamadan geçirilirken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmetlerini WCF'ye taşıma, varolan, yeniden kullanmak isteyebilirsiniz <xref:System.Xml.Serialization.XmlSerializer>-yeni veri oluşturmak yerine uyumlu türlerde sözleşme türü.  
  
- İletilerinde görünen XML üzerinde kesin denetim önemlidir, ancak bir Web Hizmetleri Açıklama Dili (WSDL) belgesi kullanılabilir değil. Örneğin, bir belirli standart için uyumlu olan türleri ile bir hizmeti oluştururken, yayımlanan şema olan DataContractSerializer ile uyumlu değildir.  
  
- Eski SOAP kodlamasına standarda uygun Hizmetleri oluştururken.  
  
 Bu ve diğer durumlarda, el ile geçiş yapabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> uygulayarak sınıfı `XmlSerializerFormatAttribute` hizmetinize aşağıdaki kodda gösterildiği gibi öznitelik.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
  
> [!NOTE]
>  Serileştirme altyapıları geçiş yaparken dikkatli olmak önemlidir. Aynı türü için XML kullanılan seri hale getirici bağlı olarak farklı serileştirebiliyorsa. Yanlış seri hale getirici yanlışlıkla kullanırsanız değil ifşa istediniz türünden bilgilerini açığa çıkarmaktan.  
  
 Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı ile işaretlenen üyelerin yalnızca serileştiren <xref:System.Runtime.Serialization.DataMemberAttribute> veri anlaşması türü seri hale getirilirken özniteliği. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı, genel üye serileştirir. Aşağıdaki kodda türüne bakın.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Türü bir servis sözleşmesi yanlışlıkla kullanılıp kullanılmadığını burada <xref:System.Xml.Serialization.XmlSerializer> sınıfı seçili `creditCardNumber` üye serileştirildiği, barındırılmasını olmayabilir.  
  
 Olsa da <xref:System.Runtime.Serialization.DataContractSerializer> (böylece hiçbir zaman gerekli olmamalıdır rağmen) açıkça hizmetiniz için seçebilirsiniz, sınıf, varsayılan uygulayarak <xref:System.ServiceModel.DataContractFormatAttribute> hizmet sözleşme türü için öznitelik.  
  
 Hizmet için kullanılan serileştiriciyi sözleşmenin önemli bir parçasıdır ve farklı bir bağlama seçerek ya da diğer yapılandırma ayarlarını değiştirerek değiştirilemez.  
  
 Diğer önemli güvenlik konuları uygulamak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. İlk olarak, herhangi bir WCF uygulama kullanan önerilir <xref:System.Xml.Serialization.XmlSerializer> ifşaatına karşı korunması bir anahtarla imzalanan sınıfı. Bu önerinin hem el ile bir anahtara geçerli <xref:System.Xml.Serialization.XmlSerializer> gerçekleştirilir ve ne zaman bir otomatik anahtar gerçekleştirilir (Svcutil.exe, hizmet Başvurusu Ekle veya benzer bir araç tarafından). Bunun nedeni, <xref:System.Xml.Serialization.XmlSerializer> serileştirme motoruna yüklenmesini destekler *önceden, serileştirme derlemelerinin oluşturulan* uygulamayla aynı anahtarla imzalanmış sürece. İmzasız bir uygulama, önceden oluşturulan serileştirme bütünleştirilmiş kodunun uygulama klasörü veya genel bütünleştirilmiş kod önbelleğine yerleştirilen beklenen adıyla eşleşen kötü amaçlı bir derleme olasılığını gelen tamamen korumasız kalır. Elbette, bir saldırganın önce bu eylemi denemek için bu iki konumdan birinde yazma erişim elde gerekir.  
  
 Her kullandığınızda var olan başka bir tehdit <xref:System.Xml.Serialization.XmlSerializer> sistem geçici klasörüne yazma erişimi ile ilgilidir. <xref:System.Xml.Serialization.XmlSerializer> Serileştirme motoruna oluşturur ve geçici *serileştirme derlemelerinin* bu klasördeki. Geçici bir klasöre yazma erişimi olan herhangi bir işlem, kötü amaçlı kod ile bu serileştirme derlemeler üzerine olduğunu bilmeniz gerekir.  
  
## <a name="rules-for-xmlserializer-support"></a>XmlSerializer desteği için kurallar  
 Doğrudan uygulanamıyor <xref:System.Xml.Serialization.XmlSerializer>-sözleşme işlemi parametreleri veya dönüş değerleri için uyumlu öznitelikleri. Ancak, yazılı ileti (ileti anlaşması gövde bölümlerini), aşağıdaki kodda gösterildiği gibi uygulanabilirler.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Yazılı ileti üyelerine uygulandığında, bu öznitelikler yazılı ileti özniteliklerinde çakışan geçersiz kılma özellikleri. Örneğin, aşağıdaki kodda, `ElementName` geçersiz kılmalar `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Kullanırken özniteliği desteklenmiyor <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  Bu durumda, <xref:System.Xml.Serialization.XmlSerializer> WCF önce yayımlanan aşağıdaki durum oluşturur: "Şemanın en üst düzeyinde tanımlaman bir öğe olamaz `maxOccurs` > 1. İçin bir sarmalayıcı öğe sağlayın 'daha fazla' kullanarak `XmlArray` veya `XmlArrayItem` yerine `XmlElementAttribute`, ya da Wrapped parametre stili kullanarak. "  
>   
>  Böyle bir özel durum alırsanız, bu durum geçerli olup olmadığını araştırın.  
  
 WCF desteklemiyor <xref:System.Xml.Serialization.SoapIncludeAttribute> ve <xref:System.Xml.Serialization.XmlIncludeAttribute> ileti sözleşmeleri ve işlem özniteliklerinde sözleşmeler; kullanın <xref:System.Runtime.Serialization.KnownTypeAttribute> yerine özniteliği.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>IXmlSerializable arabirimi uygulayan türler  
 Türleri uygulayan `IXmlSerializable` arabirimi tarafından tam olarak desteklenmektedir `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Özniteliği her zaman uygulanması, şema denetlemek için bu tür.  
  
> [!WARNING]
>  Çok biçimli türler seri hale getirme, uygulamalısınız <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> doğru türü seri hale getirilmiş emin olmak için türü.  
  
 Uygulayan türler üç çeşitleri vardır `IXmlSerializable`: bir öğeyi ve eski temsil eden rastgele içerik türlerini temsil eden türleri <xref:System.Data.DataSet> türleri.  
  
- İçerik türlerini kullanan bir şema sağlayıcı yöntemi tarafından belirtilen `XmlSchemaProviderAttribute` özniteliği. Yöntem döndürmez `null` ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik özelliği varsayılan değerinde sol `false`. Bu en yaygın kullanımı, `IXmlSerializable` türleri.  
  
- Öğe türleri kullanılır, bir `IXmlSerializable` denetlemenize kendi kök öğe adı gerekir. Bir tür bir öğe türü olarak işaretlemek için ayarlayın ya da <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özelliği <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliğini `true` veya dönüş `null` şema sağlayıcısı yönteminden. Bir şema sağlayıcısı yöntemine sahip olan öğe türleri için – isteğe bağlı, belirtebilir `null` yöntemi adı yerine `XmlSchemaProviderAttribute`. Ancak, varsa `IsAny` olduğu `true` ve şema sağlayıcı yöntemi belirtildi, yöntem döndürmelidir `null`.  
  
- Eski <xref:System.Data.DataSet> türleridir `IXmlSerializable` ile işaretli olmayan türleri `XmlSchemaProviderAttribute` özniteliği. Bunun yerine, şirketler güvenmektedir <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şeması oluşturma için yöntemi. Bu düzen için kullanılan `DataSet` türü ve kendi türü belirtilmiş veri kümesi türetilen bir sınıfta bir .NET Framework'ün önceki sürümlerinde, ancak artık kullanımdan kalkmıştır ve yalnızca eski nedenlerle desteklenir. Değil Bu modeli temel kullanır ve her zaman geçerli `XmlSchemaProviderAttribute` için `IXmlSerializable` türleri.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable içerik türleri  
 Uygulayan bir tür veri üyesi serileştirilirken `IXmlSerializable` bir içerik türü seri hale getirici veri üyesi için sarmalayıcı öğe Yazar önceden tanımlanmış aynıdır ve geçiş denetimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama sarmalayıcı öğe özniteliklerini ekleme içeren bir XML yazabilirsiniz. Sonra `WriteXml` olan Bitti, seri hale getirici öğe kapatır.  
  
 Uygulayan bir tür veri üyesi işlenirken `IXmlSerializable` ve daha önce tanımlanan bir içerik türü olan, seri durumdan çıkarıcı XML okuyucusu için veri üyesi üzerinde sarmalayıcı öğe yerleştirir ve geçiş denetimi <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemi. Yöntemi, başlangıç ve bitiş etiketleri dahil olmak üzere tüm öğeyi okumalısınız. Emin olun, `ReadXml` kod burada öğesi boş durumu işler. Ayrıca, `ReadXml` uygulama belirli bir şekilde adın geçmesi sarmalayıcı öğe üzerinde değil kullanan. Ad tarafından seçmiş seri hale getirici farklılık gösterebilir.  
  
 Atamak için izin `IXmlSerializable` içerik türleri polymorphically, örneğin, veri türü üyeleri <xref:System.Object>. Ayrıca türü örneklerinin null olmasına izin verilir. Son olarak, kullanmak mümkün mü `IXmlSerializable` türleri içeren ve etkin nesne grafiği korunması <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu özelliklerin tümünü belirli öznitelikleri sarmalayıcı öğe eklemek WCF serileştirici gerektirir ("nil" ve bir WCF özgü ad alanı içinde XML Şeması örneği ad alanı ve "Id", "Başvuru", "Type" ve "Derleme" "type").  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml uygularken yok saymak için öznitelikler  
 Denetime geçirmeden önce `ReadXml` kodu, seri durumdan çıkarıcı XML öğesi inceler, bu özel XML öznitelikleri algılar ve bunlar üzerinde çalışır. Örneğin, "nil" ise `true`, bir null değer seri durumdan ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, farklı bir tür olduğu gibi öğenin içeriğini seri. Polymorphically atanan türün uygulamasını `ReadXml` çağrılır. Herhangi bir durumda, bir `ReadXml` uygulama tarafından seri durumdan çıkarıcının işlenen çünkü bu özel öznitelikleri yoksay.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable içerik türleri için şema konuları  
 Şema dışa aktarırken ve bir `IXmlSerializable` içerik türü, şema sağlayıcısı yöntemi çağrılır. Bir <xref:System.Xml.Schema.XmlSchemaSet> şema sağlayıcısı yöntemine geçirilir. Yöntem herhangi bir geçerli şema şema kümesine ekleyebilirsiniz. Şema kümesi, şema verme ne zaman oluştuğu anda zaten biliniyor şema içeriyor. Şema sağlayıcı yöntemi şema kümesi için bir öğe eklemeniz gerektiğinde belirlemelisiniz olup olmadığını bir <xref:System.Xml.Schema.XmlSchema> uygun ad alanı ile kümede zaten mevcut. Aşması durumunda şema sağlayıcı yöntemi yeni öğenin varolan eklemelisiniz `XmlSchema`. Aksi takdirde, yeni bir oluşturmalısınız `XmlSchema` örneği. Bu önemlidir, dizilerin `IXmlSerializable` türleri kullanılmaktadır. Örneğin, bir `IXmlSerializable` "A", "B", ad alanına yazarken verilen türü onu içeren şema sağlayıcısı yöntemi, önceden şema çağrılır zamanına göre "ArrayOfA" türü tutacak "B" için şema mümkündür.  
  
 Türlere ekleme yanı sıra <xref:System.Xml.Schema.XmlSchemaSet>, içerik türleri için şema sağlayıcı yöntemi null olmayan bir değer döndürmesi gerekir. Geri dönebilirsiniz bir <xref:System.Xml.XmlQualifiedName> için kullanılacak şema türü adını belirten verilen `IXmlSerializable` türü. Bu tam ad aynı zamanda verileri olarak hizmet sözleşme adı ve türü için ad alanı. Hemen şema sağlayıcısı yöntem döndürüldüğünde ayarlayın şemada var olmayan bir tür dönmek için izin verilir. Ancak, bu zaman tüm türleri verilir ilgili beklenir ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi çağrıldığında tüm ilgili türleri için <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği erişilen), şema kümesinde türü yok. Erişim `Schemas` özelliği önce tüm ilgili `Export` çağrıları yapılan neden olabilir bir <xref:System.Xml.Schema.XmlSchemaException>. Dışarı aktarma işlemine ilişkin daha fazla bilgi için bkz. [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Şema sağlayıcı yöntemi ayrıca döndürebilir <xref:System.Xml.Schema.XmlSchemaType> kullanılacak. Türü olabilir veya anonim olmayabilir. Anonim ise şeması `IXmlSerializable` türü her zaman anonim bir tür dışarı `IXmlSerializable` türü, bir veri üyesi kullanılır. `IXmlSerializable` Türü bir veri anlaşması adına ve ad alanı yine de sahiptir. (Bu bölümünde anlatıldığı gibi belirlenir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md) dışında <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik adı özelleştirmek için kullanılamaz.) Anonim değilse içinde türlerden biri olmalıdır `XmlSchemaSet`. Bu durumda, döndürmekle eşdeğerdir `XmlQualifiedName` türü.  
  
 Ayrıca, genel bir öğe bildirimi türü için dışarı aktarılır. Türü yoksa <xref:System.Xml.Serialization.XmlRootAttribute> öğe uygulanmış özniteliğine sahip aynı ada ve bir veri anlaşması ad alanına ve onun "nillable" özelliği `true`. Bunun tek istisnası Şema ad alanı (`http://www.w3.org/2001/XMLSchema`) – türün veri anlaşması bu ad alanında ise, şema ad alanına yeni öğeler eklemek için Yasak olduğundan karşılık gelen genel öğe boş ad alanı içinde olur. Türündeyse `XmlRootAttribute` , genel bir öğe bildirimi özniteliğinin şunları kullanarak aktarılır: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> özellikleri. Varsayılan değerlerle `XmlRootAttribute` uygulanmış olan veri anlaşması adına, bir boş ad alanı ve "nillable" olan `true`.  
  
 Aynı genel öğesi bildirim kuralları, eski veri kümesi türleri için geçerlidir. Unutmayın `XmlRootAttribute` ya da eklenen özel kod aracılığıyla eklenen genel öğesi bildirimleri geçersiz kılınamaz `XmlSchemaSet` şema sağlayıcı yöntemi kullanarak aracılığıyla veya `GetSchema` eski veri kümesi türleri için.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable` öğe türleri ya da sahip `IsAny` özelliğini `true` veya dönüş şema sağlayıcısı yöntemi `null`.  
  
 Serileştirme ve seri kaldırma öğe türü seri hale getirme ve bir içerik türü seri durumdan çıkarmak için çok benzer. Ancak, bazı önemli farklar vardır:  
  
- `WriteXml` Uygulama (kuşkusuz birden çok alt öğe içerebilir) tam olarak bir öğenin yazma beklenir. Bu öznitelikler birden çok kardeş öğeler veya karma içerik bu tek öğede dışında yazılmıyor. Öğe boş olabilir.  
  
- `ReadXml` Uygulama sarmalayıcı öğe değil okumalıdır. Bir öğe okumak için beklenen, `WriteXml` üretir.  
  
- Bir öğe türü düzenli olarak (örneğin, bir veri üyesi olarak bir veri anlaşması) serileştirilirken bir sarmalayıcı öğe çağırmadan önce seri hale getirici çıkarır `WriteXml`, içerik türleri gibi. Ancak, bir öğe türü en üst düzeyde serileştirilirken seri hale getirici normalde hiç öğe çevresinde bir sarmalayıcı öğe çıktı vermez, `WriteXml` kök adı veya ad alanı serileştiricide oluştururken açıkça belirtilmediği sürece, yazar `DataContractSerializer` veya `NetDataContractSerializer` oluşturucular. Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
- En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> aslında hiçbir şey yapma ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrıları `WriteXml`. Bu modda, serileştirilmekte olan nesne olamaz `null` ve polymorphically atanamaz. Ayrıca, Nesne grafiği koruma etkinleştirilemiyor ve `NetDataContractSerializer` kullanılamaz.  
  
- Kök ad ve ad alanı oluşturma zamanında belirtmeden en üst düzeydeki bir öğe türü seri durumdan çıkarılırken zaman <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> döndürür `true` varsa herhangi bir öğenin başlangıç bulabilirsiniz. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> ile `verifyObjectName` parametresini `true` aynı şekilde davranır `IsStartObject` gerçekten nesnesi okuma önce. `ReadObject` Daha sonra denetime geçirir `ReadXml` yöntemi.  
  
 Verilen öğe türleri için şema aynı olan `XmlElement` türü bir önceki bölümde açıklandığı gibi şema sağlayıcı yöntemi herhangi bir ek şema ekleyebilirsiniz dışında <xref:System.Xml.Schema.XmlSchemaSet> içerik türleri gibi. Kullanarak `XmlRootAttribute` öğe türleri ile özniteliği izin verilmez ve genel öğesi bildirimleri hiçbir zaman bu tür için gösterilir.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer arasındaki farklar  
 `IXmlSerializable` Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri ayrıca tarafından anlaşılan <xref:System.Xml.Serialization.XmlSerializer> . Ancak, bu veri sözleşme modeli nasıl ele alındığı bazı farklar vardır. Önemli farklar aşağıda özetlenmiştir:  
  
- Şema sağlayıcı yöntemi kullanılacak genel `XmlSerializer`, ancak veri sözleşme modelinde kullanılmak üzere ortak olması gerekmez.  
  
- Şema sağlayıcı yöntemi aldığında çağrılan `IsAny` olduğu `true` veri sözleşme modelinde ancak değil `XmlSerializer`.  
  
- Zaman `XmlRootAttribute` özniteliği için içerik veya eski bir veri kümesi türleri yoksa `XmlSerializer` boş ad alanı bir genel öğesi bildiriminde dışarı aktarır. Veri sözleşmesi modelinde kullanılan ad normalde daha önce açıklandığı gibi veri anlaşması ad alanıdır.  
  
 Her iki serileştirme teknoloji ile kullanılan türler oluştururken bu farklılıklara dikkat edin.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable Şemayı içeri aktarma  
 Oluşturulan şema içeri aktarılırken `IXmlSerializable` türleri, birkaç olasılık vardır:  
  
- Oluşturulan şema açıklandığı gibi geçerli bir veri sözleşmesi şema olabilir [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu durumda, şema zamanki içeri aktarılabilir ve normal bir veri anlaşması türleri oluşturulur.  
  
- Oluşturulan şema geçerli veri sözleşmesi şema olmayabilir. Örneğin, şema sağlayıcısı yönteminizi veri sözleşme modelinde Desteklenmeyen XML öznitelikleri içeren şema oluşturabilir. Bu durumda, şema olarak içeri aktarabilirsiniz `IXmlSerializable` türleri. Bu içeri aktarma modu varsayılan olarak açık değildir ancak kolayca – örneğin ile etkinleştirilebilir `/importXmlTypes` için komut satırı anahtarı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu ayrıntılı olarak açıklanan [sınıfları oluşturmak için şema alma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Tür örnekleriniz için doğrudan XML ile iş unutmayın. Farklı bir kullanmayı da düşünebilirsiniz geniş bir şema – destekleyen serileştirme teknolojiyi kullanarak konusuna bakın `XmlSerializer`.  
  
- Mevcut yeniden kullanmak isteyebileceğiniz `IXmlSerializable` yenilerini oluşturmak yerine proxy türleri. Bu durumda, içeri aktarma şema oluşturma türleri konusuna açıklanan başvurulan türleri özellik yeniden türünü belirtmek için kullanılabilir. Bunu kullanarak karşılık gelen `/reference` yeniden kullanmak için türler içeren derlemeyi belirtir svcutil.exe üzerinde geçin.  
  
### <a name="xmlserializer-legacy-behavior"></a>XmlSerializer eski davranışı  
 .NET Framework 4.0 ve daha önce bir dosyaya C# kod yazarak XmlSerializer geçici serileştirme derlemelerinin oluşturulur. Dosyayı bir derlemeye ardından derlendi.  Bu davranış, başlangıç zamanı için seri hale getirici yavaşlatmasını gibi istenmeyen bazı sonuçları vardı. .NET Framework 4. 5 ', derleyicinin kullanılmasına gerek kalmadan derlemeleri oluşturmak için bu davranışı değiştirildi. Bazı geliştiriciler, oluşturulan C# kodunu görmek isteyebilirsiniz. Bu eski davranışı aşağıdaki yapılandırma tarafından kullanılacak belirtebilirsiniz:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />  
  </system.xml.serialization>  
  <system.diagnostics>  
    <switches>  
      <add name="XmlSerialization.Compilation" value="1" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
 Uyumluluk sorunlarını gibi çalıştırırsanız `XmlSerializer` genel olmayan yeni geçersiz kılma ile türetilmiş bir sınıf seri hale getirmek başarısız olan, geri geçiş yapabilirsiniz `XMLSerializer` aşağıdaki yapılandırmayı kullanarak eski davranışı:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Yukarıdaki yapılandırma alternatif, .NET Framework 4.5 veya sonraki sürümünü çalıştıran bir makinede aşağıdaki yapılandırma kullanabilirsiniz:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Anahtarı yalnızca .NET Framework 4.5 veya sonraki sürümünü çalıştıran bir makinede çalışır. Yukarıdaki `appSettings` yaklaşım tüm .NET Framework sürümlerinde çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Nasıl yapılır: Başlangıç zamanı, WCF istemci XmlSerializer kullanarak uygulamaları geliştirin](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
