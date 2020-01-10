---
title: CoreResponseData. m_ResponseHeaders alanı
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
ms.openlocfilehash: df0b592a5f85d4c99dee4ecb60963f4abb560a13
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741011"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="66f0e-102">CoreResponseData. d\_ResponseHeaders alanı</span><span class="sxs-lookup"><span data-stu-id="66f0e-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="66f0e-103">`CoreResponseData.m_ResponseHeaders`, sunucu yanıtıyla ilişkili üst bilgilerin bir <xref:System.Net.WebHeaderCollection>.</span><span class="sxs-lookup"><span data-stu-id="66f0e-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="66f0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66f0e-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="66f0e-105">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="66f0e-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="66f0e-106">Bunun yerine, ağ kodunu bağlamak için bir <xref:System.Diagnostics.DiagnosticSource> kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66f0e-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="66f0e-107">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="66f0e-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="66f0e-108">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66f0e-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="66f0e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66f0e-109">Requirements</span></span>

<span data-ttu-id="66f0e-110">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="66f0e-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="66f0e-111">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="66f0e-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="66f0e-112">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66f0e-112">**.NET Framework versions:** Available since 2.0.</span></span>
