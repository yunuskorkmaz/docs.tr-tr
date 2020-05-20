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
ms.openlocfilehash: dc76274d3b0acbbe0b03eb141d2b3e6ff9063afb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421130"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="ea053-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="ea053-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="ea053-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="ea053-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea053-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ea053-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea053-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea053-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ea053-106">'ndaki `szName`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ea053-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ea053-107">dışı Dizide döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="ea053-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea053-108">dışı Yürütülebilir dosyanın tam yolu da dahil olmak üzere, adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ea053-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="ea053-109">Ad null ile sonlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="ea053-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea053-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea053-110">Requirements</span></span>  
 <span data-ttu-id="ea053-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea053-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea053-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ea053-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ea053-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea053-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea053-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea053-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea053-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea053-115">See also</span></span>

- [<span data-ttu-id="ea053-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea053-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
