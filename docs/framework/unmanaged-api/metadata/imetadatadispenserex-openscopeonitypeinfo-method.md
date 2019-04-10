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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218790"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="6ab31-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ab31-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="6ab31-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6ab31-103">This method is not implemented.</span></span> <span data-ttu-id="6ab31-104">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ab31-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab31-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ab31-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ab31-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ab31-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="6ab31-107">[in] İşaretçi bir [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) kapsamı açmak tür bilgileri sağlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6ab31-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6ab31-108">[in] Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6ab31-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="6ab31-109">[in] İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="6ab31-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6ab31-110">[out] Döndürülen arabirim işaretçisi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ab31-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ab31-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ab31-111">Requirements</span></span>  
 <span data-ttu-id="6ab31-112">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ab31-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ab31-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6ab31-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ab31-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6ab31-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="6ab31-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6ab31-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ab31-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ab31-116">See also</span></span>

- [<span data-ttu-id="6ab31-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ab31-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="6ab31-118">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ab31-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
