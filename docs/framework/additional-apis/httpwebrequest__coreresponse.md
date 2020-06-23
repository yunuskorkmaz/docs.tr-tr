---
title: HttpWebRequest. _CoreResponse alanı
description: .NET 'teki HttpWebRequest. _CoreResponse alanı hakkında bilgi edinin. Bu alan, HTTP yanıtı ayrıştırma sonucunu içeren bir CoreResponseData veya Exception nesnesidir.
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
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989752"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="6e669-104">HttpWebRequest. \_ CoreResponse alanı</span><span class="sxs-lookup"><span data-stu-id="6e669-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="6e669-105">`HttpWebRequest._CoreResponse`HTTP yanıtı ayrıştırma sonucunu içeren bir nesne (bir [CoreResponseData](coreresponsedata.md) veya a <xref:System.Exception> ).</span><span class="sxs-lookup"><span data-stu-id="6e669-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e669-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e669-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="6e669-107">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="6e669-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="6e669-108">Bunun yerine, <xref:System.Diagnostics.DiagnosticSource> ağ kodunu bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e669-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="6e669-109">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="6e669-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="6e669-110">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6e669-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e669-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e669-111">Requirements</span></span>

<span data-ttu-id="6e669-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6e669-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6e669-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="6e669-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6e669-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e669-114">**.NET Framework versions:** Available since 2.0.</span></span>
