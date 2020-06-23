---
title: Exception. PrepForRemoting yöntemi (sistem)
description: .NET 'teki özel durumu gözden geçirin. Yöntemi, istemci sırasında özel durum yeniden oluşturulmadan önce iletiye sunucu tarafı yığın izlemesini ekler.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105256"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="69939-104">Exception.PrepForRemoting Metodu</span><span class="sxs-lookup"><span data-stu-id="69939-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="69939-105">Özel durum istemci çağrı sitesinde yeniden oluşturulmadan önce iletiye ekleyerek sunucu tarafı yığın izlemesini korur.</span><span class="sxs-lookup"><span data-stu-id="69939-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="69939-106">Döndürülenler</span><span class="sxs-lookup"><span data-stu-id="69939-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="69939-107">Bu <xref:System.Exception> örnek.</span><span class="sxs-lookup"><span data-stu-id="69939-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="69939-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69939-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="69939-109">`Exception.PrepForRemoting`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="69939-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="69939-110">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="69939-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="69939-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69939-111">Requirements</span></span>

<span data-ttu-id="69939-112">**Ad alanı:**<xref:System></span><span class="sxs-lookup"><span data-stu-id="69939-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="69939-113">**Bütünleştirilmiş kod:** mscorlib.dll (mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="69939-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="69939-114">**.NET Framework sürümleri:** 1,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69939-114">**.NET Framework versions:** Available since 1.0.</span></span>
