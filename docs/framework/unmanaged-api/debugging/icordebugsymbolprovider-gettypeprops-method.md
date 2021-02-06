---
description: ': ICorDebugSymbolProvider:: GetTypeProps yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: b6a4a5a68e1e377fa839940832dfc49574009641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659666"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="3a571-103">ICorDebugSymbolProvider:: GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a571-103">ICorDebugSymbolProvider::GetTypeProps Method</span></span>

<span data-ttu-id="3a571-104">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a571-104">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a571-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a571-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a571-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a571-106">Parameters</span></span>  

 `tableRva`  
 <span data-ttu-id="3a571-107">'ndaki Vtable içindeki göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="3a571-107">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="3a571-108">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="3a571-108">[in] The size of the `signature` array.</span></span> <span data-ttu-id="3a571-109">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3a571-109">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="3a571-110">dışı dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="3a571-110">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="3a571-111">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3a571-111">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a571-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a571-112">Remarks</span></span>  

 <span data-ttu-id="3a571-113">Türün dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3a571-113">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="3a571-114">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="3a571-114">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a571-115">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a571-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a571-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a571-116">Requirements</span></span>  

 <span data-ttu-id="3a571-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a571-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a571-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a571-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a571-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3a571-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a571-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a571-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a571-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a571-121">See also</span></span>

- [<span data-ttu-id="3a571-122">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a571-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="3a571-123">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a571-123">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="3a571-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3a571-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
