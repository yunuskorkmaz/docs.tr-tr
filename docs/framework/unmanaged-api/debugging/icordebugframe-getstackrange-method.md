---
title: ICorDebugFrame::GetStackRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178906"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="3638b-102">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3638b-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="3638b-103">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="3638b-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3638b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3638b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3638b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3638b-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="3638b-106">[çıkış] Bu `ICorDebugFrame` nesne `CORDB_ADDRESS` tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3638b-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="3638b-107">[çıkış] Bu `ICorDebugFrame` nesne `CORDB_ADDRESS` tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3638b-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3638b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3638b-108">Remarks</span></span>  
 <span data-ttu-id="3638b-109">Yığının adres aralığı, birden çok hata ayıklama motorundan toplanan ara sıra yığın izlerini birleştirmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3638b-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="3638b-110">Sayısal aralık, yığın çerçevesinin içeriği hakkında bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="3638b-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="3638b-111">Yalnızca yığın çerçeve konumlarının karşılaştırılması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="3638b-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3638b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3638b-112">Requirements</span></span>  
 <span data-ttu-id="3638b-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3638b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3638b-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3638b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3638b-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3638b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3638b-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3638b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
