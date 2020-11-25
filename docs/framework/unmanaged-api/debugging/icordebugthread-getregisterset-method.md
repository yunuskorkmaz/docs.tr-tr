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
ms.openlocfilehash: 7d3575909f54c8d676c9fd4246e6eac4a8a0ea1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727984"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="b9700-102">ICorDebugThread::GetRegisterSet Metodu</span><span class="sxs-lookup"><span data-stu-id="b9700-102">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="b9700-103">Bu ICorDebugThread nesnesinin etkin bölümüyle ilişkili kayıt kümesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b9700-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9700-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b9700-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9700-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9700-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="b9700-106">dışı Bu iş parçacığının etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9700-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9700-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9700-107">Requirements</span></span>  

 <span data-ttu-id="b9700-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9700-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9700-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b9700-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9700-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b9700-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9700-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9700-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
