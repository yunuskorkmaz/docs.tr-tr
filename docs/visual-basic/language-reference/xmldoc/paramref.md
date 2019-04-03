---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3e2bf7990343a325bbecc56f6d3754a77f1e08e2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818677"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
Bir sözcük, parametre olarak biçimlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 Başvurmak için parametrenin adı. Adı çift tırnak içine alın ("").  
  
## <a name="remarks"></a>Açıklamalar  
 `<paramref>` Etiketi bir sözcüğün bir parametre olduğunu belirtmek için bir yol sağlar. XML dosyası, bu parametreyi belirgin bir şekilde biçimlendirmek için işlenebilir.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<paramref>` başvurmak için etiket `id` parametresi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
