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
ms.openlocfilehash: 354e1b0dad942534068d5fb07071ed4ac695fb49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764890"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="da58c-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="da58c-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="da58c-103">Bu tarafından başvurulan işlemi için yürütülebilir dosyanın tam yolunu alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="da58c-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da58c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da58c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da58c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da58c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="da58c-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="da58c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="da58c-107">[out] Döndürülen geniş karakter sayısını `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="da58c-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="da58c-108">[out] Yürütülebilir dosyanın tam yolunu da dahil olmak üzere ad depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="da58c-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="da58c-109">Null ile sonlandırılmış adıdır.</span><span class="sxs-lookup"><span data-stu-id="da58c-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da58c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da58c-110">Requirements</span></span>  
 <span data-ttu-id="da58c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da58c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da58c-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="da58c-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="da58c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da58c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da58c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da58c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da58c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da58c-115">See also</span></span>

- [<span data-ttu-id="da58c-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da58c-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
