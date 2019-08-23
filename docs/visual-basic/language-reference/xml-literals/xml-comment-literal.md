---
title: XML Açıklama Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965407"
---
# <a name="xml-comment-literal-visual-basic"></a>XML Açıklama Değişmez Değeri (Visual Basic)
Bir <xref:System.Xml.Linq.XComment> nesneyi temsil eden sabit değer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`<!--`|Gerekli. XML açıklamasının başlangıcını gösterir.|  
|`content`|Gerekli. XML açıklamasında görüntülenecek metin. Bir dizi iki kısa çizgi (--) veya kapanış etiketinin bitişiğindeki bir tire ile bitemez.|  
|`-->`|Gerekli. XML açıklamasının sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XComment> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 XML açıklama değişmez değerleri belge içeriği içermez; Bunlar belge hakkında bilgiler içerir. XML açıklama bölümü "-->" sırasıyla biter. Bu, aşağıdaki noktaları gösterir:  
  
- Gömülü ifade sınırlayıcıları geçerli XML açıklama içeriği olduğundan, bir XML açıklama değişmez değerinde katıştırılmış ifade kullanamazsınız.  
  
- "-->" Değerini içeremediğinden `content` XML açıklama bölümleri iç içe geçirilemez.  
  
 Bir değişkene bir XML açıklama sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir. Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.  
  
 Visual Basic derleyici, XML açıklama değişmez değerini <xref:System.Xml.Linq.XComment.%23ctor%2A> oluşturucuya bir çağrıya dönüştürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek "This bir açıklamadır" metnini içeren bir XML açıklaması oluşturur.  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XComment>
- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
