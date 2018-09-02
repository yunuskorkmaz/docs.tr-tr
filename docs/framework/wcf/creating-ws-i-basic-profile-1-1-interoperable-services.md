---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 7d732f26f3f679d744f86863a13d1ca0d7c88819
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400696"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
Bir WCF Hizmeti uç noktası ile birlikte çalışabilir olacak şekilde yapılandırmak için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri:  
  
-   Kullanım <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü, hizmet uç noktası için bağlama türü olarak.  
  
-   Geri çağırma ve oturumu sözleşme özellikleri veya hareket davranışları, hizmet uç noktasında kullanmayın  
  
 İsteğe bağlı olarak, HTTPS ve bağlamadaki aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz.  
  
 Aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> sınıfı WS ötesine işlevselliği gerektiren-ı Basic Profile 1.1:  
  
-   İleti, ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama denetlenmektedir <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği. Bu özellik, kendi varsayılan değerde bırakın <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> MTOM kullanmayacak şekilde.  
  
-   İleti tarafından denetlenen güvenlik <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> değeri, WS ile uyumlu olan WS-güvenlik desteği sağlar-ı temel güvenlik profili 1.0. Bu özellik, kendi varsayılan değerde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> WS-Security kullanmayı.  
  
 Bir WCF hizmeti için meta veriler kullanılabilir hale getirmek için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Web hizmeti istemcisi oluşturma araçlarını kullanın: [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Hizmetleri bulma Aracı (Disco.exe)](https://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)ve `Add Web Reference` özellik Visual Studio'da; meta verileri yayını etkinleştirmeniz gerekir. Daha fazla bilgi için [meta veri uç noktalarını yayımlama](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod ile uyumlu bir WCF uç noktası ekleme gösterir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmet istemci kodu ve alternatif olarak, bir yapılandırma dosyası.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
