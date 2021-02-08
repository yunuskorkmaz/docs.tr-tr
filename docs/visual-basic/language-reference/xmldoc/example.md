---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <example> (Visual Basic)'
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787493"
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
