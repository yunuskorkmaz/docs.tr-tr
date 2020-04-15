---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389756"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
WCF hizmet bitiş noktasını ASP.NET Web hizmeti istemcileriyle birlikte çalışabilir şekilde yapılandırmak için:  
  
- Hizmet <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> bitiş noktanız için bağlama türü olarak türü kullanın.  
  
- Hizmet bitiş noktanızda geri arama ve oturum sözleşmesi özelliklerini veya işlem davranışlarını kullanmayın  
  
Bağlamada HTTPS ve aktarım düzeyinde istemci kimlik doğrulaması için isteğe bağlı olarak destek etkinleştirebilirsiniz.  
  
<xref:System.ServiceModel.BasicHttpBinding> Sınıfın aşağıdaki özellikleri WS-I Temel Profil 1.1'in ötesinde işlevsellik gerektirir:  
  
- İleti Aktarım Optimizasyonu Mekanizması (MTOM) ileti <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> kodlama özelliği tarafından denetlendi. MTOM'u kullanmamak için <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> bu özelliği varsayılan değerine bırakın.  
  
- <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> Değer tarafından denetlenen ileti güvenliği, WS-I Temel Güvenlik Profili 1.0 ile uyumlu WS-Security desteği sağlar. WS-Security'yi kullanmamak için <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> bu özelliği varsayılan değerine bırakın.  
  
Bir WCF hizmetinin meta verilerini ASP.NET kullanılabilir hale getirmek için Web hizmeti istemci oluşturma araçlarını kullanın: [Web Hizmetleri Açıklama Dil Aracı (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29)Web Hizmetleri Bulma Aracı [(Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)ve Visual Studio'da **Web Başvuru Ekle** özelliği. Meta veri yayımı etkinleştirin. Daha fazla bilgi için meta [veri uçlarını yayımlama](publishing-metadata-endpoints.md)bölümüne bakın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod, kod halinde ASP.NET Web hizmeti istemcisiyle ve alternatif olarak bir yapılandırma dosyasında uyumlu bir WCF bitiş noktasının nasıl ekleyeceğini gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik](./feature-details/interop-with-aspnet-web-services.md)
