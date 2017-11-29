---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 701ff252380ef93dbe3668c8aca73f08a8425d6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="http"></a>HTTP
.NET Framework ile tüm Internet trafiğini çoğunluğu yapar HTTP protokolü için kapsamlı destek sağlar. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.HttpWebResponse> sınıfları. Bu sınıfların türetilen <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, varsayılan olarak döndürülen her statik yöntemi <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> "http" veya "https" ile başlayan bir URI karşılaşır. Çoğu durumda, **WebRequest** ve **WebResponse** sınıfları sağlar, tüm istek yapılması gerekmez, ancak özellikleri olarak sunulan HTTP özgü özellikler erişmesi gerekiyorsa typecast Bu sınıfların **HttpWebRequest** veya **HttpWebResponse**.  
  
 **HttpWebRequest** ve **HttpWebResponse** bir standart HTTP istek ve yanıt işlem kapsüllemek ve ortak HTTP üst bilgilerini erişim sağlar. Bu sınıfları, ardışık düzen oluşturma, veri gönderip öbekleri, kimlik doğrulama, ön kimlik doğrulama, şifreleme, proxy desteği, sunucu sertifika doğrulaması ve bağlantı yönetimi dahil olmak üzere çoğu HTTP 1.1 özelliklerini de destekler. Özel üstbilgi ve özellikleri yoluyla sağlanmayan üstbilgileri içinde depolanabilir ve üzerinden erişilen **üstbilgileri** özelliği.  
  
 **HttpWebRequest** tarafından kullanılan varsayılan sınıfı **WebRequest** ve URI'yı geçirmeden önce kaydedilmesi gerekmez **WebRequest.Create** yöntemi.  
  
 HTTP yeniden yönlendirmeler otomatik olarak ayarlayarak izleyin, uygulamanızın yapabileceğiniz <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> özelliğine **true** (varsayılan). Uygulama istekleri yönlendirir ve <xref:System.Net.HttpWebResponse.ResponseUri%2A> özelliği **HttpWebResponse** isteğine yanıt gerçek Web kaynağına içerecektir. Ayarlarsanız **AllowAutoRedirect** için **yanlış**, uygulamanızın yeniden yönlendirmeleri işleyebilen HTTP protokolü hata olarak.  
  
 Uygulamaları alma HTTP protokolü hatalarının yakalama tarafından bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> kümesine <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Özelliği içeren **WebResponse** sunucu tarafından gönderilen ve karşılaşılan gerçek HTTP hata gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Proxy üzerinden Internet erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Uygulama protokolleri kullanma](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Nasıl yapılır: erişim HTTP özgü özellikleri](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
