---
title: 'Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 179591c272685771fbde12e161cb38b1bd969052
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597208"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme
Windows Communication Foundation (WCF) istemcileri, WCF istemcileri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında Microsoft .NET Hizmetleri için Web Hizmetleri geliştirmeleri (WCE) 3,0 ile kablo düzeyinde uyumludur. Ancak, WVA3,0 hizmetleri meta veri değişimi (MEX) protokolünü desteklemez, bu nedenle bir WCF istemci sınıfı oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullandığınızda, güvenlik ayarları oluşturulan WCF istemcisine uygulanmaz. Bu nedenle, WCF istemcisi oluşturulduktan sonra WVA3,0 hizmetinin gerektirdiği güvenlik ayarlarını belirtmeniz gerekir.  
  
 Bu güvenlik ayarlarını, WVAW 3,0 hizmetinin gereksinimlerini ve bir 3,0 WVAW hizmeti ile bir WCF istemcisi arasındaki birlikte çalışabilen gereksinimleri dikkate almak üzere özel bir bağlama kullanarak uygulayabilirsiniz. Bu birlikte çalışabilirlik gereksinimleri, Ağustos 2004 WS-Addressing belirtiminin ve WVAW 3.0 varsayılan ileti koruması 'nın belirtilen kullanımını içerir <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> . WCF için varsayılan ileti koruması <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . Bu konu, bir WVA3,0 hizmetiyle birlikte çalışan bir WCF bağlamasının nasıl oluşturulacağını açıklamaktadır. WCF Ayrıca bu bağlamayı ekleyen bir örnek sağlar. Bu örnek hakkında daha fazla bilgi için bkz. [asmx Web Hizmetleri Ile birlikte çalışma](../samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Bir WCF istemcisiyle bir WVA3,0 Web hizmetine erişmek için  
  
1. WVA3,0 Web hizmeti için bir WCF istemcisi oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
     Bir Wu 3,0 Web hizmeti için bir WCF istemcisi oluşturulur. WVA3,0, MEX protokolünü desteklemediğinden, Web hizmeti için güvenlik gereksinimlerini almak üzere aracı kullanamazsınız. Uygulama geliştiricisi, istemci için güvenlik ayarlarını eklememelidir.  
  
     WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).  
  
2. WVA3,0 Web hizmetleriyle iletişim kurabilen bir bağlamayı temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf, [Wo örneği Ile birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) 'nin bir parçasıdır:  
  
    1. Sınıfından türeten bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> .  
  
         Aşağıdaki kod örneği, sınıfından türetilen adlı bir sınıf oluşturur `WseHttpBinding` <xref:System.ServiceModel.Channels.Binding> .  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Wo hizmeti tarafından kullanılan WSESEL anahtar onayını belirten, türetilmiş anahtarların gerekli olup olmadığı, güvenli oturumların kullanılıp kullanılmayacağını, imza onaylarının gerekli olup olmadığını ve ileti koruma ayarlarını belirten sınıfa özellikler ekleyin. WSE 3,0 ' de, bir anahtar onaylama onayı, bir istemci veya Web hizmeti için güvenlik gereksinimlerini (WCF 'deki bir bağlamanın kimlik doğrulama moduna benzer şekilde) belirler.  
  
         Aşağıdaki kod örneği, `SecurityAssertion` `RequireDerivedKeys` `EstablishSecurityContext` `MessageProtectionOrder` wvasel anahtar onayını belirten,,, ve özelliklerini, türetilmiş anahtarların gerekli olup olmadığını, güvenli oturumların kullanılıp kullanılmadığını, imza onayları gerekip gerekmediğini ve ileti koruma ayarlarını sırasıyla tanımlar.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>Bağlama özelliklerini ayarlamak için yöntemini geçersiz kılın.  
  
         Aşağıdaki kod örneği, ve özelliklerinin değerlerini alarak aktarım, ileti kodlama ve ileti koruma ayarlarını belirtir `SecurityAssertion` `MessageProtectionOrder` .  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. İstemci uygulama kodunda, bağlama özelliklerini ayarlamak için kod ekleyin.  
  
     Aşağıdaki kod örneği, WCF istemcisinin WVA3,0 anahtar güvenlik onayı tarafından tanımlanan ileti koruması ve kimlik doğrulaması kullanması gerektiğini belirtir `AnonymousForCertificate` . Ayrıca, güvenli oturumlar ve türetilmiş anahtarlar gereklidir.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir WSE 3,0 anahtar güvenlik onaylaması özelliklerine karşılık gelen özellikleri kullanıma sunan özel bir bağlama tanımlar. Adlı özel bağlama, `WseHttpBinding` daha sonra Wssecurityanonsparse WDE 3,0 hızlı başlangıç örneğiyle iletişim kuran bır WCF istemcisinin bağlama özelliklerini belirtmek için kullanılır.  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Wo ile birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
