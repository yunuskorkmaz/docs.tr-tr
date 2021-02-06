---
description: ': ICorDebugSymbolProvider:: GetMethodProps Yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 53a329426ecadfe5559c0e6a08ffbd250163e177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659731"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="79e59-103">ICorDebugSymbolProvider:: GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79e59-103">ICorDebugSymbolProvider::GetMethodProps Method</span></span>

<span data-ttu-id="79e59-104">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="79e59-104">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79e59-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="79e59-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79e59-106">Parameters</span></span>  

 `codeRVA`  
 <span data-ttu-id="79e59-107">'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.</span><span class="sxs-lookup"><span data-stu-id="79e59-107">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="79e59-108">dışı Metodun meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79e59-108">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="79e59-109">dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79e59-109">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="79e59-110">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="79e59-110">[in] The size of the `signature` array.</span></span> <span data-ttu-id="79e59-111">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="79e59-111">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="79e59-112">dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="79e59-112">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="79e59-113">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="79e59-113">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79e59-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79e59-114">Remarks</span></span>  

 <span data-ttu-id="79e59-115">Yöntemin dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="79e59-115">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="79e59-116">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="79e59-116">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79e59-117">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79e59-117">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e59-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79e59-118">Requirements</span></span>  

 <span data-ttu-id="79e59-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79e59-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e59-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79e59-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79e59-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79e59-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79e59-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79e59-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e59-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79e59-123">See also</span></span>

- [<span data-ttu-id="79e59-124">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79e59-124">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="79e59-125">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79e59-125">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="79e59-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79e59-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
