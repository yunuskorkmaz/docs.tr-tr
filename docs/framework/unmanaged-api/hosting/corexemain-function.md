---
title: "_CorExeMain İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c341d578a45d72804d9ac33e2aefe513fd33922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="7c5e9-102">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="7c5e9-102">_CorExeMain Function</span></span>
<span data-ttu-id="7c5e9-103">Ortak dil çalışma zamanı (CLR) başlatır, yürütülebilir derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c5e9-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7c5e9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c5e9-105">Remarks</span></span>  
 <span data-ttu-id="7c5e9-106">Bu işlev, Yönetilen yürütülebilir derlemelerden oluşturulan işlemlerde yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="7c5e9-107">DLL derlemeler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="7c5e9-108">İşletim sistemi yükleyicisi görüntü dosyasında belirtilen giriş noktası bağımsız olarak bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="7c5e9-109">Windows 98, Windows ME, Windows NT ve Windows 2000'de, `_CorExeMain` işlevi çağrıldığında dolaylı olarak işletim sistemi yükleyicisi içinde düzeltme aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="7c5e9-110">Tüm diğer Windows sürümlerinde doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="7c5e9-111">Ek bilgi için açıklamalar bölümünde bakın [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c5e9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c5e9-112">Requirements</span></span>  
 <span data-ttu-id="7c5e9-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c5e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c5e9-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c5e9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c5e9-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7c5e9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c5e9-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c5e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5e9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c5e9-117">See Also</span></span>  
 [<span data-ttu-id="7c5e9-118">Meta veri genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="7c5e9-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
