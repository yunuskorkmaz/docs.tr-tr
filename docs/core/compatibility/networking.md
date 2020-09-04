---
title: Ağ bozan değişiklikler
description: .NET Core 'da ağ üzerindeki son değişiklikleri listeler.
ms.date: 05/05/2020
ms.openlocfilehash: fa5807c882c3bc6f66e8a27361ccc14254e90b3e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465526"
---
# <a name="networking-breaking-changes"></a>Ağ bozan değişiklikler

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Tanıtılan sürüm |
| - | - |
| [.NET çalışma zamanından WinHttpHandler kaldırıldı](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [Multicastop. Group null bir değer kabul etmez](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [Tanımlama bilgisi yol işleme artık RFC 6265 ' e uyar](#cookie-path-handling-now-conforms-to-rfc-6265) | 5.0 |
| [HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. Iptallasync her zaman hemen iptal etmez](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
