---
title: ICorDebugMergedAssemblyRecord::GetSimpleName yöntemi
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df142ea8f02d5cefc5c63a2d376afb331b4379ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197990"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="67a5c-102">ICorDebugMergedAssemblyRecord::GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="67a5c-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="67a5c-103">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="67a5c-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67a5c-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67a5c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="67a5c-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="67a5c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="67a5c-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="67a5c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="67a5c-108">Bir karakter dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67a5c-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67a5c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67a5c-109">Remarks</span></span>  
 <span data-ttu-id="67a5c-110">Bu yöntem, bir dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci (örneğin, "System.Collections"), bir derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="67a5c-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="67a5c-111">Karşılık <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> yönetilen kodda özelliği.</span><span class="sxs-lookup"><span data-stu-id="67a5c-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67a5c-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67a5c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a5c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67a5c-113">Requirements</span></span>  
 <span data-ttu-id="67a5c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a5c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a5c-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67a5c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67a5c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67a5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67a5c-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a5c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a5c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67a5c-118">See also</span></span>

- [<span data-ttu-id="67a5c-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67a5c-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="67a5c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67a5c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
