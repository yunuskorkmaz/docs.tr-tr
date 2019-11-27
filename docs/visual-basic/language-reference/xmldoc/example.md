---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348489"
---
# <a name="example-visual-basic"></a>\<örnek > (Visual Basic)
Üye için bir örnek belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 Kod örneğinin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 `<example>` etiketi, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize olanak tanır. Bu genellikle [\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) etiketinin kullanılmasını içerir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `ID` alanı kullanmak için bir örnek eklemek için `<example>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
