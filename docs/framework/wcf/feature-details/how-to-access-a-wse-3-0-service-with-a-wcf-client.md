---
title: 'Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 54d795858b85bd72a01f619b3603c9927df655d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme
WCF istemcileri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırıldıklarında Windows Communication Foundation (WCF) istemcileri hat düzeyinde Web Services Enhancements (WSE) 3.0 ile Microsoft .NET hizmetleri için uyumludur. Ancak, WSE 3.0 hizmetlerini meta veri değişimi (MEX) protokolü, bu nedenle desteklemeyen kullandığınızda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir WCF istemcisi sınıfı oluşturmak için güvenlik ayarları uygulanmaz oluşturulan WCF istemcisi. Bu nedenle, güvenlik ayarlarını belirtmeniz gerekir WCF istemcisini oluşturulduktan sonra WSE 3.0 hizmetini gerektirir.  
  
 WSE 3.0 hizmetin gereksinimleri ve bir WSE 3.0 hizmetine bir WCF istemcisi arasındaki birlikte çalışabilir gereksinimlerini dikkate almanız özel bağlama kullanarak, bu güvenlik ayarlarını uygulayabilirsiniz. Bu birlikte çalışabilirlik gereksinimleri Ağustos 2004 daha önce bahsedilen kullanımını içerir belirtimi WS adresleme ve 3.0default WSE iletisi korumasını <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. WCF için varsayılan ileti korumadır <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu konuda WSE 3.0 hizmeti ile birlikte çalışır bir WCF bağlama oluşturma ayrıntılarını verir. WCF de bu bağlamayı içeren bir örnek sağlar. Bu örnek hakkında daha fazla bilgi için bkz: [ASMX Web Hizmetleri ile birlikte çalışma](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Bir WCF istemcisi ile WSE 3.0 Web hizmetine erişmek için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturmak için.  
  
     WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturulur. WSE 3.0 MEX Protokolü desteklemediğinden, Web hizmeti için güvenlik gereksinimlerini almak için Aracı'nı kullanamazsınız. Uygulama geliştiricisi istemcisi için güvenlik ayarları eklemeniz gerekir.  
  
     Bir WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf parçası olan [WSE ile birlikte](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek:  
  
    1.  Türeyen bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Özellikler WSE hizmeti, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarları tarafından kullanılan WSE anahtar teslimi onaylama belirtin sınıfına ekleyin. WSE 3.0 sürümünde, bir anahtar teslimi onaylama bir istemci veya Web hizmeti için güvenlik gereksinimlerini belirtir — bir bağlama wcf'de kimlik doğrulama modunu benzer.  
  
         Aşağıdaki kod örneğinde tanımlar `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, ve `MessageProtectionOrder` WSE anahtar teslimi onaylama güvenli oturumlar, olup kullanılıp kullanılmayacağını türetilmiş anahtar gerekli olup olmadığını belirten özellikleri imza onayı gereklidir ve ileti koruma ayarları sırasıyla.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi bağlama özellikleri ayarlayın.  
  
         Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerleri alma belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  İstemci uygulaması kodu bağlama özelliklerini ayarlamak için kodu ekleyin.  
  
     Aşağıdaki kod örneğinde WCF istemcisini ileti koruma ve kimlik doğrulama WSE 3.0 tarafından tanımlandığı şekilde kullanması gerektiğini belirtir `AnonymousForCertificate` anahtar teslimi güvenlik onaylama işlemi. Ayrıca, güvenli oturumlar ve türetilmiş anahtar gereklidir.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde WSE 3.0 anahtar teslimi güvenlik onaylama işlemi özelliklerine karşılık özellikleri kullanıma sunan özel bir bağlama tanımlar. Adlı bu özel bağlama `WseHttpBinding`, ardından WSSecurityAnonymous WSE 3.0 QuickStart örnek ile iletişim kuran bir WCF istemcisi için bağlama özelliklerini belirtmek için kullanılır.  
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE ile birlikte çalışma](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
