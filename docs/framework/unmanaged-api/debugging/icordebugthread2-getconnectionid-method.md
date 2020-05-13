---
title: ICorDebugThread2::GetConnectionID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: c630daa50d465622c421381ac080eaa8d9d8d01d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379070"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="c167e-102">ICorDebugThread2::GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c167e-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="c167e-103">Bu ICorDebugThread2 nesnesi için bağlantı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="c167e-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c167e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c167e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c167e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c167e-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="c167e-106">dışı `CONNID`Bağlantı tanımlayıcısını temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="c167e-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c167e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c167e-107">Remarks</span></span>  
 <span data-ttu-id="c167e-108">`GetConnectionID`Yöntemi, `pdwConnectionId` Bu iş parçacığı bir bağlantının parçası değilse, parametresinde sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="c167e-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="c167e-109">Bu iş parçacığı bir Microsoft SQL Server 2005 Analysis Services (SSAS) örneğine bağlıysa, `CONNID` sunucu işlem tanımlayıcısına (SPID) eşlenir.</span><span class="sxs-lookup"><span data-stu-id="c167e-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c167e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c167e-110">Requirements</span></span>  
 <span data-ttu-id="c167e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c167e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c167e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c167e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c167e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c167e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c167e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c167e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
