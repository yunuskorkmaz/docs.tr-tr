---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core 2,1-3,1 için MSBuild 'teki son değişiklikleri listeler.
ms.date: 02/22/2021
ms.openlocfilehash: 03fcd9807a83c4f679dc659b009c857e351b9b2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105649"
---
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a>.NET Core 2,1-3,1 ' de MSBuild bölünmesi değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | - |
| [Tasarım zamanı derlemeleri yalnızca üst düzey paket başvurularını döndürüyor](#design-time-builds-only-return-top-level-package-references) | 3,1 |
| [Kaynak bildirimi dosya adı değişikliği](#resource-manifest-file-name-change) | 3.0 |
| [Proje Araçları artık SDK 'ya dahil edilmiştir](#project-tools-now-included-in-sdk) | 2.1 |

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
