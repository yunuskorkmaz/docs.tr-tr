---
title: DOM Ad Alanı Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a468d1a2b15d1f92726d8d429fbc5ddece96e6d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647855"
---
# <a name="namespace-support-in-the-dom"></a>DOM Ad Alanı Desteği
XML belge nesne modeli (DOM) ad alanı tamamen uyumlu. Yalnızca ad alanı algılayan XML belgeler desteklenir. World Wide Web Consortium (W3C) Düzey 1 uygulayan DOM uygulamalar ad alanı kullanmayan ve DOM Düzey 2 özellikleri kullanan ad alanı belirtir. Ancak, tüm özellikler XML DOM ad alanı kullanan, yöntem düzey 1 veya Düzey 2 DOM öneri ise bağımsız olarak uygulanır.  
  
 Örneğin, bir ad alanı kullanmayan ayarı, çağırma `setAttribute("A:b", "123")`, DOM belirtildiği gibi 1 öneri düzeyi, bir öznitelik öneki olan sonuçlanmaz `A` ve yerel adı `b`. Bir öznitelik değeri neden olacağından `A:b`.  
  
 DOM Düzey 2 çağrısı ad alanı kullanan bir ortamda `setAttribute("A:b", "123")` önekine sahip bir öznitelik sonuçlanıyor `A` ve yerel adı `b`. Microsoft .NET Framework DOM nasıl çalıştığını budur.  
  
 Bu nedenle, adı parametre almaz tüm yöntemleri için bu yöntemleri adı nitelemek için bir önek da alır. Name parametresi gibi `A:b` içinde **setAttribute** DOM düzey 1 yöntemi şu şekilde ayrıştırılır:  
  
- Hayır iki nokta üst üste (:) karakterler sonra yerel adı kümesine `name` parametre öneki 've NamespaceURI olan boş dize.  
  
- Bir iki nokta üst üste bulunursa, adı, ilk iki nokta üst üste karakterini konumuna bağlı olarak iki parçalara bölünür. Önek bulunan iki noktadan önce bir dizeye ayarlanır ve yerel adı iki nokta üst üste sonra bulunan dizeye ayarlanır. Bir namespaceURI değer namespaceURI çözümlenirse ve kalan almayan yöntemler için boş dize olarak ayarlayın. Aksi takdirde namespaceURI yönteme geçirilen dize ayarlanır. Önek tanımlanmamışsa, ardından **Kaydet** yöntemi ve **sınıfının InnerXml** ve **OuterXml** özellikleri başarısız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
