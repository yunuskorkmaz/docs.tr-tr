---
title: ICorDebugThread::GetID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31ae48d62221d45a8457c304a1929886738190c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="4cccf-102">ICorDebugThread::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="4cccf-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="4cccf-103">Bu Icordebugthread etkin parçası geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="4cccf-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cccf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cccf-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cccf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cccf-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="4cccf-106">[out] İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4cccf-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cccf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cccf-107">Remarks</span></span>  
 <span data-ttu-id="4cccf-108">İşletim sistemi tanımlayıcısını bir işlemin yürütülmesi sırasında değişiklik yapabilirsiniz ve iş parçacığının farklı bölümleri için farklı bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="4cccf-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cccf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cccf-109">Requirements</span></span>  
 <span data-ttu-id="4cccf-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cccf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cccf-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cccf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cccf-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cccf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cccf-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cccf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
