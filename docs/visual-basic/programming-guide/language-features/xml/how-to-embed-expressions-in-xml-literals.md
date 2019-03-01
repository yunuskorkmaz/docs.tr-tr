---
title: 'Nasıl yapılır: (Visual Basic) XML değişmez değerlerine ifade katıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 6ecb6a5d684badba68f4c224d5359ea428cfbbf2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968718"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Nasıl yapılır: (Visual Basic) XML değişmez değerlerine ifade katıştırma
XML değişmez değerleri, bir XML belge, parça veya çalışma zamanında oluşturulan içeriği içeren bir öğe oluşturmak için katıştırılmış ifadeleri ile birleştirebilirsiniz. Aşağıdaki örnekler, katıştırılmış ifadeler öğe içeriği, öznitelikleri ve öğe adları çalışma zamanında doldurmak için nasıl kullanılacağını göstermektedir.  
  
 Katıştırılmış bir ifade sözdizimi `<%=` `exp` `%>`, aynı sözdizimini olduğu, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] kullanır. Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-insert-text-as-element-content"></a>Öğe içeriği metin eklemek için  
  
-   Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `contactName` açılış ve kapanış adı öğeler arasında değişken.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Bir öznitelik değeri metin eklemek için  
  
-   Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `phoneType` değeri olarak değişken `type` özniteliği.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Bir öğe adı için metin eklemek için  
  
-   Aşağıdaki örnekte yer alan metin eklemek gösterilmektedir `elementName` değişken olarak bir öğe adı.  
  
     Bu tekniği kullanarak öğeleri oluştururken kapatmalısınız \</ > etiketi.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: XML değişmez değerleri oluşturma](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
