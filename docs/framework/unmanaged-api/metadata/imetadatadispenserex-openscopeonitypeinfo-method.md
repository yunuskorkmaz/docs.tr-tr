---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
ms.openlocfilehash: 6056a64b354f69ce39692173da01892870fba9e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682854"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="5d36b-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d36b-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="5d36b-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5d36b-103">This method is not implemented.</span></span> <span data-ttu-id="5d36b-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d36b-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d36b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5d36b-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d36b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d36b-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="5d36b-107">'ndaki Kapsamın açılacağı tür bilgilerini sağlayan bir [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d36b-107">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5d36b-108">'ndaki Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="5d36b-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="5d36b-109">'ndaki İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="5d36b-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="5d36b-110">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5d36b-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d36b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d36b-111">Requirements</span></span>  

 <span data-ttu-id="5d36b-112">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d36b-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d36b-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5d36b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d36b-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5d36b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d36b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d36b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d36b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d36b-116">See also</span></span>

- [<span data-ttu-id="5d36b-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d36b-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="5d36b-118">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d36b-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
