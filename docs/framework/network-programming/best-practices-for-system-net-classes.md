---
title: System.Net Sınıfları için En İyi Yöntemler
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
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048888"
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net Sınıfları için En İyi Yöntemler
Aşağıdaki öneriler, içinde bulunan sınıfları <xref:System.Net> en iyi şekilde kullanmanıza yardımcı olacaktır:  
  
- Aktarım Katmanı Güvenliği (TLS) için en iyi uygulamalar için [,.NET Framework ile Taşıma Katmanı Güvenliği (TLS) en iyi uygulamalarına](tls.md)bakın.

- Soyundan <xref:System.Net.WebResponse> gelen sınıflara yazı dökümü yerine mümkün olduğunca kullanın. <xref:System.Net.WebRequest> **WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek kalmadan yeni Internet protokollerinden yararlanabilir.  
  
- **System.Net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, performans açısından, asynchronous yöntemlerini <xref:System.Net.WebRequest.GetResponse%2A> kullanmak <xref:System.Net.WebResponse.GetResponseStream%2A>genellikle daha iyidir.  
  
- Bir Internet kaynağına açılan bağlantı sayısının ağ performansı ve iş bölümü üzerinde önemli bir etkisi olabilir. **System.Net** varsayılan olarak ana bilgisayar başına uygulama başına iki bağlantı kullanır. Uygulamanız <xref:System.Net.ServicePoint.ConnectionLimit%2A> <xref:System.Net.ServicePoint> için özelliği ayarlamak, belirli bir ana bilgisayar için bu sayıyı artırabilir. Özelliği <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> ayarlamak, tüm ana bilgisayarlar için bu varsayılanı artırabilir.  
  
- Soket düzeyinde protokoller yazarken, <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.UdpClient> doğrudan bir <xref:System.Net.Sockets.Socket>' ye yazmak yerine veya mümkün olduğunda kullanmaya çalışın. Bu iki istemci sınıfı, bağlantının ayrıntılarını işlemenizi gerektirmeden TCP ve UDP soketlerinin oluşturulmasını kapsüller.  
  
- Kimlik bilgileri gerektiren sitelere erişirken, her isteği sağlamak yerine bir kimlik önbelleği oluşturmak için <xref:System.Net.CredentialCache> sınıfı kullanın. **Kimlik BilgisiÖnbellek** sınıfı, bir isteksunmak için uygun kimlik bilgilerini bulmak için önbelleği arar ve URL'ye dayalı kimlik bilgileri oluşturma ve sunma sorumluluğunuzdan sizi rahatlatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ Programlaması](index.md)
