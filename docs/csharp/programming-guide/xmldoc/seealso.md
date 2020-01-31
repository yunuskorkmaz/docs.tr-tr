---
title: <seealso> - C# Programlama Kılavuzu
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
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789690"
---
# <a name="seealso-c-programming-guide"></a>\<SeeAlso > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametreler

- cref = "`member`"

  Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.`member` Çift tırnak işaretleri ("") içinde yer almalıdır.

  Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [\<](./see.md).

## <a name="remarks"></a>Açıklamalar

\<seede > etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır. Metin içinden bir bağlantı belirtmek için [\<> bakın](./see.md) .

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

Bkz. \<SeeAlso > kullanımı örneği için [\<özet >](./summary.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
