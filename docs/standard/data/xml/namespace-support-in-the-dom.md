---
title: DOM Ad Alanı Desteği
ms.date: 03/30/2017
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
ms.openlocfilehash: b71817bf8a1b2eb585ccb3b21fb361c651c2bfe9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830161"
---
# <a name="namespace-support-in-the-dom"></a>DOM Ad Alanı Desteği
XML Belge Nesne Modeli (DOM) tamamen ad alanı farkındır. Yalnızca ad alanı algılayan XML belgeleri desteklenir. World Wide Web Konsorsiyumu (W3C), düzey 1 ' i uygulayan DOM uygulamalarının ad alanı kullanmayan ve DOM düzeyi 2 özelliklerinin ad alanı duyarlı olduğunu belirtir. Ancak, yöntemin düzey 1 veya düzey 2 DOM önermesinden bağımsız olarak, XML DOM 'daki tüm özellikler ad alanı farkındır.  
  
 Örneğin, ad alanı kullanmayan bir ayarda, `setAttribute("A:b", "123")` DOM düzey 1 önerinde belirtildiği gibi çağırmak, öneki ve yerel adı olan bir öznitelik ile sonuçlanmaz `A` `b` . Bu, değerine sahip bir özniteliğe neden olur `A:b` .  
  
 Ad alanı kullanan bir ortamda, DOM düzey 2 ' ye yapılan çağrı, `setAttribute("A:b", "123")` öneki ve yerel adı olan bir özniteliğe neden olur `A` `b` . Microsoft .NET Framework DOM 'ın çalışması budur.  
  
 Bu nedenle, ad parametresi alan tüm yöntemler için, bu yöntemler adı nitelemek için de bir ön ek alır. `A:b` **SetAttribute** DOM düzey 1 yönteminde olduğu gibi ad parametresi aşağıdaki gibi ayrıştırılır:  
  
- İki nokta üst üste yoksa (:) sonra yerel ad `name` parametreye ayarlanır ve önek ve NamespaceURI Boş dizelerdir.  
  
- İki nokta üst üste bulursa, ad, ilk iki nokta karakterinin konumunu temel alarak iki bölüme ayrılır. Ön ek, iki nokta üst üste gelmeden önce bulunan dizeye ayarlanır ve yerel ad, iki nokta üst üsteden sonra bulunan dizeye ayarlanır. NamespaceURI değeri kullanmayan yöntemler için, NamespaceURI çözümlenmez ve boş dize olarak ayarlanır. Aksi halde, NamespaceURI yöntemine geçirilen dizeye ayarlanır. Ön ek tanımlanmamışsa, **Save** yöntemi ve **InnerXml** ve **OuterXml** özellikleri başarısız olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
