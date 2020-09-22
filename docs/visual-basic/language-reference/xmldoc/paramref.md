---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: d7aacc5faea22f9c5a4b865a32c832154fe624c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872608"
---
# <a name="paramref-visual-basic"></a>\<paramref> (Visual Basic)

Bir sözcüğü parametre olarak biçimlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametreler  

 `name`  
 Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  

 Etiketi, bir `<paramref>` sözcüğün bir parametre olduğunu göstermek için bir yol sağlar. XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<paramref>` parametresine başvurmak için etiketini kullanır `id` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
