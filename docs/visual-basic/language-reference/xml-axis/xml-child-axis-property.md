---
title: XML Alt Axis Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400272"
---
# <a name="xml-child-axis-property-visual-basic"></a>XML Alt Axis Özelliği (Visual Basic)
Aşağıdakilerden birinin alt öğelerine erişim sağlar: <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesne koleksiyonu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gereklidir. <xref:System.Xml.Linq.XElement>Nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya nesne koleksiyonu <xref:System.Xml.Linq.XDocument> .|  
|. <|Gereklidir. Bir alt eksen özelliğinin başlangıcını gösterir.|  
|`child`|Gereklidir. Formun erişebileceği alt düğümlerin adı `[prefix:]name` .<br /><br /> -   `Prefix`Seçim. Alt düğüm için XML ad alanı ön eki. Bir ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .<br />-   `Name`İstenir. Yerel alt düğüm adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|  
|>|Gereklidir. Alt eksen özelliğinin sonunu belirtir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XElement> nesneleri topluluğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya bir <xref:System.Xml.Linq.XElement> veya nesneleri koleksiyonundan bir ad ile erışmek için bir xml alt Axis özelliği kullanabilirsiniz <xref:System.Xml.Linq.XDocument> . `Value`Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek IÇIN XML özelliğini kullanın. Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).  
  
 Visual Basic Derleyicisi alt eksen özelliklerini yöntemine yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> .  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Alt eksen özelliğindeki ad, ifadesiyle Global olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir `Imports` . XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, nesnesinden adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir `phone` `contact` .  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `phone` `contact` nesnesinin alt eksen özelliği tarafından döndürülen koleksiyondan adlı alt düğümlere nasıl erişegösterdiğini gösterir `contacts` .  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğüme tam adı ile erişin `ns:name` .  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](index.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
