---
description: 'Daha fazla bilgi edinin: HttpStatusDescription sınıfı'
title: HttpStatusDescription sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa135a6421397ce6b7be2af05d66aa8e81beafb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802508"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="0ee23-103">HttpStatusDescription sınıfı</span><span class="sxs-lookup"><span data-stu-id="0ee23-103">HttpStatusDescription class</span></span>

<span data-ttu-id="0ee23-104">Standart HTTP durum açıklamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ee23-104">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="0ee23-105">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="0ee23-105">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="0ee23-106">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ee23-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0ee23-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0ee23-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="0ee23-108">Get yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ee23-108">Get method</span></span>

<span data-ttu-id="0ee23-109">Belirtilen HTTP durum koduyla ilişkili açıklamayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ee23-109">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="0ee23-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ee23-110">Parameters</span></span>

<span data-ttu-id="0ee23-111">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="0ee23-111">`code` <xref:System.Int32></span></span>

<span data-ttu-id="0ee23-112">HTTP durum kodu, örneğin, `404` .</span><span class="sxs-lookup"><span data-stu-id="0ee23-112">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="0ee23-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="0ee23-113">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="0ee23-114">HTTP durum açıklaması.</span><span class="sxs-lookup"><span data-stu-id="0ee23-114">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ee23-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ee23-115">Requirements</span></span>

<span data-ttu-id="0ee23-116">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0ee23-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0ee23-117">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="0ee23-117">**Assembly:** System (in System.dll)</span></span>
