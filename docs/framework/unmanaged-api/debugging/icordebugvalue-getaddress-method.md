---
title: ICorDebugValue::GetAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 906ca2540e421953b3ce39300aa7b2376f789929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137094"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="04a52-102">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="04a52-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="04a52-103">Bu "ICorDebugValue" nesnesinin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="04a52-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04a52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04a52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04a52-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="04a52-106">dışı Bu değer nesnesinin adresini belirten `CORDB_ADDRESS` nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04a52-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04a52-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04a52-107">Remarks</span></span>  
 <span data-ttu-id="04a52-108">Değer kullanılamıyorsa 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="04a52-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="04a52-109">Bu durum, değer en az kısmen Yazmaçlarda veya bir çöp toplayıcı tanıtıcısında (`GCHandle`) depolanıyorsa meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="04a52-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a52-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04a52-110">Requirements</span></span>  
 <span data-ttu-id="04a52-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a52-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a52-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04a52-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04a52-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="04a52-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04a52-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a52-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a52-115">See also</span></span>
