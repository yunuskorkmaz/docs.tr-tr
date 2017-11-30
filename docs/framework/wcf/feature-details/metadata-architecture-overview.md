---
title: "Meta Veri Mimarisi Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1fa7fea1709f2664abe45ebdb916183a46885612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-architecture-overview"></a>Meta Veri Mimarisi Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]dışarı aktarma, yayımlama, alma ve hizmet meta verileri içe aktarma için zengin bir altyapı sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmetleri, böylece Svcutil.exe gibi araçları hizmete erişim için istemci kodu otomatik olarak oluşturabilir hizmetin uç ile etkileşim kurmak nasıl açıklamak için meta verileri kullanın.  
  
 Çoğu oluşturan türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] meta verileri altyapı bulunan <xref:System.ServiceModel.Description> ad alanı.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kullanan <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet uç noktalarını tanımlamak için sınıf. Kullanabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet uç noktaları için meta verileri oluşturun veya oluşturmak için hizmet meta verilerini almak için <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir hizmet için meta veri örneği temsil eden <xref:System.ServiceModel.Description.MetadataSet> yapısını WS-MetadataExchange tanımlı meta verileri seri hale getirme biçimi için bağlı kesinlikle türü. <xref:System.ServiceModel.Description.MetadataSet> Türü sunmaktadır Web Hizmetleri Açıklama Dili (WSDL) belgeleri, XML Şeması belgelerinde veya WS-Policy ifadeler gibi gerçek hizmeti meta verileri koleksiyonu olarak <xref:System.ServiceModel.Description.MetadataSection> örnekleri. Her <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> belirli meta veriler dialect ve bir tanımlayıcı örneğini içerir. A <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> bulunan aşağıdaki öğelerin içerebilir, <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> özelliği:  
  
-   Ham meta veriler.  
  
-   A <xref:System.ServiceModel.Description.MetadataReference> örneği.  
  
-   A <xref:System.ServiceModel.Description.MetadataLocation> örneği.  
  
 A <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> örnekleri için başka bir meta veri değişimi (MEX) uç noktası ve <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> örnekleri noktası bir HTTP URL'sini kullanarak bir meta veri belgesi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmet uç noktaları, hizmet sözleşmelerini, bağlamaları, ileti açıklamak için WSDL belgeleri kullanılmasını destekler desenleri, iletileri ve hata iletileri hizmeti tarafından uygulanan exchange. Hizmet tarafından kullanılan veri türlerine XML Şeması'nı kullanarak WSDL belgelerde açıklanmıştır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Şema içeri ve dışarı aktarma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md). Kullanabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet davranışı için WSDL uzantıları almak ve vermek için davranışları ve bir hizmetin işlevlerini genişletmek bağlama öğeleri sözleşme. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][WCF uzantısı için özel meta verileri dışarı aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-service-metadata"></a>Hizmet meta verileri dışarı aktarma  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], *meta veri dışarı aktarma* hizmet uç noktaları açıklayan ve istemcilerin Hizmeti'nin nasıl kullanılacağını anlamak için kullanabileceği bir paralel, standartlaştırılmış gösterimine yansıtma işlemidir. Meta verilerini dışa aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri, kullanın uygulaması <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulama içinde kapsüllenir meta verilerini oluşturur bir <xref:System.ServiceModel.Description.MetadataSet> örneği.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Sınıfı bir uç nokta bağlama ve onun ilişkili işlemleri, iletileri ve hataları gereksinimlerini ve özelliklerini açıklayan ilke ifadeleri oluşturmak için bir çerçeve sağlar. Bu ilke ifadeleri, yakalanan bir <xref:System.ServiceModel.Description.PolicyConversionContext> örneği. A <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulama ürettiği meta veriler için bu ilke ifadelerini sonra iliştirebilirsiniz.  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> Her çağrılarını <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> uygulayan <xref:System.ServiceModel.Description.IPolicyExportExtension> bağlamasının arabiriminde bir <xref:System.ServiceModel.Description.ServiceEndpoint> oluştururken bir <xref:System.ServiceModel.Description.PolicyConversionContext> için nesne <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> uygulaması kullanın. Uygulayarak yeni ilke onaylamalarını dışa aktarabilirsiniz <xref:System.ServiceModel.Description.IPolicyExportExtension> , özel uygulamaları arabirimde <xref:System.ServiceModel.Channels.BindingElement> türü.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Türü uygulamasıdır <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> soyut sınıf ile birlikte gelen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlExporter> Türü iliştirilmiş ilke ifadelerini WSDL meta verilerini oluşturur.  
  
 Özel WSDL meta verileri veya uç nokta davranışları, sözleşme davranışları veya hizmet uç noktası bağlama öğeleri için WSDL uzantıları dışarı aktarmak için uygulayabileceğiniz <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi. <xref:System.ServiceModel.Description.WsdlExporter> Bakan bir <xref:System.ServiceModel.Description.ServiceEndpoint> öğeleri, işlemi davranışları, sözleşme davranışları ve uygulama uç noktası davranışları bağlama için örnek <xref:System.ServiceModel.Description.IWsdlExportExtension> WSDL belgesi oluştururken arabirim.  
  
## <a name="publishing-service-metadata"></a>Hizmet meta verileri yayımlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmetleri, bir veya daha fazla meta veri uç noktalarını göstererek meta veri yayımlama. Hizmet meta veri yayımlama hizmeti meta verileri MEX ve HTTP/GET istekleri gibi standart protokoller kullanılarak kullanılabilir hale getirir. Bir adresi, bağlama ve bir sözleşme sahip diğer hizmet uç noktalarına meta veri uç noktalarını benzerdir. Bir hizmet ana bilgisayar yapılandırma veya kod meta veri uç noktalar ekleyebilirsiniz.  
  
 Meta veri uç noktaları için yayımlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti örneği ilk eklemeniz gerekir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı. Ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> örneği hizmetiniz için bir veya daha fazla meta veri uç noktalarını göstererek meta verileri yayımlama olanağı hizmetinizi artırmaktadır. Eklediğiniz sonra <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmet davranışı HTTP/GET isteklerine yanıt veren MEX protokolü veya meta veri uç noktaları destek meta veri uç noktalarını sonra sunabilir.  
  
 MEX protokolünü kullanan meta veri uç noktalarını eklemek için hizmet uç noktaları IMetadataExchange adlı hizmet sözleşmesini kullanın, hizmet ana bilgisayarı ekleyin.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlar <xref:System.ServiceModel.Description.IMetadataExchange> bu hizmet sözleşmesi adı olan arabirimi. WS-MetadataExchange uç noktaları veya MEX uç birini kullanabilirsiniz üzerinde statik Fabrika yöntemler tarafından sunulan dört varsayılan bağlamaları <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı tarafından kullanılan varsayılan bağlamaları eşleşecek şekilde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Svcutil.exe gibi araçları. Özel bağlama kullanma MEX meta veri uç noktalarını da yapılandırabilirsiniz.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Kullanan bir <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> hizmetinizde tüm hizmet uç noktalarına meta verilerini dışa aktarmak için. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz. bir hizmetinden meta verileri dışa aktarma [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Ekleyerek, hizmet ana bilgisayarı güçlendirir bir <xref:System.ServiceModel.Description.ServiceMetadataExtension> örneği, hizmet ana bilgisayarı için bir uzantı olarak. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Meta veri protokolleri yayımlama uygulamasını sağlar. Aynı zamanda <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> erişerek çalışma zamanında hizmetin meta verileri almak için <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> özelliği.  
  
> [!CAUTION]
>  Uygulama yapılandırma dosyasında MEX uç nokta ekleyip ekleme girişimi <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kod, hizmet ana şu özel durum alın:  
>   
>  System.InvalidOperationException: Sözleşme adı 'IMetadataExchange' Service1 hizmeti tarafından uygulanan sözleşmeleri listesinde bulunamadı. Yapılandırma dosyası veya doğrudan bu sözleşmenin desteğini etkinleştirmek için ServiceHost bir ServiceMetadataBehavior ekleyin.  
>   
>  Her iki ekleyerek bu sorunun geçici çözümü <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırma dosyası veya her iki uç nokta ekleme ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kod.  
>   
>  Ekleme konusunda bir örnek için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> bir uygulama yapılandırma dosyasında bkz [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ekleme konusunda bir örnek için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kodda bkz [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  
  
> [!CAUTION]
>  İki farklı hizmet sunan bir hizmet için meta veri yayımlama sözleşmelerinde olduğunda, her bir işlem aynı adda bir özel durum içermesi atılır. Örneğin, adlı bir hizmet sözleşmesini kullanıma sunan bir hizmetiniz varsa bir işlem var ICarService almak (Car c) ve bir işlemin Get (defteri b) olan IBookService adlı bir hizmet sözleşmesini aynı hizmeti sunan, bir özel durum veya bir hata iletisi hizmetin meta verilerini oluştururken görüntülenir. Bu sorunu aşağıdakilerden birini yapın çalışmak için:  
>   
>  -   İşlemlerden birini yeniden adlandırın.  
> -   Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.  
> -   İşlemler ad alanlarından birini kullanılarak farklı bir ad alanı olarak ayarlanan <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
## <a name="retrieving-service-metadata"></a>Hizmet meta verilerini alma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS-MetadataExchange ve HTTP gibi standart protokoller kullanılarak hizmeti meta verileri alabilir. Bu protokollerin her ikisi de tarafından desteklenen <xref:System.ServiceModel.Description.MetadataExchangeClient> türü. Hizmet meta verileri kullanarak almak <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> bir adres ve isteğe bağlı bir bağlama sağlayarak türü. Bağlama tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örnek varsayılan bağlantılardan biri olabilir <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik sınıf, bir kullanıcı tarafından sağlanan bağlama veya bir bağlama yüklenen bir uç nokta yapılandırması için gelen `IMetadataExchange` sözleşme. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Meta verileri kullanarak HTTP URL'si başvurular de çözebilirsiniz <xref:System.Net.HttpWebRequest> türü.  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneğinin tek bir bağlı <xref:System.ServiceModel.Channels.ChannelFactoryBase> örneği. Değiştirin veya Değiştir <xref:System.ServiceModel.Channels.ChannelFactoryBase> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> kılarak <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> sanal yöntemi. Benzer şekilde, değiştirin ya da değiştirebileceğiniz <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> HTTP/GET istekleri geçersiz kılarak yapmak için <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> sanal yöntemi.  
  
 WS-MetadataExchange veya HTTP/GET istekleri Svcutil.exe aracını kullanarak ve geçirme kullanarak hizmeti meta verilerini almak **/target:metadata** anahtarı ve bir adres. Svcutil.exe belirtilen adresteki meta verileri indirir ve dosyaları diske kaydeder. Svcutil.exe kullanan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> dahili örneği ve adıyla eşleşen adres düzeni MEX uç nokta yapılandırması (uygulama yapılandırma dosyasından) varsa Svcutil.exe için geçirilen yükleri bulunmaktadır. Aksi takdirde tarafından tanımlanan bağlamalardan birini kullanarak Svcutil.exe varsayılanları <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik Fabrika türü.  
  
## <a name="importing-service-metadata"></a>Hizmet meta verileri içe aktarma  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], meta verileri alma, sistemi, hizmet ya da bileşen parçalarından soyut bir temsili kendi meta verilerini oluşturma işlemidir. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri <xref:System.ServiceModel.Channels.Binding> örnekleri veya <xref:System.ServiceModel.Description.ContractDescription> WSDL örneklerden belge için bir hizmet. Hizmet meta verilerde almak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf. Öğesinden türetilen türler <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> sınıf WS-Policy yararlanmak alma meta veri biçimleri mantığı almak için destek uygulama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 A <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> uygulama hizmeti meta verilerde iliştirilmiş ilke ifadelerini toplayan bir <xref:System.ServiceModel.Description.PolicyConversionContext> nesnesi. <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> İlkeleri uygulamaları çağırarak meta verileri içe aktarma bir parçası olarak işler <xref:System.ServiceModel.Description.IPolicyImportExtension> arabiriminde <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> özelliği.  
  
 Yeni ilke onaylamalarını içe aktarmak için destek ekleyebilirsiniz bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> kendi uyarlamasını ekleyerek <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimini <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> koleksiyonunda bir <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> örneği. Alternatif olarak, istemci uygulama yapılandırma dosyasında ilke alma uzantısına kaydedebilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü uygulamasıdır <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> soyut sınıf ile birlikte gelen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü içinde paketlendi ekli ilkeleriyle WSDL meta verileri içe aktaran bir <xref:System.ServiceModel.Description.MetadataSet> nesnesi.  
  
 WSDL uzantıları uygulayarak içe aktarmak için destek ekleyebilirsiniz <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi ve uygulamanız için ekleme <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> özelliği, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> örneği. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Ayrıca uygulamaları yükleyebilir ve <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi, istemci uygulama yapılandırma dosyasında kayıtlı.  
  
## <a name="dynamic-bindings"></a>Dinamik bağlamaları  
 Dinamik olarak bağlama uç noktası için değişiklikler gerektiğinde, hizmet uç noktası için bir kanal oluşturmak için kullandığınız bağlama güncelleştirebilir veya aynı sözleşme kullanan, ancak başka bir bağlama sahip bir uç nokta için bir kanal oluşturmak istersiniz. Kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataResolver> almak ve belirli bir sözleşmesini uygulama hizmet uç noktaları için çalışma zamanında meta verilerini içe aktarmak için statik sınıf. Daha sonra içeri aktarılan kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> bir istemci ya da kanal fabrikası istenen uç noktası oluşturmak için nesneler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description>  
 [Meta veri biçimleri](../../../../docs/framework/wcf/feature-details/metadata-formats.md)  
 [Meta veri alma ve verme](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Meta veri alma](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)  
 [Meta verilerini kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Meta veriler hakkında güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
