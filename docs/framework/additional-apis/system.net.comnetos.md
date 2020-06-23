---
title: ComNetOS sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990426"
---
# <a name="comnetos-class"></a><span data-ttu-id="d25ff-102">ComNetOS sınıfı</span><span class="sxs-lookup"><span data-stu-id="d25ff-102">ComNetOS class</span></span>

<span data-ttu-id="d25ff-103">Geçerli işletim sistemi hakkında, sürümü ve yükleme türü (istemci veya sunucu) gibi bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d25ff-103">Provides information about the current operating system, such as its version and installation type (client or server).</span></span> <span data-ttu-id="d25ff-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="d25ff-104">This class cannot be inherited.</span></span>
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> <span data-ttu-id="d25ff-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d25ff-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d25ff-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d25ff-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="iswin7orlater-field"></a><span data-ttu-id="d25ff-107">IsWin7orLater alanı</span><span class="sxs-lookup"><span data-stu-id="d25ff-107">IsWin7orLater field</span></span>

<span data-ttu-id="d25ff-108">İşletim sistemi sürümünün Windows 7 veya sonraki bir sürümü olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d25ff-108">Specifies whether the operating system version is Windows 7 or later.</span></span>

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a><span data-ttu-id="d25ff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d25ff-109">Requirements</span></span>

<span data-ttu-id="d25ff-110">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d25ff-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d25ff-111">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="d25ff-111">**Assembly:** System (in System.dll)</span></span>
