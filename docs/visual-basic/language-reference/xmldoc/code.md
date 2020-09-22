---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873030"
---
# <a name="code-visual-basic"></a>\<code> (Visual Basic)

Metnin birden çok kod satırı olduğunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametreler  

 `content`  
 Kod olarak işaretlemek için metin.  
  
## <a name="remarks"></a>Açıklamalar  

 `<code>`Birden çok satırı kod olarak göstermek için etiketini kullanın. [\<c>](c.md)Açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, \<code> alanı kullanmaya yönelik örnek kodu eklemek için etiketini kullanır `ID` .  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
