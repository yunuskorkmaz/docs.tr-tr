---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a4a8e5f99a845d2befe55f5939b41224f2aa47b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077309"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="209aa-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="209aa-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="209aa-103">Derlemenin genel anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="209aa-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="209aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="209aa-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="209aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="209aa-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="209aa-106">[in] En fazla bayt sayısını `pbPublicKeyToken` dizisi.</span><span class="sxs-lookup"><span data-stu-id="209aa-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="209aa-107">[out] Gerçek yazılan bayt sayısı için bir işaretçi `pbPublicKeyToken` dizisi.</span><span class="sxs-lookup"><span data-stu-id="209aa-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="209aa-108">[out] Derlemenin ortak anahtar belirteci içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="209aa-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="209aa-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="209aa-109">Remarks</span></span>  
 <span data-ttu-id="209aa-110">Bir derlemenin ortak anahtar belirteci, ortak anahtarı bir SHA1 karması, son sekiz bayttır.</span><span class="sxs-lookup"><span data-stu-id="209aa-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="209aa-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="209aa-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="209aa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="209aa-112">Requirements</span></span>  
 <span data-ttu-id="209aa-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="209aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="209aa-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="209aa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="209aa-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="209aa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="209aa-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="209aa-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209aa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="209aa-117">See also</span></span>

- [<span data-ttu-id="209aa-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="209aa-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="209aa-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="209aa-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
