---
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
ms.openlocfilehash: 9793424e79ed878b04a5c51daad08b5d12d439e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791462"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="321cc-102">ICorDebugThread::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="321cc-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="321cc-103">Bu ICorDebugThread nesnesinin etkin bölümüyle ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="321cc-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="321cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="321cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="321cc-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="321cc-106">dışı Bu iş parçacığının etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="321cc-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321cc-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="321cc-107">Requirements</span></span>  
 <span data-ttu-id="321cc-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321cc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321cc-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="321cc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="321cc-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="321cc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="321cc-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
