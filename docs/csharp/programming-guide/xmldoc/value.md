---
title: <value> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 4d967d671b3a27698b457c80ff5a8f7031dc6bcb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587416"
---
# <a name="value-c-programming-guide"></a>\<değer > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametreler  
 `property-description`  
 Özelliği için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 > \<Tag değeri, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar. Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için bir [ \<Özet >](./summary.md) etiketi ekleneceğini unutmayın. Daha sonra özelliğin temsil ettiği değeri \<tanımlayacak bir değer > etiketi eklemeniz gerekir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
