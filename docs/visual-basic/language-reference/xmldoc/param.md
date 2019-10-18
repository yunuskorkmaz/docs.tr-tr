---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524724"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
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
 Metodun parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada `<param>` etiketinin kullanılması gerekir.  
  
 @No__t_0 etiketinin metni aşağıdaki konumlarda görünür:  
  
- IntelliSense parametre bilgileri. Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).  
  
- Nesne Tarayıcısı. Daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `id` parametresini anlatmak için `<param>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
