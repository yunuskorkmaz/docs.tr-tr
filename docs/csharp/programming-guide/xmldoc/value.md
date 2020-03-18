---
title: <value> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793347"
---
# <a name="value-c-programming-guide"></a>\<değer> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametreler

- `property-description`

  Mülk için bir açıklama.

## <a name="remarks"></a>Açıklamalar

Etiket \<> değer, bir özelliğin temsil ettiği değeri açıklamanızı sağlar. Visual Studio .NET geliştirme ortamında kod sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için [ \<bir özet>](./summary.md) etiketi ekleyeceğini unutmayın. Daha sonra, özelliğin \<temsil ettiği değeri açıklamak için el ile bir değer> etiketi eklemeniz gerekir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
