---
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
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990356"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="0e108-102">WebHeaderCollection. Addınternal yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e108-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="0e108-103">Denetimleri atlayarak, belirtilen ad ve değere sahip yeni bir üst bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="0e108-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="0e108-104">Bu yöntem dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e108-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0e108-105">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0e108-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="0e108-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e108-106">Parameters</span></span>

- <span data-ttu-id="0e108-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0e108-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="0e108-108">Üstbilginin adı.</span><span class="sxs-lookup"><span data-stu-id="0e108-108">The name of the header.</span></span>

- <span data-ttu-id="0e108-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="0e108-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="0e108-110">Üst bilginin değeri.</span><span class="sxs-lookup"><span data-stu-id="0e108-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e108-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e108-111">Requirements</span></span>

<span data-ttu-id="0e108-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0e108-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0e108-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="0e108-113">**Assembly:** System (in System.dll)</span></span>
