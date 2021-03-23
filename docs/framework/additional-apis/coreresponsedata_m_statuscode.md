---
title: CoreResponseData.m_StatusCode alanı
description: .NET 'teki CoreResponseData.m_StatusCode alanı hakkında bilgi edinin. Alan, HTTP yanıtının durumunu içeren bir HttpStatusCode türüdür.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 29e46f71fd6e819dd311b214733fe56ff0548d74
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875908"
---
# <a name="coreresponsedatam_statuscode-field"></a><span data-ttu-id="b93bf-104">CoreResponseData. d \_ StatusCode alanı</span><span class="sxs-lookup"><span data-stu-id="b93bf-104">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="b93bf-105">`CoreResponseData.m_StatusCode`<xref:System.Net.HttpStatusCode>yanıtın durumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b93bf-105">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="b93bf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b93bf-106">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="b93bf-107">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="b93bf-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="b93bf-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b93bf-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="b93bf-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="b93bf-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="b93bf-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b93bf-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b93bf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b93bf-111">Requirements</span></span>

<span data-ttu-id="b93bf-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b93bf-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b93bf-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="b93bf-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b93bf-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b93bf-114">**.NET Framework versions:** Available since 2.0.</span></span>
