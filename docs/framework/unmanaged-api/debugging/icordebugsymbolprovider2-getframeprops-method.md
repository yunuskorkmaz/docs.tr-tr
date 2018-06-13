---
title: ICorDebugSymbolProvider2::GetFrameProps yöntemi
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419e7bae5998679fafac48ebfd5b0673e0e4bac5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419087"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="378d4-102">ICorDebugSymbolProvider2::GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="378d4-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="378d4-103">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="378d4-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="378d4-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="378d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="378d4-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="378d4-106">[in] Bir kod göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="378d4-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="378d4-107">[out] Yöntemin başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="378d4-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="378d4-108">[out] Çerçeve başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="378d4-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="378d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="378d4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="378d4-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="378d4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378d4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="378d4-111">Requirements</span></span>  
 <span data-ttu-id="378d4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378d4-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="378d4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="378d4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="378d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="378d4-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378d4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378d4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="378d4-116">See Also</span></span>  
 [<span data-ttu-id="378d4-117">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="378d4-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="378d4-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="378d4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
