---
title: Meta Veri Mimarisi Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: a6bd41fa5aed4c2a22ee7c72087e2da0d7e4ea17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598859"
---
# <a name="metadata-architecture-overview"></a>Meta Veri Mimarisi Genel Bakış
Windows Communication Foundation (WCF), hizmet meta verilerini dışarı aktarmak, yayımlamak, almak ve içeri aktarmak için zengin bir altyapı sağlar. WCF Hizmetleri, Svcutil. exe gibi araçların hizmete erişmek için otomatik olarak istemci kodu oluşturabileceği şekilde hizmetin uç noktalarıyla nasıl etkileşim kuracağınızı betimleyen meta verileri kullanır.  
  
 WCF meta veri altyapısını oluşturan türlerin çoğu <xref:System.ServiceModel.Description> ad alanında bulunur.  
  
 WCF, <xref:System.ServiceModel.Description.ServiceEndpoint> bir hizmette uç noktaları anlatmak için sınıfını kullanır. Hizmet uç noktaları için meta veriler oluşturmak üzere WCF veya örnek oluşturmak için hizmet meta verilerini içeri aktarma kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> .  
  
 WCF, türün bir örneği olarak bir hizmet için meta verileri temsil eder <xref:System.ServiceModel.Description.MetadataSet> . bu yapının, WS-MetadataExchange ' de tanımlanan meta veri serileştirme biçimine kesin bir şekilde bağlanmış olması. <xref:System.ServiceModel.Description.MetadataSet>Tür, örnek koleksiyonu olarak Web Hizmetleri Açıklama Dili (wsdl) belgeleri, XML şema belgeleri veya WS-Policy ifadeleri gibi gerçek hizmet meta verilerini paketledir <xref:System.ServiceModel.Description.MetadataSection> . Her <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> örnek, belirli bir meta veri diyalekti ve bir tanımlayıcı içerir. , <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> Özelliğinde aşağıdaki öğeleri içerebilir <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> :  
  
- Ham meta veriler.  
  
- Bir <xref:System.ServiceModel.Description.MetadataReference> örnek.  
  
- Bir <xref:System.ServiceModel.Description.MetadataLocation> örnek.  
  
 Bir <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> örnek, başka bir meta veri değişimi (MEX) uç noktasına ve örneklerine işaret eden BIR <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> http url 'si kullanarak meta veri belgesine işaret. WCF hizmet uç noktalarını, hizmet sözleşmelerini, bağlamaları, ileti değişim düzenlerini, iletileri ve bir hizmet tarafından uygulanan hata iletilerini anlatmak için WSDL belgelerinin kullanılmasını destekler. Hizmet tarafından kullanılan veri türleri, WSDL belgelerinde XML şeması kullanılarak açıklanmıştır. Daha fazla bilgi için bkz. [şema içeri ve dışarı aktarma](schema-import-and-export.md). Hizmet davranışı, sözleşme davranışları ve bir hizmetin işlevselliğini genişleten bağlama öğeleri için WSDL uzantılarını dışa ve içe aktarmak üzere WCF 'yi kullanabilirsiniz. Daha fazla bilgi için bkz. [WCF uzantısı Için özel meta verileri dışarı aktarma](../extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Hizmet meta verileri dışarı aktarılıyor  
 WCF 'de, *meta veri dışa aktarma* , hizmet uç noktalarını açıklama ve bunları istemcilerin hizmeti nasıl kullanacağınızı anlamak için kullanabileceği bir paralel ve standartlaştırılmış bir gösterimde yansıtma işlemidir. Örneklerden meta verileri dışarı aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint> soyut sınıfın bir uygulamasını kullanın <xref:System.ServiceModel.Description.MetadataExporter> . Bir <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulama, bir örnekte kapsüllenmiş meta veriler oluşturur <xref:System.ServiceModel.Description.MetadataSet> .  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Sınıfı, bir uç nokta bağlamasının özelliklerini ve gereksinimlerini ve ilişkili işlemlerini, iletilerini ve hatalarını tanımlayan ilke ifadeleri oluşturmak için bir çerçeve sağlar. Bu ilke ifadeleri bir örnek içinde yakalanır <xref:System.ServiceModel.Description.PolicyConversionContext> . <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType>Daha sonra bir uygulama, oluşturduğu meta verilere bu ilke ifadelerini ekleyebilir.  
  
 Uygulamasına, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IPolicyExportExtension> <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.PolicyConversionContext> uygulamasının kullanması için bir nesne oluştururken arabirimini uygulayan her birine yapılan çağrılar <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> . Yeni ilke onaylamalarını, <xref:System.ServiceModel.Description.IPolicyExportExtension> türün özel uygulamalarında arabirimini uygulayarak dışarı aktarabilirsiniz <xref:System.ServiceModel.Channels.BindingElement> .  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Tür, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> WCF 'ye dahil edilen soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlExporter>Tür, ekli ilke ifadeleriyle wsdl meta verileri oluşturur.  
  
 Endpoint davranışlarına, sözleşme davranışlarına veya bir hizmet uç noktasındaki bağlama öğelerine yönelik özel WSDL meta verilerini veya WSDL uzantılarını dışarı aktarmak için, <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimini uygulayabilirsiniz. , <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.IWsdlExportExtension> WSDL belgesi oluşturulurken arabirimini uygulayan bağlama öğeleri, işlem davranışları, sözleşme davranışları ve uç nokta davranışları için bir örneğe bakar.  
  
## <a name="publishing-service-metadata"></a>Hizmet meta verileri yayımlanıyor  
 WCF Hizmetleri bir veya daha fazla meta veri uç noktası ortaya çıkaran meta verileri yayımlar. Yayımlama hizmeti meta verileri, MEX ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak hizmet meta verilerinin kullanılabilmesini sağlar. Meta veri uç noktaları, bir adres, bağlama ve bir sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzerdir. Yapılandırma veya koddaki bir hizmet ana bilgisayarına meta veri uç noktaları ekleyebilirsiniz.  
  
 Bir WCF hizmeti için meta veri uç noktalarını yayımlamak için, önce hizmete bir hizmet davranışı örneği eklemeniz gerekir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> . Hizmetinize bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> örnek eklemek, bir veya daha fazla meta veri uç noktası açığa çıkarmak için hizmetinizi bir veya daha fazla meta veri yayımlama özelliğiyle genişlettiğini. <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Hizmet davranışını ekledikten sonra, http/get isteklerine yanıt veren MEX protokolünü veya meta veri uç noktalarını destekleyen meta veri uç noktalarını kullanıma sunabilirsiniz.  
  
 MEX protokolünü kullanan meta veri uç noktaları eklemek için, hizmet ana bilgisayarınıza IMetadataExchange adlı hizmet sözleşmesini kullanan hizmet uç noktaları ekleyin. WCF, <xref:System.ServiceModel.Description.IMetadataExchange> Bu hizmet sözleşmesi adına sahip arabirimi tanımlar. WS-MetadataExchange uç noktaları veya MEX uç noktaları,, <xref:System.ServiceModel.Description.MetadataExchangeBindings> Svcutil. exe gıbı WCF araçları tarafından kullanılan varsayılan bağlamaları eşleştirmek için sınıfında statik fabrika yöntemleri tarafından kullanıma sunulan dört varsayılan bağlamanın birini kullanabilir. Ayrıca, özel bağlama kullanarak MEX meta veri uç noktalarını yapılandırabilirsiniz.  
  
 , <xref:System.ServiceModel.Description.ServiceMetadataBehavior> <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Hizmetinizdeki tüm hizmet uç noktalarına ait meta verileri dışarı aktarmak için bir kullanır. Bir hizmetten meta verileri dışarı aktarma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](exporting-and-importing-metadata.md)aktarma.  
  
 Hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ana bilgisayarınıza uzantı olarak bir örnek ekleyerek hizmet ana bilgisayarınızı genişlettiğini artırmaktadır <xref:System.ServiceModel.Description.ServiceMetadataExtension> . , <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Meta veri yayımlama protokolleri için uygulama sağlar. Ayrıca, <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> özelliğine erişerek hizmetin meta verilerini çalışma zamanında almak için öğesini de kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> .  
  
> [!CAUTION]
> Uygulama yapılandırma dosyanıza bir MEX uç noktası ekler ve ardından <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kod içinde hizmet ana bilgisayarınıza eklemeyi denerseniz, aşağıdaki özel durumu alırsınız:  
>
> System. InvalidOperationException: sözleşme adı ' IMetadataExchange ', Service Service1 tarafından uygulanan sözleşmeler listesinde bulunamadı. Bu sözleşme için desteği etkinleştirmek üzere doğrudan yapılandırma dosyasına veya ServiceHost öğesine bir ServiceMetadataBehavior ekleyin.  
>
> <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Yapılandırma dosyasını ekleyerek veya hem uç noktasını hem de kodu ekleyerek bu sorunu geçici olarak çözebilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> .  
>
> <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Uygulama yapılandırma dosyasına ekleme örneği Için [Başlarken](../samples/getting-started-sample.md)bölümüne bakın. Kodda ekleme hakkında bir örnek için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , [self-Host](../samples/self-host.md) örneğine bakın.  

> [!CAUTION]
> Her birinde aynı ada sahip bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmet için meta veriler yayımlarken, bir özel durum oluşturulur. Örneğin, bir işlem Get (otomobil c) içeren IComparer adlı bir hizmet sözleşmesini sunan bir hizmetiniz varsa ve aynı hizmet, işlem al (Book b) olan IBookService adlı bir hizmet sözleşmesini kullanıma sunarsa, hizmetin meta verilerini oluştururken bir özel durum oluşur veya bir hata iletisi görüntülenir. Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:  
>
> - İşlemlerden birini yeniden adlandırın.
> - Öğesini <xref:System.ServiceModel.OperationContractAttribute.Name%2A> farklı bir ada ayarlayın.  
> - Operations ' ad alanlarından birini özelliği kullanarak farklı bir ad alanına ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .  
  
## <a name="retrieving-service-metadata"></a>Hizmet meta verileri alınıyor  
 WCF, WS-MetadataExchange ve HTTP gibi standartlaştırılmış protokolleri kullanarak hizmet meta verilerini alabilir. Bu protokollerin her ikisi de tür tarafından desteklenir <xref:System.ServiceModel.Description.MetadataExchangeClient> . Hizmet meta verilerini, türü kullanarak <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> bir adres ve isteğe bağlı bir bağlama sağlayarak elde edersiniz. Bir örnek tarafından kullanılan bağlama <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> statik sınıftan varsayılan bağlamalardan biri <xref:System.ServiceModel.Description.MetadataExchangeBindings> , Kullanıcı tarafından sağlanan bir bağlama veya sözleşmenin bir uç nokta yapılandırmasından yüklenen bir bağlama olabilir `IMetadataExchange` . <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Ayrıca, türü kullanılarak meta VERILERE http url başvurularını da çözümleyebilir <xref:System.Net.HttpWebRequest> .  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örnek tek bir <xref:System.ServiceModel.Channels.ChannelFactoryBase> örneğe bağlanır. <xref:System.ServiceModel.Channels.ChannelFactoryBase>Tarafından kullanılan örneği <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> sanal yöntemi geçersiz kılarak değiştirebilir veya değiştirebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> . Benzer şekilde, <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> sanal yöntemi GEÇERSIZ kılarak http/get istekleri yapmak için tarafından kullanılan örneği değiştirebilir veya değiştirebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> .  
  
 Svcutil. exe aracını kullanarak WS-MetadataExchange veya HTTP/GET isteklerini kullanarak hizmet meta verilerini alabilir ve **/target: Metadata** anahtarını ve bir adresini geçirerek. Svcutil. exe belirtilen adresteki meta verileri indirir ve dosyaları diske kaydeder. Svcutil. exe, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneği dahili olarak kullanır ve adı varsa Svcutil. exe ' ye geçirilen adresin düzeniyle eşleşen BIR MEX uç noktası yapılandırması (uygulama yapılandırma dosyasından) yükler. Aksi takdirde, Svcutil. exe varsayılan olarak statik fabrika türü tarafından tanımlanan bağlamalardan birini kullanmaktır <xref:System.ServiceModel.Description.MetadataExchangeBindings> .  
  
## <a name="importing-service-metadata"></a>Hizmet meta verileri içeri aktarılıyor  
 WCF 'de, meta veri alma, bir hizmetin soyut bir temsilini veya meta verilerinden bir bileşen parçalarını oluşturma işlemidir. Örneğin, WCF <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Channels.Binding> <xref:System.ServiceModel.Description.ContractDescription> bir HIZMET için bir wsdl belgesinden örnekleri, örnekleri veya örnekleri içeri aktarabilir. WCF 'de hizmet meta verilerini içeri aktarmak için soyut sınıfın bir uygulamasını kullanın <xref:System.ServiceModel.Description.MetadataImporter> . Sınıfından türetilen türler <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> , WCF 'DEKI WS-Policy Import mantığının avantajlarından yararlanan meta veri biçimlerini içeri aktarmaya yönelik destek uygular.  
  
 Bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> uygulama, bir nesnedeki hizmet meta verilerine eklenen ilke ifadelerini toplar <xref:System.ServiceModel.Description.PolicyConversionContext> . <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>Daha sonra, özelliğindeki arabirimin uygulamalarını çağırarak, meta verileri içeri aktarma işleminin bir parçası olarak ilkeleri işler <xref:System.ServiceModel.Description.IPolicyImportExtension> <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> .  
  
 Bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> örnekteki koleksiyona kendi uygulamanızı ekleyerek yeni ilke onayları alma desteği ekleyebilirsiniz <xref:System.ServiceModel.Description.IPolicyImportExtension> <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> . Alternatif olarak, ilke içeri aktarma uzantınızı istemci uygulama yapılandırma dosyanıza kaydedebilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Tür, <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> WCF 'ye dahil edilen soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Türü, wsdl meta verilerini bir nesnede paketlenmiş ekli ilkelerle içe aktarır <xref:System.ServiceModel.Description.MetadataSet> .  
  
 <xref:System.ServiceModel.Description.IWsdlImportExtension>Arabirimi uygulayarak ve sonra uygulamanızı <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> örneğiniz ÖZELLIĞINE ekleyerek WSDL uzantıları içeri aktarma desteği ekleyebilirsiniz <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> . , <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> İstemci uygulama yapılandırma dosyanıza kayıtlı arabirimin uygulamalarını da yükleyebilir.  
  
## <a name="dynamic-bindings"></a>Dinamik bağlamalar  
 Uç nokta bağlamasının değiştiği olaydaki bir hizmet uç noktasına kanal oluşturmak için kullandığınız bağlamayı dinamik olarak güncelleştirebilir veya aynı sözleşmeyi kullanan ancak farklı bir bağlamaya sahip bir uç noktaya kanal oluşturmak isteyebilirsiniz. <xref:System.ServiceModel.Description.MetadataResolver>Belirli bir sözleşmeyi uygulayan hizmet uç noktaları için çalışma zamanında meta verileri almak ve içeri aktarmak üzere statik sınıfını kullanabilirsiniz. Daha sonra, <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> istenen uç noktaya bir istemci veya kanal fabrikası oluşturmak için içeri aktarılan nesneleri kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description>
- [Meta Veri Biçimleri](metadata-formats.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](exporting-and-importing-metadata.md)
- [Meta Verileri Yayımlama](publishing-metadata.md)
- [Meta Verileri Alma](retrieving-metadata.md)
- [Meta Verileri Kullanma](using-metadata.md)
- [Meta Veriler Hakkında Güvenlik Konuları](security-considerations-with-metadata.md)
- [Meta Veri Sistemini Genişletme](../extending/extending-the-metadata-system.md)
