---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1de215eaa0c0cc7021a119e54591caede76d3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417131"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="869ab-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="869ab-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="869ab-103">Bir numaralandırıcı arabirimi türleri için geçerli nesne için cast veya bırakıldığı olarak kullanılan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="869ab-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="869ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="869ab-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="869ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="869ab-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="869ab-106">[in] Bu yöntem yalnızca döndürür olup olmadığını belirten bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı aranabilir sarmalayıcısı (RCW) önbelleğe alınan tüm COM arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="869ab-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="869ab-107">[out] Bir işaretçi önbelleğe alınmış arabirim türleri temsil eden Icordebugtype nesnelere erişim sağlayan bir Icordebugtypeenum Numaralandırıcı adresine göre filtre `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="869ab-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="869ab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="869ab-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="869ab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="869ab-109">Requirements</span></span>  
 <span data-ttu-id="869ab-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="869ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="869ab-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="869ab-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="869ab-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="869ab-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="869ab-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="869ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869ab-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="869ab-114">See Also</span></span>  
 [<span data-ttu-id="869ab-115">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="869ab-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="869ab-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="869ab-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
