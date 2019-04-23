---
title: Oluşturulmuş İstemci Kodlarını Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 226b77d1c638ec4f8505140332ad35d4029ef0b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189166"
---
# <a name="understanding-generated-client-code"></a>Oluşturulmuş İstemci Kodlarını Anlama
[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci uygulamaları oluşturmak istemci kodu ve kullanmak için bir istemci uygulama yapılandırma dosyası oluşturur. Bu konu, standart hizmet sözleşme senaryoları için tura oluşturulan kod örnekleri sağlar. Oluşturulan kod kullanarak bir istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Projeniz için Windows Communication Foundation (WCF) istemci türlerini oluşturmak için Visual Studio kullanıyorsanız, genellikle oluşturulan istemci kodunu incelemek gerekmez. Aynı hizmet gerçekleştiren bir geliştirme ortamı kullanmıyorsanız, istemci kodu oluşturmak ve ardından istemci uygulamanızı geliştirmek için bu kodu kullanmak için Svcutil.exe gibi bir araç kullanabilirsiniz.  
  
 Svcutil.exe oluşturulan tür bilgilerini değiştiren seçenek bir sayı olduğundan, bu konuda tüm senaryoları ele almaz. Ancak, oluşturulan kod bulma standart aşağıdaki görevleri içerir:  
  
-   Hizmet sözleşmesi arabirimler tanımlama.  
  
-   WCF istemci sınıfı tanımlayıcı.  
  
-   Veri türleri tanımlama.  
  
-   Geri çağırma sözleşmeleri çift yönlü hizmetler için tanımlayıcı.  
  
-   Yardımcısı hizmet sözleşme kanal arabirimi tanımlama.  
  
### <a name="finding-service-contract-interfaces"></a>Bulma hizmeti sözleşmesi arabirimleri  
 Hizmet sözleşmeleri model arabirimleri bulmak için arama ile işaretlenmiş arabirimleri için <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> özniteliği. Genellikle bu öznitelik nedeniyle diğer öznitelikleri varlığını okuma hızlı ve öznitelikte açık özellikleri bulmak zor olabilir. Hizmet sözleşmesi ve istemci sözleşme arabirimlerinden iki farklı tür olduğunu unutmayın. Aşağıdaki kod örneği, özgün hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Aşağıdaki kod örneği svcutil.exe'yi oluşturulan gibi aynı hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Oluşturulan hizmet sözleşme arabirimi ile birlikte kullanabileceğiniz <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> hangi hizmet işlemleri çağırmak bir WCF kanalı nesnesi oluşturmak için sınıf. Daha fazla bilgi için [nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>WCF istemci sınıfları bulma  
 Kullanmak istediğiniz hizmet sözleşmesini uygulayan WCF istemci sınıfı bulmak için arama uzantısı için <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, tür parametresi hizmet sözleşmesi arabirim, daha önce olduğu bir yerde ve, o arabirimini genişletir. Aşağıdaki örnekte gösterildiği kod <xref:System.ServiceModel.ClientBase%601> sınıf türünün `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Yeni bir örneğini oluşturmaktan ve bunu uygulayan yöntemleri çağırmak bu WCF istemci sınıfını kullanabilirsiniz. Bu yöntemler, bu şekilde tasarlanmış ve etkileşim kurmak için yapılandırılmış hizmet işlemini çağırın. Daha fazla bilgi için [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Bir WCF istemcisi sınıfı SvcUtil.exe oluşturur, bunu ekler bir <xref:System.Diagnostics.DebuggerStepThroughAttribute> için hata ayıklayıcılar, WCF istemci sınıfı Adımlama dan engelleyen istemci sınıfı.  
  
### <a name="finding-data-types"></a>Bulma veri türleri  
 Veri türleri oluşturulan kodda bulmak için en temel bir sözleşmede belirtilen tür adı belirleyin ve bu türü bildirimi için kod arama yapmak için mekanizmadır. Örneğin, aşağıdaki sözleşme belirtir `SampleMethod` türünde bir SOAP hatasını döndürebilir `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Arama `SampleFault` aşağıdaki tür bildirimi bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Bu durumda veri türü özel bir istemci tarafından oluşturulan ayrıntı türdür bir <xref:System.ServiceModel.FaultException%601> ayrıntılı tür parametresi olduğu `microsoft.wcf.documentation.SampleFault`. Veri türleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). İstemcileri özel durumları işleme hakkında daha fazla bilgi için bkz. [gönderme ve alma hataları](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma sözleşmeleri bulma  
 Sözleşme arabirimi için bir değer belirtir bir hizmet sözleşmesini bulursanız <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği, ardından anlaşması çift yönlü sözleşme belirtir. Çift yönlü sözleşmeler gerektirir istemci uygulamanın geri çağırma anlaşması uygulayan bir geri çağırma sınıf oluşturun ve o sınıfın bir örneğini geçirin <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> veya <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> hizmetiyle iletişim kurmak için kullanılır. Çift yönlü istemcileri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişme](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Aşağıdaki anlaşması bir geri çağırma anlaşması türü belirtir `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Bu geri çağırma anlaşması için arama istemci uygulaması uygulamalıdır yandaki arayüzü bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Bulma hizmeti sözleşmesi kanal arabirimleri  
 Kullanırken <xref:System.ServiceModel.ChannelFactory> sınıfı e dönüştürmelisiniz hizmet sözleşme arabirimi ile <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> açıkça açmak, kapatmak veya kanal iptal etmek için arabirim. Çalışmak daha kolay hale getirmek için Svcutil.exe aracını da her iki hizmet sözleşme arabirimi uygulayan bir yardımcı arabirimi oluşturur ve <xref:System.ServiceModel.IClientChannel> dönüştürme yapmak zorunda kalmadan istemci kanal altyapısıyla etkileşim sağlamak için. Aşağıdaki kod önceki hizmet sözleşmesi uygulayan yardımcı istemci kanal tanımı gösterilmektedir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF İstemcisine Genel Bakış](../../../../docs/framework/wcf/wcf-client-overview.md)
