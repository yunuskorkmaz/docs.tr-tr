---
description: ': ICorDebugComObjectValue:: Getcachedınterfacetype yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b1c65979895dfaeacae3d171adbcfd1455b7030d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764625"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="d3904-103">ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="d3904-103">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>

<span data-ttu-id="d3904-104">Geçerli nesnenin atanmış veya olarak kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3904-104">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3904-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3904-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3904-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3904-106">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="d3904-107">'ndaki Yöntemin yalnızca Windows Çalışma Zamanı arabirimleri ( `IInspectable` arabirimler) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınmış tüm com arabirimlerini döndürüp döndürmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d3904-107">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="d3904-108">dışı Öğesine göre filtrelenmiş önbelleğe alınmış arabirim türlerini temsil eden ICorDebugType nesnelerine erişim sağlayan ICorDebugTypeEnum Numaralandırıcı adresine yönelik bir işaretçi `bIInspectableOnly` .</span><span class="sxs-lookup"><span data-stu-id="d3904-108">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3904-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3904-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3904-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3904-110">Requirements</span></span>  

 <span data-ttu-id="d3904-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3904-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3904-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3904-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3904-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3904-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3904-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3904-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3904-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3904-115">See also</span></span>

- [<span data-ttu-id="d3904-116">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3904-116">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d3904-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3904-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
