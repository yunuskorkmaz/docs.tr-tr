---
title: Platformlar arası P/Invoke
description: Çalışma zamanının P/Invoke aracılığıyla yerel kitaplıkları yüklerken hangi yolları arayılacağını öğrenin. Ayrıca Setdllımportresolver 'ı kullanmayı öğrenin.
author: saul
ms.date: 01/31/2021
ms.openlocfilehash: 40ad87fe537ad043a488e4086814a58ef8e0211e
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427487"
---
# <a name="writing-cross-platform-pinvoke-code"></a>Platformlar arası P/Invoke kodu yazma

## <a name="library-name-variations"></a>Kitaplık adı çeşitlemeleri

Daha basit çapraz platform P/Invoke kodunu kolaylaştırmak için, çalışma zamanı kurallı Paylaşılan kitaplık uzantısını ( `.dll` `.so` veya `.dylib` ) yerel kitaplık adlarına ekler. Linux ve macOS 'ta çalışma zamanı de önceden bekleyen ' i dener `lib` . Yönetilmeyen kitaplıkları (örn.) yükleyen API 'Leri kullandığınızda bu kitaplık adları çeşitlemeleri otomatik olarak aranır <xref:System.Runtime.InteropServices.DllImportAttribute> .

> [!NOTE]
> Kitaplık adlarındaki mutlak yollar (örn. `/usr/lib/libc` ) olduğu gibi değerlendirilir ve hiçbir değişim aranmaz.

P/Invoke kullanma ile aşağıdaki örneği göz önünde bulundurun:

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

Windows üzerinde çalışırken, DLL aşağıdaki sırayla aranır:

1. `nativedep`
1. `nativedep.dll` (kitaplık adı zaten veya ile bitmezse `.dll` `exe` )

Linux veya macOS üzerinde çalışırken, çalışma zamanı, önceden bekleyen `lib` ve kurallı Paylaşılan kitaplık uzantısını eklemeye çalışacaktır. Bu OSE 'de, Kitaplık adı çeşitlemeleri aşağıdaki sırada denenir:

1. `nativedep.so` / `nativedep.dylib`
1. `libnativedep.so` / `libnativedep.dylib`<sup>1</sup>
1. `nativedep`
1. `libnativedep`<sup>1</sup>

Linux 'ta, Kitaplık adı ile `.so` veya Contains `.so.` (sondaki) ile bitiyorsa arama sırası farklı olur `.` . Aşağıdaki örneği inceleyin:

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

Bu durumda, Kitaplık adı çeşitlemeleri aşağıdaki sırada denenir:

1. `nativedep.so.6`
1. `libnativedep.so.6`<sup>1</sup>
1. `nativedep.so.6.so`
1. `libnativedep.so.6.so`<sup>1</sup>

<sup>1</sup> yol, yalnızca kitaplık adı bir dizin ayırıcı karakteri () içermiyorsa denetlenir `/` .

## <a name="custom-import-resolver"></a>Özel içeri aktarma Çözümleyicisi

Daha karmaşık senaryolarda, <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> çalışma ZAMANıNDA DLL içeri aktarmaları çözümlemek için kullanabilirsiniz. Aşağıdaki örnekte, `nativedep` `nativedep_avx2` CPU destekliyorsa olarak çözümlenir.

> [!TIP]
> Bu işlevsellik yalnızca .NET 5 ve .NET Core 3,1 veya üzeri sürümlerde kullanılabilir.

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma (P/Invoke)](pinvoke.md)
