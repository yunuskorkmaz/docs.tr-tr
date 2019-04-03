---
title: XML İşleme Talimatı Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3fbb16a4d47801b671d37566573215d3a57afff1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820158"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML İşleme Talimatı Değişmez Değeri (Visual Basic)
Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XProcessingInstruction> nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Bölümler  
 `<?`  
 Gerekli. XML işleme yönergesi değişmez değeri başlangıcını gösterir.  
  
 `piName`  
 Gerekli. Hangi uygulamayı gösteren işleme yönergesi hedefleri adlandırın. "Xml" veya "XML" ile başlayamaz.  
  
 `piData`  
 İsteğe bağlı. Uygulamayı nasıl hedeflenen belirten bir dize `piName` XML belgesi işlemelisiniz.  
  
 `?>`  
 Gerekli. İşleme yönergenin bitiminden gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XProcessingInstruction> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 XML işleme talimatı değişmez değerleri, bir XML belgesi uygulamaları nasıl işleneceğini gösterir. Bir XML belgesi bir uygulama yüklendiğinde uygulama belgeyi işlemek nasıl belirlemek için XML işleme yönergeleri kontrol edebilirsiniz. Uygulama anlamını yorumlar `piName` ve `piData`.  
  
 XML belgesi değişmez değeri XML işlem yönergesi için benzer bir sözdizimi kullanır. Daha fazla bilgi için [XML belgesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  `piName` Öğesi başlayamaz dizeleri "xml" veya "XML" ile XML 1.0 belirtimi bu tanımlayıcıları ayırdığından.  
  
 Bir XML işleme yönergesi değişmez değeri bir değişkene atayın ya da bir XML belgesi değişmez değeri içerir.  
  
> [!NOTE]
>  Bir XML değişmez değeri birden fazla satır, satır devamlılığı karakteri gerek kalmadan yayılabilir. Bu içerik bir XML belgesinden kopyalayıp bir Visual Basic programa doğrudan yapıştırın olanak sağlar.  
  
 Visual Basic Derleyicisi için bir çağrı XML işleme yönergesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML belgesi için bir stil sayfası tanımlayan bir işlem yönergesi oluşturur.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML Belgesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
