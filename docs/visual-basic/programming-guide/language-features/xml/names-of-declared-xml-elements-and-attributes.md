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
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819690"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)
Bu konu, XML öğeleri ve özniteliklerinin XML değişmez değerlerinde adlandırmak için Visual Basic yönergeler sağlar.  XML değişmez değer, yerel adı veya tam ad belirtebilirsiniz. Bir tam adı, bir XML ad alanı öneki, bir iki nokta üst üste ve yerel ad oluşur. XML ad alanı öneklerini hakkında daha fazla bilgi için bkz: [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Kurallar  
 Bir yerel ad öğe veya Visual Basic'te öznitelik şu kurallara uyması gerekir.  
  
-   Bu ad alanı ile başlayabilirsiniz. Alfabetik bir karakter veya alt çizgi ile başlamalıdır (`_`).  
  
-   Yalnızca alfabetik karakterler, ondalık sayılar, alt çizgi, nokta (.) ve kısa çizgi içermelidir (-).  
  
-   Çok 1024 karakterden uzun olmamalıdır.  
  
-   Görünen adlarında iki nokta üst üste ad düzenleme gösterir. Bu nedenle, yalnızca belirli bir adı için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.  
  
 Ayrıca, aşağıdaki kılavuz uyması.  
  
-   XML 1.0 belirtimi "xml" herhangi bir büyük harf Çeşitleme dizesi ile başlayan tüm adlarını saklar. Bu nedenle, bu öğeyi adlarını ve öznitelik adları kullanmayın.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  
 Pratik olursa olsun bir ad öğesi doğasını açıkça hala tanımlanırken olabildiğince kısa olmalıdır. Bu, kodunuzun okunabilirliği geliştirir ve satır uzunluğu ve kaynak dosya boyutunu azaltır.  
  
 Ancak, adınız, yeterince öğe veya nasıl kodunuzun kullandığı tanımlamaz, bu nedenle kısa olmamalıdır. Bu, kodunuzun okunabilirliği için önemlidir. Başka birisi tarafından anlayabilmek çalışıyor ya da sizin, uzun bir süre sonra yazdığınız kullanmak istiyorsanız, uygun öğe adları zamandan tasarruf edebilirsiniz.  
  
## <a name="case-sensitivity-in-names"></a>Adları büyük/küçük harf duyarlılığı  
 XML öğe adları büyük/küçük harfe duyarlıdır. Bu, Visual Basic Derleyicisi alfabetik yalnızca farklı iki ad karşılaştırır, bunları farklı adlar yorumlar, anlamına gelir. Örneğin, Yorumlar `ABC` ve `abc` öğeleri ayırmak için başvuru olarak.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Bir XML öğesi değişmez değeri oluştururken, XML ad alanı öneki öğe adı belirtebilirsiniz. Daha fazla bilgi için [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
