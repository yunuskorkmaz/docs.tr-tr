---
title: "ICorDebugSymbolProvider::GetTypeProps yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba736caf8d8d823a4cb56c75aa2202ad616983fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="67b9a-102">ICorDebugSymbolProvider::GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="67b9a-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="67b9a-103">Göreli sanal adres (RAV) bir vtable verilen imza genel parametrelerinin sayısı gibi bir tür özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="67b9a-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67b9a-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67b9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67b9a-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="67b9a-106">[in] Bir vtable'de göreli sanal adres (RAV).</span><span class="sxs-lookup"><span data-stu-id="67b9a-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="67b9a-107">[in] Boyutunu `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="67b9a-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="67b9a-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="67b9a-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="67b9a-109">[out] [out] Döndürülen boyutu gösteren bir işaretçi `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="67b9a-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="67b9a-110">[out] Tüm genel parametreler TypeSpec'te imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="67b9a-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67b9a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67b9a-111">Remarks</span></span>  
 <span data-ttu-id="67b9a-112">Tür gerekli boyutunu almak için `signature` dizisindeki, ayarlamak `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**.</span><span class="sxs-lookup"><span data-stu-id="67b9a-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="67b9a-113">Yöntem döndüğünde `pcbSignature` için gereken bayt sayısını içerecektir `signature` dizi.</span><span class="sxs-lookup"><span data-stu-id="67b9a-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67b9a-114">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67b9a-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b9a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67b9a-115">Requirements</span></span>  
 <span data-ttu-id="67b9a-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67b9a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b9a-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67b9a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67b9a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67b9a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67b9a-119">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b9a-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b9a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67b9a-120">See Also</span></span>  
 [<span data-ttu-id="67b9a-121">GetMethodProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="67b9a-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [<span data-ttu-id="67b9a-122">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="67b9a-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="67b9a-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67b9a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
