---
description: 'Hakkında daha fazla bilgi edinin: _CorExeMain2 Işlevi'
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
ms.openlocfilehash: 4629ea2f6c2ba13351c409bc382077eea926b507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717114"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="b93ff-103">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="b93ff-103">_CorExeMain2 Function</span></span>

<span data-ttu-id="b93ff-104">Giriş noktasını belirtilen bellek eşlemeli kodda yürütür.</span><span class="sxs-lookup"><span data-stu-id="b93ff-104">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="b93ff-105">Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b93ff-105">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93ff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b93ff-106">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b93ff-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b93ff-107">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="b93ff-108">'ndaki Bellek eşlemeli koda yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b93ff-108">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="b93ff-109">'ndaki Öğelerin sayısı `pUnmappedPE` tutabilirler.</span><span class="sxs-lookup"><span data-stu-id="b93ff-109">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="b93ff-110">'ndaki Yürütülebilir görüntünün adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b93ff-110">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="b93ff-111">'ndaki Yükleyici dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="b93ff-111">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="b93ff-112">'ndaki Varsa komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="b93ff-112">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93ff-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b93ff-113">Requirements</span></span>  

 <span data-ttu-id="b93ff-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b93ff-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b93ff-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b93ff-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b93ff-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b93ff-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b93ff-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b93ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b93ff-118">See also</span></span>

- [<span data-ttu-id="b93ff-119">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b93ff-119">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
