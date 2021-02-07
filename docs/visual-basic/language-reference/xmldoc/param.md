---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <param> (Visual Basic)'
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 94fe5e11d5846f7fa00eb73c1c4363990ae23b2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700302"
---
# <a name="param-visual-basic"></a>\<param> (Visual Basic)

Bir parametre adı ve açıklama tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parametreler  

 `name`  
 Bir yöntem parametresinin adı. Adı çift tırnak işareti ("") içine alın.  
  
 `description`  
 Parametresi için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  

 `<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.  
  
 `<param>`Etiketin metni aşağıdaki konumlarda görünür:  
  
- IntelliSense parametre bilgileri. Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).  
  
- Nesne Tarayıcısı. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<param>` parametresini anlatmak için etiketini kullanır `id` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
