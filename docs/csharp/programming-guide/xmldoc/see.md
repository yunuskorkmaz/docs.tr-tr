---
title: <see> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <see> . Bu etiket, örneğin bir cref özniteliği kullanarak metin içinden bir bağlantı belirtmenize olanak tanır.
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477767"
---
# <a name="see-c-programming-guide"></a>\<see> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = " `member` "

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir. *Üyeyi* çift tırnak işareti ("") içine koyun.

## <a name="remarks"></a>Açıklamalar

`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır. [\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın. Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın. Ayrıca, ``href`` köprü olarak işlev sağlayacak geçerli bir özniteliktir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
