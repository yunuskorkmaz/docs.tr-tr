---
title: "&lt;param&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a>&lt;param&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Yöntem parametresinin adı. Ad çift tırnak işaretleri içine alın ("").  
  
 `description`  
 Parametresi için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Param > etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır. Birden çok parametre belgelemek için birden çok kullanmak \<param > etiketler.  
  
 Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklama Web raporu görüntülenir.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
