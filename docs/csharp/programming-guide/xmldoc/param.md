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
ms.openlocfilehash: 3f1099da6a43ed7f48389a16e3be6a3b6b98a148
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271583"
---
# <a name="param-c-programming-guide"></a>\<param > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Bir yöntem parametresi adı. Adı çift tırnak içine alın ("").  
  
 `description`  
 Parametre için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Param > Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için. Birden çok parametre belgeye birden çok kullanın \<param > etiketleri.  
  
 Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklaması Web rapor görüntülenir.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
