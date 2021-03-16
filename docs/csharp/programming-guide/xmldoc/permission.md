---
title: <permission> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <permission> Etiket. Bu etiket bir üyenin erişimini belgelemenizi sağlar, ancak PermissionSet sınıfı bir üyeye erişim belirtmenize izin verir.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 379d3fda06c50e9e988784e671061d604e6e5b36
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477845"
---
# <a name="permission-c-programming-guide"></a>\<permission> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametreler

- cref = " `member` "

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir. *üye* çift tırnak işareti ("") içinde yer almalıdır.

  Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).

- `description`

  Üyeye erişim açıklaması.

## <a name="remarks"></a>Açıklamalar

`<permission>`Etiketi bir üyenin erişimini belgelemenizi sağlar. <xref:System.Security.PermissionSet>Sınıfı, bir üyeye erişim belirtmenize olanak sağlar.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
