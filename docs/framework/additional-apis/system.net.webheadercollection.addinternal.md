---
description: 'Daha fazla bilgi edinin: WebHeaderCollection. Addınternal yöntemi'
title: WebHeaderCollection. Addınternal yöntemi (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7bc84f84e6656dba5230b627fe9decfc4e0b4746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699486"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="11260-103">WebHeaderCollection. Addınternal yöntemi</span><span class="sxs-lookup"><span data-stu-id="11260-103">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="11260-104">Denetimleri atlayarak, belirtilen ad ve değere sahip yeni bir üst bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="11260-104">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="11260-105">Bu yöntem dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="11260-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="11260-106">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="11260-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="11260-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11260-107">Parameters</span></span>

- <span data-ttu-id="11260-108">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="11260-108">`name` <xref:System.String></span></span>

  <span data-ttu-id="11260-109">Üstbilginin adı.</span><span class="sxs-lookup"><span data-stu-id="11260-109">The name of the header.</span></span>

- <span data-ttu-id="11260-110">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="11260-110">`value` <xref:System.String></span></span>

  <span data-ttu-id="11260-111">Üst bilginin değeri.</span><span class="sxs-lookup"><span data-stu-id="11260-111">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="11260-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11260-112">Requirements</span></span>

<span data-ttu-id="11260-113">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="11260-113">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="11260-114">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="11260-114">**Assembly:** System (in System.dll)</span></span>
