---
title: <value> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793347"
---
# <a name="value-c-programming-guide"></a>\<değeri > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametreler

- `property-description`

  Özelliği için bir açıklama.

## <a name="remarks"></a>Açıklamalar

\<Value > etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar. Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için bir [\<summary >](./summary.md) etiketi ekleneceğini unutmayın. Sonra özelliğin temsil ettiği değeri tanımlayan bir \<değer > etiketi eklemeniz gerekir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
