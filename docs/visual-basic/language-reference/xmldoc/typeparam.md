---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 0a68cf0a495c2809961e8ec99effa459b0647fec
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866386"
---
# <a name="typeparam-visual-basic"></a>\<typeparam> (Visual Basic)

Bir tür parametresi adı ve açıklaması tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametreler  

 `name`  
 Tür parametresinin adı. Adı çift tırnak işareti ("") içine alın.  
  
 `description`  
 Tür parametresinin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  

 `<typeparam>`Tür parametrelerinden birini belirtmek için genel bir tür veya genel üye bildirimi için açıklamadaki etiketini kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<typeparam>` parametresini anlatmak için etiketini kullanır `id` .  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
