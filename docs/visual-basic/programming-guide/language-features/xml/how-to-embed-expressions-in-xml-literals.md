---
title: 'Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652275"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)
XML değişmez değerleri, bir XML belgesi, parça veya çalışma zamanında oluşturulmuş içeriğe öğesi oluşturmak için katıştırılmış ifadeler ile birleştirebilirsiniz. Aşağıdaki örnekler katıştırılmış ifadeler öğe içeriği, öznitelikleri ve öğe adları çalışma zamanında doldurmak için nasıl kullanılacağını göstermektedir.  
  
 Katıştırılmış bir ifade sözdizimi `<%=` `exp` `%>`, aynı sözdizimini olduğu, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] kullanır. Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Aynı zamanda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'lerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-insert-text-as-element-content"></a>Metin öğe içeriği eklemek için  
  
-   Aşağıdaki örnekte yer metin eklemek gösterilmiştir `contactName` açma ve kapatma adı öğeler arasında değişken.  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     Bu örnek şu çıkışı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Öznitelik değeri olarak metin eklemek için  
  
-   Aşağıdaki örnekte yer metin eklemek gösterilmiştir `phoneType` değeri olarak değişken `type` özniteliği.  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     Bu örnek şu çıkışı üretir:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Bir öğe adı için metin eklemek için  
  
-   Aşağıdaki örnekte yer metin eklemek gösterilmiştir `elementName` değişken, bir öğenin adı.  
  
     Bu yöntemi kullanarak öğeleri oluştururken, kapatmalısınız \</ > etiketi.  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     Bu örnek şu çıkışı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: XML Değişmez Değerleri Oluşturma](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
