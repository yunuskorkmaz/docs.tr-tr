---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 16d10b2f955a4d9a02075ee4cc40dfa2b18c3541
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940885"
---
# <a name="para-visual-basic"></a>\<para > (Visual Basic)
İçerik paragraf olarak biçimlendirileceğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Paragraf metni.  
  
## <a name="remarks"></a>Açıklamalar  
 `<para>` Gibi olan bir etiketi içinde kullanmak için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), veya [ \<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md), ve metnin yapısını eklemenizi sağlar.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<para>` için Açıklamalar bölümüne ayırmak için etiket `UpdateRecord` iki paragraf yönteme.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
