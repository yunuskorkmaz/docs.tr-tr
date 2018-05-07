---
title: Oluşturulmuş İstemci Kodlarını Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 8a28b52d786793308d8609704b564b75f23d95d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-generated-client-code"></a>Oluşturulmuş İstemci Kodlarını Anlama
[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci uygulamaları oluşturmak istemci kodu ve kullanmak için bir istemci uygulama yapılandırma dosyası oluşturur. Bu konu, standart hizmet sözleşmesi senaryoları için oluşturulan kod örnekleri turu sağlar. Oluşturulan kod kullanarak bir istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz: [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Projeniz için Windows Communication Foundation (WCF) istemci türleri oluşturmak için Visual Studio kullanıyorsanız, genellikle oluşturulan istemci kodu incelemek gerekmez. Aynı hizmetleri gerçekleştiren bir geliştirme ortamı kullanmıyorsanız, istemci kodu oluşturmak ve ardından bu kodu istemci uygulamanızı geliştirmek için Svcutil.exe gibi bir araç kullanabilirsiniz.  
  
 Oluşturulan tür bilgileri değiştirmek seçenekleri sayısı svcutil.exe sahip olduğundan, bu konuda tüm senaryoları açıklanmamıştır. Ancak, aşağıdaki standart görevler oluşturulan kod bulma içerir:  
  
-   Hizmet sözleşmesi arabirimleri tanımlama.  
  
-   WCF istemci sınıfı tanımlama.  
  
-   Veri türleri tanımlama.  
  
-   Geri çağırma sözleşmeleri çift yönlü hizmetler için tanımlayıcı.  
  
-   Yardımcı hizmet sözleşmesi kanal arabirimi tanımlama.  
  
### <a name="finding-service-contract-interfaces"></a>Bulma Hizmet sözleşmesi arabirimleri  
 Hizmet sözleşmeleri model arabirimleri bulmak için arama ile işaretlenen arabirimleri için <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> özniteliği. Genellikle bu öznitelik diğer öznitelikleri varlığı nedeniyle okuma hızlı ve açık özellikleri öznitelikte ayarlanmış bulması zor olabilir. Hizmet sözleşmesi arabirimi ve istemci sözleşme arabirimi iki farklı olduğunu unutmayın. Aşağıdaki kod örneğinde özgün hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Aşağıdaki kod örneğinde Svcutil.exe tarafından oluşturulan aynı hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Oluşturulan hizmet sözleşme arabirimi ile birlikte kullanabileceğiniz <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> hangi hizmet işlemleri çağırmak WCF kanalı nesnesi oluşturmak için sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>WCF istemci sınıfları bulma  
 Kullanmak istediğiniz hizmet sözleşmesini uygulayan WCF istemci sınıfı bulmak için uzantı için arama <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, burada tür parametresi hizmet sözleşmesi arabirim, daha önce bulunan ve bu arabirim genişletir. Aşağıdaki örnekte gösterildiği kod <xref:System.ServiceModel.ClientBase%601> sınıf türü `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu WCF istemci sınıfın yeni bir örneğini oluşturmak ve bunu uygulayan yöntemleri çağırma kullanabilirsiniz. Bu yöntemler, onu tasarlanmış ve etkileşim kurmak için yapılandırılmış hizmet işlemini çağırır. Daha fazla bilgi için bkz: [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  SvcUtil.exe WCF istemci sınıfı oluşturduğunda ekler bir <xref:System.Diagnostics.DebuggerStepThroughAttribute> istemci sınıfına WCF istemci sınıfı aracılığıyla atlama gelen hata ayıklayıcıları engeller.  
  
### <a name="finding-data-types"></a>Bulma veri türleri  
 Veri türleri oluşturulan kodda bulmak için en temel bir sözleşmede belirtilen tür adı belirleyin ve bu tür bildirimi kodunu aramak için mekanizmadır. Örneğin, aşağıdaki sözleşme belirtir `SampleMethod` türünde bir SOAP hatası döndürebilir `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Arama `SampleFault` aşağıdaki türü bildirimi bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Bu durumda veri türü, istemci üzerinde belirli bir özel durum tarafından oluşturulan ayrıntı türüdür bir <xref:System.ServiceModel.FaultException%601> ayrıntı tür parametresi olduğu `microsoft.wcf.documentation.SampleFault`. Veri türleri hakkında daha fazla bilgi için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). İstemcileri özel durum işleme hakkında daha fazla bilgi için bkz: [gönderme ve alma hataları](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma sözleşmeleri bulma  
 Sözleşme arabirimi için bir değer belirten bir hizmet sözleşmesini bulursanız <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özelliği, sonra bu sözleşme çift yönlü bir sözleşme belirtir. Çift yönlü sözleşmeler gerektirir geri çağırma sözleşme uygulayan bir geri çağırma sınıf oluşturun ve o sınıfın örneğini geçirmek için istemci uygulaması <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> veya <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> hizmetiyle iletişim kurmak için kullanılır. Çift yönlü istemcileri hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme ile Erişim Hizmetleri](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Bir geri çağırma sözleşme türü aşağıdaki sözleşme belirtir `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Geri çağırma sözleşme arama istemci uygulaması uygulamalıdır aşağıdaki arabirimi bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Bulma Hizmet sözleşmesi kanalı arabirimleri  
 Kullanırken <xref:System.ServiceModel.ChannelFactory> sınıfı için atamalısınız hizmet sözleşme arabirimi ile <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> açıkça açmak, kapatmak veya kanal iptal etmek için arabirim. Çalışmak kolaylaştırmak için Svcutil.exe aracı ayrıca her iki hizmet sözleşmesi arabirimini uygulayan bir yardımcı arabirimi oluşturur ve <xref:System.ServiceModel.IClientChannel> cast gerek kalmadan istemci kanal altyapısıyla etkileşime geçmesini sağlamak için. Aşağıdaki kod, önceki hizmet sözleşmesini uygulayan bir yardımcı istemci kanal tanımını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF İstemcisine Genel Bakış](../../../../docs/framework/wcf/wcf-client-overview.md)
