---
title: ICorPublishProcess::GetDisplayName Metodu
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 815f2e2f695837c973210a21ab3631ef307c23d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423643"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="738db-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="738db-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="738db-103">Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="738db-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="738db-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="738db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="738db-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="738db-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="738db-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="738db-107">[out] Döndürülen geniş karakter sayısını `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="738db-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="738db-108">[out] Yürütülebilir dosyanın tam yolunu dahil adını depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="738db-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="738db-109">Sonlandırılmış adıdır.</span><span class="sxs-lookup"><span data-stu-id="738db-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738db-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="738db-110">Requirements</span></span>  
 <span data-ttu-id="738db-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="738db-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="738db-112">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="738db-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="738db-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="738db-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="738db-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="738db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738db-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="738db-115">See Also</span></span>  
 [<span data-ttu-id="738db-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="738db-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
