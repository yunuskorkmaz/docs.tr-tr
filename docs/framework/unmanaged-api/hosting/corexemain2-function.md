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
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183163"
---
# <a name="corexemain2-function"></a><span data-ttu-id="2afbc-102">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="2afbc-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="2afbc-103">Belirtilen bellek eşlemeli kod içinde giriş noktasını yürütür.</span><span class="sxs-lookup"><span data-stu-id="2afbc-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="2afbc-104">Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2afbc-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2afbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2afbc-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2afbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2afbc-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="2afbc-107">[in] Bellek eşlemeli kod için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2afbc-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="2afbc-108">[in] Öğe sayısı `pUnmappedPE` basılı tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2afbc-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="2afbc-109">[in] Yürütülebilir resmin adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2afbc-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="2afbc-110">[in] Yükleyici dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="2afbc-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="2afbc-111">[in] Komut satırı parametreleri, varsa.</span><span class="sxs-lookup"><span data-stu-id="2afbc-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2afbc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2afbc-112">Requirements</span></span>  
 <span data-ttu-id="2afbc-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2afbc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2afbc-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2afbc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2afbc-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2afbc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2afbc-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2afbc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afbc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2afbc-117">See also</span></span>

- [<span data-ttu-id="2afbc-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2afbc-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
