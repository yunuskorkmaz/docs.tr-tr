---
title: ICorDebugSymbolProvider::GetMethodProps yöntemi
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dacfd6538dbf42a757a0e3534978238421644ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490443"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="f78ce-102">ICorDebugSymbolProvider::GetMethodProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="f78ce-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="f78ce-103">Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri belirteci ve kendi genel parametreler hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f78ce-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f78ce-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f78ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f78ce-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="f78ce-106">[in] Göreli sanal adres hakkında bilgi alınacak yöntemi içinde.</span><span class="sxs-lookup"><span data-stu-id="f78ce-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="f78ce-107">[out] Yöntemin meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f78ce-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="f78ce-108">[out] Bu yöntemle ilişkili genel parametre sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f78ce-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="f78ce-109">[in] Boyutu `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f78ce-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="f78ce-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f78ce-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="f78ce-111">[out] Boyut döndürülen işaretçi `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f78ce-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="f78ce-112">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="f78ce-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f78ce-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f78ce-113">Remarks</span></span>  
 <span data-ttu-id="f78ce-114">Yöntemin gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="f78ce-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="f78ce-115">Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f78ce-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f78ce-116">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f78ce-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f78ce-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f78ce-117">Requirements</span></span>  
 <span data-ttu-id="f78ce-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f78ce-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f78ce-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f78ce-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f78ce-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f78ce-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f78ce-121">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f78ce-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78ce-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f78ce-122">See also</span></span>
- [<span data-ttu-id="f78ce-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f78ce-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="f78ce-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f78ce-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f78ce-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f78ce-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
