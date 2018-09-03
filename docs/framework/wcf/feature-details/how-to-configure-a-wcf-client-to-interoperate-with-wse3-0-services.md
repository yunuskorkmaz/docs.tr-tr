---
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 9d7cb4869e9e460373bffbf33f61f61ecb6e9948
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486733"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma
WCF istemcileri belirtiminin WS-Addressing Ağustos 2004 sürümü kullanmak için yapılandırıldığı zaman Windows Communication Foundation (WCF) istemcileri hat düzeyinde Web Hizmetleri iyileştirmeleri 3.0 ile Microsoft .NET (WSE) Hizmetleri için uyumludur.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>WSE 3.0 Web hizmetiyle çalışmak için WCF istemcisini yapılandırmak için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturma.  
  
     WSE Web hizmeti, bir WCF istemcisi sınıfı oluşturulur.  
  
     Bir WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf parçasıdır [WSE ile birlikte](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek.  
  
    1.  Türetilen bir sınıf oluşturmanız <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Özellikleri WSE anahtar teslimi onaylama, türetilen anahtarlar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten sınıfına ekleyin.  
  
         Aşağıdaki kod örneği tanımlar `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` WSE anahtar teslimi onaylama, türetilen anahtarlar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten özellikleri sırasıyla.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> bağlama özellikleri ayarlamak için yöntemi.  
  
         Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerlerini alarak belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  İstemci uygulama kodunda bağlama özellikleri ayarlamak için kod ekleyin.  
  
     Aşağıdaki kod örneği WCF istemcisini iletisi koruma ve kimlik doğrulaması WSE 3.0 tarafından tanımlandığı şekilde kullanması gerektiğini belirtir `AnonymousForCertificate` kullanıma hazır güvenlik onaylama işlemi. Ayrıca, güvenli oturumlar ve türetilen anahtarlar gereklidir.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir WSE 3.0 kullanıma hazır güvenlik onaylama işlemi özelliklerine karşılık gelen özelliklerle sunan özel bir bağlama tanımlar. Olarak adlandırılan özel bağlama `WseHttpBinding`, ardından bir WCF istemcisi için bağlama özelliklerini belirtmek için kullanılır.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE ile birlikte çalışma](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
