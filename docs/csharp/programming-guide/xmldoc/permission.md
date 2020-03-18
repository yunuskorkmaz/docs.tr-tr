---
title: <permission> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093480"
---
# <a name="permission-c-programming-guide"></a>\<izin> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametreler

- cref = `member`" "

  Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru. Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki kanonik öğe adına çevirir. *üye* çift tırnak içinde görünmelidir (" ").

  Genel bir türe nasıl bir cref başvurusu oluşturabilirsiniz hakkında bilgi için [bkz.](./cref-attribute.md)

- `description`

  Üyeye erişimin açıklaması.

## <a name="remarks"></a>Açıklamalar

İzin \<> etiketi, bir üyenin erişimini belgelemenize olanak tanır. Sınıf, <xref:System.Security.PermissionSet> bir üyeye erişimi belirtmenizi sağlar.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
