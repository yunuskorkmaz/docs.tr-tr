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
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138683"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="81700-102">ICorDebugThread2::GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81700-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="81700-103">Bu ICorDebugThread2 nesnesi için bağlantı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="81700-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81700-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81700-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81700-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81700-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="81700-106">dışı Bağlantı tanımlayıcısını temsil eden bir `CONNID`.</span><span class="sxs-lookup"><span data-stu-id="81700-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81700-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81700-107">Remarks</span></span>  
 <span data-ttu-id="81700-108">`GetConnectionID` yöntemi, bu iş parçacığı bir bağlantının parçası değilse `pdwConnectionId` parametresinde sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="81700-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="81700-109">Bu iş parçacığı bir Microsoft SQL Server 2005 Analysis Services (SSAS) örneğine bağlıysa `CONNID` bir sunucu işlem tanımlayıcısına (SPID) eşlenir.</span><span class="sxs-lookup"><span data-stu-id="81700-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81700-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81700-110">Requirements</span></span>  
 <span data-ttu-id="81700-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81700-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81700-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81700-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81700-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="81700-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81700-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81700-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
