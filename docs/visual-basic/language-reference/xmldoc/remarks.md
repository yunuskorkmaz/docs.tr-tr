---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524668"
---
# <a name="remarks-visual-basic"></a>\<remarks > (Visual Basic)
Üye için bir açıklamalar bölümü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 Üyenin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 [@No__t_2summary >](../../../visual-basic/language-reference/xmldoc/summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için `<remarks>` etiketini kullanın.  
  
 Bu bilgiler Nesne Tarayıcısı görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `UpdateRecord` yönteminin ne yaptığını açıklamak için `<remarks>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
