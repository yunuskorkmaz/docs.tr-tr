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
ms.openlocfilehash: 868e1e8d670a438d7a93bfac27f213c9c35ea58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="4112d-102">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="4112d-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="4112d-103">Bir modül için simge sağlayıcısı bu modül temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="4112d-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4112d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4112d-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4112d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4112d-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="4112d-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) bir modül temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="4112d-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="4112d-107">[out] Adresine bir işaretçi bir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4112d-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4112d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4112d-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4112d-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4112d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4112d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4112d-110">Requirements</span></span>  
 <span data-ttu-id="4112d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4112d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4112d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4112d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4112d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4112d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4112d-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4112d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4112d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4112d-115">See Also</span></span>  
 [<span data-ttu-id="4112d-116">Icordebugdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4112d-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="4112d-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4112d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
