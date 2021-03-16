---
title: <value> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <value> Etiket. Bu etiket, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477637"
---
# <a name="value-c-programming-guide"></a>\<value> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametreler

- `property-description`

  Özelliği için bir açıklama.

## <a name="remarks"></a>Açıklamalar

`<value>`Etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar. Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, [\<summary>](./summary.md) yeni özellik için bir etiket ekler. Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
