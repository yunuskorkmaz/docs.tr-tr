---
description: 'Hakkında daha fazla bilgi edinin: TlsStream.m_Worker alanı'
title: TlsStream.m_Worker alanı (System.Net)
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
ms.openlocfilehash: d929b0b1949bc1902425c016bfd770d4c66a3257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699525"
---
# <a name="tlsstreamm_worker-field"></a><span data-ttu-id="d45db-103">TlsStream.m_Worker alanı</span><span class="sxs-lookup"><span data-stu-id="d45db-103">TlsStream.m_Worker Field</span></span>

<span data-ttu-id="d45db-104">SSL akışının durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d45db-104">Represents the state of the SSL stream.</span></span>

## <a name="syntax"></a><span data-ttu-id="d45db-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d45db-105">Syntax</span></span>

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a><span data-ttu-id="d45db-106">Alan değeri</span><span class="sxs-lookup"><span data-stu-id="d45db-106">Field value</span></span>

`System.Net.Security.SslState`  
<span data-ttu-id="d45db-107">SSL akışının durumu.</span><span class="sxs-lookup"><span data-stu-id="d45db-107">The state of the SSL stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="d45db-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d45db-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d45db-109">`TlsStream.m_Worker`Alan özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="d45db-109">The `TlsStream.m_Worker` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d45db-110">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d45db-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d45db-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d45db-111">Requirements</span></span>

<span data-ttu-id="d45db-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d45db-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d45db-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="d45db-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d45db-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d45db-114">**.NET Framework versions:** Available since 2.0.</span></span>
