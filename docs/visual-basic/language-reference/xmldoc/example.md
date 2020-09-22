---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872980"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)

Üye için bir örnek belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parametreler  

 `description`  
 Kod örneğinin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  

 `<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar. Bu genellikle etiketinin kullanılmasını içerir [\<code>](code.md) .  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<example>` alanı kullanmak için bir örnek eklemek için etiketini kullanır `ID` .  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
