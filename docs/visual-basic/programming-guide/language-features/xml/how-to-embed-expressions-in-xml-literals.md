---
title: 'Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392320"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerlerine İfade Katıştırma (Visual Basic)
Çalışma zamanında oluşturulan içeriği içeren bir XML belgesi, parça veya öğe oluşturmak için gömülü ifadelerle XML değişmez değerlerini birleştirebilirsiniz. Aşağıdaki örneklerde, çalışma zamanında öğe içeriğini, öznitelikleri ve öğe adlarını doldurmak için katıştırılmış ifadelerin nasıl kullanılacağı gösterilmektedir.  
  
 Gömülü ifade için sözdizimi `<%=` `exp` `%>` , ASP.net 'in kullandığı söz dizimi olan sözdizimidir. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](embedded-expressions-in-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]API 'leri, nesneleri oluşturmak için de kullanabilirsiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-insert-text-as-element-content"></a>Metni öğe içeriği olarak eklemek için  
  
- Aşağıdaki örnek, `contactName` açma ve kapatma adı öğeleri arasındaki değişkende bulunan metnin nasıl ekleneceğini gösterir.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Bir öznitelik değeri olarak metin eklemek için  
  
- Aşağıdaki örnek, değişkeninde bulunan metnin `phoneType` özniteliğin değeri olarak nasıl ekleneceğini gösterir `type` .  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Öğe adı için metin eklemek için  
  
- Aşağıdaki örnek, `elementName` bir öğenin adı olarak değişkende bulunan metnin nasıl ekleneceğini gösterir.  
  
     Bu tekniği kullanarak öğe oluştururken, bunları \</> etiketiyle kapatmalısınız.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Bu örnek aşağıdaki çıktıyı üretir:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML Değişmez Değerleri Oluşturma](how-to-create-xml-literals.md)
- [XML'de Katıştırılmış İfadeler](embedded-expressions-in-xml.md)
- [Visual Basic'de XML Oluşturma](creating-xml.md)
- [XML](index.md)
