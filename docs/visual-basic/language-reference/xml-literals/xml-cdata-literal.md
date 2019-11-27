---
title: XML CDATA Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349429"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA Değişmez Değeri (Visual Basic)
<xref:System.Xml.Linq.XCData> nesnesini temsil eden bir sabit değer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Bölümler  
 `<![CDATA[`  
 Gerekli. XML CDATA bölümünün başlangıcını gösterir.  
  
 `content`  
 Gerekli. XML CDATA bölümünde görünecek metin içeriği.  
  
 `]]>`  
 Gerekli. Bölümün sonunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XCData> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML CDATA kısımları, kendisini içeren XML ile birlikte dahil edilmelidir, ancak ayrıştırılmaz olması gereken ham metni içerir. Bir XML CDATA bölümü, herhangi bir metin içerebilir. Bu, ayrılmış XML karakterleri içerir. XML CDATA bölümü "]] >" dizisiyle biter. Bu, aşağıdaki noktaları gösterir:  
  
- Gömülü ifade sınırlayıcıları geçerli XML CDATA içeriği olduğundan, bir XML CDATA değişmez değerinde gömülü bir ifade kullanamazsınız.  
  
- `content` "]] >" değerini içeremediğinden, XML CDATA bölümleri iç içe geçirilemez.  
  
 Bir değişkene bir XML CDATA sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri birden fazla satıra yayılabilir, ancak satır devamlılık karakterlerini kullanmaz. Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.  
  
 Visual Basic derleyici, XML CDATA değişmez değerini <xref:System.Xml.Linq.XCData.%23ctor%2A> oluşturucusuna bir çağrıya dönüştürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, "değişmez \<XML > etiketleri içerebilir" metnini içeren bir CDATA bölümü oluşturur.  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XCData>
- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
