---
title: <see>- C# programlama kılavuzu
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
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627678"
---
# <a name="see-c-programming-guide"></a>\<bkz.> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref =`member`" "

  Geçerli derleme ortamından çağrılabilecek bir üye veya alana başvuru. Derleyici, verilen kod öğesinin var `member` olduğunu denetler ve XML çıkışındaki öğe adına geçer. *Üyeyi* çift tırnak işaretleri (" ") içine yerleştirin.

## <a name="remarks"></a>Açıklamalar

Bkz. \<> etiketi, metin içinden bir bağlantı belirtmenize olanak tanır. Metnin Bkz. Also bölümüne yerleştirilmesi gerektiğini belirtmek için [ \<seealso>](./seealso.md) kullanın. Kod öğeleri için belge sayfalarına dahili köprüler oluşturmak için [cref Özniteliği'ni](./cref-attribute.md) kullanın.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

Aşağıdaki örnekte, \<özet bölümünde> etiketi ni gösterilmektedir.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
