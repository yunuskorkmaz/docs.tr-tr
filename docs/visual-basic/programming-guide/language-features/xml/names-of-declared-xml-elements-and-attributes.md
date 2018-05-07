---
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 9b586936281bfbf2dcace7cf2892bebf305fc842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)
Bu konu, XML öğeleri ve özniteliklerinin XML değişmez değerlerinde adlandırmak için Visual Basic yönergeler sağlar.  XML değişmez değer, bir yerel adı veya tam adı belirtebilirsiniz. Tam adı, bir XML ad alanı öneki, iki nokta ve yerel ad oluşur. XML ad alanı önekleri hakkında daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Kurallar  
 Öğe veya öznitelik Visual Basic'te bir yerel adı aşağıdaki kurallara uyması gerekir.  
  
-   Bir ad alanı ile başlayabilirsiniz. Alfabetik bir karakter veya alt çizgi ile başlaması gerekir (`_`).  
  
-   Yalnızca alfabetik karakterler, ondalık sayılar, alt çizgi, nokta (.) ve kısa çizgi içermelidir (-).  
  
-   Birden fazla 1024 karakterden uzun olmamalıdır.  
  
-   Ad alanı düzenleme adlarında görünen iki nokta üst üste gösterir. Bu nedenle, yalnızca belirli bir adı için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.  
  
 Ayrıca, aşağıdaki kılavuz uyması.  
  
-   XML 1.0 belirtimi "xml" büyük/küçük harf Çeşitleme dize ile başlayan tüm adları ayırır. Bu nedenle, bu öğeyi adlarını ve öznitelik adları kullanmayın.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  
 Pratik geçtiğinden bağımsız, bir ad öğesi yapısını hala açık bir şekilde tanımlanırken olabildiğinde kısa olması gerekir. Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğu ve kaynak dosya boyutu azaltır.  
  
 Ancak, adınızı, yeterli öğesi veya nasıl kodunuzu kullanıyorsa açıklanmaz, bu nedenle kısa olmamalıdır. Bu, kodunuzu okunabilirlik için önemlidir. Başkası anladığınızı çalışıyor ya da sizin, uzun süre yazdığınız sonra arıyorsanız, uygun öğe adları zamandan tasarruf edebilirsiniz.  
  
## <a name="case-sensitivity-in-names"></a>Adları büyük/küçük harfe duyarlılık  
 XML öğe adları büyük/küçük harfe duyarlıdır. Bu, Visual Basic derleyici yalnızca alfabetik durumlarda farklı iki ad karşılaştırır, bunları farklı adları olarak yorumlar olduğunu anlamına gelir. Örneğin, Yorumlar `ABC` ve `abc` öğeleri ayırmak için başvuran olarak.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Bir XML öğesi değişmez değer oluştururken, öğe adı için XML ad alanı öneki belirtebilirsiniz. Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
