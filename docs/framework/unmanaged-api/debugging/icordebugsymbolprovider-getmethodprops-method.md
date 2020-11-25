---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 5412b2f06445627c1240d6c8f4efb3ce6bbbec54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730831"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="2ea38-102">ICorDebugSymbolProvider:: GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ea38-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>

<span data-ttu-id="2ea38-103">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ea38-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea38-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ea38-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2ea38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ea38-105">Parameters</span></span>  

 `codeRVA`  
 <span data-ttu-id="2ea38-106">'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.</span><span class="sxs-lookup"><span data-stu-id="2ea38-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="2ea38-107">dışı Metodun meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ea38-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="2ea38-108">dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ea38-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="2ea38-109">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2ea38-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="2ea38-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2ea38-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="2ea38-111">dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="2ea38-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="2ea38-112">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2ea38-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ea38-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ea38-113">Remarks</span></span>  

 <span data-ttu-id="2ea38-114">Yöntemin dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ea38-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="2ea38-115">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="2ea38-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ea38-116">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ea38-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea38-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ea38-117">Requirements</span></span>  

 <span data-ttu-id="2ea38-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea38-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea38-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2ea38-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ea38-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2ea38-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ea38-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea38-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea38-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea38-122">See also</span></span>

- [<span data-ttu-id="2ea38-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ea38-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="2ea38-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ea38-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2ea38-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ea38-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
