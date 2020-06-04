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
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400234"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA Değişmez Değeri (Visual Basic)
Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XCData> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Bölümler  
 `<![CDATA[`  
 Gereklidir. XML CDATA bölümünün başlangıcını gösterir.  
  
 `content`  
 Gereklidir. XML CDATA bölümünde görünecek metin içeriği.  
  
 `]]>`  
 Gereklidir. Bölümün sonunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XCData> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML CDATA kısımları, kendisini içeren XML ile birlikte dahil edilmelidir, ancak ayrıştırılmaz olması gereken ham metni içerir. Bir XML CDATA bölümü, herhangi bir metin içerebilir. Bu, ayrılmış XML karakterleri içerir. XML CDATA bölümü "]] >" dizisiyle biter. Bu, aşağıdaki noktaları gösterir:  
  
- Gömülü ifade sınırlayıcıları geçerli XML CDATA içeriği olduğundan, bir XML CDATA değişmez değerinde gömülü bir ifade kullanamazsınız.  
  
- `content`"]] >" değerini IÇEREMEDIĞINDEN XML CDATA bölümleri iç içe geçirilemez.  
  
 Bir değişkene bir XML CDATA sabit değeri atayabilir veya onu bir XML öğesi değişmez değerine dahil edebilirsiniz.  
  
> [!NOTE]
> Bir XML sabit değeri birden fazla satıra yayılabilir, ancak satır devamlılık karakterlerini kullanmaz. Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.  
  
 Visual Basic derleyici, XML CDATA değişmez değerini oluşturucuya bir çağrıya dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, "değişmez Etiketler içerebilir" metnini içeren bir CDATA bölümü oluşturur \<XML> .  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XCData>
- [XML Öğesi Değişmez Değeri](xml-element-literal.md)
- [XML Değişmez Değerleri](index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
