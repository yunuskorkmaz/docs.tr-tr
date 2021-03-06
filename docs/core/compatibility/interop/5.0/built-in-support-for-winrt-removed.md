---
title: "Son değişiklik: WinRT için yerleşik destek .NET 'ten kaldırılmıştır"
description: .NET 5 ' teki birlikte çalışma için yerleşik desteğin .NET 'ten kaldırıldığı hakkında bilgi edinin.
ms.date: 10/13/2020
ms.openlocfilehash: 986b810b74c7e7d7514ec2b734bfab45e29b87fa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256692"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a>WinRT için yerleşik destek .NET 'ten kaldırılmıştır

.NET 'te [Windows çalışma zamanı (WinRT)](/uwp/winrt-cref/winrt-type-system) API 'leri tüketimi için yerleşik destek kaldırılmıştır.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce CoreCLR, etkin ve WinRT türlerini tüketen [Windows meta verileri (WinMD) dosyalarını](/uwp/winrt-cref/winmd-files) tüketebilir. .NET 5 ' den başlayarak CoreCLR artık WinMD dosyalarını doğrudan tüketmez.

Desteklenmeyen bir derlemeye başvuru yapmaya çalışırsanız, bir ile karşılaşırsınız <xref:System.IO.FileNotFoundException> . Bir WinRT sınıfını etkinleştirirseniz bir ile karşılaşırsınız <xref:System.PlatformNotSupportedException> .

Bu son değişiklik aşağıdaki nedenlerden dolayı yapılmıştır:

- Bu nedenle, WinRT .NET çalışma zamanından ayrı olarak geliştirilebilir ve artırılabilir.
- İOS ve Android gibi diğer işletim sistemleri için sunulan birlikte çalışma sistemlerine sahip simetri için.
- C# özellikleri, ara dil (IL) bağlama ve zaman içinde (AOT) derleme gibi diğer .NET özelliklerinden yararlanmak için.
- .NET çalışma zamanı kod temelinin basitleşmesini sağlar.

## <a name="recommended-action"></a>Önerilen eylem

- [Microsoft. Windows. SDK. Contracts paketine](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)başvuruları kaldırın.  Bunun yerine, projenin özelliği aracılığıyla erişmek istediğiniz Windows API 'lerinin sürümünü belirtin `TargetFramework` .  Örnek:

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- .NET 5 ve sonraki sürümler için WinRT API 'Leri ve türleri oluşturmak veya özelleştirmek üzere [C#/wınrt](/windows/uwp/csharp-winrt/) araç zincirini kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
