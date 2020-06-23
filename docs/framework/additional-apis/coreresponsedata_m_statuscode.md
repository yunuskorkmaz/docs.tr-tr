---
title: CoreResponseData. m_StatusCode alanı
description: .NET 'teki CoreResponseData. m_StatusCode alanı hakkında bilgi edinin. Alan, HTTP yanıtının durumunu içeren bir HttpStatusCode türüdür.
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
ms.openlocfilehash: 05950290bde96511432941ce679e663126878663
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989783"
---
# <a name="coreresponsedatam_statuscode-field"></a><span data-ttu-id="85f85-104">CoreResponseData. d \_ StatusCode alanı</span><span class="sxs-lookup"><span data-stu-id="85f85-104">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="85f85-105">`CoreResponseData.m_StatusCode`<xref:System.Net.HttpStatusCode>yanıtın durumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="85f85-105">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="85f85-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="85f85-106">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="85f85-107">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="85f85-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="85f85-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="85f85-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="85f85-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="85f85-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="85f85-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="85f85-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="85f85-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85f85-111">Requirements</span></span>

<span data-ttu-id="85f85-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="85f85-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="85f85-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="85f85-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="85f85-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85f85-114">**.NET Framework versions:** Available since 2.0.</span></span>
