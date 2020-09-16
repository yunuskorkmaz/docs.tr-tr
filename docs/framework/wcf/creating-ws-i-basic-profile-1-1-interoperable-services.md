---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 5fc29432bdd55daff2d60d641a4cea4925278032
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543023"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
WCF hizmet uç noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilen şekilde yapılandırmak için:  
  
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>Hizmet uç noktanız için bağlama türü olarak türü kullanın.  
  
- Hizmet uç noktanıza geri çağırma ve oturum sözleşmesi özellikleri ya da işlem davranışları kullanmayın  
  
İsteğe bağlı olarak, bağlamada HTTPS ve aktarım düzeyi istemci kimlik doğrulaması desteğini etkinleştirebilirsiniz.  
  
Sınıfının aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> WS-ı temel profil 1,1 ' nin ötesinde işlevsellik gerektirir:  
  
- İleti Iletimi Iyileştirme mekanizması (MTOM) özelliği tarafından denetlenen ileti kodlaması <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> . Bu özelliği varsayılan değerinde bırakın ve bu, MTOM 'yi <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> kullanmaz.  
  
- Değere göre denetlenen ileti güvenliği, WS <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> -ı temel güvenlik profili 1,0 ile uyumlu WS-güvenlik desteği sağlar. Bu özelliği, WS-Security ' i kullanmayan varsayılan değerinde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> .  
  
Bir WCF hizmetinin meta verilerini ASP.NET için kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçları: [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Hizmetleri bulma aracı (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))ve Visual Studio 'daki **Web başvurusu Ekle** özelliğini kullanın. Meta veri yayımlamayı etkinleştirin. Daha fazla bilgi için bkz. [meta veri uç noktalarını yayımlama](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek kod, bir yapılandırma dosyasında, koddaki ASP.NET Web hizmeti istemcileriyle uyumlu bir WCF uç noktasının nasıl ekleneceğini gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik](./feature-details/interop-with-aspnet-web-services.md)
