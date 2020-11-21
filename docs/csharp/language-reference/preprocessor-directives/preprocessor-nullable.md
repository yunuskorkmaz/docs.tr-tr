---
description: '#Nullable-C# başvurusu'
title: '#Nullable-C# başvurusu'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099465"
---
# <a name="nullable-c-reference"></a>#nullable (C# Başvurusu)

`#nullable`Önişlemci yönergesi *null yapılabilir ek açıklama bağlamını* ve *null yapılabilir uyarı bağlamını* ayarlar. Bu yönerge, null yapılabilir ek açıklamaların geçerli olup olmadığını ve null olabilme uyarılarının verilip verilmediğini denetler. Her bağlam *devre dışı* ya da *etkin*.

Her iki içerik de proje düzeyinde belirtilebilir (C# kaynak kodu dışında). `#nullable`Yönergesi ek açıklamanın ve uyarı bağlamlarını denetler ve proje düzeyi ayarlarından önceliklidir. Bir yönerge, başka bir yönerge tarafından geçersiz kılınana kadar veya kaynak dosyanın sonuna kadar denetlediği bağlamı ayarlar.

Yönergelerin etkisi aşağıdaki gibidir:

- `#nullable disable`: Nullable ek açıklama ve uyarı bağlamlarını *devre dışı* olarak ayarlar.
- `#nullable enable`: Null yapılabilir ek açıklama ve uyarı bağlamlarını *etkin* olarak ayarlar.
- `#nullable restore`: Proje ayarlarına Nullable ek açıklama ve uyarı bağlamlarını geri yükler.
- `#nullable disable annotations`: Nullable ek açıklama bağlamını *devre dışı* olarak ayarlar.
- `#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını *etkin* olarak ayarlar.
- `#nullable restore annotations`: Null yapılabilir ek açıklama bağlamını proje ayarlarına geri yükler.
- `#nullable disable warnings`: Nullable uyarı bağlamını *devre dışı* olarak ayarlar.
- `#nullable enable warnings`: Null yapılabilir uyarı bağlamını *etkin* olarak ayarlar.
- `#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
