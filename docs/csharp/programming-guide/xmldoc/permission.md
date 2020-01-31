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
ms.openlocfilehash: 14abb5bd181f401a4e6834d110e20fa920566580
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789731"
---
# <a name="permission-c-programming-guide"></a>\<izin > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametreler

- cref = "`member`"

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. *üye* çift tırnak işareti ("") içinde yer almalıdır.

  Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [\<](./see.md).

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
