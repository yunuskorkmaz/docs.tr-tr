---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346967"
---
# <a name="exception-visual-basic"></a>\<özel durum > (Visual Basic)
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
