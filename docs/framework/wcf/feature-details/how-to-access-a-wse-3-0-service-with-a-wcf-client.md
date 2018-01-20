---
title: "Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme"
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
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49ff6378bcd35ab2d4e2adf3783a1c4e73025d3a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]istemcileridir hat düzeyinde uyumlu Web Services Enhancements (WSE) 3.0 ile ne zaman Microsoft .NET hizmetleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırılır. Ancak, WSE 3.0 hizmetlerini meta veri değişimi (MEX) protokolü, bu nedenle desteklemeyen kullandığınızda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci sınıfı, güvenlik ayarları uygulanmaz için oluşturulan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci. Bu nedenle, sonra WSE 3.0 hizmet gerektiren güvenlik ayarlarını belirtmeniz gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci oluşturulur.  
  
 WSE 3.0 hizmetin gereksinimleri ve WSE 3.0 hizmet arasındaki birlikte çalışabilir gereksinimlerini dikkate almanız özel bağlama kullanarak bu güvenlik ayarlarını uygulayabilirsiniz ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci. Bu birlikte çalışabilirlik gereksinimleri Ağustos 2004 daha önce bahsedilen kullanımını içerir belirtimi WS adresleme ve 3.0default WSE iletisi korumasını <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. Varsayılan ileti koruması [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu konuda oluşturma ayrıntıları bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlaması WSE 3.0 hizmeti ile birlikte çalışır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca bu bağlamayı içeren bir örnek sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu örnek, bkz: [ASMX Web Hizmetleri ile birlikte çalışma](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Bir WCF istemcisi ile WSE 3.0 Web hizmetine erişmek için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web hizmeti istemci.  
  
     WSE 3.0 Web hizmeti için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci oluşturulur. WSE 3.0 MEX Protokolü desteklemediğinden, Web hizmeti için güvenlik gereksinimlerini almak için Aracı'nı kullanamazsınız. Uygulama geliştiricisi istemcisi için güvenlik ayarları eklemeniz gerekir.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]oluşturma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf parçası olan [WSE ile birlikte](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek:  
  
    1.  Türeyen bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Özellikler WSE hizmeti, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarları tarafından kullanılan WSE anahtar teslimi onaylama belirtin sınıfına ekleyin. WSE 3.0 sürümünde, bir anahtar teslimi onaylama bir istemci veya Web hizmeti için güvenlik gereksinimlerini belirtir — bir bağlamanın kimlik doğrulama modu için benzer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
         Aşağıdaki kod örneğinde tanımlar `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, ve `MessageProtectionOrder` WSE anahtar teslimi onaylama güvenli oturumlar, olup kullanılıp kullanılmayacağını türetilmiş anahtar gerekli olup olmadığını belirten özellikleri imza onayı gereklidir ve ileti koruma ayarları sırasıyla.  
  
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
 Aşağıdaki kod örneğinde WSE 3.0 anahtar teslimi güvenlik onaylama işlemi özelliklerine karşılık özellikleri kullanıma sunan özel bir bağlama tanımlar. Adlı bu özel bağlama `WseHttpBinding`, ardından bağlama özelliklerini belirtmek için kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSSecurityAnonymous WSE 3.0 QuickStart örnek ile iletişim kuran istemci.  
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE ile birlikte çalışma](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
