---
title: <param> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: ed7a8f8a06771a18dc4244bffbda53e9adbd4e90
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523422"
---
# <a name="param-c-programming-guide"></a>\<param > (C# Programlama Kılavuzu)
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
 Yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimi için açıklamasında \<param > etiketi kullanılmalıdır. Birden çok parametreyi belgelemek için birden çok \<param > etiketi kullanın.  
  
 @No__t_0param > etiketinin metni IntelliSense 'de, Nesne Tarayıcısı ve kod yorumu Web raporunda görüntülenir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
