---
title: CoreResponseData Sınıfı
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
ms.openlocfilehash: fd0ffb982c22b0a8b6cb5dd677faafb9921bf5d9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741027"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="bbf35-102">CoreResponseData Sınıfı</span><span class="sxs-lookup"><span data-stu-id="bbf35-102">CoreResponseData Class</span></span>

<span data-ttu-id="bbf35-103">`CoreResponseData` sınıfı, HTTP üst bilgilerinin ve yanıt gövdesinin ayrıştırılmasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bbf35-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbf35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbf35-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="bbf35-105">Bu API iç ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="bbf35-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="bbf35-106">Bunun yerine, ağ kodunu bağlamak için bir <xref:System.Diagnostics.DiagnosticSource> kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbf35-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="bbf35-107">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="bbf35-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="bbf35-108">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bbf35-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbf35-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbf35-109">Requirements</span></span>

<span data-ttu-id="bbf35-110">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bbf35-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bbf35-111">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="bbf35-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="bbf35-112">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf35-112">**.NET Framework versions:** Available since 2.0.</span></span>
