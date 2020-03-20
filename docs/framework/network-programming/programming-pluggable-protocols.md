---
title: Takılabilir Protokoller Programlama
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
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047394"
---
# <a name="programming-pluggable-protocols"></a>Takılabilir Protokoller Programlama
Soyut <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar takılabilir protokoller için temel sağlar. Bir uygulama, protokole özgü <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>sınıfları bir Internet kaynağından veri isteyebilir ve kullanılan protokolü belirtmeden yanıtı okuyabilir.  
  
 Protokole özgü <xref:System.Net.WebRequest>bir yöntem oluşturmadan önce, oluştur yöntemini kaydetmeniz gerekir. Belirli bir <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> Internet <xref:System.Net.WebRequest> düzenine, bir düzene ve sunucuya veya bir şemaya, sunucuya ve yola bir dizi isteği işlemek için bir soyundan geleni <xref:System.Net.WebRequest> kaydetmek için statik yöntemi kullanın.  
  
 Çoğu <xref:System.Net.WebRequest> durumda, sınıfın yöntemlerini ve özelliklerini kullanarak veri gönderip alabilirsiniz. Ancak, protokole özgü özelliklere erişmeniz gerekiyorsa, <xref:System.Net.WebRequest> a'dan türemiş sınıf örneğine dakti-resmon yazabilirsiniz.  
  
 Takılabilir protokollerden yararlanmak için, <xref:System.Net.WebRequest> torunlarınızın protokole özgü özelliklerin ayarlanmasını gerektirmeyen varsayılan istek ve yanıt hareketi sağlaması gerekir. Örneğin, HTTP <xref:System.Net.HttpWebRequest> <xref:System.Net.WebRequest> için sınıfı uygulayan sınıf varsayılan olarak `GET` bir istek sağlar <xref:System.Net.HttpWebResponse> ve Web sunucusundan döndürülen akışı içeren bir istek verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WebRequest’ten Türetme](deriving-from-webrequest.md)
- [WebResponse’tan Türetme](deriving-from-webresponse.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
