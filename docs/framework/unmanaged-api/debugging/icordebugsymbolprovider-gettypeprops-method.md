---
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: e116716284bb2081edb669e7fc9083cde10f6457
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379357"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="1330f-102">ICorDebugSymbolProvider:: GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="1330f-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="1330f-103">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1330f-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1330f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1330f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1330f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1330f-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="1330f-106">'ndaki Vtable içindeki göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="1330f-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="1330f-107">'ndaki `signature`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1330f-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="1330f-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1330f-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="1330f-109">dışı dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="1330f-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="1330f-110">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1330f-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1330f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1330f-111">Remarks</span></span>  
 <span data-ttu-id="1330f-112">Türün dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1330f-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="1330f-113">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="1330f-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1330f-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1330f-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1330f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1330f-115">Requirements</span></span>  
 <span data-ttu-id="1330f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1330f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1330f-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1330f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1330f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1330f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1330f-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1330f-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1330f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1330f-120">See also</span></span>

- [<span data-ttu-id="1330f-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1330f-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="1330f-122">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1330f-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1330f-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1330f-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
