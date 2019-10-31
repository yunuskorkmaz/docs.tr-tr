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
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136956"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="495ec-102">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="495ec-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="495ec-103">Giriş noktasını belirtilen bellek eşlemeli kodda yürütür.</span><span class="sxs-lookup"><span data-stu-id="495ec-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="495ec-104">Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="495ec-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="495ec-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="495ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="495ec-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="495ec-107">'ndaki Bellek eşlemeli koda yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="495ec-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="495ec-108">'ndaki `pUnmappedPE` öğe sayısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="495ec-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="495ec-109">'ndaki Yürütülebilir görüntünün adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="495ec-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="495ec-110">'ndaki Yükleyici dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="495ec-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="495ec-111">'ndaki Varsa komut satırı parametreleri.</span><span class="sxs-lookup"><span data-stu-id="495ec-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495ec-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="495ec-112">Requirements</span></span>  
 <span data-ttu-id="495ec-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="495ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495ec-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="495ec-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="495ec-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="495ec-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="495ec-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495ec-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="495ec-117">See also</span></span>

- [<span data-ttu-id="495ec-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="495ec-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
