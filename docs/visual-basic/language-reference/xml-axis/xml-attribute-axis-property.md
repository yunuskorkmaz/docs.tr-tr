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
ms.openlocfilehash: 3e02fd2ddc3928bdd2e9741737fc31fb2b16901c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604919"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML Özniteliği Axis Özelliği (Visual Basic)
İçin bir öznitelik değeri erişim sağlayan bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonunu ilk öğe <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Bölümler  
 `object`  
 Gerekli. Bir <xref:System.Xml.Linq.XElement> nesne ya da bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.  
  
 .@  
 Gerekli. Attribute axis özelliği başlangıcını gösterir.  
  
 <  
 İsteğe bağlı. Özniteliğin adını başlangıcını gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.  
  
 `attribute`  
 Gerekli. Biçiminde erişmeye özniteliğinin adı [`prefix`:]`name`.  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`prefix`|İsteğe bağlı. Öznitelik için XML ad alanı öneki. Genel bir XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.|  
|`name`|Gerekli. Yerel öznitelik adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 İsteğe bağlı. Özniteliğin adını sonunu gösterir, `attribute` Visual Basic'te geçerli bir tanımlayıcı değil.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Değerini içeren bir dize `attribute`. Öznitelik adı yoksa, `Nothing` döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir XML özniteliği axis özelliği adından tarafından özniteliğin değerini erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> nesnesi veya bir koleksiyonunu ilk öğe <xref:System.Xml.Linq.XElement> nesneleri. Ada göre bir öznitelik değeri alınamıyor veya öncesinde yeni bir ad belirterek bir öğeye yeni bir öznitelik Ekle @ tanımlayıcı.  
  
 Ne zaman başvuran bir XML özniteliği kullanmaya tanımlayıcısı öznitelik değeri bir dize olarak döndürülür ve açıkça belirtmek gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.  
  
 Visual Basic tanımlayıcıları için adlandırma kuralları XML öznitelikleri için adlandırma kuralları farklıdır. Adı, geçerli bir Visual Basic tanımlayıcısı değil bir ada sahip bir XML özniteliği erişmek için açılı ayraç içine alın (\< ve >).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Attribute axis özelliği adı kullanarak genel olarak bildirilen XML ad alanı önekleri kullanabilirsiniz `Imports` deyimi. XML ad alanı önekleri XML öğesi değişmez içinde yerel olarak bildirilen kullanamazsınız. Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı XML özniteliklerinin değerlerini alma gösterir `type` adlandırıldığı XML öğeleri koleksiyonundan `phone`.  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki bir XML öğesi özniteliklerini bildirimli olarak, XML ve dinamik olarak bir öznitelik örneğine ekleyerek bir parçası olarak oluşturulacağını gösterir bir <xref:System.Xml.Linq.XElement> nesnesi. `type` Özniteliği bildirimli olarak oluşturulur ve `owner` özniteliği dinamik olarak oluşturulur.  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, adlı XML özniteliğinin değerini almak için açılı ayraç sözdizimini kullanır. `number-type`, Visual Basic'te geçerli bir tanımlayıcı değil.  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone type: work`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak. XML değişmez değer oluşturmak ve ilk alt düğüm tam adı ile erişmek için ad alanı öneki sonra kullanan "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
