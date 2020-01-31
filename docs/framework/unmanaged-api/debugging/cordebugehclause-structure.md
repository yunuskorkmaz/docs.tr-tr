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
ms.openlocfilehash: 197c33511a474eb8291e4361ebb3c21fb3720cae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789421"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="14e94-102">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="14e94-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="14e94-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="14e94-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="14e94-104">Belirli bir ara dil (IL) kodu parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14e94-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e94-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14e94-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="14e94-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="14e94-106">Members</span></span>  
  
|<span data-ttu-id="14e94-107">Üye</span><span class="sxs-lookup"><span data-stu-id="14e94-107">Member</span></span>|<span data-ttu-id="14e94-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14e94-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="14e94-109">EH yan tümcesindeki özel durum bilgilerini açıklayan bir bit alanı.</span><span class="sxs-lookup"><span data-stu-id="14e94-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="14e94-110">Daha fazla bilgi için, açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="14e94-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="14e94-111">Yöntem gövdesinin başlangıcından itibaren `try` bloğunun bayt cinsinden değeri.</span><span class="sxs-lookup"><span data-stu-id="14e94-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="14e94-112">`try` bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="14e94-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="14e94-113">Bu `try` bloğunun işleyicisinin konumu.</span><span class="sxs-lookup"><span data-stu-id="14e94-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="14e94-114">İşleyici kodunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="14e94-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="14e94-115">Tür tabanlı özel durum işleyicisi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="14e94-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="14e94-116">Filtre tabanlı özel durum işleyicisi için Yöntem gövdesinin başından itibaren bayt cinsinden fark.</span><span class="sxs-lookup"><span data-stu-id="14e94-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14e94-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14e94-117">Remarks</span></span>  
 <span data-ttu-id="14e94-118">`CoreDebugEHClause` değerleri dizisi [Getehyan tümceleri](icordebugilcode-getehclauses-method.md) yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="14e94-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="14e94-119">EH yan tümce bilgileri CLı belirtimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="14e94-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="14e94-120">Daha fazla bilgi için bkz. [standart ECMA-355: ortak dil altyapısı (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="14e94-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="14e94-121">`flags` alanı aşağıdaki bayrakları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="14e94-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="14e94-122">Bunların CorDebug. IDL veya CorDebug. h içinde tanımlanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="14e94-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="14e94-123">Bayrağı</span><span class="sxs-lookup"><span data-stu-id="14e94-123">Flag</span></span>|<span data-ttu-id="14e94-124">Değer</span><span class="sxs-lookup"><span data-stu-id="14e94-124">Value</span></span>|<span data-ttu-id="14e94-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14e94-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="14e94-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="14e94-126">0x00000000</span></span>|<span data-ttu-id="14e94-127">Türü belirtilmiş bir özel durum yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14e94-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="14e94-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="14e94-128">0x00000001</span></span>|<span data-ttu-id="14e94-129">Özel durum filtresi ve işleyici yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14e94-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="14e94-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="14e94-130">0x00000002</span></span>|<span data-ttu-id="14e94-131">`finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14e94-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="14e94-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="14e94-132">0x00000004</span></span>|<span data-ttu-id="14e94-133">Bir hata tümcesi (yalnızca bir özel durum oluştuğunda çağrılan bir `finally` yan tümcesi).</span><span class="sxs-lookup"><span data-stu-id="14e94-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14e94-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14e94-134">Requirements</span></span>  
 <span data-ttu-id="14e94-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e94-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e94-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="14e94-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14e94-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14e94-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14e94-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e94-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e94-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14e94-139">See also</span></span>

- [<span data-ttu-id="14e94-140">GetEHClauses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14e94-140">GetEHClauses Method</span></span>](icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="14e94-141">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="14e94-141">Debugging Structures</span></span>](debugging-structures.md)
