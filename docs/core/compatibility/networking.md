---
title: Ağ bozan değişiklikler
description: .NET Core 'da ağ üzerindeki son değişiklikleri listeler.
ms.date: 05/05/2020
ms.openlocfilehash: 568d26bde43ccd6e19fbe2d947f576ef5f99450a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608473"
---
# <a name="networking-breaking-changes"></a>Ağ bozan değişiklikler

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Tanıtılan sürüm |
| - | - |
| [.NET çalışma zamanından WinHttpHandler kaldırıldı](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [Multicastop. Group null bir değer kabul etmez](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi](#default-value-of-httprequestmessageversion-changed-to-11) | 3,0 |
| [WebClient. Iptallasync her zaman hemen iptal etmez](#webclientcancelasync-doesnt-always-cancel-immediately) | 2,0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
