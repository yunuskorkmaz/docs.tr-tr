---
title: Takılabilir protokoller programlama
ms.date: 03/30/2017
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
ms.openlocfilehash: 74dd44e704836b209366a7975d08a43375318e90
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190794"
---
# <a name="programming-pluggable-protocols"></a>Takılabilir protokoller programlama
Özet <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları, takılabilir protokolleri temel sağlar. Protokole özgü sınıflarından türetme tarafından <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>, bir uygulama bir Internet kaynağından veri istek ve yanıt kullanılan protokol belirtmeden okuyun.  
  
 Bir protokole özgü oluşturabilmeniz için önce <xref:System.Net.WebRequest>, kendi Create yöntemini kaydetmeniz gerekir. Statik <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> yöntemi <xref:System.Net.WebRequest> kaydetmek için bir <xref:System.Net.WebRequest> istekleri belirli bir Internet düzeni, bir şema ve sunucu için veya bir şema, sunucu ve yol için bir dizi işlemek için alt.  
  
 Çoğu durumda, yöntemlerini ve özelliklerini kullanarak veri göndermek ve almak mümkün olmayacak <xref:System.Net.WebRequest> sınıfı. Ancak, protokole özgü özelliklere erişmek gereksinim duyarsanız, türü atayarak bir <xref:System.Net.WebRequest> belirli bir türetilmiş sınıf örneği.  
  
 Takılabilir protokoller yararlanmak için <xref:System.Net.WebRequest> alt öğeleri ayarlamak için protokole özgü özellikleri gerektirmeyen varsayılan bir istek ve yanıt işlem sağlamalıdır. Örneğin, <xref:System.Net.HttpWebRequest> sınıfını <xref:System.Net.WebRequest> sağlar, HTTP için sınıf bir `GET` isteği varsayılan ve döndürür bir <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akış içeriyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WebRequest’ten Türetme](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [WebResponse’tan Türetme](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)  
 [Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
