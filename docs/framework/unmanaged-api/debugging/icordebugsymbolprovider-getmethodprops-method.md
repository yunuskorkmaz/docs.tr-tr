---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791576"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="6049e-102">ICorDebugSymbolProvider:: GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6049e-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="6049e-103">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6049e-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6049e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6049e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6049e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6049e-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="6049e-106">'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.</span><span class="sxs-lookup"><span data-stu-id="6049e-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="6049e-107">dışı Metodun meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6049e-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="6049e-108">dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6049e-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="6049e-109">'ndaki `signature` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="6049e-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="6049e-110">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6049e-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="6049e-111">dışı Döndürülen `signature` dizisinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6049e-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="6049e-112">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="6049e-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6049e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6049e-113">Remarks</span></span>  
 <span data-ttu-id="6049e-114">Yöntemin `signature` dizisinin gereken boyutunu almak için, `cbSignature` bağımsız değişkenini 0 olarak ayarlayın ve **null**olarak `signature`.</span><span class="sxs-lookup"><span data-stu-id="6049e-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="6049e-115">Yöntemi döndürüldüğünde, `pcbSignature` `signature` dizisi için gerekli olan bayt sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="6049e-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6049e-116">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6049e-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6049e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6049e-117">Requirements</span></span>  
 <span data-ttu-id="6049e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6049e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6049e-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6049e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6049e-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6049e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6049e-121">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6049e-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6049e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6049e-122">See also</span></span>

- [<span data-ttu-id="6049e-123">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6049e-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="6049e-124">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6049e-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="6049e-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6049e-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
