---
title: XML'de Katıştırılmış İfadeler (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c6dff88d123f33ad4c33e91685104b760ecca3b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML'de Katıştırılmış İfadeler (Visual Basic)
Katıştırılmış ifadeler çalışma zamanında değerlendirilir ifadeleri içeren XML değişmez değerleri oluşturma olanak sağlar. Katıştırılmış bir ifade sözdizimi `<%=` `expression` `%>`, olduğu aynı sözdizimini kullanılan gibi [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Örneğin, bir XML öğesi değişmez değeri metin içeriği katıştırılmış ifadeler birleştirme oluşturabilirsiniz.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Varsa `isbnNumber` 12345 tamsayı içerir ve `modifiedDate` tarihini içerir 3/5/ne zaman bu kodu yürütür, değerini 2006, `book` değil:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Katıştırılmış ifade konumu ve doğrulama  
 Katıştırılmış ifadeler yalnızca XML değişmez ifadeleri içinde belirli konumlarda yer alabilir. İfade türleri ifade konumu denetimleri döndürebilir ve nasıl `Nothing` ele alınır. Aşağıdaki tabloda, izin verilen konumların ve katıştırılmış ifadeler türleri açıklanmaktadır.  
  
|Değişmez değeri konumda|İfade türü|İşleme `Nothing`|  
|---|---|---|  
|XML öğesi adı|<xref:System.Xml.Linq.XName>|Hata|  
|XML öğesi içeriği|`Object` veya dizi `Object`|Yoksayıldı|  
|XML öğesi öznitelik adı|<xref:System.Xml.Linq.XName>|Hata, öznitelik değeri de olmadığı sürece `Nothing`|  
|XML öğesi öznitelik değeri|`Object`|Göz ardı özniteliği bildirimi|  
|XML öğe özniteliği|<xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute>|Yoksayıldı|  
|XML belge kök öğesi|<xref:System.Xml.Linq.XElement> veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesne ve isteğe bağlı sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri|Yoksayıldı|  
  
-   Bir XML öğesi adı katıştırılmış bir ifadede örneği:  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Katıştırılmış içerik ifadede bir XML öğesi örneği:  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Bir XML öğesi öznitelik adı katıştırılmış bir ifadede örneği:  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Bir XML öğesi öznitelik değerinde katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Bir XML öğesi özniteliğindeki katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Bir XML belgesi kök öğesi içinde katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Etkinleştirirseniz, `Option Strict`, her katıştırılmış ifade türü için gerekli tür widens derleyici denetler. Kod çalıştığında doğrulanır bir XML belgesi kök öğesi için yalnızca istisnadır. Olmadan derleme yaparsanız `Option Strict`, türünde ifadeler katıştırmak `Object` ve bunların türü çalışma zamanında doğrulanır.  
  
 İçerik nerede isteğe bağlı, konumlarda içeren ifadeleri katıştırılmış `Nothing` göz ardı edilir. Bu öznitelik değerleri, o öğe içeriği denetleyin gerekmez ve dizi öğeleri olmayan anlamına gelir `Nothing` bir XML değişmez değeri kullanmadan önce. Öğe ve öznitelik adları gibi değerler olamaz gerekli `Nothing`.  
  
 Katıştırılmış bir ifade hazır değer belirli bir tür kullanma hakkında daha fazla bilgi için bkz: [XML belgesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Kapsam kuralları  
 Derleyici Oluşturucusu çağrısı uygun değişmez değer türü için her XML değişmez değer dönüştürür. Değişmez değer içeriğine ve XML değişmez değeri katıştırılmış ifadeler oluşturucuya bağımsız değişken olarak geçirilir. Başka bir deyişle, bir XML değişmez değer kullanılabilir tüm Visual Basic programlama öğeleri de kendi katıştırılmış ifadeler için kullanılabilir.  
  
 XML değişmez değer içinde önekleri bildirilen ile XML ad alanına erişebildiğinizi `Imports` deyimi. Yeni bir XML ad alanı önekini bildirmek veya kullanarak bir öğedeki var olan bir XML ad alanı öneki gölge `xmlns` özniteliği. Yeni ad alanı, o öğesinin alt düğümleri, ancak katıştırılmış ifadelerde XML değişmez değerleri kullanılabilir.  
  
> [!NOTE]
>  Ne zaman bildirdiğiniz bir XML ad alanı öneki kullanarak `xmlns` namespace özniteliği öznitelik değerinin bir sabit dize olması gerekir. Bu bağlamda kullanarak `xmlns` özniteliktir kullanarak gibi `Imports` bir XML ad alanı bildirmek için deyimi. XML ad alanı değeri belirtmek için katıştırılmış bir ifade kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [XML Değişmez Değerlerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
