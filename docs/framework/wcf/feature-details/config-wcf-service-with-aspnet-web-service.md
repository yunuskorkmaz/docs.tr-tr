---
title: 'Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 52f7857a2dc7108eb308fde942bf153d85d8e8ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593613"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma

Windows Communication Foundation (WCF) hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için, <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü hizmet uç noktanız için bağlama türü olarak kullanın.  
  
 İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz. ASP.NET Web hizmeti istemcileri, MTOM ileti kodlamasını desteklemez, <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> Bu nedenle özelliğin varsayılan değeri olarak bırakılması gerekir <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> . ASP.NET Web hizmeti istemcileri WS-Security ' yi desteklemediğinden, <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> olarak ayarlanmalıdır <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> .  
  
 Bir WCF hizmetinin meta verilerini ASP.NET Web hizmeti proxy oluşturma araçları (yani, [Web Hizmetleri Açıklama Dili Aracı (wsdl. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), [Web Hizmetleri bulma aracı (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))ve Visual Studio 'da **Web başvurusu Ekle** özelliği için KULLANILABILIR hale getırmek için, bir http/get meta veri uç noktası kullanıma sunmalısınız.  
  
## <a name="add-an-endpoint-in-code"></a>Kodda bir uç nokta ekleme  
  
1. Yeni örnek oluştur <xref:System.ServiceModel.BasicHttpBinding>  
  
2. İsteğe bağlı olarak, bağlantısı için güvenlik modunu ayarlayarak bu hizmet uç noktası bağlamasının aktarım güvenliğini etkinleştirin <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> . Ayrıntılar için bkz. [taşıma güvenliği](transport-security.md).  
  
3. Az önce oluşturduğunuz bağlama örneğini kullanarak hizmet ana bilgisayarınıza yeni bir uygulama uç noktası ekleyin. Kodda hizmet uç noktası ekleme hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: kod Içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md).  
  
4. Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: kod kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>Yapılandırma dosyasına bir uç nokta ekleme  
  
1. Yeni bir <xref:System.ServiceModel.BasicHttpBinding> bağlama yapılandırması oluşturun. Ayrıntılar için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).  
  
2. İsteğe bağlı olarak, bu hizmet uç noktası bağlama için güvenlik modunu ayarlayarak bu hizmet uç noktası bağlama yapılandırması için taşıma güvenliğini etkinleştirin <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> . Ayrıntılar için bkz. [taşıma güvenliği](transport-security.md).  
  
3. Az önce oluşturduğunuz bağlama yapılandırmasını kullanarak hizmetiniz için yeni bir uygulama uç noktası yapılandırın. Bir yapılandırma dosyasına hizmet uç noktası ekleme hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: yapılandırma Içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Hizmetiniz için bir HTTP/GET meta veri uç noktası etkinleştirin. Ayrıntılar için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, kodda ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini ve alternatif olarak yapılandırma dosyalarını gösterir.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma](how-to-create-a-service-endpoint-in-code.md)
- [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](how-to-publish-metadata-for-a-service-using-code.md)
- [Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme](../how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Aktarım Güvenliği](transport-security.md)
- [Meta Verileri Kullanma](using-metadata.md)
