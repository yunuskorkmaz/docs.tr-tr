---
title: Meta Veri Mimarisi Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: f9c903dd520f1aa85fc0577264288ecbc8c62a7f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111481"
---
# <a name="metadata-architecture-overview"></a>Meta Veri Mimarisi Genel Bakış
Windows Communication Foundation (WCF) hizmet meta verileri içeri dışarı aktarma, yayımlama, alma ve zengin bir altyapı sağlar. WCF hizmetleri, böylece Svcutil.exe gibi araçları otomatik olarak hizmete erişim için istemci kodu oluşturmak hizmet uç noktaları ile etkileşim kurmayı açıklamak için meta verileri kullanın.  
  
 WCF meta verilerini altyapısını oluşturan türlerin çoğu bulunan <xref:System.ServiceModel.Description> ad alanı.  
  
 WCF kullanan <xref:System.ServiceModel.Description.ServiceEndpoint> bir hizmet uç noktalarını tanımlamak için sınıf. WCF hizmet uç noktaları için meta verileri oluşturun veya oluşturmak için hizmet meta verileri almak için kullanabileceğiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri.  
  
 WCF temsil eden bir hizmet için meta veri örneği <xref:System.ServiceModel.Description.MetadataSet> yapısını WS-MetadataExchange tanımlanmış meta verileri seri hale getirme biçimi için bağlı kesin türü. <xref:System.ServiceModel.Description.MetadataSet> Türü toplamıştır gerçek hizmet meta verileri, Web Hizmetleri Açıklama Dili (WSDL) belgeleri, XML şema belgeleri veya WS-Policy ifadeler gibi bir koleksiyonu olarak <xref:System.ServiceModel.Description.MetadataSection> örnekleri. Her <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> örneği belirli meta veriler diyalekti ve bir tanımlayıcı içerir. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> aşağıdaki öğeleri içerebilir, <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> özelliği:  
  
- Ham meta verileri.  
  
- A <xref:System.ServiceModel.Description.MetadataReference> örneği.  
  
- A <xref:System.ServiceModel.Description.MetadataLocation> örneği.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> örnekleri için başka bir meta veri değişimi (MEX) uç noktası ve <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> örnekleri bir HTTP URL'sini kullanarak bir meta veri belgesi gelin. Hizmet uç noktaları, hizmet sözleşmeleri, bağlamaları, ileti exchange desenleri, iletileri ve hata iletileri hizmeti tarafından uygulanan açıklayan WSDL belgeleri kullanarak WCF destekler. Hizmet tarafından kullanılan veri türleri XML Şeması'nı kullanarak WSDL belgelerinde açıklanmıştır. Daha fazla bilgi için [şema içeri ve dışarı aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). WCF hizmet davranışı, sözleşme davranışları ve bağlama öğeleri, bir hizmet işlevlerini genişletmek için WSDL uzantıları almak ve vermek için kullanabilirsiniz. Daha fazla bilgi için [WCF uzantısı için özel meta verileri dışarı aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Hizmet meta verileri dışarı aktarma  
 Wcf'de, *meta veri dışarı aktarma* , hizmet uç noktaları açıklayan ve bunları istemcilere hizmetin nasıl kullanılacağını anlamak için kullanabileceğiniz bir paralel, standartlaştırılmış gösterimine yansıtma işlemidir. Meta verileri dışarı aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri kullanmak uygulaması <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulama içinde kapsüllenir meta verilerini oluşturur bir <xref:System.ServiceModel.Description.MetadataSet> örneği.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Sınıfı, bir uç nokta bağlaması ve ilişkili operations, iletilerin ve hataların gereksinimlerini ve özelliklerini açıklayan ilke ifadeleri oluşturmak için bir çerçeve sağlar. Bu ilke ifadeleri, yakalanan bir <xref:System.ServiceModel.Description.PolicyConversionContext> örneği. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulama ürettiği meta veriler için bu ilke ifadeleri ardından iliştirebilirsiniz.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Her çağırıyor <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> uygulayan <xref:System.ServiceModel.Description.IPolicyExportExtension> bağlamasının arabiriminde bir <xref:System.ServiceModel.Description.ServiceEndpoint> oluştururken bir <xref:System.ServiceModel.Description.PolicyConversionContext> nesnesi <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> kullanılacak uygulama. Uygulayarak yeni ilke onaylamalarını dışa aktarabilirsiniz <xref:System.ServiceModel.Description.IPolicyExportExtension> özel, uygulamalarını bir arabirimdeki <xref:System.ServiceModel.Channels.BindingElement> türü.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Türüdür yürütmesinin <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> soyut sınıf ile WCF dahil. <xref:System.ServiceModel.Description.WsdlExporter> Türü iliştirilmiş ilke ifadeleri WSDL meta verilerini oluşturur.  
  
 Özel WSDL meta verileri veya uç nokta davranışları, sözleşme davranışları veya bir hizmet uç noktası bağlama öğeleri için WSDL uzantıları dışarı aktarmak için uygulayabileceğiniz <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi. <xref:System.ServiceModel.Description.WsdlExporter> Bakan bir <xref:System.ServiceModel.Description.ServiceEndpoint> öğelerini, işlem davranışları, sözleşme davranışları ve uygulayan uç nokta davranışları Binding örneği <xref:System.ServiceModel.Description.IWsdlExportExtension> WSDL belgesi oluşturulurken kullanılan arabirim.  
  
## <a name="publishing-service-metadata"></a>Hizmet meta verileri yayımlama  
 WCF hizmetleri, bir veya daha fazla meta veri uç noktalarını göstererek meta verileri yayımlama. Hizmet meta verileri yayımlama hizmeti meta verileri MEX ve HTTP/GET istekleri gibi standart protokolleri kullanarak kullanılabilir hale getirir. Bir adresi, bağlama ve bir sözleşme sahip diğer hizmet uç noktaları için meta veri uç noktalarını benzerdir. Meta veri uç noktalarını bir hizmet konağı yapılandırma veya kod ekleyebilirsiniz.  
  
 Bir WCF hizmeti için meta veri uç noktalarını yayımlamak için önce bir örneğini eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı. Ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmetinize örneği, bir veya daha fazla meta veri uç noktalarını göstererek meta veri yayımlama olanağı ile hizmetinizi artırmaktadır. Eklediğiniz sonra <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmet davranışı, HTTP/GET isteklerine yanıt veren MEX protokolü veya meta veri uç noktaları destekleyen bir meta veri uç noktalarını ardından koyabileceğiniz.  
  
 MEX protokolünü kullanan bir meta veri uç noktalarını eklemek için adlandırılmış IMetadataExchange.WCF tanımlar hizmet sözleşmesini kullanmak, hizmet konağı için hizmet uç noktaları Ekle <xref:System.ServiceModel.Description.IMetadataExchange> bu hizmet sözleşmesi adı olan arabirimi. WS-MetadataExchange uç noktalarına veya MEX uç noktaları, birini kullanabilirsiniz üzerinde statik Fabrika yöntemleri tarafından sunulan dört varsayılan bağlamaları <xref:System.ServiceModel.Description.MetadataExchangeBindings> Svcutil.exe gibi WCF araçları tarafından kullanılan varsayılan bağlamaları eşleştirilecek sınıfı. Özel bağlama kullanma MEX meta veri uç noktalarını da yapılandırabilirsiniz.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Kullanan bir <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> hizmetinizi tüm hizmet uç noktalarına meta verileri dışarı aktarmak için. Bir hizmet meta verileri dışarı aktarma hakkında daha fazla bilgi için bkz. [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Ekleyerek, hizmet ana bilgisayarı çoğaltan bir <xref:System.ServiceModel.Description.ServiceMetadataExtension> örneği, hizmet ana bilgisayarı için bir genişletme olarak. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Protokolleri yayımlama meta verileri uygulamasını sağlar. Ayrıca <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> erişerek çalışma zamanında hizmet meta verileri alınacak <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> özelliği.  
  
> [!CAUTION]
> Uygulama yapılandırma dosyanızda bir MEX uç nokta ekleyin ve ekleme denemesi <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kod, hizmet ana bilgisayar için şu özel durum alın:  
>
> System.InvalidOperationException: Sözleşme Adı 'IMetadataExchange' Service1 hizmeti tarafından uygulanan sözleşmelerin listesinde bulunamadı. Yapılandırma dosyası veya doğrudan bu sözleşme desteğini etkinleştirmek için ServiceHost bir ServiceMetadataBehavior ekleyin.  
>
> Ya da ekleyerek bu sorunu geçici olarak çözmek <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırma dosyası veya her iki uç nokta ekleme ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kod.  
>
> Ekleme örneği <xref:System.ServiceModel.Description.ServiceMetadataBehavior> bir uygulama yapılandırma dosyasında bkz [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ekleme örneği <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kodda bkz [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  

> [!CAUTION]
> İki farklı hizmet sunan bir hizmet için meta verileri yayımlama sözleşmeleri her bir işlem aynı adlı bir özel durum içeren oluşturulur. Örneğin, adlı bir hizmet sözleşmesini gösteren bir hizmetiniz varsa bir işlem var ICarService almak (araba c) ve bir işlemin Get (kitap b) olan IBookService adlı bir hizmet sözleşmesini aynı hizmet sunan, bir özel durum veya hata iletisi Hizmet meta verilerini oluştururken görüntülenir. Bu sorunu geçici olarak aşağıdakilerden birini yapın çalışmak için:  
>
> - İşlemlerden birini yeniden adlandırın.
> - Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.  
> - İşlemleri ad alanlarından birini kullanarak farklı bir ad alanı için ayarlanmış <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
## <a name="retrieving-service-metadata"></a>Hizmet meta verilerini alma  
 WCF hizmet meta verileri WS-MetadataExchange ve HTTP gibi standart protokoller kullanarak alabilirsiniz. Bu protokollerin her ikisi de tarafından desteklenen <xref:System.ServiceModel.Description.MetadataExchangeClient> türü. Hizmet meta verileri kullanarak almak <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> bir adresi ve isteğe bağlı bir bağlama sağlayarak türü. Bağlama tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneği varsayılan bağlantılardan biri olabilir <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik sınıf, bir kullanıcı tarafından sağlanan bağlama veya bir bağlama yüklenen bir uç nokta yapılandırması için gelen `IMetadataExchange` sözleşme. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Meta verileri kullanarak HTTP URL'si başvurular da çözebilirsiniz <xref:System.Net.HttpWebRequest> türü.  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneği için tek bir bağlı <xref:System.ServiceModel.Channels.ChannelFactoryBase> örneği. Değiştirin veya değiştirebileceğiniz <xref:System.ServiceModel.Channels.ChannelFactoryBase> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> kılarak <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> sanal yöntem. Benzer şekilde, değiştirin veya değiştirebileceğiniz <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> geçersiz kılarak HTTP/GET isteğinde bulunmak için <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> sanal yöntem.  
  
 Hizmet meta verileri Svcutil.exe aracını kullanarak ve bu işleve geçirerek, WS-MetadataExchange veya HTTP/GET istekleri kullanarak alabilirsiniz **/target:metadata** anahtarı ve bir adres. Svcutil.exe belirtilen adreste meta verileri indirir ve dosyaları diske kaydeder. Svcutil.exe kullanan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> yükleri adıyla eşleşen adresi düzeni MEX uç nokta yapılandırması (uygulama yapılandırma dosyasından) geçirilen için Svcutil.exe, varsa var ve dahili olarak örneği. Aksi takdirde, Svcutil.exe tarafından tanımlanan bağlamalardan biri varsayılan <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik Fabrika türü.  
  
## <a name="importing-service-metadata"></a>Hizmet meta verileri alma  
 WCF'de, meta verileri alma, meta verilerinden bir hizmet veya bileşen parçalarından soyut bir temsilini oluşturma işlemidir. Örneğin, WCF aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri <xref:System.ServiceModel.Channels.Binding> örnekleri veya <xref:System.ServiceModel.Description.ContractDescription> bir WSDL örneklerden belge için bir hizmet. WCF hizmet meta verileri içeri aktarmak için uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf. Öğesinden türetilen türler <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> WS-Policy yararlanan alma meta veri biçimleri WCF mantığı içeri aktarmak için sınıf uygulama desteği.  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> uygulama hizmeti meta verilerde iliştirilmiş ilke ifadeleri toplayan bir <xref:System.ServiceModel.Description.PolicyConversionContext> nesne. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> Ardından ilkeleri uygulamalarından birine çağrı yaparak meta verileri içe aktarma işleminin parçası olarak işler <xref:System.ServiceModel.Description.IPolicyImportExtension> arabiriminde <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> özelliği.  
  
 İçin yeni ilke onaylamalarını içe aktarma için destek ekleyebilirsiniz bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> kendi uygulaması ekleyerek <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimini <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> koleksiyonunda bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> örneği. Alternatif olarak, istemci uygulama yapılandırma dosyanızda, ilke içeri aktarma uzantısı kaydedebilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türüdür yürütmesinin <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> soyut sınıf ile WCF dahil. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü içinde paketlenir ekli ilkeleriyle WSDL meta verileri alır bir <xref:System.ServiceModel.Description.MetadataSet> nesne.  
  
 WSDL uzantıları uygulayarak almak için destek ekleyebilirsiniz <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi ve uygulamanız için ekleyerek <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> özelliği, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> örneği. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Uygulamaları da yükleyebilirsiniz <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi istemci uygulama yapılandırma dosyasında kayıtlı.  
  
## <a name="dynamic-bindings"></a>Dinamik bağlama  
 Uç nokta için bağlama değişiklikleri olay, hizmet uç noktası için bir kanal oluşturmak için kullandığınız bağlama dinamik olarak güncelleştir veya aynı anlaşmaya kullanan, ancak farklı bir bağlama sahip bir uç nokta için bir kanal oluşturmak istiyorsunuz. Kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataResolver> almak ve çalışma zamanında belirli sözleşmesini uygulama hizmet uç noktaları için meta verileri içeri aktarmak için statik sınıf. Daha sonra içeri aktarılan kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> nesneleri istenen uç noktası için bir istemci veya kanal fabrikası oluşturursunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description>
- [Meta Veri Biçimleri](../../../../docs/framework/wcf/feature-details/metadata-formats.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [Meta Verileri Alma](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
