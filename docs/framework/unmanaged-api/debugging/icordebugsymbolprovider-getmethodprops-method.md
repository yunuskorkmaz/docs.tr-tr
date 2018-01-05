---
title: "ICorDebugSymbolProvider::GetMethodProps yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf92727139dc912107484b1e13944c679c944726
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="437f4-102">ICorDebugSymbolProvider::GetMethodProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="437f4-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="437f4-103">Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri simgesi ve kendi genel parametreleri hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="437f4-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="437f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="437f4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="437f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="437f4-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="437f4-106">[in] Hakkında bilgi alınabilecek olduğu yönteminde göreli bir sanal adres.</span><span class="sxs-lookup"><span data-stu-id="437f4-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="437f4-107">[out] Yöntemin meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="437f4-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="437f4-108">[out] Bu yöntem ile ilgili genel parametreleri sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="437f4-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="437f4-109">[in] Boyutunu `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="437f4-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="437f4-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="437f4-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="437f4-111">[out] Döndürülen boyutu gösteren bir işaretçi `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="437f4-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="437f4-112">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="437f4-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="437f4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="437f4-113">Remarks</span></span>  
 <span data-ttu-id="437f4-114">Yöntemin gerekli boyutunu almak için `signature` dizisindeki, ayarlamak `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="437f4-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="437f4-115">Yöntem döndüğünde `pcbSignature` için gereken bayt sayısını içerecektir `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="437f4-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="437f4-116">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="437f4-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="437f4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="437f4-117">Requirements</span></span>  
 <span data-ttu-id="437f4-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="437f4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="437f4-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="437f4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="437f4-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="437f4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="437f4-121">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="437f4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437f4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="437f4-122">See Also</span></span>  
 [<span data-ttu-id="437f4-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="437f4-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [<span data-ttu-id="437f4-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="437f4-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="437f4-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="437f4-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
