---
title: XML Özniteliği Axis Özelliği (Visual Basic)
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
ms.openlocfilehash: 081359f32438c6474fe5c229634b60969e25a24e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965390"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML Özniteliği Axis Özelliği (Visual Basic)
İçin bir öznitelik değeri erişim sağlayan bir <xref:System.Xml.Linq.XElement> nesne veya koleksiyonu içindeki ilk öğeye <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Bölümler  
 `object`  
 Gerekli. Bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.  
  
 .@  
 Gerekli. Bir özniteliği axis özelliği başlangıcını gösterir.  
  
 <  
 İsteğe bağlı. Özniteliğin adını başlangıcını gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.  
  
 `attribute`  
 Gerekli. Biçiminde erişmeye özniteliğin adı [`prefix`:]`name`.  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`prefix`|İsteğe bağlı. Özniteliği için XML ad alanı öneki. Genel XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.|  
|`name`|Gerekli. Yerel bir öznitelik adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 İsteğe bağlı. Özniteliğin adını sonuna gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Değerini içeren bir dize `attribute`. Öznitelik adı mevcut değilse `Nothing` döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir XML özniteliği axis özelliği bir özniteliğin değerini adından tarafından erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> nesne veya koleksiyonu içindeki ilk öğeyi <xref:System.Xml.Linq.XElement> nesneleri. Bir özniteliği değeri ada göre alabilirsiniz veya koyarak yeni bir ad belirterek, bir öğeye yeni bir öznitelik eklemek @ tanımlayıcı.  
  
 Ne zaman başvuru kullanarak bir XML özniteliği tanımlayıcı, dize olarak öznitelik değeri döndürülür ve açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.  
  
 Visual Basic tanımlayıcıları için adlandırma kuralları adlandırma kuralları için XML özniteliklerini farklıdır. Geçerli bir Visual Basic tanımlayıcı bir ada sahip bir XML özniteliği erişmek için ad, açılı ayraçlar içine (\< ve >).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Bir özniteliği axis özelliği adı genel olarak kullanılarak bildirilen XML ad alanı öneklerini kullanabilirsiniz `Imports` deyimi. XML ad alanı öneklerini XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız. Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı XML öznitelik değerleri, alınacağı gösterilmektedir `type` adlı XML öğesi bir koleksiyondan `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hem bir XML öğesi için öznitelikleri bildirimli olarak, XML ve dinamik olarak örneğine bir öznitelik ekleyerek bir parçası olarak oluşturma işlemi gösterilmektedir bir <xref:System.Xml.Linq.XElement> nesne. `type` Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek açılı ayraç sözdizimini XML özniteliğinin değerini almak için kullanır. `number-type`, Visual Basic'te geçerli bir tanımlayıcı değil.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone type: work`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki. XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
