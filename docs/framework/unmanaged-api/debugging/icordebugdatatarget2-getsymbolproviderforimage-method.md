---
title: ICorDebugDataTarget2::GetSymbolProviderForImage Metodu
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7800630be0ed9afb321d607046be308088781388
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976453"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="bcb4d-102">ICorDebugDataTarget2::GetSymbolProviderForImage Metodu</span><span class="sxs-lookup"><span data-stu-id="bcb4d-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="bcb4d-103">Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bcb4d-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcb4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcb4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bcb4d-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="bcb4d-106">'ndaki Bir modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="bcb4d-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="bcb4d-107">dışı [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bcb4d-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcb4d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcb4d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcb4d-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bcb4d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcb4d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcb4d-110">Requirements</span></span>  
 <span data-ttu-id="bcb4d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcb4d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb4d-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bcb4d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcb4d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bcb4d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcb4d-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb4d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb4d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcb4d-115">See also</span></span>

- [<span data-ttu-id="bcb4d-116">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcb4d-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="bcb4d-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bcb4d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
