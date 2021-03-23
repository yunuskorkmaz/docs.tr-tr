---
title: HttpWebRequest._CoreResponse alanı
description: .NET 'teki HttpWebRequest._CoreResponse alanı hakkında bilgi edinin. Bu alan, HTTP yanıtı ayrıştırma sonucunu içeren bir CoreResponseData veya Exception nesnesidir.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: f5fb71c21922285c0e18c2d1f28eeaf2353dcaee
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873841"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="6da8e-104">HttpWebRequest. \_ CoreResponse alanı</span><span class="sxs-lookup"><span data-stu-id="6da8e-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="6da8e-105">`HttpWebRequest._CoreResponse` HTTP yanıtı ayrıştırma sonucunu içeren bir nesne (bir [CoreResponseData](coreresponsedata.md) veya a <xref:System.Exception> ).</span><span class="sxs-lookup"><span data-stu-id="6da8e-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="6da8e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6da8e-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="6da8e-107">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="6da8e-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="6da8e-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6da8e-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="6da8e-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="6da8e-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="6da8e-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6da8e-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6da8e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6da8e-111">Requirements</span></span>

<span data-ttu-id="6da8e-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6da8e-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6da8e-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="6da8e-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6da8e-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6da8e-114">**.NET Framework versions:** Available since 2.0.</span></span>
