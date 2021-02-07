---
description: ': ICorDebugValue:: GetAddress yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c922388fbab820e50edffc140be94a2c0920099d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690437"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="c4445-103">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="c4445-103">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="c4445-104">Bu "ICorDebugValue" nesnesinin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="c4445-104">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4445-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4445-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4445-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4445-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="c4445-107">dışı `CORDB_ADDRESS` Bu değer nesnesinin adresini belirten nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c4445-107">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4445-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4445-108">Remarks</span></span>  

 <span data-ttu-id="c4445-109">Değer kullanılamıyorsa 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4445-109">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="c4445-110">Bu durum, değer en az kısmen Yazmaçlarda veya çöp toplayıcı tanıtıcısında () depolanıyorsa meydana gelebilir `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="c4445-110">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4445-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4445-111">Requirements</span></span>  

 <span data-ttu-id="c4445-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4445-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4445-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4445-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4445-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4445-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4445-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4445-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4445-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4445-116">See also</span></span>
