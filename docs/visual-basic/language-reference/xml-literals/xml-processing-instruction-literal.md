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
ms.openlocfilehash: 3d18e58cb643fa075f6eb08eb6fe909d27a6737b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866408"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML İşleme Talimatı Değişmez Değeri (Visual Basic)

Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XProcessingInstruction> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Bölümler  

 `<?`  
 Gereklidir. XML işleme yönergesi sabit değerinin başlangıcını gösterir.  
  
 `piName`  
 Gereklidir. İşleme yönergesinin hangi uygulamayı hedeflediğini belirten ad. "Xml" veya "XML" ile başlayamaz.  
  
 `piData`  
 İsteğe bağlı. Tarafından hedeflenen uygulamanın `piName` XML belgesini işlemesi gerektiğini belirten dize.  
  
 `?>`  
 Gereklidir. İşleme yönergesinin sonunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bir <xref:System.Xml.Linq.XProcessingInstruction> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  

 XML işleme yönergesi sabit değerleri, uygulamaların bir XML belgesini nasıl işleyeceğini gösterir. Bir uygulama bir XML belgesi yüklediğinde, uygulama, belgeyi nasıl işleyeceğini belirleyebilmek için XML işleme talimatlarını denetleyebilir. Uygulama, ve anlamını Yorumlar `piName` `piData` .  
  
 XML belgesi değişmez değeri, XML işleme yönergesinden benzer bir sözdizimi kullanır. Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](xml-document-literal.md).  
  
> [!NOTE]
> `piName`Xml 1,0 belirtimi Bu tanımlayıcıları ayırdığından, öğe "xml" veya "xml" dizeleriyle başlayamaz.  
  
 Bir değişkene XML işlem yönergesi sabit değeri atayabilir veya onu bir XML belge değişmez değerine ekleyebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterlerine gerek duymadan birden çok satıra yayılabilir. Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.  
  
 Visual Basic Derleyicisi, XML işleme yönerge hazır değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir XML belgesi için stil sayfası tanımlayan bir işleme yönergesi oluşturur.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML Belgesi Değişmez Değeri](xml-document-literal.md)
- [XML Değişmez Değerleri](index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
