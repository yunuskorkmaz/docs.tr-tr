---
title: System.Net Sınıfları için En İyi Yöntemler
description: System.Net ' de bulunan sınıfları .NET Framework programlamada en iyi şekilde kullanmak için bu önerileri izleyin.
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
ms.openlocfilehash: 583fa5e57c7c4d60252dddfd425596e7acad7c0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502684"
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net Sınıfları için En İyi Yöntemler
Aşağıdaki öneriler, ' de bulunan sınıfları <xref:System.Net> en iyi avantajları ile kullanmanıza yardımcı olur:  
  
- Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları için bkz. [.NET Framework Ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](tls.md).

- Alt <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> sınıflara tür atama yapmak yerine ve mümkün olan her seferinde kullanın. **WebRequest** ve **WebResponse** kullanan uygulamalar, kapsamlı kod değişikliklerine gerek duymadan yeni Internet protokollerinden yararlanabilir.  
  
- **System.net** sınıflarını kullanarak bir sunucuda çalışan ASP.NET uygulamaları yazarken, bir performans açısından, ve için zaman uyumsuz yöntemleri kullanmak genellikle daha iyidir <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A> .  
  
- Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimlilik üzerinde önemli bir etkiye sahip olabilir. **System.net** , varsayılan olarak her konak için uygulama başına iki bağlantı kullanır. <xref:System.Net.ServicePoint.ConnectionLimit%2A>Uygulamanız için içindeki özelliğinin ayarlanması, <xref:System.Net.ServicePoint> belirli bir konak için bu sayıyı artırabilir. Özelliği ayarlamak, <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> tüm konaklar için bu varsayılanı artırabilir.  
  
- Yuva düzeyi protokoller yazarken, ' <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.UdpClient> a doğrudan yazmak yerine veya mümkün olduğunca kullanmayı deneyin <xref:System.Net.Sockets.Socket> . Bu iki istemci sınıfı, bağlantının ayrıntılarını işleyebilmeniz gerekmeden TCP ve UDP yuvaları oluşturmayı kapsüller.  
  
- Kimlik bilgileri gerektiren sitelere erişirken, <xref:System.Net.CredentialCache> her istekte bunları sağlamak yerine, kimlik bilgilerinin bir önbelleğini oluşturmak için sınıfını kullanın. **CredentialCache** sınıfı, bir istekle birlikte sunmak üzere uygun kimlik bilgisini bulmak için önbelleği arar, bu da URL 'ye göre kimlik bilgileri oluşturma ve sunma sorumluluğunu ortadan kaldırmak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ Programlaması](index.md)
