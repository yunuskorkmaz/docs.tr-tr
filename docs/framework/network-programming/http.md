---
title: HTTP
description: .NET Framework HttpWebRequest ve HttpWebResponse sınıflarını kullanarak sağladığı HTTP için kapsamlı destek hakkında bilgi edinin.
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
ms.openlocfilehash: ffb7a5d027ef7691d03caf0ac45d4a3dd9bdb652
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502424"
---
# <a name="http"></a>HTTP
.NET Framework, ve sınıflarının yanı sıra tüm Internet trafiğinin çoğunu oluşturan HTTP protokolü için kapsamlı destek sağlar <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> . Ve ' den türetilen bu sınıflar, <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> statik yöntem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" Ile başlayan bir URI ile karşılaştığında varsayılan olarak döndürülür. Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları isteği yapmak için gereken tüm öğeleri sağlar, ancak özellikler olarak sunulan http 'ye özgü özelliklere erişmeniz gerekiyorsa, bu sınıfları **HttpWebRequest** veya **HttpWebResponse**olarak yazabilirsiniz.  
  
 **HttpWebRequest** ve **HttpWebResponse** standart bir http isteği-ve-yanıt işlemini kapsülle ve ortak http üst bilgilerine erişim sağlar. Bu sınıflar, ardışık düzen oluşturma, verileri parçalara gönderme ve alma, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifikası doğrulama ve bağlantı yönetimi dahil olmak üzere HTTP 1,1 özelliklerinin çoğunu da destekler. Özellikler aracılığıyla sağlanmayan özel üstbilgiler ve üstbilgiler içinde depolanabilir ve **üstbilgiler** özelliği aracılığıyla erişilebilir.  
  
 **HttpWebRequest** **WebRequest** tarafından kullanılan varsayılan sınıftır ve **WebRequest. Create** yöntemine bir URI geçirebilmeniz için önce kaydedilmesi gerekmez.  
  
 <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A>Özelliği **true** (varsayılan) olarak ayarlayarak uygulamanızın http yeniden yönlendirmelerini otomatik olarak izlemesini sağlayabilirsiniz. Uygulama istekleri yeniden yönlendirecektir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> **HttpWebResponse** özelliği, isteğe yanıt veren gerçek Web kaynağını içerir. **Allowoto yeniden yönlendirme** 'yi **false**olarak ayarlarsanız uygulamanız http protokol hataları olarak yeniden yönlendirmeyi işleyebilmelidir.  
  
 Uygulamalar, kümesi ile bir ile birleştirerek HTTP protokol hataları alır <xref:System.Net.WebException> <xref:System.Net.WebException.Status%2A> <xref:System.Net.WebExceptionStatus> . <xref:System.Net.WebException.Response%2A>Özelliği, sunucu tarafından gönderilen **WebResponse** 'u içerir ve karşılaşılan gerçek http hatası olduğunu gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ara Sunucu Üzerinden İnternet Erişimi](accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
- [Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim](how-to-access-http-specific-properties.md)
