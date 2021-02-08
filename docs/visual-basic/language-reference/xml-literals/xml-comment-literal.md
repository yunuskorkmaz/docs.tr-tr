---
description: 'Hakkında daha fazla bilgi edinin: XML açıklama değişmez değeri (Visual Basic)'
title: XML Açıklama Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: f44d2e132236d74d312910921fabb3a85afd82d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768746"
---
# <a name="xml-comment-literal-visual-basic"></a>XML Açıklama Değişmez Değeri (Visual Basic)

Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XComment> .  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Bölümler  
  
|Süre|Tanım|  
|---|---|  
|`<!--`|Gereklidir. XML açıklamasının başlangıcını gösterir.|  
|`content`|Gereklidir. XML açıklamasında görüntülenecek metin. Bir dizi iki kısa çizgi (--) veya kapanış etiketinin bitişiğindeki bir tire ile bitemez.|  
|`-->`|Gereklidir. XML açıklamasının sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bir <xref:System.Xml.Linq.XComment> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  

 XML açıklama değişmez değerleri belge içeriği içermez; Bunlar belge hakkında bilgiler içerir. XML açıklama bölümü "-->" sırasıyla biter. Bu, aşağıdaki noktaları gösterir:  
  
- Gömülü ifade sınırlayıcıları geçerli XML açıklama içeriği olduğundan, bir XML açıklama değişmez değerinde katıştırılmış ifade kullanamazsınız.  
  
- `content`"-->" değerini IÇEREMEDIĞINDEN XML açıklama bölümleri iç içe geçirilemez.  
  
 Bir değişkene bir XML açıklama sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir. Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.  
  
 Visual Basic derleyici, XML açıklama değişmez değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek "This bir açıklamadır" metnini içeren bir XML açıklaması oluşturur.  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XComment>
- [XML Öğesi Değişmez Değeri](xml-element-literal.md)
- [XML Değişmez Değerleri](index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
