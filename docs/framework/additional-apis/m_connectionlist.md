---
title: ConnectionGroup.m_ConnectionList Alanı
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155856"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="d2535-102">ConnectionGroup.m\_ConnectionList Alanı</span><span class="sxs-lookup"><span data-stu-id="d2535-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="d2535-103">`ConnectionGroup.m_ConnectionList`<xref:System.Collections.ArrayList> aynı URI'ye hizmet eden ve son kullanma ve kimlik doğrulama gibi diğer bazı özellikler için aynı değerleri paylaşan bağlantı nesnelerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="d2535-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2535-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2535-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="d2535-105">Alan `ConnectionGroup.m_ConnectionList` özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2535-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d2535-106">Microsoft, hiçbir koşulda bir üretim uygulamasında bu alanın kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d2535-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2535-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2535-107">Requirements</span></span>

<span data-ttu-id="d2535-108">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d2535-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d2535-109">**Montaj:** Sistem (System.dll'de)</span><span class="sxs-lookup"><span data-stu-id="d2535-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d2535-110">**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d2535-110">**.NET Framework versions:** Available since 2.0.</span></span>
