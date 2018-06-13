---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40820a805310786eeb0effd7c5284c1a70a6e70b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407606"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="1a999-102">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="1a999-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="1a999-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="1a999-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1a999-104">Bir özel durum işleme için belirli bir ara dile (IL) kod (EH) yan tümcesinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a999-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a999-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a999-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1a999-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1a999-106">Members</span></span>  
  
|<span data-ttu-id="1a999-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1a999-107">Member</span></span>|<span data-ttu-id="1a999-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a999-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="1a999-109">Özel durum bilgilerini EH yan tümcesinde açıklar bir bit alanı.</span><span class="sxs-lookup"><span data-stu-id="1a999-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="1a999-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1a999-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="1a999-111">Bayt cinsinden uzaklık, `try` blok yöntem gövdesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="1a999-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="1a999-112">Bayt cinsinden uzunluğu, `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="1a999-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="1a999-113">Bu işleyici konumunu `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="1a999-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="1a999-114">İşleyici kod bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1a999-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="1a999-115">Meta veri simgesi türü dayalı bir özel durum işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1a999-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="1a999-116">Bir filtre dayalı bir özel durum işleyicisi yöntem gövdesi başından bayt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1a999-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a999-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a999-117">Remarks</span></span>  
 <span data-ttu-id="1a999-118">Bir dizi `CoreDebugEHClause` değerleri tarafından döndürülen [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a999-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="1a999-119">EH yan tümcesi bilgi CLI belirtimine göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1a999-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="1a999-120">Daha fazla bilgi için bkz: [standart ECMA-355: ortak dil altyapısı (CLI), 6 Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="1a999-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="1a999-121">`flags` Alan aşağıdaki bayraklar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1a999-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="1a999-122">Bunlar CorDebug.idl veya CorDebug.h tanımlanmayan olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1a999-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="1a999-123">Bayrağı</span><span class="sxs-lookup"><span data-stu-id="1a999-123">Flag</span></span>|<span data-ttu-id="1a999-124">Değer</span><span class="sxs-lookup"><span data-stu-id="1a999-124">Value</span></span>|<span data-ttu-id="1a999-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a999-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="1a999-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="1a999-126">0x00000000</span></span>|<span data-ttu-id="1a999-127">Türü belirtilmiş özel durum yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a999-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="1a999-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="1a999-128">0x00000001</span></span>|<span data-ttu-id="1a999-129">Bir özel durum filtresi ve işleyici yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a999-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="1a999-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="1a999-130">0x00000002</span></span>|<span data-ttu-id="1a999-131">A `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1a999-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="1a999-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="1a999-132">0x00000004</span></span>|<span data-ttu-id="1a999-133">Bir arıza yan tümcesi (bir `finally` yalnızca bir özel durum oluştuğunda çağrılır yan tümcesi).</span><span class="sxs-lookup"><span data-stu-id="1a999-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a999-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a999-134">Requirements</span></span>  
 <span data-ttu-id="1a999-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a999-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a999-136">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a999-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a999-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a999-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a999-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a999-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a999-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a999-139">See Also</span></span>  
 [<span data-ttu-id="1a999-140">GetEHClauses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a999-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="1a999-141">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1a999-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
