---
title: DOM Namespace desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e91ce2b36462780925dcaef701583a966c5f59b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569457"
---
# <a name="namespace-support-in-the-dom"></a>DOM Namespace desteği
XML belge nesne modeli (DOM) ad alanı tamamen uyumlu. Yalnızca ad alanı algılayan XML belgelerini desteklenir. World Wide Web Konsorsiyumu (W3C) Düzey 1 uygulamak DOM uygulamaları ad alanı kullanmayan olabilir ve DOM Düzey 2 özellikleri ad alanı algılayan belirtir. Ancak, XML DOM'ındaki tüm özelliklere ad alanı algılayan, yöntem düzey 1 veya Düzey 2 DOM öneri ise bakılmaksızın değildir.  
  
 Örneğin, bir ad alanı kullanmayan ayarı içinde çağırma `setAttribute("A:b", "123")`, düzey 1 öneri DOM belirtildiği gibi bir öznitelikte öneki olan sonuçlanmaz `A` ve yerel adını `b`. Bir öznitelik değeri ile neden olacağından `A:b`.  
  
 DOM Düzey 2 çağrısı ad alanı kullanan bir ortamda `setAttribute("A:b", "123")` önekine sahip bir öznitelik sonuçlanıyor `A` ve yerel adını `b`. Microsoft .NET Framework DOM nasıl çalıştığını budur.  
  
 Bu nedenle, adı bir parametre alan tüm yöntemleri için bu yöntemleri adı nitelemek için bir önek de olur. Name parametresi gibi `A:b` içinde **setAttribute** DOM düzey 1 yöntemi, aşağıdaki gibi Ayrıştırılan:  
  
-   Hayır iki nokta üst üste (:) karakterler sonra yerel ad kümesine `name` parametresi, önek ve namespaceURI boş dizeler taşımaktadır.  
  
-   İki nokta bulunursa, adı ilk iki nokta karakteri konumuna bağlı iki parçalara bölünür. Önek dizesi iki nokta üst üste önce bulunamadı ayarlanır ve yerel ad sonra iki nokta üst üste bulunan dizeye ayarlayın. NamespaceURI değeri namespaceURI ediyorsa ve kalır almayan yöntemleri için boş dize olarak ayarlayın. Aksi takdirde namespaceURI yönteme geçirilen dize ayarlanır. Önek tanımsızsa sonra **kaydetmek** yöntemi ve **InnerXml** ve **OuterXml** özellikleri başarısız olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
