---
title: Birlikte çalışma son değişiklikleri
description: .NET Core ve .NET 5,0 ve üzeri sürümlerde birlikte çalışma içindeki son değişiklikleri listeler.
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438054"
---
# <a name="interop-breaking-changes"></a>Birlikte çalışma son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [Bir arabirime RCW atama `InterfaceIsIInspectable` PlatformNotSupportedException oluşturur](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | 5.0 |
| [Windows dışı platformlarda bir/W soneki yoklama yok](#no-aw-suffix-probing-on-non-windows-platforms) | 5.0 |
| [WinRT için yerleşik destek .NET 'ten kaldırılmıştır](#built-in-support-for-winrt-is-removed-from-net) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
