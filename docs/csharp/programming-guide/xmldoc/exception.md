---
title: <exception>-C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <exception> . Bu etiket hangi özel durumların atılamayacağını belirtmenizi sağlar ve yöntemlere, özelliklere, olaylara ve Dizin oluşturuculara uygulanabilir.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381742"
---
# <a name="exception-c-programming-guide"></a>\<exception>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametreler

- cref = " `member` "

  Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru. Derleyici verilen özel durumun var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir. `member`Çift tırnak işaretleri ("") içinde yer almalıdır.

  Genel bir türe başvurmak için biçimlendirme hakkında daha fazla bilgi için `member` bkz. [XML dosyasını işleme](processing-the-xml-file.md).

- `description`

  Özel durumun açıklaması.

## <a name="remarks"></a>Açıklamalar

`<exception>`Etiketi hangi özel durumların atılamayacağını belirtmenizi sağlar. Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](recommended-tags-for-documentation-comments.md)
