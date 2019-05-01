---
title: ICorDebugProcess::GetID Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9239ccfe8ce08e5b50b762a6fede11ab8a439b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994506"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="ba5ec-102">ICorDebugProcess::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="ba5ec-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="ba5ec-103">İşletim sistemi (OS) işlem Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="ba5ec-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba5ec-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba5ec-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="ba5ec-106">[out] İşlem benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="ba5ec-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5ec-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba5ec-107">Requirements</span></span>  
 <span data-ttu-id="ba5ec-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba5ec-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5ec-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba5ec-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba5ec-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba5ec-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba5ec-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba5ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
