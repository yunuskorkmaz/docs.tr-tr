---
title: '&lt;param&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338019"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
