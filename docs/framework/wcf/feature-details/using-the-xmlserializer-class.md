---
title: XmlSerializer Sınıfını Kullanma
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
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c541c44f0043000ccd4e7edb0d38eba2c66d0844
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="using-the-xmlserializer-class"></a>XmlSerializer Sınıfını Kullanma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iki farklı serileştirme teknolojileri, istemciler ve hizmetler, serileştirme adlı bir işlem arasında iletilir XML uygulamanıza içinde veri kapatmak için kullanabilirsiniz.  
  
## <a name="datacontractserializer-as-the-default"></a>Varsayılan olarak DataContractSerializer  
 Varsayılan olarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan <xref:System.Runtime.Serialization.DataContractSerializer> veri türleri serileştirmek için sınıfı. Bu serileştiricinin aşağıdaki türlerini destekler:  
  
-   Temel (örneğin, tamsayı, dizeleri ve bayt dizileri için) gibi bazı özel türleri yanı sıra türler <xref:System.Xml.XmlElement> ve <xref:System.DateTime>, hangi temel olarak kabul edilir.  
  
-   Veri sözleşmesi türleri (türleri ile işaretlenen <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği).  
  
-   Türleri ile işaretlenen <xref:System.SerializableAttribute> dahil öznitelik türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi.  
  
-   Birçok genel koleksiyon türleri dahil birçok genel koleksiyon türleri.  
  
 Birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ikinci iki kategoriye ayrılır ve böylece seri hale getirilebilir. Seri hale getirilebilir türlerin dizileri de seri hale getirilebilir. Tam bir listesi için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Anlaşma türleri verileri ile birlikte kullanılan, yeni yazmak için önerilen yöntem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>XmlSerializer sınıfını kullanma zamanı  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ayrıca destekler <xref:System.Xml.Serialization.XmlSerializer> sınıfı. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı için benzersiz değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Aynı seri hale getirme altyapısı olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri kullanın. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı bir kadar dar kümesini destekler türlerinden daha <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı, ancak sonuç XML üzerinde daha fazla denetim olanağı sağlar ve XML Şeması Tanım Dili (XSD) standart çok daha fazla destekler. Seri hale getirilebilir türler bildirim temelli öznitelikleri de gerektirmez. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] XML serileştirme konusunda [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] belgeleri. <xref:System.Xml.Serialization.XmlSerializer> Sınıf veri sözleşme türleri desteklemez.  
  
 Svcutil.exe kullanırken veya **hizmet Başvurusu Ekle** özelliği bir üçüncü taraf hizmeti için istemci kodu oluşturmak veya bir üçüncü taraf şeması, uygun bir seri hale getirici erişmek için Visual Studio otomatik olarak seçilir sizin için. Şema ile uyumlu değilse, <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> seçilir.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>XmlSerializer el ile geçiş  
 Bazen, el ile geçmek zorunda kalabilirsiniz <xref:System.Xml.Serialization.XmlSerializer>. Bu, örneğin, aşağıdaki durumlarda gerçekleşir:  
  
-   Bir uygulamadan geçirirken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], varolan, yeniden isteyebilirsiniz <xref:System.Xml.Serialization.XmlSerializer>-yeni veri oluşturmak yerine uyumlu türleri sözleşme türleri.  
  
-   Kesin bir denetim iletileri görünür XML üzerinden önemlidir, ancak bir Web Hizmetleri Açıklama Dili (WSDL) belgesi kullanılabilir değil, örneğin, bir hizmet bir belirli yöntem için uyması gereken türleriyle oluşturulurken yayımlanan şema tutulduğunda DataContractSerializer ile uyumlu değildir.  
  
-   Eski SOAP kodlama standarda Hizmetleri oluştururken.  
  
 Bu ve diğer durumlarda, el ile geçiş <xref:System.Xml.Serialization.XmlSerializer> uygulayarak sınıfı `XmlSerializerFormatAttribute` aşağıdaki kodda gösterildiği gibi hizmetinize özniteliği.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
  
> [!NOTE]
>  Seri hale getirme altyapısı geçiş yaparken dikkatli olmak önemlidir. Aynı türde XML farklı kullanılan seri hale getirici bağlı olarak seri hale getirebilir. Yanlış seri hale getirici yanlışlıkla kullanırsanız, bilgi değil ifşa istiyordunuz türünden açıklamadan.  
  
 Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı ile işaretlenen üyelerin yalnızca serileştiren <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşme türleri serileştirilirken özniteliği. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı ortak üye serileştirir. Aşağıdaki kodda türü bakın.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Türü bir hizmet sözleşmesini yanlışlıkla kullanılıyorsa, burada <xref:System.Xml.Serialization.XmlSerializer> sınıfı seçildiğinde, `creditCardNumber` üyesi serileştirildiği, büyük olasılıkla yöneliktir.  
  
 Olsa bile <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı varsayılan, (bunu hiçbir zaman gerekip gerekmeyeceğini rağmen) açıkça, hizmetiniz için seçebileceğiniz uygulayarak <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği için hizmet sözleşmesi türü.  
  
 Hizmeti için kullanılan seri hale getirici sözleşme ayrılmaz bir parçasıdır ve diğer yapılandırma ayarlarını değiştirerek veya başka bir bağlama seçerek değiştirilemez.  
  
 Diğer önemli güvenlik konuları uygulamak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. İlk olarak, herhangi bir önerilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan uygulama <xref:System.Xml.Serialization.XmlSerializer> sınıfı ifşaatına karşı korunması bir anahtarı ile imzalanmış. Bu öneri hem el ile bir anahtara geçerlidir <xref:System.Xml.Serialization.XmlSerializer> gerçekleştirilir ve ne zaman otomatik anahtar gerçekleştirildiğini (Svcutil.exe, hizmet Başvurusu Ekle veya benzer bir aracı tarafından). Bunun nedeni, <xref:System.Xml.Serialization.XmlSerializer> serileştirme motoruna yüklenmesini destekler *serileştirme derlemelerini'önceden oluşturulan* uygulamayla aynı anahtar ile imzalanmış sürece. İmzasız uygulamanın uygulama klasörü veya genel derleme önbelleği yerleştirilen önceden oluşturulmuş serileştirme derlemenin beklenen adıyla eşleşen bir kötü amaçlı derleme olasılığını gelen tamamen korumasız kalır. Elbette, bir saldırganın ilk yazma Bu eylem denemek için bu iki konumlardan birine erişim gerekir.  
  
 Kullandığınız zaman, mevcut başka bir tehdit <xref:System.Xml.Serialization.XmlSerializer> sistem geçici klasöre yazma erişimi ile ilgilidir. <xref:System.Xml.Serialization.XmlSerializer> Serileştirme motoruna oluşturur ve geçici kullanır *serileştirme derlemelerini* bu klasörde. Geçici klasöre yazma erişimi olan herhangi bir işlem, kötü amaçlı kod kullanarak bu serileştirme derlemelerini üzerine olduğunu bilmeniz gerekir.  
  
## <a name="rules-for-xmlserializer-support"></a>XmlSerializer desteği için kurallar  
 Doğrudan uygulanamıyor <xref:System.Xml.Serialization.XmlSerializer>-sözleşme işlemi parametreleri veya dönüş değerleri için uyumlu öznitelikleri. Ancak, bunlar yazılan iletileri (ileti sözleşmesi gövde bölümlerinin), aşağıdaki kodda gösterildiği gibi uygulanabilir.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Yazılı ileti üyelerine uygulandığında, bu öznitelikler yazılı ileti özniteliklerinde çakışan özellikler geçersiz kılar. Örneğin, aşağıdaki kodda, `ElementName` geçersiz kılmaları `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Kullanırken özniteliği desteklenmiyor <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  Bu durumda, <xref:System.Xml.Serialization.XmlSerializer> öncesinde yayımlanan bir aşağıdaki durum oluşturduğunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "bir şema en üst düzeyde bildirilen bir öğe olamaz `maxOccurs` > 1. İçin bir kapsayıcı öğe sağlamak 'daha fazla' kullanarak `XmlArray` veya `XmlArrayItem` yerine `XmlElementAttribute`, paketlenmiş parametre stilini kullanarak veya. "  
>   
>  Bu tür bir özel durum almaya devam ederseniz, bu durum geçerli olup olmadığını araştırın.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desteklemediği <xref:System.Xml.Serialization.SoapIncludeAttribute> ve <xref:System.Xml.Serialization.XmlIncludeAttribute> ileti sözleşmeleri ve işlem özniteliklere sözleşmeler; kullanın <xref:System.Runtime.Serialization.KnownTypeAttribute> yerine özniteliği.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>IXmlSerializable arabirimini uygulama türleri  
 Türleri uygulayan `IXmlSerializable` arabirimi tarafından tam olarak desteklenmektedir `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Özniteliği her zaman uygulanamaz kendi şema denetlemek için bu tür.  
  
> [!WARNING]
>  Çok biçimli türleri seri hale getirme, uygulamalısınız <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> doğru türü seri hale getirilmiş emin olmak için türü.  
  
 Uygulama türleri üç çeşitleri vardır `IXmlSerializable`: tek bir öğe ve eski temsil eden rasgele içerik, türleri temsil eden türlerin <xref:System.Data.DataSet> türleri.  
  
-   İçerik türleri tarafından belirtilen bir şema sağlayıcısı yöntemi kullanır `XmlSchemaProviderAttribute` özniteliği. Yöntem döndürmez `null` ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik özelliği varsayılan değerinde sol `false`. En yaygın kullanımı budur `IXmlSerializable` türleri.  
  
-   Öğe türleri kullanılır olduğunda bir `IXmlSerializable` denetlemenize kendi kök öğe adı gerekir. Bir tür bir öğe türü olarak işaretlemek için ya da ayarlamak <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özelliği <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliğini `true` veya return `null` şema sağlayıcısı yönteminden. Bir şema sağlayıcı yöntemi sahip öğe türleri için – isteğe bağlı, belirtebilir `null` yöntemi adı yerine `XmlSchemaProviderAttribute`. Ancak, varsa `IsAny` olan `true` ve şema sağlayıcı yöntemi belirtilirse, yöntem döndürmelidir `null`.  
  
-   Eski <xref:System.Data.DataSet> türleri `IXmlSerializable` ile işaretli olmayan türleri `XmlSchemaProviderAttribute` özniteliği. Bunun yerine, güvenirler <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şema oluşturma için yöntem. Bu model için kullanılan `DataSet` türü ve onun türü belirtilmiş veri kümesi türeyen bir sınıf .NET Framework'ün önceki sürümlerindeki ancak artık kullanımdan kalkmıştır ve yalnızca eski nedenlerle desteklenir. Değil Bu deseni temel kullanır ve her zaman geçerli `XmlSchemaProviderAttribute` için `IXmlSerializable` türleri.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable içerik türleri  
 Veri üyesi uygulayan bir tür serileştirilirken `IXmlSerializable` bir içerik türü seri hale getirici veri üyesi için sarmalayıcı öğesi Yazar daha önce tanımlanan aynıdır ve geçişleri denetlemek için <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama sarmalayıcı öğesine öznitelikleri eklemeyi içerir, XML yazabilirsiniz. Sonra `WriteXml` olan Bitti, seri hale getirici öğesi kapatır.  
  
 Veri üyesi uygulayan bir tür çıkarılırken `IXmlSerializable` ve önceden tanımlanan bir içerik türü olan, seri durumdan çıkarıcının XML okuyucusu sarmalayıcı öğede veri üyesi için yerleştirir ve geçişleri denetlemek için <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemi. Yöntemi başlangıç ve bitiş etiketleri de dahil olmak üzere tüm öğeyi okumalısınız. Emin olun, `ReadXml` kodu nereye öğe boş durumu işler. Ayrıca, `ReadXml` uygulama belirli bir şekilde adın geçmesi sarmalayıcı öğede değil kullanan. Adı tarafından seçilen seri hale getirici değişebilir.  
  
 Atamak için izin `IXmlSerializable` içerik türleri polymorphically, örneğin, veri türü üyeleri <xref:System.Object>. Ayrıca türü örnekleri boş olmasına izin verilir. Son olarak, kullanmak mümkün `IXmlSerializable` türleri ile etkin nesne grafiği koruma ile <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu özelliklerin tümü gerektiren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sarmalayıcı öğesine belirli öznitelikler eklemek için seri hale getirici ("nil" ve XML şema örneği ad ve "Id", "Ref", "Tür" ve "Derlemesindeki" "type" bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirli bir ad alanı).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml uygularken yoksaymak için öznitelikler  
 Denetime geçirmeden önce `ReadXml` kodu, seri durumdan çıkarıcının XML öğesi inceler, bu özel XML öznitelikleri algılar ve bunlar üzerinde çalışır. Örneğin, "nil" ise `true`, bir null değer serisi ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, öğenin içeriğini farklı bir tür boşmuş gibi serisi. Polymorphically atanan tür uyarlamasını `ReadXml` olarak adlandırılır. Herhangi bir durumda, bir `ReadXml` uygulaması tarafından seri durumdan çıkarıcının işlenir çünkü bu özel öznitelikler yoksay.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable içerik türleri için şema konuları  
 Şema verirken ve bir `IXmlSerializable` içerik türü, şema sağlayıcısı yöntemi çağrılır. Bir <xref:System.Xml.Schema.XmlSchemaSet> şema sağlayıcısı yönteme geçirilen. Yöntemin geçerli bir şema şema kümesine ekleyebilirsiniz. Şema kümesini şema verme oluştuğunda zamanında zaten biliniyor bir şema içeriyor. Şema sağlayıcı yöntemi şema kümesine bir öğe eklemelisiniz olduğunda belirlemeniz gerekir olup bir <xref:System.Xml.Schema.XmlSchema> uygun ad alanı zaten kümesinde var. Destekliyorsa, şema sağlayıcı yöntemi yeni öğe varolan eklemelisiniz `XmlSchema`. Aksi takdirde, yeni bir oluşturmalısınız `XmlSchema` örneği. Bu önemlidir, dizilerin `IXmlSerializable` türleri kullanılmaktadır. Örneğin, bir `IXmlSerializable` ad "B", "A" türü olarak dışarı türü içeren şema sağlayıcısı yöntemi, önceden ayarlanmış şema çağrılır zamana göre "ArrayOfA" türü tutmak "B" için şemayı mümkün değil.  
  
 Türlere ekleme yanı sıra <xref:System.Xml.Schema.XmlSchemaSet>, içerik türleri için şema sağlayıcı yöntemi null olmayan bir değer döndürmesi gerekir. Geri dönebilirsiniz bir <xref:System.Xml.XmlQualifiedName> için kullanılacak şema türü adını belirtir verilen `IXmlSerializable` türü. Bu tam adı da verileri olarak hizmet sözleşme adı ve türü için ad alanı. Var olmayan bir tür hemen şema sağlayıcı yöntem döndüğünde kümesi şemasında dönüş izin verilir. Ancak, bunu zamanına göre tüm türleri verilir ilgili beklenen ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi, üzerinde tüm ilgili türleri için çağrılır <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği erişilir), şema kümesinde türü mevcut. Erişme `Schemas` tüm önce özelliği ilgili `Export` çağrıları yapılan sonuçlanabilir bir <xref:System.Xml.Schema.XmlSchemaException>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] dışa aktarma işlemi bkz [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Şema sağlayıcı yöntem de döndürebilir <xref:System.Xml.Schema.XmlSchemaType> kullanmak için. Türü olabilir veya anonim olmayabilir. Anonim, ise için şemayı `IXmlSerializable` türü her zaman anonim bir tür olarak dışarı `IXmlSerializable` türü, bir veri üyesi olarak kullanılır. `IXmlSerializable` Türü hala sahip bir veri sözleşmesi adı ve ad alanı. (Bu açıklandığı gibi belirlenir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md) dışında <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği, adını özelleştirmek için kullanılamaz.) Anonim değilse, türlerden biri olmalıdır `XmlSchemaSet`. Bu durumda döndürmek için eşdeğer `XmlQualifiedName` türü.  
  
 Ayrıca, bir genel öğesi bildirimi türü için verilir. Tür yoksa <xref:System.Xml.Serialization.XmlRootAttribute> , öğe özniteliğinin aynı ad ve veri sözleşmesi ad alanına ve "bırakılabilir" özelliği `true`. Bunun tek istisnası Şema ad alanıdır ("http://www.w3.org/2001/XMLSchema") – tür veri sözleşmesi bu ad alanında Şema ad alanına yeni öğeler eklemek için Yasak olduğundan karşılık gelen bir genel öğesi boş ad alanında ise,. Türündeyse `XmlRootAttribute` , genel bir öğe bildirimi özniteliğinin, aşağıdakileri kullanarak aktarılır: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> özellikleri. Varsayılan değerlerle `XmlRootAttribute` veri sözleşme adına, boş bir ad ve "bırakılabilir" olan uygulanmış olan `true`.  
  
 Aynı genel öğesi bildirim kuralları eski veri kümesi türleri için geçerlidir. Unutmayın `XmlRootAttribute` ya da eklenen özel kod aracılığıyla eklenen genel öğesi bildirimleri geçersiz kılamaz `XmlSchemaSet` şema sağlayıcı yöntemi kullanarak aracılığıyla veya `GetSchema` eski veri kümesi türleri için.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable` öğe türleri ya da sahip `IsAny` özelliğini `true` veya dönüş kendi şema sağlayıcı yöntemi `null`.  
  
 Seri hale getirme ve bir öğe türü seri durumdan seri hale getirme ve bir içerik türü seri durumdan çıkarmak için çok benzer. Ancak, önemli bazı farklar vardır:  
  
-   `WriteXml` Uygulaması (elbette birden çok alt öğelerini içerebilir) tam olarak bir öğe yazma beklenir. Birden çok kardeş öğeler veya karışık içerik bu tek öğe dışında öznitelikleri yazmayı değil. Öğe boş olabilir.  
  
-   `ReadXml` Uygulama sarmalayıcı öğesi değil kimler. Bir öğeyi okumak için beklenen, `WriteXml` üretir.  
  
-   Düzenli olarak bir öğe türü (örneğin, bir veri üyesi olarak bir veri sözleşmesi) serileştirilirken bir kapsayıcı öğe çağırmadan önce seri hale getirici çıkarır `WriteXml`, içerik türleri gibi. Ancak, en üst düzeyinde bir öğe türü seri hale getirme, seri hale getirici normalde hiç öğe çevresinde bir sarmalayıcı öğesi çıktı vermez, `WriteXml` bir kök ve ad alanına getiricisi oluştururken açıkça belirtilmediği sürece, yazar `DataContractSerializer` veya `NetDataContractSerializer` oluşturucular. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> temelde hiçbir şey yapma ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrıları `WriteXml`. Bu modda, serileştirilen nesnenin olamaz `null` ve polymorphically atanamaz. Ayrıca, Nesne grafiği korunması olamaz etkin ve `NetDataContractSerializer` kullanılamaz.  
  
-   En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden çıkarılırken <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> döndürür `true` herhangi bir öğenin başlangıç bulursanız. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> ile `verifyObjectName` parametre kümesine `true` aynı şekilde davranır `IsStartObject` gerçekten nesnesi okuma önce. `ReadObject` Ardından, denetimine geçirir `ReadXml` yöntemi.  
  
 Öğe türleri için verilen şema olarak aynıdır `XmlElement` türü bir önceki bölümde açıklandığı gibi şema sağlayıcı yöntemi herhangi bir ek şema ekleyebilirsiniz dışında <xref:System.Xml.Schema.XmlSchemaSet> gibi içerik türleri. Kullanarak `XmlRootAttribute` öğe türleri özniteliğiyle izin verilmez ve genel öğesi bildirimleri hiçbir zaman bu türleri için gösterilen.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer arasındaki farklar  
 `IXmlSerializable` Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri ayrıca tarafından anlaşılan <xref:System.Xml.Serialization.XmlSerializer> . Ancak, bu veri sözleşmesi modelinde nasıl işlenir bazı farklar vardır. Aşağıdaki listede önemli farklılıklar özetlenmiştir:  
  
-   Şema sağlayıcı yöntemi kullanılmak üzere ortak `XmlSerializer`, ancak veri sözleşmesi modelinde kullanılmak üzere ortak olması gerekmez.  
  
-   Şema sağlayıcı yöntemi aldığında çağrılan `IsAny` olan `true` veri sözleşmesi modelindeki ancak değil `XmlSerializer`.  
  
-   Zaman `XmlRootAttribute` özniteliği içeriği veya eski veri kümesi türleri için mevcut değil `XmlSerializer` boş ad alanı bir genel öğesi bildiriminde dışa aktarır. Veri sözleşmesi modeli kullanılan ad normal olarak daha önce açıklandığı gibi veri sözleşmesi ad alanıdır.  
  
 Her iki serileştirme teknolojileriyle kullanılan türleri oluştururken bu farklılıkları unutmayın.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable şemayı içe aktarma  
 Üretilen bir şema alırken `IXmlSerializable` türleri, birkaç olasılık vardır:  
  
-   Oluşturulan şema açıklandığı gibi geçerli bir veri sözleşmesi şema olabilir [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu durumda, şema her zamanki gibi alınabilir ve normal veri sözleşme türleri üretilir.  
  
-   Oluşturulan şema geçerli bir veri sözleşmesi şema olmayabilir. Örneğin, şema sağlayıcısı yönteminizi veri sözleşmesi modelde Desteklenmeyen XML öznitelikleri içerir şema oluşturabilir. Bu durumda, şema olarak içeri aktarabilirsiniz `IXmlSerializable` türleri. Bu içeri aktarma mod varsayılan olarak açık değildir ancak kolayca – örneğin ile etkinleştirilebilir `/importXmlTypes` komut satırı anahtarını [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu ayrıntılı olarak açıklanmıştır [oluşturmak sınıfları içeri aktarma şemaya](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Türü örnekleri için doğrudan XML ile çalışmalıdır unutmayın. Farklı bir kullanarak düşünebilirsiniz geniş bir şema – destekleyen serileştirme teknolojisini kullanarak konusuna bakın `XmlSerializer`.  
  
-   Var olan yeniden isteyebilirsiniz `IXmlSerializable` yenilerini oluşturmak yerine proxy türlerinde. Bu durumda, türleri oluşturmak konu alma şemaya açıklanan başvurulan tür özelliği yeniden türünü belirtmek için kullanılabilir. Bu kullanarak karşılık gelen `/reference` yeniden türleri içeren bütünleştirilmiş kodun belirten svcutil.exe üzerinde geçin.  
  
### <a name="xmlserializer-legacy-behavior"></a>XmlSerializer eski davranışı  
 .NET Framework 4.0 ve önceki sürümlerinde, XmlSerializer geçici serileştirme derlemelerini C# kod bir dosyaya yazma tarafından oluşturulur. Dosyayı daha sonra bir derlemeye derlendi.  Bu davranış için seri hale getirici başlangıç zamanını yavaşlamasının gibi bazı istenmeyen sonuçlara vardı. .NET Framework 4.5 içinde derleyici kullanılmasına gerek kalmadan derlemeler oluşturmak için bu davranış değiştirildi. Bazı geliştiriciler, oluşturulan C# kodu görmek isteyebilirsiniz. Bu eski davranış aşağıdaki yapılandırma tarafından kullanılacak belirtebilirsiniz:  
  
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
  
 Uyumluluk sorunları gibi çalıştırırsanız `XmlSerializer` türetilmiş bir sınıf genel olmayan yeni geçersiz kılma ile seri hale getirmek başarısız olan, size geri dönebilirsiniz `XMLSerializer` aşağıdaki yapılandırmayı kullanarak eski davranışı:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Yukarıdaki yapılandırma alternatif olarak, .NET Framework 4.5 veya sonraki bir sürümünü çalıştıran bir makineye aşağıdaki yapılandırmayı kullanabilirsiniz:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Anahtar yalnızca .NET Framework 4.5 veya sonraki bir sürümünü çalıştıran bir makineye çalışır. Yukarıdaki `appSettings` yaklaşım tüm .NET Framework sürümleri üzerinde çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.DataContractFormatAttribute>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute>  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
