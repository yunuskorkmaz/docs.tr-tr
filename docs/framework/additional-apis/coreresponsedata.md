---
title: CoreResponseData Sınıfı
description: HTTP üstbilgilerinin ve yanıt gövdesinin ayrıştırılmasını temsil eden CoreResponseData sınıfını anlayın. .NET 'teki System.Net ad alanıdır.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 8248cc20f6528a1c3bc64c9b9339a3a3000d03a0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989806"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="40299-104">CoreResponseData Sınıfı</span><span class="sxs-lookup"><span data-stu-id="40299-104">CoreResponseData Class</span></span>

<span data-ttu-id="40299-105">`CoreResponseData`Sınıfı, http üst bilgilerinin ve yanıt gövdesinin ayrıştırılmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40299-105">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="40299-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="40299-106">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="40299-107">Bu API iç ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="40299-107">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="40299-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="40299-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="40299-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="40299-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="40299-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="40299-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="40299-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40299-111">Requirements</span></span>

<span data-ttu-id="40299-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="40299-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="40299-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="40299-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="40299-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40299-114">**.NET Framework versions:** Available since 2.0.</span></span>
