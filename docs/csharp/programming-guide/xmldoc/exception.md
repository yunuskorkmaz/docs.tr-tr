---
title: <exception> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789797"
---
# <a name="exception-c-programming-guide"></a>\<özel durum >C# (Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametreler

- cref = "`member`"

  Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru. Derleyici verilen özel durumun var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. `member` çift tırnak işaretleri ("") içinde yer almalıdır.

  Genel bir türe başvurmak üzere `member` biçimlendirme hakkında daha fazla bilgi için bkz. [XML dosyasını işleme](processing-the-xml-file.md).

- `description`

  Özel durumun açıklaması.

## <a name="remarks"></a>Açıklamalar

\<özel durum > etiketi hangi özel durumların atılamayacağını belirlemenizi sağlar. Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](recommended-tags-for-documentation-comments.md)
