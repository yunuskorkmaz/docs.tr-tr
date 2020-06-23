---
title: CoreResponseData. m_ResponseHeaders alanı
description: .NET 'teki CoreResponseData. m_ResponseHeaders alanını anlayın. Bu alan, sunucu yanıtıyla ilişkili üst bilgilerin bulunduğu bir WebHeaderCollection türüdür.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989787"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="ee749-104">CoreResponseData. d \_ ResponseHeaders alanı</span><span class="sxs-lookup"><span data-stu-id="ee749-104">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="ee749-105">`CoreResponseData.m_ResponseHeaders`, <xref:System.Net.WebHeaderCollection> sunucu yanıtıyla ilişkili üst bilgilerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ee749-105">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee749-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee749-106">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="ee749-107">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="ee749-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="ee749-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee749-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="ee749-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="ee749-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="ee749-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee749-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee749-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee749-111">Requirements</span></span>

<span data-ttu-id="ee749-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ee749-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ee749-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="ee749-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ee749-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee749-114">**.NET Framework versions:** Available since 2.0.</span></span>
