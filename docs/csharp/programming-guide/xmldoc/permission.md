---
title: <permission> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287278"
---
# <a name="permission-c-programming-guide"></a>\<permission>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

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

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
