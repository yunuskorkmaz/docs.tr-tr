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
ms.openlocfilehash: 8deefe026e32a56d853e173e6a8fa3be942ccd9c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431136"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="967b9-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="967b9-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="967b9-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="967b9-103">This method is not implemented.</span></span> <span data-ttu-id="967b9-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="967b9-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="967b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="967b9-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="967b9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="967b9-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="967b9-107">'ndaki Kapsamın açılacağı tür bilgilerini sağlayan bir [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="967b9-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="967b9-108">'ndaki Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="967b9-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="967b9-109">'ndaki İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="967b9-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="967b9-110">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="967b9-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="967b9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="967b9-111">Requirements</span></span>  
 <span data-ttu-id="967b9-112">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="967b9-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="967b9-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="967b9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="967b9-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="967b9-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="967b9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="967b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967b9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="967b9-116">See also</span></span>

- [<span data-ttu-id="967b9-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="967b9-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="967b9-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="967b9-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
