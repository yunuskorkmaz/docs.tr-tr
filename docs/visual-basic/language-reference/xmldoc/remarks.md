---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 70078752495240ab8c72fe1bbecdca554166fb22
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866420"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)

Üye için bir açıklamalar bölümü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
