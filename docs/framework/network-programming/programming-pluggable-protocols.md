---
title: "Programlama takılabilir protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 51d9b6e444cfa49bfbf7854ee7f33f5a45d80e31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="programming-pluggable-protocols"></a>Programlama takılabilir protokolleri
Özet <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları takılabilir protokoller için temel sağlar. Protokole özgü sınıflarından türetme tarafından <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, bir uygulama bir Internet kaynağından veri istek ve yanıt kullanılan protokolü belirtmeden okuyun.  
  
 Bir protokole özgü oluşturabilmeniz için önce <xref:System.Net.WebRequest>, Create yöntemini kaydetmeniz gerekir. Statik kullanmak <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> yöntemi <xref:System.Net.WebRequest> kaydetmek için bir <xref:System.Net.WebRequest> isteklerini belirli bir Internet düzeni, bir şema ve sunucu için veya bir şema, sunucu ve yol için bir dizi işlemek için alt.  
  
 Çoğu durumda, özelliklerini ve yöntemlerini kullanarak veri gönderip kuramaz <xref:System.Net.WebRequest> sınıfı. Ancak, protokole özgü özellikleri erişmeniz gerekiyorsa, typecast bir <xref:System.Net.WebRequest> belirli türetilmiş sınıf örneğinin.  
  
 Takılabilir Protokol yararlanmak için <xref:System.Net.WebRequest> descendants ayarlanacak özellikler protokole özgü gerektirmeyen bir varsayılan istek ve yanıt işlem sağlamalıdır. Örneğin, <xref:System.Net.HttpWebRequest> sınıfı, hangi uygular <xref:System.Net.WebRequest> sınıfı için HTTP, sağlar bir `GET` varsayılan ve döndürür isteğiyle bir <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akış içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WebRequest türetme](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [WebResponse türetme](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [.NET Framework'te ağ programlaması](../../../docs/framework/network-programming/index.md)  
 [Nasıl yapılır: bir WebRequest erişim protokolü belirli özellikleri için Typecast](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
