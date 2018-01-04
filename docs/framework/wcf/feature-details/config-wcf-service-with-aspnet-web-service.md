---
title: "Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma"
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
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4bd1dce4128e6f25294525f10226d98f732cd4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma
Yapılandırmak için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] birlikte çalışabilir olmasını Hizmeti uç noktası [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmeti istemcileri, kullanın <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü olarak hizmet uç noktası için bağlama türü.  
  
 İsteğe bağlı olarak, HTTPS ve bağlama üzerinde aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web hizmeti istemcileri desteklemediği ileti MTOM kodlama, böylece <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği olan varsayılan değer olarak sol <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. ASP.Net Web hizmeti istemcileri desteklemediği WS-Security, böylece <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> ayarlanmalı <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 İçin meta verileri oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti için kullanılabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmeti proxy üretimi Araçları (diğer bir deyişle, [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833), [Web Hizmetleri bulma Aracı () Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)ve Visual Studio Web Başvuru Ekle özelliğinde), bir HTTP/GET meta veri uç noktasının maruz bırakmamalısınız.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>ASP.NET Web hizmeti istemcileri kodda ile uyumlu bir WCF uç noktası eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.BasicHttpBinding> örneği  
  
2.  İsteğe bağlı olarak bu hizmet uç noktası bağlama için taşıma güvenliği bağlama için güvenlik modunu ayarlayarak etkinleştir <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Ayrıntılar için lütfen bkz [taşıma güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Yeni bir uygulama uç noktası, yeni oluşturduğunuz bağlama örneği kullanarak, hizmet ana bilgisayarı ekleyin. Kod içinde hizmet uç noktası ekleme hakkında daha fazla bilgi için bkz [nasıl yapılır: kod içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4.  Hizmetiniz için bir HTTP/GET meta veri uç nokta etkinleştirin. Ayrıntılar için bkz: [nasıl yapılır: meta verileri kullanarak bir hizmet kodu yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Yapılandırma dosyasında ASP.NET Web hizmeti istemcileri ile uyumlu bir WCF uç noktası eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.BasicHttpBinding> bağlama yapılandırması. Ayrıntılar için bkz [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2.  İsteğe bağlı olarak bu hizmeti uç noktası bağlama yapılandırması için taşıma güvenliği bağlama için güvenlik modunu ayarlayarak etkinleştir <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Ayrıntılar için bkz [taşıma güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3.  Yeni oluşturduğunuz bağlama Yapılandırması'nı kullanarak hizmetiniz için yeni bir uygulama uç noktası yapılandırın. Bir yapılandırma dosyasında bir hizmet uç noktası ekleme hakkında daha fazla bilgi için bkz [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4.  Hizmetiniz için bir HTTP/GET meta veri uç nokta etkinleştirin. Ayrıntılar için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği nasıl ekleneceği gösterilmektedir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ile uyumlu uç nokta [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web hizmeti istemcileri kodda ve alternatif olarak yapılandırma dosyalarında.  
  
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
