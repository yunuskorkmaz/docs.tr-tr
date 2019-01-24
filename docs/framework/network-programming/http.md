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
ms.openlocfilehash: c0c8bcca55dc54b2dd89be2e45dade4d09a67362
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574137"
---
# <a name="http"></a>HTTP
.NET Framework ile tüm Internet trafiği, çoğu yapar HTTP protokolü için kapsamlı destek sağlar. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıfları. Bu sınıflar türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, varsayılan olarak döndürülen her statik yöntem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> URI başlayan bir "http" veya "https" ile karşılaşır. Çoğu durumda **WebRequest** ve **WebResponse** sınıfları sağlar, tüm istek yapmak gerekli olduğu, ancak özellik olarak kullanıma HTTP'ye özgü özelliklere erişim gerekiyorsa, türü atayarak Bu sınıfa **HttpWebRequest** veya **HttpWebResponse**.  
  
 **HttpWebRequest** ve **HttpWebResponse** standart bir HTTP istek ve yanıt hareket halinde kapsüller ve ortak HTTP üst bilgilerine erişim sağlar. Bu sınıfların ardışık düzen, veri gönderip öbekleri, kimlik doğrulaması, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifika doğrulaması ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini de destekler. Özel üst bilgiler özellikleri aracılığıyla sağlanmayan üst bilgiler depolanır ve aracılığıyla erişilen **üstbilgileri** özelliği.  
  
 **HttpWebRequest** tarafından kullanılan varsayılan sınıf **WebRequest** ve bir URI geçirebilirsiniz önce kayıtlı olması gerekmez **WebRequest.Create** yöntemi.  
  
 HTTP yeniden yönlendirmelerini otomatik olarak ayarlayarak izleyin, uygulamanızın yapabileceğiniz <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> özelliğini **true** (varsayılan). Uygulama istekleri yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> özelliği **HttpWebResponse** isteğine yanıt olarak verilen gerçek bir Web kaynağı içerir. Ayarlarsanız **AllowAutoRedirect** için **false**, uygulamanızı yeniden yönlendirmeleri işleyebilen HTTP protokolü hata olarak.  
  
 Uygulamaları, yakalama tarafından HTTP protokolü hataları alan bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> kümesine <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Özelliği içeren **WebResponse** sunucu tarafından gönderilen ve karşılaşılan gerçek HTTP hata gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
- [Nasıl yapılır: HTTP'ye özgü özelliklere erişim](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
