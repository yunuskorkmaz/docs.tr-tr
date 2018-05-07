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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ed61a8addd204320560c773e917613c52e56bff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="http"></a>HTTP
.NET Framework ile tüm Internet trafiğini çoğunluğu yapar HTTP protokolü için kapsamlı destek sağlar. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıfları. Bu sınıfların türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, varsayılan olarak döndürülen her statik yöntemi <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" ile başlayan bir URI karşılaşır. Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları sağlar, tüm istek yapılması gerekmez, ancak özellikleri olarak sunulan HTTP özgü özellikler erişmesi gerekiyorsa typecast Bu sınıfların **HttpWebRequest** veya **HttpWebResponse**.  
  
 **HttpWebRequest** ve **HttpWebResponse** bir standart HTTP istek ve yanıt işlem kapsüllemek ve ortak HTTP üst bilgilerini erişim sağlar. Bu sınıfları, ardışık düzen oluşturma, veri gönderip öbekleri, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifika doğrulaması ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini de destekler. Özel üstbilgi ve özellikleri yoluyla sağlanmayan üstbilgileri içinde depolanabilir ve üzerinden erişilen **üstbilgileri** özelliği.  
  
 **HttpWebRequest** tarafından kullanılan varsayılan sınıfı **WebRequest** ve URI'yı geçirmeden önce kaydedilmesi gerekmez **WebRequest.Create** yöntemi.  
  
 HTTP yeniden yönlendirmeler otomatik olarak ayarlayarak izleyin, uygulamanızın yapabileceğiniz <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> özelliğine **true** (varsayılan). Uygulama istekleri yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> özelliği **HttpWebResponse** isteğine yanıt gerçek Web kaynağına içerecektir. Ayarlarsanız **AllowAutoRedirect** için **yanlış**, uygulamanızın yeniden yönlendirmeleri işleyebilen HTTP protokolü hata olarak.  
  
 Uygulamaları alma HTTP protokolü hatalarının yakalama tarafından bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> kümesine <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Özelliği içeren **WebResponse** sunucu tarafından gönderilen ve karşılaşılan gerçek HTTP hata gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Nasıl yapılır: HTTP’ye Özgü Özelliklere Erişim](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
