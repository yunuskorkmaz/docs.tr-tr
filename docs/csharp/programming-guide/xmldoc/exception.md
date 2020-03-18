---
title: <exception>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789797"
---
# <a name="exception-c-programming-guide"></a>\<özel durum> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametreler

- cref = `member`" "

  Geçerli derleme ortamından kullanılabilen bir özel durum için bir başvuru. Derleyici, verilen özel durum var `member` olduğunu denetler ve xml çıkışındaki kanonik öğe adına çevirir. `member`çift tırnak işaretleri içinde görünmelidir (" ").

  Genel bir türe `member` başvurmak için biçimlendirme hakkında daha fazla bilgi için Bkz. [XML Dosyasını İşleme.](processing-the-xml-file.md)

- `description`

  Özel durum açıklaması.

## <a name="remarks"></a>Açıklamalar

Özel \<durum> etiketi, hangi özel durumların atılacağını belirtmenize olanak tanır. Bu etiket, yöntemler, özellikler, olaylar ve dizin leyiciler için tanımlara uygulanabilir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

Özel durum işleme hakkında daha fazla bilgi için [bkz.](../exceptions/index.md)

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](recommended-tags-for-documentation-comments.md)
