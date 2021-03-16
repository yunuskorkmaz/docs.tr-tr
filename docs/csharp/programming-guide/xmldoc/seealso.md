---
title: <seealso> -C# Programlama Kılavuzu
description: XML 'i kullanmayı öğrenin <seealso> Etiket. Bu etiket, ' Ayrıca bkz. ' bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır.
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
ms.openlocfilehash: c5baefbfca3a94095a90eb43c2bf13eb924c8cdc
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477758"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = " `member` "

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir.`member` Çift tırnak işaretleri ("") içinde yer almalıdır.

  Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [cref özniteliği](./cref-attribute.md).

## <a name="remarks"></a>Açıklamalar

`<seealso>`Etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize imkan sağlar. [\<see>](./see.md)Metnin içinden bir bağlantı belirtmek için kullanın.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[\<summary>](./summary.md)Hakkında bir örnek için bkz \<seealso> ..

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
