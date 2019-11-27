---
title: XML İşleme Talimatı Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347039"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML İşleme Talimatı Değişmez Değeri (Visual Basic)
<xref:System.Xml.Linq.XProcessingInstruction> nesnesini temsil eden bir sabit değer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Bölümler  
 `<?`  
 Gerekli. XML işleme yönergesi sabit değerinin başlangıcını gösterir.  
  
 `piName`  
 Gerekli. İşleme yönergesinin hangi uygulamayı hedeflediğini belirten ad. "Xml" veya "XML" ile başlayamaz.  
  
 `piData`  
 İsteğe bağlı. `piName` tarafından hedeflenen uygulamanın XML belgesini nasıl işleyeceğini belirten dize.  
  
 `?>`  
 Gerekli. İşleme yönergesinin sonunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XProcessingInstruction> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML işleme yönergesi sabit değerleri, uygulamaların bir XML belgesini nasıl işleyeceğini gösterir. Bir uygulama bir XML belgesi yüklediğinde, uygulama, belgeyi nasıl işleyeceğini belirleyebilmek için XML işleme talimatlarını denetleyebilir. Uygulama `piName` ve `piData`anlamını yorumlar.  
  
 XML belgesi değişmez değeri, XML işleme yönergesinden benzer bir sözdizimi kullanır. Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> XML 1,0 belirtimi Bu tanımlayıcıları ayırdığından `piName` öğesi "xml" veya "XML" dizeleriyle başlayamaz.  
  
 Bir değişkene XML işlem yönergesi sabit değeri atayabilir veya onu bir XML belge değişmez değerine ekleyebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterlerine gerek duymadan birden çok satıra yayılabilir. Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.  
  
 Visual Basic derleyici, XML işleme yönergesi sabit değerini <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> oluşturucusuna bir çağrıya dönüştürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML belgesi için stil sayfası tanımlayan bir işleme yönergesi oluşturur.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML Belgesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
