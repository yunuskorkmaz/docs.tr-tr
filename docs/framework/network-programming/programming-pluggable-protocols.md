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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047394"
---
# <a name="programming-pluggable-protocols"></a>Takılabilir Protokoller Programlama
Soyut <xref:System.Net.WebRequest> ve<xref:System.Net.WebResponse> sınıflar takılabilir protokoller için temel sağlar. <xref:System.Net.WebRequest> Ve<xref:System.Net.WebResponse>' den protokolüne özgü sınıfları türeterek, bir uygulama bir Internet kaynağından veri talep edebilir ve kullanılan protokolü belirtmeden yanıtı okuyabilir.  
  
 Protokolüne özgü <xref:System.Net.WebRequest>bir oluşturabilmeniz için önce Create yöntemini kaydetmeniz gerekir. Belirli bir Internet <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> şemasına, bir düzene ve <xref:System.Net.WebRequest> sunucuya ya da bir düzen, sunucu ve yol için bir istek kümesini işlemek üzere bir alt öğesi kaydetmek için ' ın <xref:System.Net.WebRequest> statik metodunu kullanın.  
  
 Çoğu durumda, <xref:System.Net.WebRequest> sınıfının yöntemlerini ve özelliklerini kullanarak veri gönderebileceksiniz ve alabilirsiniz. Ancak, protokole özgü özelliklere erişmeniz gerekiyorsa, a <xref:System.Net.WebRequest> 'yı belirli bir türetilmiş sınıf örneğine yazabilirsiniz.  
  
 Takılabilir protokollerinden yararlanmak için, alt bilgileriniz <xref:System.Net.WebRequest> , protokole özgü özelliklerin ayarlanmasına gerek olmayan varsayılan bir istek-yanıt işlemi sağlamalıdır. Örneğin, <xref:System.Net.HttpWebRequest> http için <xref:System.Net.WebRequest> sınıfını uygulayan sınıfı, varsayılan olarak bir `GET` istek sağlar ve Web sunucusundan döndürülen akışı içeren bir <xref:System.Net.HttpWebResponse> döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WebRequest’ten Türetme](deriving-from-webrequest.md)
- [WebResponse’tan Türetme](deriving-from-webresponse.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Nasıl yapılır: Web Isteği protokolüne özgü özelliklere erişim için tür dönüştürme](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
