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
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429140"
---
# <a name="corexemain-function"></a><span data-ttu-id="777d7-102">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="777d7-102">_CorExeMain Function</span></span>
<span data-ttu-id="777d7-103">Ortak dil çalışma zamanı (CLR) başlatır, yürütülebilir derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="777d7-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="777d7-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="777d7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="777d7-105">Remarks</span></span>  
 <span data-ttu-id="777d7-106">Bu işlev, Yönetilen yürütülebilir derlemelerden oluşturulan işlemlerde yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="777d7-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="777d7-107">DLL derlemeler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="777d7-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="777d7-108">İşletim sistemi yükleyicisi görüntü dosyasında belirtilen giriş noktası bağımsız olarak bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="777d7-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="777d7-109">Windows 98, Windows ME, Windows NT ve Windows 2000'de, `_CorExeMain` işlevi çağrıldığında dolaylı olarak işletim sistemi yükleyicisi içinde düzeltme aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="777d7-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="777d7-110">Tüm diğer Windows sürümlerinde doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="777d7-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="777d7-111">Ek bilgi için açıklamalar bölümünde bakın [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="777d7-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777d7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="777d7-112">Requirements</span></span>  
 <span data-ttu-id="777d7-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777d7-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="777d7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="777d7-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="777d7-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="777d7-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777d7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="777d7-117">See Also</span></span>  
 [<span data-ttu-id="777d7-118">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="777d7-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
