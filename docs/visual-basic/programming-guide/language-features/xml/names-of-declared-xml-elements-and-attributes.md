---
title: "Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)
Bu konuda verilmektedir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] XML öğeleri ve özniteliklerinin XML değişmez değerlerinde adlandırma yönergeleri.  XML değişmez değer, bir yerel adı veya tam adı belirtebilirsiniz. Tam adı, bir XML ad alanı öneki, iki nokta ve yerel ad oluşur. XML ad alanı önekleri hakkında daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Kurallar  
 Bir öğe veya öznitelik yerel adını [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aşağıdaki kurallara uyması gerekir.  
  
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
 XML öğe adları büyük/küçük harfe duyarlıdır. Yani [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici karşılaştırır yalnızca alfabetik durumlarda farklı iki ad, bu gibi farklı adlar yorumlar. Örneğin, Yorumlar `ABC` ve `abc` öğeleri ayırmak için başvuran olarak.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Bir XML öğesi değişmez değer oluştururken, öğe adı için XML ad alanı öneki belirtebilirsiniz. Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
