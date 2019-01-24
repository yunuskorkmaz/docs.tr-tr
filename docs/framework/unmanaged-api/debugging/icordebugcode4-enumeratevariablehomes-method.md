---
title: ICorDebugCode4::EnumerateVariableHomes yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c765cb2e0e59fe2fcac562fdb2e926e878298c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530297"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="2468b-102">ICorDebugCode4::EnumerateVariableHomes yöntemi</span><span class="sxs-lookup"><span data-stu-id="2468b-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="2468b-103">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="2468b-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2468b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2468b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2468b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2468b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2468b-106">Adresine bir işaretçi bir [Icordebugvariablehomeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirimi nesnesi yerel değişkenleri ve bir işlevde bağımsız değişken için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="2468b-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2468b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2468b-107">Remarks</span></span>  
 <span data-ttu-id="2468b-108">[Icordebugvariablehomeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirimi nesnedir listeleme olanak tanıyan "ICorDebugEnum" arabirimden türetilmiş standart bir numaralandırıcı [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2468b-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="2468b-109">Birden çok koleksiyon bulunabilir [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) işlevi farklı noktalarda farklı havaalanlarından oluşturulduysa nesneleri aynı yuva veya bağımsız değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="2468b-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2468b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2468b-110">Requirements</span></span>  
 <span data-ttu-id="2468b-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2468b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2468b-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2468b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2468b-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2468b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2468b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2468b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2468b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2468b-115">See also</span></span>
- [<span data-ttu-id="2468b-116">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2468b-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="2468b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2468b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
