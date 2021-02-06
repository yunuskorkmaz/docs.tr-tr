---
description: ': Icordebugmergedassemblyrecord:: GetSimpleName metodu hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetSimpleName yöntemi'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: e77a5cc7df009a5bc55a7eb952ead80e5f81f271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650397"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="171dc-103">Icordebugmergedassemblyrecord:: GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="171dc-103">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>

<span data-ttu-id="171dc-104">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="171dc-104">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="171dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="171dc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="171dc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="171dc-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="171dc-107">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="171dc-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="171dc-108">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="171dc-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="171dc-109">Karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="171dc-109">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="171dc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="171dc-110">Remarks</span></span>  

 <span data-ttu-id="171dc-111">Bu yöntem, bir derlemenin ("System. Collections" gibi) basit adını dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan alır.</span><span class="sxs-lookup"><span data-stu-id="171dc-111">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="171dc-112"><xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>Yönetilen koddaki özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="171dc-112">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="171dc-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="171dc-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="171dc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="171dc-114">Requirements</span></span>  

 <span data-ttu-id="171dc-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="171dc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="171dc-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="171dc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="171dc-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="171dc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="171dc-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="171dc-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="171dc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="171dc-119">See also</span></span>

- [<span data-ttu-id="171dc-120">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="171dc-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="171dc-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="171dc-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
