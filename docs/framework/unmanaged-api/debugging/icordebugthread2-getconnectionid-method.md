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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768973"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="ce5fc-102">ICorDebugThread2::GetConnectionID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce5fc-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="ce5fc-103">Icordebugthread2 nesneye bağlantı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce5fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce5fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce5fc-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="ce5fc-106">[out] A `CONNID` temsil eden bağlantı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce5fc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce5fc-107">Remarks</span></span>  
 <span data-ttu-id="ce5fc-108">`GetConnectionID` Yöntemi sıfır döndürür `pdwConnectionId` bu iş parçacığı bir bağlantının bir parçası değilse, parametre.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="ce5fc-109">Bu iş parçacığı örneğine, Microsoft SQL Server 2005 Analysis Services (SSAS), bağlı olup olmadığını `CONNID` eşleyen bir sunucu işlemi tanımlayıcısını (SPID).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce5fc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce5fc-110">Requirements</span></span>  
 <span data-ttu-id="ce5fc-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce5fc-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce5fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce5fc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce5fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce5fc-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce5fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
