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
ms.openlocfilehash: 5e1c8157d5a5e4a1bd52f187de7c1d3bfcc4e66d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410926"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="201f4-102">ICorDebugCode4::EnumerateVariableHomes yöntemi</span><span class="sxs-lookup"><span data-stu-id="201f4-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="201f4-103">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="201f4-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="201f4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="201f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="201f4-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="201f4-106">Adresine bir işaretçi bir [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="201f4-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="201f4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="201f4-107">Remarks</span></span>  
 <span data-ttu-id="201f4-108">[ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabiriminin nesnesidir Numaralandırılacak izin veren "ICorDebugEnum" arabirimden türetilmiş standart bir numaralandırıcı [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="201f4-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="201f4-109">Birden çok koleksiyonu içerebilir [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) işlevinde farklı noktalarda farklı ev varsa aynı yuva veya bağımsız değişken dizini nesneleri.</span><span class="sxs-lookup"><span data-stu-id="201f4-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201f4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="201f4-110">Requirements</span></span>  
 <span data-ttu-id="201f4-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="201f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201f4-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="201f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="201f4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="201f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="201f4-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201f4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="201f4-115">See Also</span></span>  
 [<span data-ttu-id="201f4-116">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="201f4-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [<span data-ttu-id="201f4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="201f4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
