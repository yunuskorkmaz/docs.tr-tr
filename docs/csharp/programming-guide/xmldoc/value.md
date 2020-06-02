---
title: <value> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287200"
---
# <a name="value-c-programming-guide"></a>\<value>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametreler

- `property-description`

  Özelliği için bir açıklama.

## <a name="remarks"></a>Açıklamalar

`<value>`Etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar. Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, [\<summary>](./summary.md) yeni özellik için bir etiket ekler. Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
