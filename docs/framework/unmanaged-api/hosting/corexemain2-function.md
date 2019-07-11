---
title: _CorExeMain2 İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46dab35c44e59a149822005575c83c13e9350455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758537"
---
# <a name="corexemain2-function"></a><span data-ttu-id="7d4eb-102">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="7d4eb-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="7d4eb-103">Belirtilen bellek eşlemeli kod içinde giriş noktasını yürütür.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="7d4eb-104">Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d4eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d4eb-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d4eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d4eb-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="7d4eb-107">[in] Bellek eşlemeli kod için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="7d4eb-108">[in] Öğe sayısı `pUnmappedPE` basılı tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="7d4eb-109">[in] Yürütülebilir resmin adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="7d4eb-110">[in] Yükleyici dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="7d4eb-111">[in] Komut satırı parametreleri, varsa.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4eb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d4eb-112">Requirements</span></span>  
 <span data-ttu-id="7d4eb-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d4eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4eb-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7d4eb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d4eb-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d4eb-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d4eb-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d4eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4eb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d4eb-117">See also</span></span>

- [<span data-ttu-id="7d4eb-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7d4eb-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
