---
title: Takılabilir Protokoller Programlama
description: Soyut WebRequest ve WebResponse sınıflarının, bir uygulamanın protokol belirtmeden veri almasını sağlayan takılabilir protokolleri nasıl desteklediğini öğrenin.
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
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502203"
---
# <a name="programming-pluggable-protocols"></a>Takılabilir Protokoller Programlama
Soyut <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar takılabilir protokoller için temel sağlar. Ve ' den protokolüne özgü sınıfları türeterek <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> , bir uygulama bir Internet kaynağından veri talep edebilir ve kullanılan protokolü belirtmeden yanıtı okuyabilir.  
  
 Protokolüne özgü bir oluşturabilmeniz için önce <xref:System.Net.WebRequest> Create yöntemini kaydetmeniz gerekir. <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> <xref:System.Net.WebRequest> Belirli bir Internet şemasına, bir düzene ve sunucuya ya da bir düzen, sunucu ve yol için bir istek kümesini işlemek üzere bir alt öğesi kaydetmek için ' ın statik metodunu kullanın.  
  
 Çoğu durumda, sınıfının yöntemlerini ve özelliklerini kullanarak veri gönderebileceksiniz ve alabilirsiniz <xref:System.Net.WebRequest> . Ancak, protokole özgü özelliklere erişmeniz gerekiyorsa, a 'yı <xref:System.Net.WebRequest> belirli bir türetilmiş sınıf örneğine yazabilirsiniz.  
  
 Takılabilir protokollerinden yararlanmak için, alt bilgileriniz, <xref:System.Net.WebRequest> protokole özgü özelliklerin ayarlanmasına gerek olmayan varsayılan bir istek-yanıt işlemi sağlamalıdır. Örneğin, <xref:System.Net.HttpWebRequest> <xref:System.Net.WebRequest> http için sınıfını uygulayan sınıfı, `GET` Varsayılan olarak bir Istek sağlar ve <xref:System.Net.HttpWebResponse> Web sunucusundan döndürülen akışı içeren bir döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WebRequest’ten Türetme](deriving-from-webrequest.md)
- [WebResponse’tan Türetme](deriving-from-webresponse.md)
- [.NET Framework'te Ağ Programlaması](index.md)
- [Nasıl yapılır: WebRequest Türü Atayarak Protokole Özgü Özelliklere Erişim](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
