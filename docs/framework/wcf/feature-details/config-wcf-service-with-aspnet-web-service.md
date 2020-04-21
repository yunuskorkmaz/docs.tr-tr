---
title: 'Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: ddd7e8c95701532010b54e5136a33d37d139f6a4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739225"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma

Bir Windows Communication Foundation (WCF) hizmet bitiş noktasını ASP.NET Web hizmeti istemcisiyle <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> birlikte çalışabilir olarak yapılandırmak için, hizmet bitiş noktanız için bağlama türü olarak türü kullanın.  
  
 Bağlamada HTTPS ve aktarım düzeyinde istemci kimlik doğrulaması için isteğe bağlı olarak destek etkinleştirebilirsiniz. ASP.NET Web hizmeti istemcileri MTOM ileti kodlamasını desteklemez, bu nedenle <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özellik <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>varsayılan değeri olarak bırakılmalıdır. ASP.NET Web Hizmeti istemcileri WS-Security'yi desteklemez, bu nedenle <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> . <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>  
  
 Bir WCF hizmetinin meta verilerini ASP.NET Web hizmeti proxy oluşturma araçları (diğer bir deyişle, [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)), Web Hizmetleri Bulma Aracı [(Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))ve Visual Studio'da **Web Başvuru Ekle** özelliği ni ASP.NET için kullanılabilir hale getirmek için, bir HTTP/GET meta veri bitiş noktasını ortaya çıkarmalısınız.  
  
## <a name="add-an-endpoint-in-code"></a>Kodda bir uç nokta ekleme  
  
1. Yeni <xref:System.ServiceModel.BasicHttpBinding> bir örnek oluşturma  
  
2. İsteğe bağlı olarak, bu hizmetin bitiş noktası bağlamaiçin <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>aktarım güvenliğini, 'ye bağlama için güvenlik modunu ayarlayarak etkinleştirin. Ayrıntılar için [Transport Security'ye](../../../../docs/framework/wcf/feature-details/transport-security.md)bakın.  
  
3. Yeni oluşturduğunuz bağlama örneğini kullanarak hizmet ana bilgisayarınıza yeni bir uygulama bitiş noktası ekleyin. Koda bir hizmet bitiş noktası nın nasıl eklenebildiğini öğrenmek için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
  
4. Hizmetiniz için bir HTTP/GET meta veri bitiş noktasını etkinleştirin. Ayrıntılar [için bkz.](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>Yapılandırma dosyasına bitiş noktası ekleme  
  
1. Yeni <xref:System.ServiceModel.BasicHttpBinding> bir bağlama yapılandırması oluşturun. Ayrıntılar için, Nasıl Yapılacağını şuna [bakın: Yapılandırmada Bir Hizmet Bağlama belirtin.](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
  
2. İsteğe bağlı olarak, bu hizmetin bitiş noktası bağlama yapılandırması <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>için aktarım güvenliğini, 'ye bağlama için güvenlik modunu ayarlayarak etkinleştirin. Ayrıntılar için [Transport Security'ye](../../../../docs/framework/wcf/feature-details/transport-security.md)bakın.  
  
3. Yeni oluşturduğunuz bağlama yapılandırmasını kullanarak hizmetiniz için yeni bir uygulama bitiş noktası yapılandırın. Yapılandırma dosyasına hizmet bitiş noktası nın nasıl eklendirilenle ilgili ayrıntılar için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
  
4. Hizmetiniz için bir HTTP/GET meta veri bitiş noktasını etkinleştirin. Ayrıntılar için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, kod ve alternatif olarak yapılandırma dosyalarında ASP.NET Web hizmeti istemcileri ile uyumlu bir WCF bitiş noktasının nasıl ekleyeceğini gösterir.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
