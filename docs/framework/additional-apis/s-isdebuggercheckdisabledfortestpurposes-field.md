---
description: 'Hakkında daha fazla bilgi edinin: s_isDebuggerCheckDisabledForTestPurposes alanı'
title: s_isDebuggerCheckDisabledForTestPurposes alanı
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: a71235c13a7a35872bcf5374be8077bafad5ff9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802664"
---
# <a name="s_isdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="56c62-103">s_isDebuggerCheckDisabledForTestPurposes alanı</span><span class="sxs-lookup"><span data-stu-id="56c62-103">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="56c62-104">Sınıftaki bu özel alan `System.Windows.Diagnostics.VisualDiagnostics` , Visual Studio tarafından etkin bir hata ayıklayıcı için iç denetim yapılıp yapılmayacağını anlamak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56c62-104">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="56c62-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="56c62-105">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="56c62-106">Sınıftaki API 'Ler `System.Windows.Diagnostics.VisualDiagnostics` yalnızca bir uygulama hata ayıklayıcı altında çalışırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56c62-106">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="56c62-107">`s_isDebuggerCheckDisabledForTestPurposes` `true` Bir hata ayıklayıcı dışında API 'lere erişmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56c62-107">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="56c62-108">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="56c62-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="56c62-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56c62-109">Requirements</span></span>

<span data-ttu-id="56c62-110">**Ad alanı:**<xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="56c62-110">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="56c62-111">**Bütünleştirilmiş kod:** PresentationCore (PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="56c62-111">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="56c62-112">**.NET Framework sürümleri:** 4,6 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56c62-112">**.NET Framework versions:** Available since 4.6.</span></span>
