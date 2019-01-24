---
title: _CorExeMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6887d390ded1846e201711c9278663b9ff2888
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520285"
---
# <a name="corexemain-function"></a><span data-ttu-id="6cd8d-102">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="6cd8d-102">_CorExeMain Function</span></span>
<span data-ttu-id="6cd8d-103">Ortak dil çalışma zamanı (CLR) başlatır, derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cd8d-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6cd8d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cd8d-105">Remarks</span></span>  
 <span data-ttu-id="6cd8d-106">Bu işlev, yürütülebilir yönetilen derlemelerden oluşturan işlemlerde yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="6cd8d-107">DLL derlemeler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevini.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="6cd8d-108">İşletim sistemi yükleyicisi görüntü dosyasında belirtilen giriş noktası bakılmaksızın bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="6cd8d-109">Windows 98, Windows ME, Windows NT, Windows 2000'de, `_CorExeMain` çağrıldığında dolaylı olarak işletim sistemi yükleyicisi'nde bir düzeltme aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="6cd8d-110">Tüm diğer Windows sürümlerinde, doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="6cd8d-111">Ek bilgi için bkz açıklamalar bölümünde [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd8d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cd8d-112">Requirements</span></span>  
 <span data-ttu-id="6cd8d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd8d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd8d-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6cd8d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cd8d-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6cd8d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd8d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd8d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd8d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cd8d-117">See also</span></span>
- [<span data-ttu-id="6cd8d-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6cd8d-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
