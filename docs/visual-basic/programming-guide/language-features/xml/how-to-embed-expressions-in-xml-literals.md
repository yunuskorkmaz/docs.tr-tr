---
title: 'Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332935"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)
Çalışma zamanında oluşturulan içeriği içeren bir XML belgesi, parça veya öğe oluşturmak için gömülü ifadelerle XML değişmez değerlerini birleştirebilirsiniz. Aşağıdaki örneklerde, çalışma zamanında öğe içeriğini, öznitelikleri ve öğe adlarını doldurmak için katıştırılmış ifadelerin nasıl kullanılacağı gösterilmektedir.  
  
 Gömülü bir ifadenin sözdizimi, ASP.NET tarafından kullanılan söz dizimi olan `<%=` `exp` `%>`. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri oluşturmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API 'Lerini de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-insert-text-as-element-content"></a>Metni öğe içeriği olarak eklemek için  
  
- Aşağıdaki örnek, `contactName` değişkeninde içerilen metnin açılış ve kapanış adı öğeleri arasında nasıl ekleneceğini gösterir.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Bir öznitelik değeri olarak metin eklemek için  
  
- Aşağıdaki örnek, `phoneType` değişkeninde bulunan metnin `type` özniteliğinin değeri olarak nasıl ekleneceğini gösterir.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Öğe adı için metin eklemek için  
  
- Aşağıdaki örnek, `elementName` değişkeninde bulunan metnin bir öğenin adı olarak nasıl ekleneceğini gösterir.  
  
     Bu tekniği kullanarak öğe oluştururken, \</> etiketiyle bunları kapatmalısınız.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML Değişmez Değerleri Oluşturma](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
