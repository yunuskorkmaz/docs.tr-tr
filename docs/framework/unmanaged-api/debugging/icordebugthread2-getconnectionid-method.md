---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: GetConnectionID yöntemi'
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
ms.openlocfilehash: 0f8035e703d3638b11f4206d9c47e39fe487d71d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658743"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="6e3b9-103">ICorDebugThread2::GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e3b9-103">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="6e3b9-104">Bu ICorDebugThread2 nesnesi için bağlantı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6e3b9-104">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e3b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e3b9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e3b9-106">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="6e3b9-107">dışı `CONNID` Bağlantı tanımlayıcısını temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="6e3b9-107">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e3b9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e3b9-108">Remarks</span></span>  

 <span data-ttu-id="6e3b9-109">`GetConnectionID`Yöntemi, `pdwConnectionId` Bu iş parçacığı bir bağlantının parçası değilse, parametresinde sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e3b9-109">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="6e3b9-110">Bu iş parçacığı bir Microsoft SQL Server 2005 Analysis Services (SSAS) örneğine bağlıysa, `CONNID` sunucu işlem tanımlayıcısına (SPID) eşlenir.</span><span class="sxs-lookup"><span data-stu-id="6e3b9-110">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e3b9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e3b9-111">Requirements</span></span>  

 <span data-ttu-id="6e3b9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e3b9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e3b9-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e3b9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e3b9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e3b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e3b9-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e3b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
