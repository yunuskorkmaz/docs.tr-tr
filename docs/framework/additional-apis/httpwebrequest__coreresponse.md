---
title: HttpWebRequest._CoreResponse Alanı
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
ms.openlocfilehash: b275f3eece96ac8a9ae3fb0ebd030c8d79e21fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155927"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="c8b20-102">httpwebrequest. \_CoreResponse Alanı</span><span class="sxs-lookup"><span data-stu-id="c8b20-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="c8b20-103">`HttpWebRequest._CoreResponse`http yanıt ayrıştırma sonucunu <xref:System.Exception>içeren bir nesnedir (coreresponsedata veya bir) [CoreResponseData](coreresponsedata.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8b20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8b20-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="c8b20-105">Bu API doğrudan kodunuzda kullanılmak üzere değildir.</span><span class="sxs-lookup"><span data-stu-id="c8b20-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="c8b20-106">Bunun yerine, bir <xref:System.Diagnostics.DiagnosticSource> bağlantı ağ kodu kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c8b20-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="c8b20-107">[Bkz. DiagnosticSource Kullanıcı Kılavuzu.](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)</span><span class="sxs-lookup"><span data-stu-id="c8b20-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="c8b20-108">Microsoft, hiçbir koşulda bir üretim uygulamasında bu sınıfın kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c8b20-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c8b20-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8b20-109">Requirements</span></span>

<span data-ttu-id="c8b20-110">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c8b20-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c8b20-111">**Montaj:** Sistem (System.dll'de)</span><span class="sxs-lookup"><span data-stu-id="c8b20-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c8b20-112">**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c8b20-112">**.NET Framework versions:** Available since 2.0.</span></span>
