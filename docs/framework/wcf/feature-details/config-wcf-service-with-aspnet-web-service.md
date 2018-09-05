---
title: 'Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: f4c4a66de1b50f7953d76e0e9a0ab8b0e030df09
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513905"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma
Bir Windows Communication Foundation (WCF) hizmet uç noktası ile birlikte çalışabilir olacak şekilde yapılandırmak için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kullanın, Web hizmeti istemcileriyle <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü, hizmet uç noktası için bağlama türü olarak.  
  
 İsteğe bağlı olarak, HTTPS ve bağlamadaki aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmeti istemcileri desteklemediği ileti MTOM kodlama, bu nedenle <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği olan varsayılan değer olarak sol <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. ASP.Net Web hizmeti istemcileri desteklemediği WS-Security, bu nedenle <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> ayarlanmalıdır <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Bir WCF hizmeti için meta veriler kullanılabilir hale getirmek için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmeti proxy oluşturma araçları (diğer bir deyişle, [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://go.microsoft.com/fwlink/?LinkId=73833), [Web Hizmetleri bulma Aracı (Disco.exe)](https://go.microsoft.com/fwlink/?LinkId=73834)ve Visual Studio'da Web Başvurusu Ekle özelliğini), bir HTTP/GET meta veri uç noktası sunmalıdır.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>ASP.NET Web hizmeti istemcileriyle kod ile uyumlu bir WCF uç noktası eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.BasicHttpBinding> örneği  
  
2.  İsteğe bağlı olarak Aktarım güvenliği için hizmet uç noktası bağlaması Bu bağlama için güvenlik modunu ayarlama etkinleştirme <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Ayrıntılar için lütfen bkz [aktarım güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Yeni bir uygulama uç noktasını kullanarak yeni oluşturduğunuz bağlama örneği, hizmet ana bilgisayar ekleyin. Kod içinde hizmet uç noktası ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: meta veri yayımlama için bir hizmet kullanarak kod](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Bir yapılandırma dosyasında ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktası eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.BasicHttpBinding> bağlama yapılandırması. Ayrıntılar için bkz [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  İsteğe bağlı olarak bu hizmet uç noktası bağlama yapılandırması için Aktarım güvenliği bağlama için güvenlik modunu ayarlama etkinleştirme <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Ayrıntılar için bkz [aktarım güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Yeni oluşturduğunuz bağlama yapılandırması kullanarak hizmetiniz için yeni bir uygulama uç noktası yapılandırın. Bir yapılandırma dosyasında bir hizmet uç noktası ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: meta veri yayımlama için yapılandırma dosyası kullanarak bir hizmet](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod ile uyumlu bir WCF uç noktası ekleme gösterir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmetinde istemcilere kodu ve alternatif olarak yapılandırma dosyalarında.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
