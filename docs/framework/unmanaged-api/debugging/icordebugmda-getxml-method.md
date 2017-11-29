---
title: ICorDebugMDA::GetXML Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetXML
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9f1ad3ac70f001feebb0b28eec13cb45ca2c866
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="d0740-102">ICorDebugMDA::GetXML Metodu</span><span class="sxs-lookup"><span data-stu-id="d0740-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="d0740-103">Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ile ilişkili tam XML akışı alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d0740-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0740-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0740-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0740-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0740-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d0740-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="d0740-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d0740-107">[out] XML akışı uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0740-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="d0740-108">[out] XML akışı depolanacağı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="d0740-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="d0740-109">Dizi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0740-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0740-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0740-110">Remarks</span></span>  
 <span data-ttu-id="d0740-111">`GetXML` Yöntemi olası ilişkili XML akışı boyutuna bağlı olarak performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="d0740-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0740-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0740-112">Requirements</span></span>  
 <span data-ttu-id="d0740-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0740-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0740-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0740-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0740-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0740-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0740-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0740-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0740-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0740-117">See Also</span></span>  
 [<span data-ttu-id="d0740-118">Icordebugmda arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0740-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="d0740-119">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="d0740-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
