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
ms.openlocfilehash: df2750f082ddc40bbeee121116c3e877d037da84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140425"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="0c8d0-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="0c8d0-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="0c8d0-103">Bu [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c8d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c8d0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0c8d0-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0c8d0-107">dışı `szName` dizisinde döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="0c8d0-108">dışı Yürütülebilir dosyanın tam yolu da dahil olmak üzere, adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="0c8d0-109">Ad null ile sonlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8d0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c8d0-110">Requirements</span></span>  
 <span data-ttu-id="0c8d0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8d0-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="0c8d0-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0c8d0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c8d0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8d0-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8d0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8d0-115">See also</span></span>

- [<span data-ttu-id="0c8d0-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8d0-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
