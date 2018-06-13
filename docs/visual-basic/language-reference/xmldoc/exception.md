---
title: '&lt;özel durum&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: f29b8e01239f46b0d56319ba3da1a8fe179a17e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601159"
---
# <a name="ltexceptiongt-visual-basic"></a>&lt;özel durum&gt; (Visual Basic)
Hangi özel durum belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından kullanılabilir bir özel durum referansı. Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı. `member` çift tırnak işaretleri içinde görünmesi gerekir ("").  
  
 `description`  
 Bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<exception>` etiketi hangi özel durum belirtin. Bu etiket için bir yöntem tanımını uygulanır.  
  
 İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 Bu örnek kullanır `<exception>` bir özel durum açıklamak için etiket, `IntDivide` işlevi throw.  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
