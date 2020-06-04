---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400027"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)
Üye için bir açıklamalar bölümü belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 Üyenin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 `<remarks>`İle belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için etiketini kullanın [\<summary>](summary.md) .  
  
 Bu bilgiler Nesne Tarayıcısı görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<remarks>` yönteminin ne yaptığını açıklamak için etiketini kullanır `UpdateRecord` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
