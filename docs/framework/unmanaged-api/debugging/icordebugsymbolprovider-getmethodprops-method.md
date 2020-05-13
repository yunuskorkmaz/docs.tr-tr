---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: c9e73c4de7389405d9e4b643036709ff2dbb82e6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379574"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="0627f-102">ICorDebugSymbolProvider:: GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0627f-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="0627f-103">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0627f-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0627f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0627f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0627f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0627f-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="0627f-106">'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.</span><span class="sxs-lookup"><span data-stu-id="0627f-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="0627f-107">dışı Metodun meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0627f-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0627f-108">dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0627f-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="0627f-109">'ndaki `signature`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="0627f-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="0627f-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0627f-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="0627f-111">dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="0627f-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="0627f-112">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0627f-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0627f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0627f-113">Remarks</span></span>  
 <span data-ttu-id="0627f-114">Yöntemin dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0627f-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="0627f-115">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="0627f-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0627f-116">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0627f-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0627f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0627f-117">Requirements</span></span>  
 <span data-ttu-id="0627f-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0627f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0627f-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0627f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0627f-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0627f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0627f-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0627f-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0627f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0627f-122">See also</span></span>

- [<span data-ttu-id="0627f-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0627f-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="0627f-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0627f-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0627f-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0627f-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
