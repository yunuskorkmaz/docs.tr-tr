---
title: Oluşturulmuş İstemci Kodlarını Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 6bc921355e54023ead3a308a7877ab609f868221
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968621"
---
# <a name="understanding-generated-client-code"></a>Oluşturulmuş İstemci Kodlarını Anlama
[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci uygulamaları oluşturmakta kullanmak için istemci kodu ve bir istemci uygulama yapılandırma dosyası oluşturur. Bu konu, standart hizmet sözleşmesi senaryoları için oluşturulan kod örnekleri turuna yöneliktir. Oluşturulan kodu kullanarak bir istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Projeniz için Windows Communication Foundation (WCF) istemci türleri oluşturmak üzere Visual Studio kullanıyorsanız, genellikle oluşturulan istemci kodunu incelemeniz gerekmez. Sizin için aynı hizmetleri gerçekleştiren bir geliştirme ortamı kullanmıyorsanız, istemci kodu oluşturmak için Svcutil. exe gibi bir araç kullanabilir ve ardından bu kodu kullanarak istemci uygulamanızı geliştirebilirsiniz.  
  
 Svcutil. exe ' nin, üretilen tür bilgilerini değiştiren sayıda seçeneği olduğundan, bu konu tüm senaryoları ele almaz. Ancak, aşağıdaki standart görevler oluşturulan kodu konumlandırmayı içerir:  
  
- Hizmet sözleşmesi arabirimlerini tanımlama.  
  
- WCF istemci sınıfını tanımlama.  
  
- Veri türlerini tanımlama.  
  
- Çift yönlü hizmetler için geri çağırma sözleşmelerini tanımlama.  
  
- Yardımcı hizmet sözleşmesi kanal arabirimini tanımlama.  
  
### <a name="finding-service-contract-interfaces"></a>Hizmet sözleşmesi arabirimlerini bulma  
 Hizmet sözleşmelerini modellediği arabirimleri bulmak için, <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> özniteliğiyle işaretlenmiş arabirimleri arayın. Genellikle bu özniteliğin, diğer özniteliklerin varlığı ve özniteliğin kendisi üzerinde ayarlanan açık özellikler nedeniyle hızlı bir okuma ile bulunması zor olabilir. Hizmet sözleşmesi arabiriminin ve istemci sözleşmesi arabiriminin iki farklı tür olduğunu unutmayın. Aşağıdaki kod örneği, özgün hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Aşağıdaki kod örneği, Svcutil. exe tarafından oluşturulan hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Hizmet işlemlerini çağırabileceğiniz bir WCF kanal nesnesi oluşturmak için, <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> oluşturulan hizmet sözleşmesi arabirimini sınıfıyla birlikte kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ChannelFactory öğesini](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)kullanın.  
  
### <a name="finding-wcf-client-classes"></a>WCF Istemci sınıflarını bulma  
 Kullanmak istediğiniz hizmet sözleşmesini uygulayan WCF istemci sınıfını bulmak için, bir uzantısı <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>arayın; burada tür parametresi, daha önce bulduğunuz ve bu arabirimi genişleten hizmet sözleşmesi arabirimidir. Aşağıdaki kod örneği, türünde <xref:System.ServiceModel.ClientBase%601> `ISampleService`sınıfını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu WCF istemci sınıfını, yeni bir örneğini oluşturup uyguladığı yöntemleri çağırarak kullanabilirsiniz. Bu yöntemler, tasarlandığı ve etkileşime geçmek üzere yapılandırıldığı hizmet işlemini çağırır. Daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
> Svcutil. exe bir WCF istemci sınıfı oluşturduğunda, hata ayıklayıcıların WCF <xref:System.Diagnostics.DebuggerStepThroughAttribute> istemci sınıfı aracılığıyla adımlamasını engelleyen istemci sınıfına bir ekler.  
  
### <a name="finding-data-types"></a>Veri türlerini bulma  
 Oluşturulan koddaki veri türlerini bulmak için en temel mekanizma, bir sözleşmede belirtilen tür adını belirlemektir ve kodu bu tür bildirimine göre arar. Örneğin, aşağıdaki sözleşme, `SampleMethod` öğesinin türünde `microsoft.wcf.documentation.SampleFault`bir soap hatası döndürebilirler.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 İçin `SampleFault` arama, aşağıdaki tür bildirimini konumlandırır.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Bu durumda, veri türü, istemci üzerindeki belirli bir özel durum tarafından oluşturulan ayrıntı türüdür, <xref:System.ServiceModel.FaultException%601> burada ayrıntı türü parametresi olur. `microsoft.wcf.documentation.SampleFault` Veri türleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). İstemcilerde özel durumları işleme hakkında daha fazla bilgi için bkz. [hata gönderme ve alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Çift yönlü hizmetler için geri arama sözleşmeleri bulma  
 Sözleşme arabiriminin <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> özellik için bir değer belirttiğinden bir hizmet sözleşmesi buldıysanız, bu sözleşme bir çift yönlü sözleşmeyi belirtir. Çift yönlü sözleşmeler, istemci uygulamanın geri çağırma sözleşmesini uygulayan ve bu sınıfın <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> bir örneğini hizmetle iletişim kurmak için kullanılan bir geri çağırma sınıfı oluşturmasını gerektirir. Çift yönlü istemciler hakkında daha fazla bilgi için [bkz. nasıl yapılır: Çift yönlü sözleşmeyle](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)hizmetlere erişin.  
  
 Aşağıdaki sözleşme, türünde `SampleDuplexHelloCallback`bir geri çağırma anlaşması belirtir.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Bu geri arama sözleşmesinin aranması, istemci uygulamanın uygulaması gereken aşağıdaki arabirimi bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Hizmet sözleşmesi kanal arabirimlerini bulma  
 <xref:System.ServiceModel.ChannelFactory> Sınıfını bir hizmet sözleşmesi arabirimiyle kullanırken, kanalı açıkça açmak, kapatmak veya iptal etmek <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> için arabirimine dönüştürmelisiniz. , İle çalışmayı kolaylaştırmak için, Svcutil. exe aracı, hem hizmet sözleşmesi arabirimini <xref:System.ServiceModel.IClientChannel> uygulayan hem de istemci kanal altyapısına dönüştürme yapmak zorunda kalmadan etkileşim kurmanızı sağlayan bir yardımcı arabirim oluşturur. Aşağıdaki kod, önceki hizmet sözleşmesini uygulayan bir yardımcı istemci kanalının tanımını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF İstemcisine Genel Bakış](../../../../docs/framework/wcf/wcf-client-overview.md)
