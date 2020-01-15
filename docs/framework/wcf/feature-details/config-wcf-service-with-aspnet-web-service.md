---
title: 'Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 7e07e8d8781040d4ddc1d5643446f5a42354a557
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963557"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma
Windows Communication Foundation (WCF) hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için, hizmet uç noktanız için bağlama türü olarak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türünü kullanın.  
  
 İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz. ASP.NET Web hizmeti istemcileri, MTOM ileti kodlamasını desteklemez, bu nedenle <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği varsayılan değeri olarak bırakılmalıdır ve bu <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. ASP.Net Web hizmeti istemcileri WS-Security ' yi desteklemediğinden <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>olarak ayarlanmalıdır.  
  
 Bir WCF hizmetinin meta verilerini ASP.NET Web hizmeti proxy oluşturma araçları (yani, [Web Hizmetleri Açıklama Dili Aracı (wsdl. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), [Web Hizmetleri bulma aracı (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))ve Visual Studio 'da Web başvurusu Ekle özelliği için kullanılabilir hale getırmek için, bir http/get meta veri uç noktası kullanıma sunmalısınız.  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>Koddaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktası eklemek için  
  
1. Yeni bir <xref:System.ServiceModel.BasicHttpBinding> örneği oluştur  
  
2. İsteğe bağlı olarak, <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>bağlama için güvenlik modunu ayarlayarak bu hizmet uç noktası bağlamasının aktarım güvenliğini etkinleştirin. Ayrıntılar için lütfen [Aktarım güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)' ne bakın.  
  
3. Az önce oluşturduğunuz bağlama örneğini kullanarak hizmet ana bilgisayarınıza yeni bir uygulama uç noktası ekleyin. Kodda hizmet uç noktası ekleme hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: kod Içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: kod kullanarak bir hizmet Için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>Bir yapılandırma dosyasındaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktası eklemek için  
  
1. Yeni bir <xref:System.ServiceModel.BasicHttpBinding> bağlama yapılandırması oluşturun. Ayrıntılar için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. İsteğe bağlı olarak, <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>bağlama için güvenlik modunu ayarlayarak bu hizmet uç noktası bağlama yapılandırması için taşıma güvenliğini etkinleştirin. Ayrıntılar için bkz. [taşıma güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Az önce oluşturduğunuz bağlama yapılandırmasını kullanarak hizmetiniz için yeni bir uygulama uç noktası yapılandırın. Bir yapılandırma dosyasına hizmet uç noktası ekleme hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: yapılandırma Içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, kodda ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini ve alternatif olarak yapılandırma dosyalarını gösterir.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
