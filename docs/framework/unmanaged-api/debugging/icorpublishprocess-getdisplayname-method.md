---
title: ICorPublishProcess::GetDisplayName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bbaa05d767302bcd75303ec902a82e7992e1db3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="81171-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="81171-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="81171-103">Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="81171-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81171-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81171-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81171-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81171-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="81171-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="81171-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="81171-107">[out] Döndürülen geniş karakter sayısını `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="81171-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="81171-108">[out] Yürütülebilir dosyanın tam yolunu dahil adını depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="81171-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="81171-109">Sonlandırılmış adıdır.</span><span class="sxs-lookup"><span data-stu-id="81171-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81171-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81171-110">Requirements</span></span>  
 <span data-ttu-id="81171-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81171-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81171-112">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="81171-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="81171-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81171-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81171-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81171-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81171-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81171-115">See Also</span></span>  
 [<span data-ttu-id="81171-116">Icorpublishprocess arabirimi</span><span class="sxs-lookup"><span data-stu-id="81171-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
