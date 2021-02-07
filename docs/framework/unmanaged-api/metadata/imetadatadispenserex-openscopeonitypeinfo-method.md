---
description: ': Imetadatadağıtıserex:: Openscopeonittypeınfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bc36bac9e7c63f56f442f1e25fd7a6a93f75924b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753529"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="ac0af-103">IMetaDataDispenserEx::OpenScopeOnITypeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac0af-103">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="ac0af-104">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ac0af-104">This method is not implemented.</span></span> <span data-ttu-id="ac0af-105">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac0af-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0af-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac0af-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac0af-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac0af-107">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="ac0af-108">'ndaki Kapsamın açılacağı tür bilgilerini sağlayan bir [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac0af-108">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ac0af-109">'ndaki Açık mod bayrakları.</span><span class="sxs-lookup"><span data-stu-id="ac0af-109">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="ac0af-110">'ndaki İstenen arabirim.</span><span class="sxs-lookup"><span data-stu-id="ac0af-110">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="ac0af-111">dışı Döndürülen arabirime yönelik işaretçinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac0af-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac0af-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac0af-112">Requirements</span></span>  

 <span data-ttu-id="ac0af-113">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac0af-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac0af-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ac0af-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac0af-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ac0af-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac0af-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac0af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac0af-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac0af-117">See also</span></span>

- [<span data-ttu-id="ac0af-118">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac0af-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="ac0af-119">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac0af-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
