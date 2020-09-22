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
ms.openlocfilehash: 9eddd132b2d4dd6ffbd935a0c8c57a03a3d65435
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869440"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML Özniteliği Axis Özelliği (Visual Basic)

Bir nesne için bir özniteliğin değerine <xref:System.Xml.Linq.XElement> veya nesne koleksiyonundaki ilk öğeye erişim sağlar <xref:System.Xml.Linq.XElement> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Bölümler  

 `object`  
 Gereklidir. <xref:System.Xml.Linq.XElement>Nesne veya nesne koleksiyonu <xref:System.Xml.Linq.XElement> .  
  
 .@  
 Gereklidir. Öznitelik ekseni özelliğinin başlangıcını gösterir.  
  
 <  
 İsteğe bağlı. Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının başlangıcını gösterir `attribute` .  
  
 `attribute`  
 Gereklidir. [:] Biçiminde erişebileceğiniz özniteliğin adı `prefix` `name` .  
  
|Bölüm|Açıklama|  
|----------|-----------------|  
|`prefix`|İsteğe bağlı. Öznitelik için XML ad alanı ön eki. Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .|  
|`name`|Gereklidir. Yerel öznitelik adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|  
  
 \>  
 İsteğe bağlı. Visual Basic geçerli bir tanımlayıcı olmadığında özniteliğin adının sonunu belirtir `attribute` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Değerini içeren bir dize `attribute` . Öznitelik adı yoksa, `Nothing` döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir özniteliğin değerine bir <xref:System.Xml.Linq.XElement> nesneden veya nesne koleksiyonundaki ilk öğeden ada göre erişmek için BIR XML özniteliği eksen özelliği kullanabilirsiniz <xref:System.Xml.Linq.XElement> . Ada göre bir öznitelik değeri alabilir veya bir öğeye yeni bir öznitelik ekleyerek @ tanımlayıcısının önüne yeni bir ad belirterek ekleyebilirsiniz.  
  
 @ Tanımlayıcısını kullanarak bir XML özniteliğine başvurduğunuzda, öznitelik değeri bir dize olarak döndürülür ve özelliği açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> .  
  
 XML öznitelikleri için adlandırma kuralları Visual Basic Tanımlayıcılarla ilgili adlandırma kurallarından farklıdır. Geçerli bir Visual Basic tanımlayıcı olmayan bir ada sahip bir XML özniteliğine erişmek için, adı açılı ayraç () içine alın \< and > .  
  
## <a name="xml-namespaces"></a>XML ad alanları  

 Öznitelik ekseni özelliğindeki ad, yalnızca, ifadesini kullanarak genel olarak belirtilen XML ad alanı öneklerini kullanabilir `Imports` . XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `type` adlı XML öğelerinin bir koleksiyonundan ADLı XML özniteliklerinin değerlerinin nasıl alınacağını gösterir `phone` .  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir XML öğesi için, XML 'nin bir parçası olarak ve bir nesne örneğine bir öznitelik ekleyerek dinamik olarak nasıl öznitelik oluşturulacağını gösterir <xref:System.Xml.Linq.XElement> . `type`Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `number-type` , Visual Basic ' de geçerli bir tanımlayıcı olmayan ADLı xml özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Phone type: work`  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir. Daha sonra, bir XML sabit değeri oluşturmak ve "" tam adına sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:name` .  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](index.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
