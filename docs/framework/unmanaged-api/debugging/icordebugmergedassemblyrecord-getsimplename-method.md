---
title: 'Icordebugmergedassemblyrecord:: GetSimpleName yöntemi'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 565e27b47f2454dec1e4c2b89ee46ac5279b08b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130546"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="b439b-102">Icordebugmergedassemblyrecord:: GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="b439b-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="b439b-103">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="b439b-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b439b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b439b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b439b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b439b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b439b-106">'ndaki `szName` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b439b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b439b-107">dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b439b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b439b-108">Karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b439b-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b439b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b439b-109">Remarks</span></span>  
 <span data-ttu-id="b439b-110">Bu yöntem, bir derlemenin ("System. Collections" gibi) basit adını dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan alır.</span><span class="sxs-lookup"><span data-stu-id="b439b-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="b439b-111">Yönetilen koddaki <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b439b-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b439b-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b439b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b439b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b439b-113">Requirements</span></span>  
 <span data-ttu-id="b439b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b439b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b439b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b439b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b439b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b439b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b439b-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b439b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b439b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b439b-118">See also</span></span>

- [<span data-ttu-id="b439b-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b439b-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b439b-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b439b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
