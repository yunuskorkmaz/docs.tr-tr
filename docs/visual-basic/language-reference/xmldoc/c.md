---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523935"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
Açıklama içindeki metnin kod olduğunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`text`|Kod olarak göstermek istediğiniz metin.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar. Birden çok satırı kod olarak göstermek için [\<code >](../../../visual-basic/language-reference/xmldoc/code.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Counter` kodun olduğunu göstermek için Özet bölümündeki `<c>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
