---
title: ICorDebugDataTarget2::GetSymbolProviderForImage Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e802ad662130169d67227803eb017075c94f4361
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="5ec50-102">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="5ec50-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="5ec50-103">Bir modül için simge sağlayıcısı bu modül temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ec50-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ec50-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ec50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ec50-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="5ec50-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) bir modül temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="5ec50-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="5ec50-107">[out] Adresine bir işaretçi bir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5ec50-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ec50-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ec50-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ec50-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ec50-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ec50-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ec50-110">Requirements</span></span>  
 <span data-ttu-id="5ec50-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec50-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec50-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ec50-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ec50-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec50-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec50-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec50-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec50-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ec50-115">See Also</span></span>  
 [<span data-ttu-id="5ec50-116">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ec50-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="5ec50-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ec50-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
