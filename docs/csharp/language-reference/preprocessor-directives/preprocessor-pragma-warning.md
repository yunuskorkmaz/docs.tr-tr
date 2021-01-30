---
description: '#pragma warning-C# başvurusu'
title: '#pragma warning-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215998"
---
# <a name="pragma-warning-c-reference"></a>#pragma uyarısı (C# Başvurusu)

`#pragma warning` Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.

## <a name="syntax"></a>Sözdizimi

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a>Parametreler

 `warning-list` Uyarı numaralarının virgülle ayrılmış bir listesi. "CS" ön eki isteğe bağlıdır.

 Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.

> [!NOTE]
> Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.

## <a name="example"></a>Örnek

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
- [C# derleyici hataları](../compiler-messages/index.md)
- [Kod Analizi uyarılarını gösterme](../../../fundamentals/code-analysis/suppress-warnings.md)
