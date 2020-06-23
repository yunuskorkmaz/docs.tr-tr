---
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
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990423"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="d8626-102">HttpStatusDescription sınıfı</span><span class="sxs-lookup"><span data-stu-id="d8626-102">HttpStatusDescription class</span></span>

<span data-ttu-id="d8626-103">Standart HTTP durum açıklamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8626-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="d8626-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="d8626-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="d8626-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8626-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d8626-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d8626-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="d8626-107">Get yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8626-107">Get method</span></span>

<span data-ttu-id="d8626-108">Belirtilen HTTP durum koduyla ilişkili açıklamayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8626-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="d8626-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8626-109">Parameters</span></span>

<span data-ttu-id="d8626-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="d8626-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="d8626-111">HTTP durum kodu, örneğin, `404` .</span><span class="sxs-lookup"><span data-stu-id="d8626-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="d8626-112">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="d8626-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="d8626-113">HTTP durum açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d8626-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8626-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8626-114">Requirements</span></span>

<span data-ttu-id="d8626-115">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d8626-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d8626-116">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="d8626-116">**Assembly:** System (in System.dll)</span></span>
