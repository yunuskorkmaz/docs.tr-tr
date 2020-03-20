---
title: ICorDebugMergedAssemblyRecord::GetSimpleName Yöntemi
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178714"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="04b46-102">ICorDebugMergedAssemblyRecord::GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04b46-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="04b46-103">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="04b46-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04b46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04b46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04b46-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="04b46-106">[içinde] `szName` Arabellekteki karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="04b46-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="04b46-107">[çıkış] Arabelleğe yazılan karakter sayısına `szName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04b46-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="04b46-108">Karakter dizisiiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04b46-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04b46-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04b46-109">Remarks</span></span>  
 <span data-ttu-id="04b46-110">Bu yöntem, dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan bir derlemenin ("System.Collections" gibi) basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="04b46-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="04b46-111">Yönetilen koddaki <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğe karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="04b46-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04b46-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04b46-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04b46-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04b46-113">Requirements</span></span>  
 <span data-ttu-id="04b46-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04b46-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04b46-115">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04b46-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04b46-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04b46-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04b46-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04b46-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b46-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b46-118">See also</span></span>

- [<span data-ttu-id="04b46-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04b46-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="04b46-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04b46-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
