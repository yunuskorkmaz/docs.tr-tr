---
title: ICorDebugMDA::GetFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 38a5c2da900530b6bf78f24e224714496ceaa62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710967"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="647fe-102">ICorDebugMDA::GetFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="647fe-102">ICorDebugMDA::GetFlags Method</span></span>

<span data-ttu-id="647fe-103">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="647fe-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647fe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="647fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="647fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="647fe-105">Parameters</span></span>  

 `pFlags`  
 <span data-ttu-id="647fe-106">'ndaki Bu MDA için bayrakların ayarlarını belirten [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="647fe-106">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="647fe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="647fe-107">Requirements</span></span>  

 <span data-ttu-id="647fe-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="647fe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="647fe-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="647fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="647fe-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="647fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="647fe-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="647fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647fe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="647fe-112">See also</span></span>

- [<span data-ttu-id="647fe-113">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="647fe-113">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="647fe-114">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="647fe-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
