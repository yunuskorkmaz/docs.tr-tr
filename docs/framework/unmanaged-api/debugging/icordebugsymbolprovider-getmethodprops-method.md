---
title: ICorDebugSymbolProvider::GetMethodProps yöntemi
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 784fcb10e9c0c3c6ff50c25d47bb4fb3fd5762ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161115"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="e5a61-102">ICorDebugSymbolProvider::GetMethodProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5a61-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="e5a61-103">Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri belirteci ve kendi genel parametreler hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5a61-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a61-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5a61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5a61-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="e5a61-106">[in] Göreli sanal adres hakkında bilgi alınacak yöntemi içinde.</span><span class="sxs-lookup"><span data-stu-id="e5a61-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="e5a61-107">[out] Yöntemin meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5a61-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="e5a61-108">[out] Bu yöntemle ilişkili genel parametre sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5a61-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="e5a61-109">[in] Boyutu `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e5a61-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="e5a61-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a61-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="e5a61-111">[out] Boyut döndürülen işaretçi `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e5a61-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="e5a61-112">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="e5a61-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a61-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a61-113">Remarks</span></span>  
 <span data-ttu-id="e5a61-114">Yöntemin gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="e5a61-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="e5a61-115">Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e5a61-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5a61-116">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5a61-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5a61-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5a61-117">Requirements</span></span>  
 <span data-ttu-id="e5a61-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a61-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a61-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5a61-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5a61-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5a61-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e5a61-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e5a61-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a61-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a61-122">See also</span></span>

- [<span data-ttu-id="e5a61-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5a61-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="e5a61-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5a61-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e5a61-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5a61-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
