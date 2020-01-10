---
title: <param> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711733"
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
 Yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimi için açıklamasında \<param > etiketi kullanılmalıdır. Birden çok parametreyi belgelemek için, birden çok \<param > etiketi kullanın.  
  
 \<param > etiketinin metni IntelliSense 'de, Nesne Tarayıcısı ve kod yorumu Web raporunda görüntülenir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
