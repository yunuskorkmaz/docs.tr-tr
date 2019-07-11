---
title: ICorDebugSymbolProvider::GetTypeProps yöntemi
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 435a814d20e039c794f4f9eeb024d5afbfcd6dbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771189"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="133ea-102">ICorDebugSymbolProvider::GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="133ea-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="133ea-103">Göreli sanal adres (RVA) içinde bir vtable verilen imza, genel parametrelerinin sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="133ea-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="133ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="133ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="133ea-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="133ea-106">[in] Bir vtable'da göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="133ea-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="133ea-107">[in] Boyutu `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="133ea-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="133ea-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="133ea-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="133ea-109">[out] [out] Boyut döndürülen işaretçi `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="133ea-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="133ea-110">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="133ea-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="133ea-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="133ea-111">Remarks</span></span>  
 <span data-ttu-id="133ea-112">Türün gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="133ea-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="133ea-113">Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="133ea-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="133ea-114">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="133ea-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="133ea-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="133ea-115">Requirements</span></span>  
 <span data-ttu-id="133ea-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="133ea-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="133ea-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="133ea-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="133ea-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="133ea-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="133ea-119">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="133ea-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133ea-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="133ea-120">See also</span></span>

- [<span data-ttu-id="133ea-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="133ea-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="133ea-122">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="133ea-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="133ea-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="133ea-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
