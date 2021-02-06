---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <returns> (Visual Basic)'
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: ba5f1e231502a67e86ffbb92cf8868c3aecb05d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640387"
---
# <a name="returns-visual-basic"></a>\<returns> (Visual Basic)

Özelliğin veya işlevin dönüş değerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parametreler  

 `description`  
 Dönüş değerinin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  

 `<returns>`Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında etiketini kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<returns>` işlevin ne döndürdüğünü açıklamak için etiketini kullanır `DoesRecordExist` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
