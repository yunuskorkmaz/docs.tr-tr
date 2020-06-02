---
title: <see>-C# Programlama Kılavuzu
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
ms.openlocfilehash: 0f10feb0931c6d38c817fdecb925f68d439abb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287252"
---
# <a name="see-c-programming-guide"></a>\<see>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = " `member` "

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir. *Üyeyi* çift tırnak işareti ("") içine koyun.

## <a name="remarks"></a>Açıklamalar

`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır. [\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın. Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
