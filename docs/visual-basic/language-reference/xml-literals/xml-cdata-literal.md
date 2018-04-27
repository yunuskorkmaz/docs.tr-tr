---
title: XML CDATA Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8dfc091409e060e20970b0b6d6bc19b4fc2aeea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA Değişmez Değeri (Visual Basic)
Değişmez değer gösteren bir <xref:System.Xml.Linq.XCData> nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Bölümler  
 `<![CDATA[`  
 Gerekli. XML CDATA bölümünün başlangıç gösterir.  
  
 `content`  
 Gerekli. XML CDATA bölümünde görüntülenecek metin içeriği.  
  
 `]]>`  
 Gerekli. Bölümün sonuna gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XCData> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML CDATA bölümler dahil, ancak, içerdiği XML çözümlenmemiş ham metni içerir. XML CDATA bölümünde herhangi bir metin içerebilir. Bu ayrılmış XML karakterleri içerir. XML CDATA bölümü dizisi ile biten "]] >". Bu, aşağıdaki noktaları anlamına gelir:  
  
-   Katıştırılmış ifade sınırlayıcıları geçerli XML CDATA içerik olduğundan, bir XML CDATA değişmez değer katıştırılmış bir ifade kullanamazsınız.  
  
-   XML CDATA bölümleri iç içe geçirilemez, çünkü `content` değer içeremez "]] >".  
  
 Bir XML CDATA değişmez değer bir değişkene atayın veya bir XML öğesi değişmez değeri içerir.  
  
> [!NOTE]
>  XML değişmez değer birden çok satıra yayılmış olabilir ancak satır devamlılığı karakterleri kullanmaz. Bu, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmasını sağlar.  
  
 Visual Basic derleyici yapılan bir çağrı XML CDATA değişmez değer dönüştürür <xref:System.Xml.Linq.XCData.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek metin içeren bir CDATA bölümü oluşturur "değişmez değer içerebilir \<XML > etiketleri".  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XCData>  
 [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
