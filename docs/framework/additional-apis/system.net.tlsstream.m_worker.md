---
title: TlsStream. m_Worker alanı (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.TlsStream.m_Worker
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: d335820d13e1e15e054e824a284615cdbf6c2094
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847194"
---
# <a name="tlsstreamm_worker-field"></a><span data-ttu-id="5f1e6-102">TlsStream. m_Worker alanı</span><span class="sxs-lookup"><span data-stu-id="5f1e6-102">TlsStream.m_Worker Field</span></span>

<span data-ttu-id="5f1e6-103">SSL akışının durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f1e6-103">Represents the state of the SSL stream.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f1e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f1e6-104">Syntax</span></span>

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a><span data-ttu-id="5f1e6-105">Alan değeri</span><span class="sxs-lookup"><span data-stu-id="5f1e6-105">Field value</span></span>

`System.Net.Security.SslState`  
<span data-ttu-id="5f1e6-106">SSL akışının durumu.</span><span class="sxs-lookup"><span data-stu-id="5f1e6-106">The state of the SSL stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f1e6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f1e6-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5f1e6-108">`TlsStream.m_Worker` alanı özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f1e6-108">The `TlsStream.m_Worker` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5f1e6-109">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5f1e6-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f1e6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f1e6-110">Requirements</span></span>

<span data-ttu-id="5f1e6-111">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5f1e6-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5f1e6-112">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="5f1e6-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5f1e6-113">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f1e6-113">**.NET Framework versions:** Available since 2.0.</span></span>
