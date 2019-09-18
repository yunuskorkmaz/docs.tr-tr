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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048006"
---
# <a name="http"></a>HTTP
.NET Framework, <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıflarının yanı sıra tüm Internet trafiğinin çoğunu oluşturan http protokolü için kapsamlı destek sağlar. Ve <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> ' den türetilen bu sınıflar, statik yöntem "http" veya "https" ile başlayan bir URI ile karşılaştığında varsayılan olarak döndürülür. <xref:System.Net.WebResponse> Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellikler olarak sunulan http 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** 'e yazabilirsiniz veya **HttpWebResponse**.  
  
 **HttpWebRequest** ve **HttpWebResponse** standart bir http isteği-ve-yanıt işlemini kapsülle ve ortak http üst bilgilerine erişim sağlar. Bu sınıflar, ardışık düzen oluşturma, verileri parçalara gönderme ve alma, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere HTTP 1,1 özelliklerinin çoğunu da destekler. Özellikler aracılığıyla sağlanmayan özel üstbilgiler ve üstbilgiler içinde depolanabilir ve **üstbilgiler** özelliği aracılığıyla erişilebilir.  
  
 **HttpWebRequest** **WebRequest** tarafından kullanılan varsayılan sınıftır ve **WebRequest. Create** yöntemine bir URI geçirebilmeniz için önce kaydedilmesi gerekmez.  
  
 <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> Özelliği **true** (varsayılan) olarak ayarlayarak uygulamanızın http yeniden yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz. Uygulama istekleri yeniden yönlendirecektir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği, isteğe yanıt veren gerçek Web kaynağını içerir. **Allowoto yeniden yönlendirme** 'yi **false**olarak ayarlarsanız uygulamanız http protokol hataları olarak yeniden yönlendirmeyi işleyebilmelidir.  
  
 Uygulamalar, <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> kümesi ilebirilebirleştirerekhttpprotokolhatalarıalır.<xref:System.Net.WebExceptionStatus> Özelliği, sunucu tarafından gönderilen WebResponse 'u içerir ve karşılaşılan gerçek http hatası olduğunu gösterir. <xref:System.Net.WebException.Response%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Nasıl yapılır: HTTP 'e özgü özelliklere erişin](how-to-access-http-specific-properties.md)
