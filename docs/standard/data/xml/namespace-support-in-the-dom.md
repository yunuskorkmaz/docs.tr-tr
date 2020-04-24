---
title: DOM Ad Alanı Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
ms.openlocfilehash: 7efe03f25fde0681ebd9e3c7c8ea81f6686a8ec1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710615"
---
# <a name="namespace-support-in-the-dom"></a>DOM Ad Alanı Desteği
XML Belge Nesne Modeli (DOM) tamamen ad alanı farkındır. Yalnızca ad alanı algılayan XML belgeleri desteklenir. World Wide Web Konsorsiyumu (W3C), düzey 1 ' i uygulayan DOM uygulamalarının ad alanı kullanmayan ve DOM düzeyi 2 özelliklerinin ad alanı duyarlı olduğunu belirtir. Ancak, yöntemin düzey 1 veya düzey 2 DOM önermesinden bağımsız olarak, XML DOM 'daki tüm özellikler ad alanı farkındır.  
  
 Örneğin, ad alanı kullanmayan bir ayarda, DOM düzey 1 Önerinde `setAttribute("A:b", "123")`belirtildiği gibi çağırmak, öneki `A` ve yerel adı olan bir öznitelik ile sonuçlanmaz `b`. Bu, değerine `A:b`sahip bir özniteliğe neden olur.  
  
 Ad alanı kullanan bir ortamda, DOM düzey 2 `setAttribute("A:b", "123")` ' ye yapılan çağrı, öneki `A` ve yerel adı olan bir özniteliğe neden olur. `b` Microsoft .NET Framework DOM 'ın çalışması budur.  
  
 Bu nedenle, ad parametresi alan tüm yöntemler için, bu yöntemler adı nitelemek için de bir ön ek alır. **SetAttribute** DOM düzey 1 yönteminde olduğu `A:b` gibi ad parametresi aşağıdaki gibi ayrıştırılır:  
  
- İki nokta üst üste yoksa (:) sonra yerel ad `name` parametreye ayarlanır ve önek ve NamespaceURI Boş dizelerdir.  
  
- İki nokta üst üste bulursa, ad, ilk iki nokta karakterinin konumunu temel alarak iki bölüme ayrılır. Ön ek, iki nokta üst üste gelmeden önce bulunan dizeye ayarlanır ve yerel ad, iki nokta üst üsteden sonra bulunan dizeye ayarlanır. NamespaceURI değeri kullanmayan yöntemler için, NamespaceURI çözümlenmez ve boş dize olarak ayarlanır. Aksi halde, NamespaceURI yöntemine geçirilen dizeye ayarlanır. Ön ek tanımlanmamışsa, **Save** yöntemi ve **InnerXml** ve **OuterXml** özellikleri başarısız olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
