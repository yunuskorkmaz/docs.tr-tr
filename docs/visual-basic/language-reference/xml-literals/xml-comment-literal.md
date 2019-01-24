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
ms.openlocfilehash: 96a7281cde546c3077cf15c625c6e09d2d0ee46f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624684"
---
# <a name="xml-comment-literal-visual-basic"></a>XML Açıklama Değişmez Değeri (Visual Basic)
Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XComment> nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`<!--`|Gerekli. XML yorumu başlangıcını gösterir.|  
|`content`|Gerekli. XML açıklamasında görüntülenecek metin. İki kısa çizgi (-) veya kapanış etiketi için bitişik bir tire ile biten bir dizi içeremez.|  
|`-->`|Gerekli. XML yorumu sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XComment> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 XML açıklama değişmez değerleri, belge içeriğini içermez; Belge hakkındaki bilgileri içerirler. XML açıklama bölümü dizisi "--> ile" sona erer. Bu, aşağıdaki noktaları anlamına gelir:  
  
-   Gömülü ifade sınırlayıcılar geçerli XML yorumu içerik olduğundan, bir katıştırılmış deyim bir XML açıklama değişmez değeri kullanamazsınız.  
  
-   XML açıklama bölümleri iç içe geçirilemez, çünkü `content` değeri içeremez "-->".  
  
 Bir XML açıklama değişmez değeri bir değişkene atayın ya da bir XML öğesi değişmez değeri içerir.  
  
> [!NOTE]
>  XML değişmez değer birden fazla satır, satır devamlılığı karakteri kullanmadan yayılabilir. Bu özellik, bir XML belgesinden içeriği kopyalayın ve doğrudan bir Visual Basic programına yapıştırın sağlar.  
  
 XML açıklama değişmez değer Visual Basic Derleyicisi için bir çağrı dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, "Bu bir açıklamadır" metni içeren bir XML yorumu oluşturur.  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XComment>
- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
