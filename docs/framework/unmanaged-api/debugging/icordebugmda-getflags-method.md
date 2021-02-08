---
description: ': ICorDebugMDA:: GetFlags yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 53476da06252771627d4883ef9056eb7f945e1b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801182"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="6a288-103">ICorDebugMDA::GetFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="6a288-103">ICorDebugMDA::GetFlags Method</span></span>

<span data-ttu-id="6a288-104">[ICorDebugMDA](icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ilişkili bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="6a288-104">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a288-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a288-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a288-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a288-106">Parameters</span></span>  

 `pFlags`  
 <span data-ttu-id="6a288-107">'ndaki Bu MDA için bayrakların ayarlarını belirten [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6a288-107">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a288-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a288-108">Requirements</span></span>  

 <span data-ttu-id="6a288-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a288-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a288-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a288-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a288-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a288-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a288-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a288-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a288-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a288-113">See also</span></span>

- [<span data-ttu-id="6a288-114">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a288-114">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="6a288-115">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="6a288-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
