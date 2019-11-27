---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 78227a17584271f91283198e95f5aa389b3ef14b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352275"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
Bir sözcüğü parametre olarak biçimlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 `<paramref>` etiketi, bir sözcüğün bir parametre olduğunu göstermek için bir yol sağlar. XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `id` parametresine başvurmak için `<paramref>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
