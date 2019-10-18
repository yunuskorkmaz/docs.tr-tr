---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524687"
---
# <a name="returns-visual-basic"></a>\<returns > (Visual Basic)
Özelliğin veya işlevin dönüş değerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 Dönüş değerinin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında `<returns>` etiketini kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `DoesRecordExist` işlevinin döndürdüğü şeyi açıklamak için `<returns>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
