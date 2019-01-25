---
title: System.Net sınıfları için en iyi uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 0ed97626d86b380565453191f7840c1d1a180dfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689084"
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net sınıfları için en iyi uygulamalar
Aşağıdaki öneriler içinde bulunan sınıfları kullanmanıza yardımcı olacak <xref:System.Net> en iyi kendi lehlerine için:  
  
-   Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler için bkz: [Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler .NET Framework ile](tls.md).

-   Kullanım <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> mümkün olduğunda yerine alt sınıflar için tür atama. Kullanan uygulamalar **WebRequest** ve **WebResponse** yeni Internet protokollerinden kapsamlı bir kod değişikliği gerekmeden yararlanabilirsiniz.  
  
-   Kullanarak sunucu üzerinde çalışan ASP.NET uygulamaları yazarken **System.Net** sınıfları, genellikle zaman uyumsuz yöntemler için kullanılacak bir performans açısından iyi <xref:System.Net.WebRequest.GetResponse%2A> ve <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Bir Internet kaynağına için açılan bağlantılar sayısı, ağ performansını ve aktarım hızı üzerinde önemli bir etkisi olabilir. **System.Net** varsayılan olarak konak başına uygulama başına iki bağlantı kullanır. Ayarı <xref:System.Net.ServicePoint.ConnectionLimit%2A> özelliğinde <xref:System.Net.ServicePoint> için uygulamanızı belirli bir ana bilgisayar için bu sayıyı artırabilirsiniz. Ayarı <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> özelliği, tüm konaklar için bu varsayılan artırabilirsiniz.  
  
-   Yuva düzeyi protokolleri yazarken kullanmaya çalıştığınızda <xref:System.Net.Sockets.TcpClient> veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunda doğrudan yazmak yerine bir <xref:System.Net.Sockets.Socket>. Bu iki istemci sınıfları bağlantı ayrıntılarını işlemek gerek kalmadan TCP ve UDP yuva oluşturulmasını kapsüller.  
  
-   Kimlik bilgileri gerektiren siteleri erişirken <xref:System.Net.CredentialCache> bunları her istekle sağlama yerine kimlik bilgileri önbellek oluşturmak için sınıf. **CredentialCache** sınıfı önbellek oluşturma ve sunma URL'sini temel alarak kimlik bilgileri sorumluluğu, yoğun bir istekle sunmak için uygun kimlik bilgilerini bulmak için arama yapar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)
