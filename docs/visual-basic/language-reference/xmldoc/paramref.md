---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331365"
---
# <a name="ltparamrefgt-visual-basic"></a>&lt;paramref&gt; (Visual Basic)
Bir sözcük, parametre olarak biçimlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Başvurmak için parametrenin adı. Adı çift tırnak içine alın ("").  
  
## <a name="remarks"></a>Açıklamalar  
 `<paramref>` Etiketi bir sözcüğün bir parametre olduğunu belirtmek için bir yol sağlar. XML dosyası, bu parametreyi belirgin bir şekilde biçimlendirmek için işlenebilir.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<paramref>` başvurmak için etiket `id` parametresi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
