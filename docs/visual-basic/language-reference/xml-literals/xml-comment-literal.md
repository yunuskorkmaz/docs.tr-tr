---
title: "XML Açıklama Değişmez Değeri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36be34ac22cfe926a2eea946f5e4c4eb534de696
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
>  XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir. Bu özellik, bir XML belgesinden içeriği Kopyala ve doğrudan yapıştırın sağlar bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici yapılan bir çağrı XML açıklama değişmez değer dönüştürür <xref:System.Xml.Linq.XComment.%23ctor%2A> Oluşturucusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, "Bu bir açıklamadır" metnini içeren bir XML açıklama oluşturur.  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XComment>  
 [XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML değişmez değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
