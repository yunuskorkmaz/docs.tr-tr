---
title: ICorDebugSymbolProvider2::GetFrameProps yöntemi
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd8cc461519b01a9bf62a28610386e51630060d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646207"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="6e7e3-102">ICorDebugSymbolProvider2::GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e7e3-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="6e7e3-103">Bir yöntemi ve üst çerçevenin bir kod göreli sanal adres verilen göreli sanal adres başlangıç yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e7e3-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e7e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e7e3-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="6e7e3-106">[in] Bir kod göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="6e7e3-107">[out] Göreli sanal adres yöntemin başlangıç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="6e7e3-108">[out] Çerçeve göreli sanal adres başlangıç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e7e3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e7e3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e7e3-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7e3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e7e3-111">Requirements</span></span>  
 <span data-ttu-id="6e7e3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7e3-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e7e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e7e3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e7e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e7e3-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7e3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7e3-116">See also</span></span>
- [<span data-ttu-id="6e7e3-117">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e7e3-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="6e7e3-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e7e3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
