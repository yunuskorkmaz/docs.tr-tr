---
title: ICorDebugAssembly::GetProcess Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1c3bcc0ed22fa970d92e2384277d0786016db19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402115"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="752da-102">ICorDebugAssembly::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="752da-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="752da-103">Arabirim işaretçisi bu Icordebugassembly örneğinin çalıştığı işlem alır.</span><span class="sxs-lookup"><span data-stu-id="752da-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="752da-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="752da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="752da-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="752da-106">[out] İşlemi temsil eden bir Icordebugprocess arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="752da-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="752da-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="752da-107">Requirements</span></span>  
 <span data-ttu-id="752da-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="752da-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="752da-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="752da-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="752da-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="752da-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="752da-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="752da-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
