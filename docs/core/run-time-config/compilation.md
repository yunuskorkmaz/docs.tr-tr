---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802822"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="63d9e-103">Derleme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="63d9e-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="63d9e-104">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="63d9e-104">Tiered compilation</span></span>

- <span data-ttu-id="63d9e-105">JıT derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="63d9e-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="63d9e-106">.NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="63d9e-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="63d9e-107">.NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="63d9e-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="63d9e-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="63d9e-108">Setting name</span></span> | <span data-ttu-id="63d9e-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="63d9e-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="63d9e-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="63d9e-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="63d9e-111">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="63d9e-111">`true` - enabled</span></span><br/><span data-ttu-id="63d9e-112">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="63d9e-112">`false` - disabled</span></span> |
| <span data-ttu-id="63d9e-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="63d9e-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="63d9e-114">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="63d9e-114">`1` - enabled</span></span><br/><span data-ttu-id="63d9e-115">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="63d9e-115">`0` - disabled</span></span> |
