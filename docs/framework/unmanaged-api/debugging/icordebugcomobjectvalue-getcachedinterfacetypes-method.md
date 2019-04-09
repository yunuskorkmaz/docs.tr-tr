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
ms.openlocfilehash: 36e6313ae7b4c67a20bee6d2a76a4ed1da84acbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115225"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="1372b-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="1372b-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="1372b-103">Bir numaralandırıcı, geçerli nesne için tür dönüştürme veya bırakıldığı olarak kullanılan, arabirim türlerinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="1372b-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1372b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1372b-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1372b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1372b-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="1372b-106">[in] Yöntemi yalnızca döndürüp döndürmediğini gösteren bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) önbelleğe alınmış tüm COM arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="1372b-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="1372b-107">[out] Önbelleğe alınmış arabirim türleri temsil eden Icordebugtype nesneleri erişim sağlayan bir Icordebugtypeenum Numaralandırıcı adresini bir işaretçiye şunlara göre filtrelenmiş `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="1372b-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1372b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1372b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1372b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1372b-109">Requirements</span></span>  
 <span data-ttu-id="1372b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1372b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1372b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1372b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1372b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1372b-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1372b-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1372b-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1372b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1372b-114">See also</span></span>

- [<span data-ttu-id="1372b-115">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1372b-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="1372b-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1372b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
