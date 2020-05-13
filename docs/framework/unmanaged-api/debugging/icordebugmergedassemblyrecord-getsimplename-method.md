---
title: 'Icordebugmergedassemblyrecord:: GetSimpleName yöntemi'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: f6c6682c8bb23143d308aa4f1a6887b28ea82fcd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209714"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="96ea4-102">Icordebugmergedassemblyrecord:: GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="96ea4-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="96ea4-103">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="96ea4-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ea4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96ea4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ea4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96ea4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="96ea4-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="96ea4-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="96ea4-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="96ea4-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="96ea4-108">Karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96ea4-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96ea4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96ea4-109">Remarks</span></span>  
 <span data-ttu-id="96ea4-110">Bu yöntem, bir derlemenin ("System. Collections" gibi) basit adını dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan alır.</span><span class="sxs-lookup"><span data-stu-id="96ea4-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="96ea4-111"><xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>Yönetilen koddaki özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="96ea4-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96ea4-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96ea4-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ea4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96ea4-113">Requirements</span></span>  
 <span data-ttu-id="96ea4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ea4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ea4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96ea4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96ea4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96ea4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ea4-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ea4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ea4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96ea4-118">See also</span></span>

- [<span data-ttu-id="96ea4-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96ea4-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="96ea4-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96ea4-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
