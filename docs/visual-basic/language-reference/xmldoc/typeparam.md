---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <typeparam> (Visual Basic)'
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: efb4394ee2badcf52bac75d7d9e317c732789746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640270"
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
