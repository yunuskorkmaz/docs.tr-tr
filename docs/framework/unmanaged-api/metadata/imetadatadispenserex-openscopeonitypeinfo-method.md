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
ms.openlocfilehash: 91ef9eaa855ed841bc75bfaeead462f045eb1d8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007461"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="4fd51-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fd51-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="4fd51-103">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4fd51-103">This method is not implemented.</span></span> <span data-ttu-id="4fd51-104">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fd51-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd51-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4fd51-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd51-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fd51-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="4fd51-107">'ndaki Kapsamın açılacağı tür bilgilerini sağlayan bir [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4fd51-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4fd51-108">'ndaki Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="4fd51-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="4fd51-109">'ndaki İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="4fd51-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4fd51-110">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4fd51-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd51-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fd51-111">Requirements</span></span>  
 <span data-ttu-id="4fd51-112">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fd51-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd51-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4fd51-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fd51-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4fd51-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fd51-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd51-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd51-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fd51-116">See also</span></span>

- [<span data-ttu-id="4fd51-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fd51-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="4fd51-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fd51-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
