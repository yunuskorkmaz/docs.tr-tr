---
title: 'Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 2e01d3de6ee7b415c7b3f18a20e840b8ec4ab9b6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210539"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Nasıl yapılır: WCF Aracısı ile WSE 3.0 Hizmetine Erişme
WCF istemcileri belirtiminin WS-Addressing Ağustos 2004 sürümü kullanmak için yapılandırıldığı zaman Windows Communication Foundation (WCF) istemcileri hat düzeyinde Web Services Enhancements (WSE) 3.0 ile Microsoft .NET hizmetleri için uyumludur. Ancak, WSE 3.0 hizmetlerini meta veri değişimi (MEX) protokolü, bu nedenle desteklemeyen kullandığınızda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir WCF istemcisi sınıfı oluşturmak için güvenlik ayarları uygulanmaz oluşturulan WCF istemcisi. Bu nedenle, güvenlik ayarlarını belirtmelisiniz WCF istemcisini oluşturulduktan sonra WSE 3.0 hizmet gerektirir.  
  
 WSE 3.0 hizmetin gereksinimlerini ve bir WCF istemcisi ile WSE 3.0 hizmet arasındaki birlikte çalışabilen gereksinimlerini dikkate almanız için özel bir bağlama kullanarak bu güvenlik ayarları uygulayabilirsiniz. Bu bir birlikte çalışabilirlik gereksinimleri Ağustos 2004 yukarıda sözü edilen kullanımını içerir ve WS-Addressing belirtim 3.0default WSE iletisi koruma <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. WCF için varsayılan ileti korumadır <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Bu konuda, birlikte çalışan bir WCF bağlama ile WSE 3.0 hizmet oluşturma işlemi açıklanmaktadır. WCF de bu bağlamayı içeren bir örnek sağlar. Bu örnek hakkında daha fazla bilgi için bkz: [ASMX Web Hizmetleri ile birlikte çalışma](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Bir WCF istemcisi ile WSE 3.0 Web hizmetine erişmek için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturma.  
  
     WSE 3.0 Web hizmeti, bir WCF istemcisi oluşturulur. WSE 3.0 MEX Protokolü desteklemediğinden, Web hizmeti için güvenlik gereksinimlerini almak için Aracı'nı kullanamazsınız. Uygulama geliştiricisi, istemci güvenlik ayarlarını eklemeniz gerekir.  
  
     Bir WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.  
  
     Aşağıdaki sınıf parçasıdır [WSE ile birlikte](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek:  
  
    1.  Türetilen bir sınıf oluşturmanız <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  WSE hizmeti, türetilen anahtarlar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarları tarafından kullanılan WSE anahtar teslimi onaylama belirtin sınıfı özellikleri ekleyin. WSE 3.0 sürümünde, kullanıma hazır bir onaylama işlemi bir istemci veya Web hizmetine ilişkin güvenlik gereksinimlerini belirtir; bağlama wcf'de kimlik doğrulama modu için benzer.  
  
         Aşağıdaki kod örneği tanımlar `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, ve `MessageProtectionOrder` WSE anahtar teslimi onaylama güvenli oturumlar, mi kullanılıp kullanılmayacağını türetilen anahtarlar gerekli olup olmadığını belirten özelliği imzası onayları gereklidir ve ileti koruma ayarları, sırasıyla.  
  
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
 Aşağıdaki kod örneği bir WSE 3.0 kullanıma hazır güvenlik onaylama işlemi özelliklerine karşılık gelen özelliklerle sunan özel bir bağlama tanımlar. Adlı, özel bağlama `WseHttpBinding`, ardından WSSecurityAnonymous WSE 3.0 hızlı başlangıç örnek ile iletişim kuran bir WCF istemcisi bağlama özelliklerini belirtmek için kullanılır.  
  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [WSE ile birlikte çalışma](https://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
