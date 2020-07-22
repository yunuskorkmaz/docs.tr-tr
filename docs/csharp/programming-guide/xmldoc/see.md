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
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863792"
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

`<see>`Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır. [\<seealso>](./seealso.md)Metnin Ayrıca bkz. bölümüne yerleştirilmesi gerektiğini belirtmek için kullanın. Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın. Ayrıca, ``href`` köprü olarak işlev sağlayacak geçerli bir özniteliktir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

Aşağıdaki örnek bir `<see>` Özet bölümü içindeki bir etiketi gösterir.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
