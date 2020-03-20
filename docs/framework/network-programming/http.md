---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048006"
---
# <a name="http"></a>HTTP
.NET Framework, tüm Internet trafiğinin <xref:System.Net.HttpWebRequest> çoğunluğunu oluşturan HTTP protokolü için kapsamlı <xref:System.Net.HttpWebResponse> bir destek sağlar. Statik yöntem <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" ile başlayan bir URI ile karşılaştığında, türetilen ve ,, varsayılan olarak döndürülen bu sınıflar. Çoğu durumda, **Webİstek** ve **WebResponse** sınıfları isteği gerçekleştirmek için gerekli olan her şeyi sağlar, ancak özellikleri olarak açığa çıkarılan HTTP'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** veya **HttpWebResponse**adresine yazabilirsiniz.  
  
 **HttpWebRequest** ve **HttpWebResponse** standart bir HTTP istek ve yanıt hareketi kapsüllemek ve ortak HTTP üstbilgi erişim sağlar. Bu sınıflar ayrıca pipelining, yığınlar halinde veri gönderme ve alma, kimlik doğrulama, ön authentication, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini destekler. Özellikler aracılığıyla sağlanmayan özel üstbilgi ve üstbilgi **üstbilgi** üstbilgi özelliği nden depolanabilir ve erişilebilir.  
  
 **HttpWebRequest,** **WebRequest** tarafından kullanılan varsayılan sınıftır ve Bir URI'yi **WebRequest.Create** yöntemine geçirmeden önce kaydedilmesi gerekmez.  
  
 <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> Uygulamanızın, özelliği **doğru** (varsayılan) olarak ayarlayarak HTTP yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz. Uygulama istekleri yeniden yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği isteğe yanıt veren gerçek Web kaynağını içerir. **AllowAutoRedirect'i** **false**olarak ayarlarsanız, uygulamanız yönlendirmeleri HTTP iletişim kuralı hataları olarak işleyebilir.  
  
 Uygulamalar için <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> ayarlanmış bir yakalayarak HTTP <xref:System.Net.WebExceptionStatus>protokol hataları alırsınız. Özellik, <xref:System.Net.WebException.Response%2A> sunucu tarafından gönderilen **WebYanıt'ı** içerir ve karşılaşılan gerçek HTTP hatasını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim](how-to-access-http-specific-properties.md)
