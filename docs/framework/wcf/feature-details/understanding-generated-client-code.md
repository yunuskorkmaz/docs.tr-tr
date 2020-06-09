---
title: Oluşturulmuş İstemci Kodlarını Anlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: f04b67ae13307fb3c2a2981204526880f55d58f1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595069"
---
# <a name="understanding-generated-client-code"></a>Oluşturulmuş İstemci Kodlarını Anlama
[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) istemci uygulamaları oluşturmakta kullanmak için istemci kodu ve bir istemci uygulama yapılandırma dosyası oluşturur. Bu konu, standart hizmet sözleşmesi senaryoları için oluşturulan kod örnekleri turuna yöneliktir. Oluşturulan kodu kullanarak bir istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](../wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Projeniz için Windows Communication Foundation (WCF) istemci türleri oluşturmak üzere Visual Studio kullanıyorsanız, genellikle oluşturulan istemci kodunu incelemeniz gerekmez. Sizin için aynı hizmetleri gerçekleştiren bir geliştirme ortamı kullanmıyorsanız, istemci kodu oluşturmak için Svcutil. exe gibi bir araç kullanabilir ve ardından bu kodu kullanarak istemci uygulamanızı geliştirebilirsiniz.  
  
 Svcutil. exe ' nin, üretilen tür bilgilerini değiştiren sayıda seçeneği olduğundan, bu konu tüm senaryoları ele almaz. Ancak, aşağıdaki standart görevler oluşturulan kodu konumlandırmayı içerir:  
  
- Hizmet sözleşmesi arabirimlerini tanımlama.  
  
- WCF istemci sınıfını tanımlama.  
  
- Veri türlerini tanımlama.  
  
- Çift yönlü hizmetler için geri çağırma sözleşmelerini tanımlama.  
  
- Yardımcı hizmet sözleşmesi kanal arabirimini tanımlama.  
  
### <a name="finding-service-contract-interfaces"></a>Hizmet sözleşmesi arabirimlerini bulma  
 Hizmet sözleşmelerini modellediği arabirimleri bulmak için, özniteliğiyle işaretlenmiş arabirimleri arayın <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> . Genellikle bu özniteliğin, diğer özniteliklerin varlığı ve özniteliğin kendisi üzerinde ayarlanan açık özellikler nedeniyle hızlı bir okuma ile bulunması zor olabilir. Hizmet sözleşmesi arabiriminin ve istemci sözleşmesi arabiriminin iki farklı tür olduğunu unutmayın. Aşağıdaki kod örneği, özgün hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Aşağıdaki kod örneği, Svcutil. exe tarafından oluşturulan hizmet sözleşmesini gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>Hizmet işlemlerini çağırabileceğiniz BIR WCF kanal nesnesi oluşturmak için, oluşturulan hizmet sözleşmesi arabirimini sınıfıyla birlikte kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ChannelFactory kullanma](how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>WCF Istemci sınıflarını bulma  
 Kullanmak istediğiniz hizmet sözleşmesini uygulayan WCF istemci sınıfını bulmak için, bir uzantısı arayın <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ; burada tür parametresi, daha önce bulduğunuz ve bu arabirimi genişleten hizmet sözleşmesi arabirimidir. Aşağıdaki kod örneği, <xref:System.ServiceModel.ClientBase%601> türünde sınıfını gösterir `ISampleService` .  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu WCF istemci sınıfını, yeni bir örneğini oluşturup uyguladığı yöntemleri çağırarak kullanabilirsiniz. Bu yöntemler, tasarlandığı ve etkileşime geçmek üzere yapılandırıldığı hizmet işlemini çağırır. Daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](../wcf-client-overview.md).  
  
> [!NOTE]
> SvcUtil. exe bir WCF istemci sınıfı oluşturduğunda, <xref:System.Diagnostics.DebuggerStepThroughAttribute> hata AYıKLAYıCıLARıN WCF istemci sınıfı aracılığıyla adımlamasını engelleyen istemci sınıfına bir ekler.  
  
### <a name="finding-data-types"></a>Veri türlerini bulma  
 Oluşturulan koddaki veri türlerini bulmak için en temel mekanizma, bir sözleşmede belirtilen tür adını belirlemektir ve kodu bu tür bildirimine göre arar. Örneğin, aşağıdaki sözleşme, `SampleMethod` öğesinin türünde BIR SOAP hatası döndürebilirler `microsoft.wcf.documentation.SampleFault` .  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 İçin arama `SampleFault` , aşağıdaki tür bildirimini konumlandırır.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Bu durumda, veri türü, istemci üzerindeki belirli bir özel durum tarafından oluşturulan ayrıntı türüdür, <xref:System.ServiceModel.FaultException%601> burada ayrıntı türü parametresi olur `microsoft.wcf.documentation.SampleFault` . Veri türleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](specifying-data-transfer-in-service-contracts.md). İstemcilerde özel durumları işleme hakkında daha fazla bilgi için bkz. [hata gönderme ve alma](../sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Çift yönlü hizmetler için geri arama sözleşmeleri bulma  
 Sözleşme arabiriminin özellik için bir değer belirttiğinden bir hizmet sözleşmesi buldıysanız <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> , bu sözleşme bir çift yönlü sözleşmeyi belirtir. Çift yönlü sözleşmeler, istemci uygulamanın geri çağırma sözleşmesini uygulayan ve bu sınıfın bir örneğini <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> hizmetle iletişim kurmak için kullanılan bir geri çağırma sınıfı oluşturmasını gerektirir. Çift yönlü istemciler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme Ile hizmetlere erişme](how-to-access-services-with-a-duplex-contract.md).  
  
 Aşağıdaki sözleşme, türünde bir geri çağırma anlaşması belirtir `SampleDuplexHelloCallback` .  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Bu geri arama sözleşmesinin aranması, istemci uygulamanın uygulaması gereken aşağıdaki arabirimi bulur.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Hizmet sözleşmesi kanal arabirimlerini bulma  
 <xref:System.ServiceModel.ChannelFactory>Sınıfını bir hizmet sözleşmesi arabirimiyle kullanırken, <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> kanalı açıkça açmak, kapatmak veya iptal etmek için arabirimine dönüştürmelisiniz. , İle çalışmayı kolaylaştırmak için, Svcutil. exe aracı, hem hizmet sözleşmesi arabirimini uygulayan hem de <xref:System.ServiceModel.IClientChannel> istemci kanal altyapısına dönüştürme yapmak zorunda kalmadan etkileşim kurmanızı sağlayan bir yardımcı arabirim oluşturur. Aşağıdaki kod, önceki hizmet sözleşmesini uygulayan bir yardımcı istemci kanalının tanımını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF İstemcisi Genel Bakış](../wcf-client-overview.md)
