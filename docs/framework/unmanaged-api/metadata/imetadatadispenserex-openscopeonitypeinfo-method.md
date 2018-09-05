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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5fd96f390b0bba60d1b95d20273bbf670208d41
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562503"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="5317c-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5317c-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="5317c-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5317c-103">This method is not implemented.</span></span> <span data-ttu-id="5317c-104">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="5317c-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5317c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5317c-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5317c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5317c-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="5317c-107">[in] İşaretçi bir [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) kapsamı açmak tür bilgileri sağlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5317c-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5317c-108">[in] Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="5317c-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="5317c-109">[in] İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="5317c-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="5317c-110">[out] Döndürülen arabirim işaretçisi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5317c-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5317c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5317c-111">Requirements</span></span>  
 <span data-ttu-id="5317c-112">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5317c-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5317c-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5317c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5317c-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="5317c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5317c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5317c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5317c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5317c-116">See Also</span></span>  
 [<span data-ttu-id="5317c-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5317c-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="5317c-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5317c-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
