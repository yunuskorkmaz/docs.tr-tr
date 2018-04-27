---
title: XML Açıklama Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5bb8c10c28a4ab864220c1b4ce4702622e55c92
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-comment-literal-visual-basic"></a>XML Açıklama Değişmez Değeri (Visual Basic)
Değişmez değer gösteren bir <xref:System.Xml.Linq.XComment> nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`<!--`|Gerekli. XML açıklama başlangıcını gösterir.|  
|`content`|Gerekli. XML açıklama görüntülenecek metin. İki kısa çizgi (-) veya kapanış etiketi bitişik bir tire ile biten bir dizi içeremez.|  
|`-->`|Gerekli. XML açıklama sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XComment> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML açıklama değişmez değerleri belgesinin içeriği içermez; Belge hakkındaki bilgileri içerir. XML açıklama bölümüne sona erer sırası "--> ile". Bu, aşağıdaki noktaları anlamına gelir:  
  
-   Katıştırılmış ifade sınırlayıcıları geçerli XML açıklama içerik olduğundan, bir XML açıklama değişmez değer katıştırılmış bir ifade kullanamazsınız.  
  
-   XML açıklama bölümleri iç içe geçirilemez, çünkü `content` değer içeremez "-->".  
  
 Bir değişkene bir XML açıklama değişmez değer atayabilir veya bir XML öğesi değişmez değeri içerir.  
  
> [!NOTE]
>  XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir. Bu özellik, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmak sağlar.  
  
 Visual Basic derleyici yapılan bir çağrı XML açıklama değişmez değer dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, "Bu bir açıklamadır" metnini içeren bir XML açıklama oluşturur.  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XComment>  
 [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
