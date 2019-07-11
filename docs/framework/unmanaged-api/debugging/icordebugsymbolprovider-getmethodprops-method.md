---
title: ICorDebugSymbolProvider::GetMethodProps yöntemi
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6971c7991f5e54973d96d9b3f662b54be564d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771338"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="0cbf9-102">ICorDebugSymbolProvider::GetMethodProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cbf9-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="0cbf9-103">Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri belirteci ve kendi genel parametreler hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cbf9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cbf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cbf9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cbf9-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="0cbf9-106">[in] Göreli sanal adres hakkında bilgi alınacak yöntemi içinde.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="0cbf9-107">[out] Yöntemin meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0cbf9-108">[out] Bu yöntemle ilişkili genel parametre sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="0cbf9-109">[in] Boyutu `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="0cbf9-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="0cbf9-111">[out] Boyut döndürülen işaretçi `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="0cbf9-112">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cbf9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cbf9-113">Remarks</span></span>  
 <span data-ttu-id="0cbf9-114">Yöntemin gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="0cbf9-115">Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cbf9-116">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cbf9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cbf9-117">Requirements</span></span>  
 <span data-ttu-id="0cbf9-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cbf9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cbf9-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cbf9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cbf9-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cbf9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cbf9-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cbf9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbf9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cbf9-122">See also</span></span>

- [<span data-ttu-id="0cbf9-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cbf9-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="0cbf9-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cbf9-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0cbf9-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0cbf9-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
