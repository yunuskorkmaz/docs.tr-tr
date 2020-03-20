---
title: ICorDebugDataTarget2::GetSymbolProviderForImage Metodu
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178930"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="0ad2f-102">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="0ad2f-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="0ad2f-103">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ad2f-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad2f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ad2f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ad2f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ad2f-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="0ad2f-106">[içinde] Modülün temel adresini temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="0ad2f-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="0ad2f-107">[çıkış] [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0ad2f-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ad2f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ad2f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ad2f-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad2f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ad2f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ad2f-110">Requirements</span></span>  
 <span data-ttu-id="0ad2f-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ad2f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad2f-112">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ad2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ad2f-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ad2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ad2f-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad2f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad2f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad2f-115">See also</span></span>

- [<span data-ttu-id="0ad2f-116">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ad2f-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="0ad2f-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ad2f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
