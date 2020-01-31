---
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 5fa091eaf2cf93b0c645effeec3c959d42665fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791540"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="0f4a2-102">ICorDebugSymbolProvider:: GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f4a2-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="0f4a2-103">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f4a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f4a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f4a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f4a2-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="0f4a2-106">'ndaki Vtable içindeki göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="0f4a2-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="0f4a2-107">'ndaki `signature` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="0f4a2-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="0f4a2-109">dışı dışı Döndürülen `signature` dizisinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="0f4a2-110">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f4a2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f4a2-111">Remarks</span></span>  
 <span data-ttu-id="0f4a2-112">Türün `signature` dizisinin gereken boyutunu almak için, `cbSignature` bağımsız değişkenini 0 olarak ayarlayın ve **null**olarak `signature`.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="0f4a2-113">Yöntemi döndürüldüğünde, `pcbSignature` `signature` dizisi için gerekli olan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f4a2-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f4a2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f4a2-115">Requirements</span></span>  
 <span data-ttu-id="0f4a2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f4a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f4a2-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f4a2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f4a2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0f4a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f4a2-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f4a2-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4a2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f4a2-120">See also</span></span>

- [<span data-ttu-id="0f4a2-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f4a2-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="0f4a2-122">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f4a2-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0f4a2-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f4a2-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
