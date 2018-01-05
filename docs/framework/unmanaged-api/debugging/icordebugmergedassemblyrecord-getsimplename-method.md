---
title: "ICorDebugMergedAssemblyRecord::GetSimpleName yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 085ca56b3a839689ea38459057957faa81d1dfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="cc567-102">ICorDebugMergedAssemblyRecord::GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc567-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="cc567-103">Basit derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="cc567-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc567-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc567-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc567-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc567-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cc567-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="cc567-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cc567-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="cc567-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cc567-108">Bir karakter dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc567-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc567-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc567-109">Remarks</span></span>  
 <span data-ttu-id="cc567-110">Bu yöntem, bir dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci bir derleme (örneğin, "System.Collections"), basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="cc567-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="cc567-111">İçin karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> yönetilen kodda özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc567-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc567-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc567-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc567-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc567-113">Requirements</span></span>  
 <span data-ttu-id="cc567-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc567-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc567-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc567-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc567-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc567-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc567-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc567-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc567-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc567-118">See Also</span></span>  
 [<span data-ttu-id="cc567-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc567-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="cc567-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc567-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
