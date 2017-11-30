---
title: "Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2dbd83de39f7daa96ec5566084e925f878e32154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]istemcileri Microsoft .NET (WSE) ne zaman Hizmetleri için Web Hizmetleri geliştirmeleri 3.0 hat düzeyinde uyumlu olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırılır.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>WSE 3.0 Web hizmeti ile birlikte çalışmak için WCF istemcisini yapılandırmak için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web hizmeti istemci.  
  
     WSE Web hizmeti için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci sınıfı oluşturulur.  
  
     Oluşturma hakkında daha fazla ayrıntı için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf parçası olan [WSE ile birlikte](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek.  
  
    1.  Türeyen bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Özellikler WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup olmadığı ve ileti koruma ayarlarını belirtin sınıfına ekleyin.  
  
         Aşağıdaki kod örneğinde tanımlar `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten özellikleri sırasıyla.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi bağlama özellikleri ayarlayın.  
  
         Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerleri alma belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  İstemci uygulaması kodu bağlama özelliklerini ayarlamak için kodu ekleyin.  
  
     Aşağıdaki kod örneğinde belirleyen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kullanmalıdır ileti koruma ve kimlik doğrulama WSE 3.0 tarafından tanımlandığı şekilde `AnonymousForCertificate` anahtar teslimi güvenlik onaylama işlemi. Ayrıca, güvenli oturumlar ve türetilmiş anahtar gereklidir.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde WSE 3.0 anahtar teslimi güvenlik onaylama işlemi özelliklerine karşılık özellikleri kullanıma sunan özel bir bağlama tanımlar. Adlı özel bağlama `WseHttpBinding`, ardından bağlama özelliklerini belirtmek için kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE ile birlikte çalışma](http://msdn.microsoft.com/en-us/f6816861-96a0-45f9-8736-8e4e82cd3a41)
