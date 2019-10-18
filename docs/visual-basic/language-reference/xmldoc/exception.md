---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523926"
---
# <a name="exception-visual-basic"></a>\<exception > (Visual Basic)
Hangi özel durumların atılamayacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru. Derleyici verilen özel durumun var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. `member` çift tırnak işaretleri ("") içinde yer almalıdır.  
  
 `description`  
 Bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 Hangi özel durumların atılamayacağını belirtmek için `<exception>` etiketini kullanın. Bu etiket bir yöntem tanımına uygulanır.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `IntDivide` işlevinin oluşturabildiğini belirten bir özel durumu tanımlayan `<exception>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
