---
title: <see> C# Programlama Kılavuzu
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
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627678"
---
# <a name="see-c-programming-guide"></a>\<bkz. >C# (Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = "`member`"

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir. *Üyeyi* çift tırnak işareti ("") içine koyun.

## <a name="remarks"></a>Açıklamalar

\<bkz. > etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır. Metnin Ayrıca See de bir bölümüne yerleştirilmesi gerektiğini belirtmek için [\<see>](./seealso.md) kullanın. Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

Aşağıdaki örnek bir Özet bölümü içinde bir \<> etiketini gösterir.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
