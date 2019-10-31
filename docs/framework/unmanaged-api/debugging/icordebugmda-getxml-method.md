---
title: ICorDebugMDA::GetXML Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: f80bdffbf5c0ba39980bd27c6e89a368547340c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129803"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="4cd28-102">ICorDebugMDA::GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cd28-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="4cd28-103">[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ILIŞKILI tam XML akışını alır.</span><span class="sxs-lookup"><span data-stu-id="4cd28-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cd28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cd28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cd28-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4cd28-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="4cd28-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4cd28-107">dışı XML akışının uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cd28-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="4cd28-108">dışı XML akışının depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4cd28-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="4cd28-109">Dizi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4cd28-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cd28-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cd28-110">Remarks</span></span>  
 <span data-ttu-id="4cd28-111">`GetXML` yöntemi, ilişkili XML akışının boyutuna bağlı olarak performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4cd28-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cd28-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cd28-112">Requirements</span></span>  
 <span data-ttu-id="4cd28-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cd28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cd28-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4cd28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cd28-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4cd28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cd28-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd28-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cd28-117">See also</span></span>

- [<span data-ttu-id="4cd28-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cd28-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="4cd28-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4cd28-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
