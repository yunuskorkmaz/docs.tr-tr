---
title: ICorDebugThread2::GetConnectionID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetConnectionID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28fa949de768191061bd747034a5c951a03b8596
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="26d4c-102">ICorDebugThread2::GetConnectionID Metodu</span><span class="sxs-lookup"><span data-stu-id="26d4c-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="26d4c-103">Bağlantı kimliği için bu Icordebugthread2 nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="26d4c-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26d4c-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26d4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26d4c-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="26d4c-106">[out] A `CONNID` , bağlantı kimliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="26d4c-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26d4c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26d4c-107">Remarks</span></span>  
 <span data-ttu-id="26d4c-108">`GetConnectionID` Yöntemi döndürür sıfır `pdwConnectionId` parametresi, bu iş parçacığı bir bağlantısının parçası değilse.</span><span class="sxs-lookup"><span data-stu-id="26d4c-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="26d4c-109">Örneğine, Microsoft SQL Server 2005 Analysis Services (SSAS), bu iş parçacığı bağlıysa `CONNID` eşleyen bir sunucu işlemi tanımlayıcısını (SPID).</span><span class="sxs-lookup"><span data-stu-id="26d4c-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d4c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26d4c-110">Requirements</span></span>  
 <span data-ttu-id="26d4c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d4c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d4c-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26d4c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26d4c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d4c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d4c-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d4c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
