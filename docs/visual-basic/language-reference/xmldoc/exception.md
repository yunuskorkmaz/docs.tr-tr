---
description: 'Hakkında daha fazla bilgi edinin: <exception> (Visual Basic)'
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 14b7f78dd2521f7d5b3d62f635baa5b50969afa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787480"
---
# <a name="exception-visual-basic"></a>\<exception> (Visual Basic)

Hangi özel durumların atılamayacağını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametreler  

 `member`  
 Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru. Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir. `member` Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
 `description`  
 Bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  

 `<exception>`Hangi özel durumların atılamayacağını belirtmek için etiketini kullanın. Bu etiket bir yöntem tanımına uygulanır.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<exception>` işlevin oluşturabildiğini belirten bir özel durumu tanımlayan etiketini kullanır `IntDivide` .  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
