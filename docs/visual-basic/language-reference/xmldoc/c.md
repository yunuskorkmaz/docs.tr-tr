---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871703"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)

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

 `<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar. [\<code>](code.md)Birden çok satırı kod olarak göstermek için kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<c>` kod olduğunu göstermek için Özet bölümündeki etiketini kullanır `Counter` .  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
