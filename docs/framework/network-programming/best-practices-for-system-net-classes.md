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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048888"
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net Sınıfları için En İyi Yöntemler
Aşağıdaki öneriler, ' de <xref:System.Net> bulunan sınıfları en iyi avantajları ile kullanmanıza yardımcı olur:  
  
- Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları için bkz. [.NET Framework Ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](tls.md).

- Alt <xref:System.Net.WebRequest> sınıflara <xref:System.Net.WebResponse> tür atama yapmak yerine ve mümkün olan her seferinde kullanın. **WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek duymadan yeni Internet protokollerinden yararlanabilir.  
  
- **System.net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, bir performans açısından, ve <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A>için zaman uyumsuz yöntemleri kullanmak genellikle daha iyidir.  
  
- Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimlilik üzerinde önemli bir etkiye sahip olabilir. **System.net** , varsayılan olarak her konak için uygulama başına iki bağlantı kullanır. Uygulamanız için içindeki <xref:System.Net.ServicePoint> özelliğinin ayarlanması, belirli bir konak için bu sayıyı artırabilir. <xref:System.Net.ServicePoint.ConnectionLimit%2A> Özelliği ayarlamak <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> , tüm konaklar için bu varsayılanı artırabilir.  
  
- Yuva düzeyi protokoller yazarken, ' a <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.Socket>doğrudan yazmak yerine veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunca kullanmayı deneyin. Bu iki istemci sınıfı, bağlantının ayrıntılarını işleyebilmeniz gerekmeden TCP ve UDP yuvaları oluşturmayı kapsüller.  
  
- Kimlik bilgileri gerektiren sitelere erişirken, her istekte bunları <xref:System.Net.CredentialCache> sağlamak yerine, kimlik bilgilerinin bir önbelleğini oluşturmak için sınıfını kullanın. **CredentialCache** sınıfı, bir istekle birlikte sunmak üzere uygun kimlik bilgisini bulmak için önbelleği arar, bu da URL 'ye göre kimlik bilgileri oluşturma ve sunma sorumluluğunu ortadan kaldırmak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ Programlaması](index.md)
