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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e78b8a2069671d0fe790956ca914225325a78bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916623"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="1660d-102">ICorDebugMDA::GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1660d-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="1660d-103">Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ilişkili bir tam XML akışı alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1660d-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1660d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1660d-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1660d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1660d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1660d-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="1660d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1660d-107">[out] XML akışı uzunluğunu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1660d-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="1660d-108">[out] XML akışı depolanacağı dizisi.</span><span class="sxs-lookup"><span data-stu-id="1660d-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="1660d-109">Dizi, boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1660d-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1660d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1660d-110">Remarks</span></span>  
 <span data-ttu-id="1660d-111">`GetXML` Yöntemi büyük olasılıkla ilişkili XML akışı boyutuna bağlı olarak performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1660d-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1660d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1660d-112">Requirements</span></span>  
 <span data-ttu-id="1660d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1660d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1660d-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1660d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1660d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1660d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1660d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1660d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1660d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1660d-117">See also</span></span>

- [<span data-ttu-id="1660d-118">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1660d-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="1660d-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1660d-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
