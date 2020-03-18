---
title: <seealso> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093467"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = `member`" "

  Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru. Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki öğe adına geçer.`member` çift tırnak işaretleri içinde görünmelidir (" ").

  Genel bir türe nasıl bir cref başvurusu oluşturabilirsiniz hakkında bilgi için [bkz.](./cref-attribute.md)

## <a name="remarks"></a>Açıklamalar

Seealso> etiketi, \<Bkz. Ayrıca bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır. Metin içinden bir bağlantı belirtmek için [ \<bkz.>](./see.md) kullanın.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

Seealso> kullanma \<örneği için özet [ \<>](./summary.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
