---
title: ICorDebugDataTarget2::GetSymbolProviderForImage Metodu
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 817103e4aa5b3f56d0601382bbc268b969a919e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750042"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="458c5-102">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="458c5-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="458c5-103">Bir modül için Sembol sağlayıcısı Bu modülün temel adres döndürür.</span><span class="sxs-lookup"><span data-stu-id="458c5-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="458c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="458c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="458c5-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="458c5-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) bir modül temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="458c5-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="458c5-107">[out] Adresine bir işaretçi bir [Icordebugsymbolprovider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="458c5-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="458c5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="458c5-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="458c5-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="458c5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458c5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="458c5-110">Requirements</span></span>  
 <span data-ttu-id="458c5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="458c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458c5-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458c5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458c5-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458c5-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458c5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458c5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="458c5-115">See also</span></span>

- [<span data-ttu-id="458c5-116">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="458c5-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="458c5-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="458c5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
