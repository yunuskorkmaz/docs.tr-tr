---
description: ': ICorDebugThread:: GetRegisterSet Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetRegisterSet Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: f61ccb34eabc1f4d8b8db8a0b78e3ddde9aa136d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658912"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="323ad-103">ICorDebugThread::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="323ad-103">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="323ad-104">Bu ICorDebugThread nesnesinin etkin bölümüyle ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="323ad-104">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="323ad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="323ad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="323ad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="323ad-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="323ad-107">dışı Bu iş parçacığının etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="323ad-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="323ad-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="323ad-108">Requirements</span></span>  

 <span data-ttu-id="323ad-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="323ad-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="323ad-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="323ad-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="323ad-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="323ad-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="323ad-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="323ad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
