---
title: XML İşleme Talimatı Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d2df93a46d426358988b3ad7f3161c7ae0c7b9e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML İşleme Talimatı Değişmez Değeri (Visual Basic)
Değişmez değer gösteren bir <xref:System.Xml.Linq.XProcessingInstruction> nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Bölümler  
 `<?`  
 Gerekli. XML işleme yönergesi değişmez değeri başlangıcını gösterir.  
  
 `piName`  
 Gerekli. Hangi uygulamanın belirten işleme yönergesi hedefleri adı. "Xml" veya "XML" ile başlayamaz.  
  
 `piData`  
 İsteğe bağlı. Uygulamayı nasıl hedeflenen gösteren dize `piName` XML belgesi işleme.  
  
 `?>`  
 Gerekli. İşleme yönergesi sonunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XProcessingInstruction> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML işleme talimatı değişmez değerleri, uygulamalar bir XML belgesi nasıl işleneceğini gösterir. Bir uygulama bir XML belgesi yüklenirken, uygulama belgeyi işlemek nasıl belirlemek için XML işleme yönergelerini kontrol edebilirsiniz. Uygulama anlamını yorumlar `piName` ve `piData`.  
  
 XML belgesi değişmez değeri, XML işleme talimatı benzer sözdizimini kullanır. Daha fazla bilgi için bkz: [XML belgesi değişmez değer](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  `piName` Öğesi başlayamaz dizeleri "xml" veya "XML" ile XML 1.0 belirtimi bu tanımlayıcıları ayırdığından.  
  
 Bir XML işleme yönergesi değişmez değeri bir değişkene atayın veya bir XML belgesi değişmez değeri içerir.  
  
> [!NOTE]
>  XML değişmez değeri birden fazla satır satır devamlılığı karakterleri gerek kalmadan yayılabilir. Bu, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmasını sağlar.  
  
 Visual Basic derleyici yapılan bir çağrı XML işleme yönergesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML belgesi için bir stil sayfası tanımlayan bir işleme yönergesi oluşturur.  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [XML Belgesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
