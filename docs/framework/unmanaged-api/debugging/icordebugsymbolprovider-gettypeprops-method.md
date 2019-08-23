---
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ea3a201cc94ef7bdf679371ef43ab2641b791
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955545"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="321b9-102">ICorDebugSymbolProvider:: GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="321b9-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="321b9-103">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="321b9-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="321b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="321b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="321b9-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="321b9-106">'ndaki Vtable içindeki göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="321b9-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="321b9-107">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="321b9-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="321b9-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="321b9-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="321b9-109">dışı dışı Döndürülen `signature` dizinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="321b9-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="321b9-110">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="321b9-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321b9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="321b9-111">Remarks</span></span>  
 <span data-ttu-id="321b9-112">Türün `signature` dizisinin gerekli boyutunu almak için, `cbSignature` bağımsız değişkenini 0 ve `signature` **null**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="321b9-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="321b9-113">Yöntemi döndüğünde, `pcbSignature` `signature` dizi için gereken bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="321b9-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="321b9-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="321b9-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321b9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="321b9-115">Requirements</span></span>  
 <span data-ttu-id="321b9-116">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321b9-117">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="321b9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="321b9-118">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="321b9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="321b9-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321b9-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321b9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="321b9-120">See also</span></span>

- [<span data-ttu-id="321b9-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="321b9-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="321b9-122">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="321b9-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="321b9-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="321b9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
