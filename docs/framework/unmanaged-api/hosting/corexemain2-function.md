---
title: "_CorExeMain2 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain2
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorExeMain2
helpviewer_keywords: _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69e03de14a2a86600b7acbc7ff8ceca4d845f0ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corexemain2-function"></a><span data-ttu-id="56b36-102">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="56b36-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="56b36-103">Giriş noktası belirtilen bellekle eşlenen kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="56b36-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="56b36-104">Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="56b36-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56b36-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56b36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56b36-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="56b36-107">[in] Bellek eşlemeli kodu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56b36-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="56b36-108">[in] Öğe sayısını `pUnmappedPE` basılı tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56b36-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="56b36-109">[in] Yürütülebilir görüntü adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56b36-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="56b36-110">[in] Yükleyici dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="56b36-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="56b36-111">[in] Komut satırı parametreleri, varsa.</span><span class="sxs-lookup"><span data-stu-id="56b36-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b36-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56b36-112">Requirements</span></span>  
 <span data-ttu-id="56b36-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b36-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56b36-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56b36-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="56b36-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56b36-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b36-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56b36-117">See Also</span></span>  
 [<span data-ttu-id="56b36-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="56b36-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
