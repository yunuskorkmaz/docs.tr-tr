---
title: <permission> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093480"
---
# <a name="permission-c-programming-guide"></a>\<izin > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametreler

- cref = "`member`"

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. *üye* çift tırnak işareti ("") içinde yer almalıdır.

  Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).

- `description`

  Üyeye erişim açıklaması.

## <a name="remarks"></a>Açıklamalar

\<izin > etiketi bir üyenin erişimini belgelemenizi sağlar. <xref:System.Security.PermissionSet> sınıfı, bir üyeye erişim belirtmenize olanak tanır.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
