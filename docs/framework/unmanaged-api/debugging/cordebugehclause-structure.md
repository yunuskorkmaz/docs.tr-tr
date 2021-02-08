---
description: 'Daha fazla bilgi edinin: Corhata ayıklama Gehclause yapısı'
title: CorDebugEHClause Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: ecb00e2a110719ab82de32fb1f1c861e2033a528
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801676"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="cea10-103">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="cea10-103">CorDebugEHClause Structure</span></span>

<span data-ttu-id="cea10-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="cea10-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cea10-105">Belirli bir ara dil (IL) kodu parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cea10-105">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cea10-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cea10-106">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="cea10-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cea10-107">Members</span></span>  
  
|<span data-ttu-id="cea10-108">Üye</span><span class="sxs-lookup"><span data-stu-id="cea10-108">Member</span></span>|<span data-ttu-id="cea10-109">Description</span><span class="sxs-lookup"><span data-stu-id="cea10-109">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="cea10-110">EH yan tümcesindeki özel durum bilgilerini açıklayan bir bit alanı.</span><span class="sxs-lookup"><span data-stu-id="cea10-110">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="cea10-111">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cea10-111">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="cea10-112">`try`Metot gövdesinin başlangıcından itibaren bloğunun bayt cinsinden değeri.</span><span class="sxs-lookup"><span data-stu-id="cea10-112">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="cea10-113">Bloğun bayt cinsinden uzunluğu `try` .</span><span class="sxs-lookup"><span data-stu-id="cea10-113">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="cea10-114">Bu bloktaki işleyicinin konumu `try` .</span><span class="sxs-lookup"><span data-stu-id="cea10-114">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="cea10-115">İşleyici kodunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cea10-115">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="cea10-116">Tür tabanlı özel durum işleyicisi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cea10-116">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="cea10-117">Filtre tabanlı özel durum işleyicisi için Yöntem gövdesinin başından itibaren bayt cinsinden fark.</span><span class="sxs-lookup"><span data-stu-id="cea10-117">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cea10-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cea10-118">Remarks</span></span>  

 <span data-ttu-id="cea10-119">Bir dizi `CoreDebugEHClause` değer, [Getehyan tümceleri](icordebugilcode-getehclauses-method.md) yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cea10-119">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="cea10-120">EH yan tümce bilgileri CLı belirtimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cea10-120">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="cea10-121">Daha fazla bilgi için bkz. [standart ECMA-355: ortak dil altyapısı (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="cea10-121">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="cea10-122">`flags`Alanda aşağıdaki bayraklar bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cea10-122">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="cea10-123">Bunların CorDebug. IDL veya CorDebug. h içinde tanımlanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cea10-123">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="cea10-124">Bayrak</span><span class="sxs-lookup"><span data-stu-id="cea10-124">Flag</span></span>|<span data-ttu-id="cea10-125">Değer</span><span class="sxs-lookup"><span data-stu-id="cea10-125">Value</span></span>|<span data-ttu-id="cea10-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cea10-126">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="cea10-127">0x00000000</span><span class="sxs-lookup"><span data-stu-id="cea10-127">0x00000000</span></span>|<span data-ttu-id="cea10-128">Türü belirtilmiş bir özel durum yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="cea10-128">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="cea10-129">0x00000001</span><span class="sxs-lookup"><span data-stu-id="cea10-129">0x00000001</span></span>|<span data-ttu-id="cea10-130">Özel durum filtresi ve işleyici yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="cea10-130">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="cea10-131">0x00000002</span><span class="sxs-lookup"><span data-stu-id="cea10-131">0x00000002</span></span>|<span data-ttu-id="cea10-132">`finally`Yan tümce.</span><span class="sxs-lookup"><span data-stu-id="cea10-132">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="cea10-133">0x00000004</span><span class="sxs-lookup"><span data-stu-id="cea10-133">0x00000004</span></span>|<span data-ttu-id="cea10-134">Bir fault yan tümcesi ( `finally` yalnızca bir özel durum oluştuğunda çağrılan bir yan tümce).</span><span class="sxs-lookup"><span data-stu-id="cea10-134">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cea10-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cea10-135">Requirements</span></span>  

 <span data-ttu-id="cea10-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cea10-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cea10-137">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cea10-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cea10-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cea10-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cea10-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cea10-139">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea10-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cea10-140">See also</span></span>

- [<span data-ttu-id="cea10-141">GetEHClauses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cea10-141">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="cea10-142">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="cea10-142">Debugging Structures</span></span>](debugging-structures.md)
