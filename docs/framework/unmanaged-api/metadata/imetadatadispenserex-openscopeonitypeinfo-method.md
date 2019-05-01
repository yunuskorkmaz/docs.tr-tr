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
ms.openlocfilehash: deecd9ed4161bbd72e97a6320188961ae76d1e7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044271"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="7f49d-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f49d-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="7f49d-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="7f49d-103">This method is not implemented.</span></span> <span data-ttu-id="7f49d-104">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f49d-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f49d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f49d-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f49d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f49d-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="7f49d-107">[in] İşaretçi bir [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) kapsamı açmak tür bilgileri sağlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7f49d-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7f49d-108">[in] Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="7f49d-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="7f49d-109">[in] İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="7f49d-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7f49d-110">[out] Döndürülen arabirim işaretçisi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f49d-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f49d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f49d-111">Requirements</span></span>  
 <span data-ttu-id="7f49d-112">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f49d-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f49d-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f49d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f49d-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7f49d-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f49d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f49d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f49d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f49d-116">See also</span></span>

- [<span data-ttu-id="7f49d-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f49d-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="7f49d-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f49d-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
