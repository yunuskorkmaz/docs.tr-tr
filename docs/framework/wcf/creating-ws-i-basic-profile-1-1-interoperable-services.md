---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320135"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
WCF hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için:  
  
- Hizmet uç noktanız için bağlama türü olarak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türünü kullanın.  
  
- Hizmet uç noktanıza geri çağırma ve oturum sözleşmesi özellikleri ya da işlem davranışları kullanmayın  
  
 İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz.  
  
 @No__t-0 sınıfının aşağıdaki özellikleri, WS-ı temel profil 1,1 ' den daha fazla işlevsellik gerektirir:  
  
- @No__t-0 özelliği tarafından denetlenen ileti Iletimi Iyileştirme mekanizması (MTOM) ileti kodlaması. Bu özelliği varsayılan değerinde bırakın, bu, MTOM 'yi kullanmak için <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> ' dır.  
  
- @No__t-0 değeri tarafından denetlenen ileti güvenliği, WS-ı temel güvenlik profili 1,0 ile uyumlu WS-güvenlik desteği sağlar. Bu özelliği, WS-Security ' i kullanmak için <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> olan varsayılan değerinde bırakın.  
  
 Bir WCF hizmetinin meta verilerini ASP.NET için kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçları: [Web Hizmetleri Açıklama Dili Aracı (wsdl. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Hizmetleri bulma aracı (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)ve Visual Studio 'da `Add Web Reference` özelliği kullanın; meta veri yayımlamayı etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [meta veri uç noktalarını yayımlama](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod, bir yapılandırma dosyasında, koddaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik](./feature-details/interop-with-aspnet-web-services.md)
