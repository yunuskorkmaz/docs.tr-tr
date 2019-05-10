---
title: XML CDATA Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 889ec7f93d0503edac51652dda217c6a9f654f9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621428"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA Değişmez Değeri (Visual Basic)
Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XCData> nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Bölümler  
 `<![CDATA[`  
 Gerekli. XML CDATA bölümü başlangıcını gösterir.  
  
 `content`  
 Gerekli. XML CDATA bölümde görüntülenecek metin içeriği.  
  
 `]]>`  
 Gerekli. Bölümün sonuna gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XCData> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 XML CDATA bölümler dahil, ancak, içerdiği XML çözümlenmemiş ham metni içerir. XML CDATA bölümü herhangi bir metin içerebilir. Bu, ayrılmış XML karakterlerini içerir. XML CDATA bölümü dizisi ile biter "]] >". Bu, aşağıdaki noktaları anlamına gelir:  
  
- Gömülü ifade sınırlayıcılar geçerli XML CDATA içerik olduğundan, bir katıştırılmış deyim bir XML CDATA değişmez değeri kullanamazsınız.  
  
- XML CDATA kısımları iç içe geçirilemez, çünkü `content` değeri içeremez "]] >".  
  
 Bir XML CDATA değişmez değeri bir değişkene atayın ya da bir XML öğesi değişmez değeri içerir.  
  
> [!NOTE]
>  XML değişmez değer birden fazla satırı kapsayabilir ancak satır devamlılığı karakteri kullanmaz. Bu içerik bir XML belgesinden kopyalayıp bir Visual Basic programa doğrudan yapıştırın olanak sağlar.  
  
 XML CDATA değişmez değer Visual Basic Derleyicisi için bir çağrı dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, metni içeren CDATA bölümü oluşturur. "değişmez değer içerebilir \<XML > etiketleri".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XCData>
- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
