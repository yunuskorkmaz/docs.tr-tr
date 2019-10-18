---
title: <paramref> C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 43e98565ff7294ebb6fa7e71d1be17522dbb15de
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523407"
---
# <a name="paramref-c-programming-guide"></a>\<paramref > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0paramref > etiketi, kod açıklamalarındaki bir sözcüğün bir \<summary > veya \<remarks > bloğunun bir parametreye başvurduğunu göstermek için bir yol sağlar. Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
