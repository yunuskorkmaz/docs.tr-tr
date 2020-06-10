---
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579585"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma
Windows Communication Foundation (WCF) istemcileri, WCF istemcileri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) Hizmetleri için Web Hizmetleri geliştirmeleri 3,0 ile kablo düzeyinde uyumludur.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Bir WCF istemcisini bir WVA3,0 Web hizmeti ile birlikte çalışmak üzere yapılandırmak için  
  
1. WVA3,0 Web hizmeti için bir WCF istemcisi oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.  
  
     Bir Wo Web hizmeti için bir WCF istemci sınıfı oluşturulur.  
  
     WCF istemcisi oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).  
  
2. WVA3,0 Web hizmetleriyle iletişim kurabilen bir bağlamayı temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf, [Wo örneği ile birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) 'nin bir parçasıdır.  
  
    1. Sınıfından türeten bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> .  
  
         Aşağıdaki kod örneği, sınıfından türetilen adlı bir sınıf oluşturur `WseHttpBinding` <xref:System.ServiceModel.Channels.Binding> .  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Wo anahtar onaylama onayını belirten sınıfa, türetilmiş anahtarların gerekli olup olmadığına, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığına ve ileti koruma ayarlarına yönelik özellikler ekleyin.  
  
         Aşağıdaki kod örneği,,, `SecurityAssertion` `RequireDerivedKeys` `EstablishSecurityContext` ve `MessageProtectionOrder` özelliklerini tanımlar. Bunlar, türetilmiş anahtarların gerekli olup olmadığını, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığını ve ileti koruma ayarlarını sırasıyla belirler.  
  
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
 Aşağıdaki kod örneği, bir WSE 3,0 anahtar güvenlik onaylaması özelliklerine karşılık gelen özellikleri kullanıma sunan özel bir bağlama tanımlar. Adlı özel bağlama `WseHttpBinding` daha sonra BIR WCF istemcisinin bağlama özelliklerini belirtmek için kullanılır.  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Wo ile birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
