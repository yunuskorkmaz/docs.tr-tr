---
title: XML Özniteliği Axis Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352666"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML Özniteliği Axis Özelliği (Visual Basic)
Bir <xref:System.Xml.Linq.XElement> nesnesi veya bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğe için bir özniteliğin değerine erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Bölümler  
 `object`  
 Gerekli. <xref:System.Xml.Linq.XElement> nesnesi veya <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu.  
  
 .@  
 Gerekli. Öznitelik ekseni özelliğinin başlangıcını gösterir.  
  
 <  
 İsteğe bağlı. `attribute` Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının başlangıcını gösterir.  
  
 `attribute`  
 Gerekli. [`prefix`:]`name`biçiminde erişebileceğiniz özniteliğin adı.  
  
|Bölümüyle|Açıklama|  
|----------|-----------------|  
|`prefix`|İsteğe bağlı. Öznitelik için XML ad alanı ön eki. Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır.|  
|`name`|Gerekli. Yerel öznitelik adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|  
  
 \>  
 İsteğe bağlı. `attribute` Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının sonunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `attribute`değerini içeren bir dize. Öznitelik adı yoksa `Nothing` döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özniteliğin değerine bir <xref:System.Xml.Linq.XElement> nesnesinden veya bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğeden ada göre erişmek için bir XML öznitelik ekseni özelliği kullanabilirsiniz. Ada göre bir öznitelik değeri alabilir veya bir öğeye yeni bir öznitelik ekleyerek @ tanımlayıcısının önüne yeni bir ad belirterek ekleyebilirsiniz.  
  
 @ Tanımlayıcısını kullanarak bir XML özniteliğine başvurduğunuzda, öznitelik değeri bir dize olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini açık bir şekilde belirtmeniz gerekmez.  
  
 XML öznitelikleri için adlandırma kuralları Visual Basic Tanımlayıcılarla ilgili adlandırma kurallarından farklıdır. Geçerli bir Visual Basic tanımlayıcı olmayan bir ada sahip bir XML özniteliğine erişmek için, adı açılı ayraçlar (\< ve >) içine alın.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Öznitelik ekseni özelliğindeki ad, `Imports` ifadesini kullanarak genel olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir. XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `phone`adlı bir XML öğeleri koleksiyonundan `type` adlı XML özniteliklerinin değerlerinin nasıl alınacağını gösterir.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML öğesi için, XML 'nin bir parçası olarak ve bir <xref:System.Xml.Linq.XElement> nesnesinin örneğine bir öznitelik ekleyerek dinamik olarak nasıl öznitelik oluşturulacağını gösterir. `type` özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual Basic ' de geçerli bir tanımlayıcı olmayan `number-type`adlı XML özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Phone type: work`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve "`ns:name`" tam adına sahip ilk alt düğüme erişir.  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
