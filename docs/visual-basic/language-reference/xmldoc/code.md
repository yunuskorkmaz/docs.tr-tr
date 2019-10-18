---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524040"
---
# <a name="code-visual-basic"></a>\<code > (Visual Basic)
Metnin birden çok kod satırı olduğunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Kod olarak işaretlemek için metin.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden çok satırı kod olarak göstermek için `<code>` etiketini kullanın. Bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `ID` alanının kullanılmasına ilişkin örnek kodu eklemek için \<code > etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
