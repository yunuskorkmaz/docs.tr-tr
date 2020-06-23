---
title: Connection. m_WriteList alanı
description: .NET 'teki Connection. m_WriteList alanı hakkında bilgi alın. Bu ArrayList alanı, HTTP üzerinden gönderilmek üzere sıralanmış olan HttpWebRequest nesnelerini içerir.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: a627cb062036e3ab098c2d6e97f9a77ebfa75a33
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989601"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="527a2-104">Connection. d \_ writelist alanı</span><span class="sxs-lookup"><span data-stu-id="527a2-104">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="527a2-105">`Connection.m_WriteList`, <xref:System.Collections.ArrayList> <xref:System.Net.HttpWebRequest> http üzerinden gönderilmek üzere sıralanmış bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="527a2-105">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="527a2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="527a2-106">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="527a2-107">`Connection.m_WriteList`Alan özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="527a2-107">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="527a2-108">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="527a2-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="527a2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="527a2-109">Requirements</span></span>

<span data-ttu-id="527a2-110">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="527a2-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="527a2-111">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="527a2-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="527a2-112">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="527a2-112">**.NET Framework versions:** Available since 2.0.</span></span>
