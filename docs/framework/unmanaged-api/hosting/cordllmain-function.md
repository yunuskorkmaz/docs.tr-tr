---
title: "_CorDllMain İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 985f2284026054217671de767c316b1fba35c098
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordllmain-function"></a><span data-ttu-id="6e31c-102">_CorDllMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="6e31c-102">_CorDllMain Function</span></span>
<span data-ttu-id="6e31c-103">Ortak dil çalışma zamanı (CLR) başlatır, DLL derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="6e31c-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e31c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e31c-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e31c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e31c-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="6e31c-106">[in] Yüklenen modülün örneği tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e31c-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="6e31c-107">[in] DLL giriş noktası işlevi neden çağrılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e31c-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="6e31c-108">Bu parametre aşağıdaki değerlerden biri olabilir: DLL_PROCESS_ATTACH, DllMain, DllMain veya DLL_PROCESS_DETACH.</span><span class="sxs-lookup"><span data-stu-id="6e31c-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="6e31c-109">Bu değerleri açıklamaları için bkz: `DllMain` Platform SDK Belgeleri.</span><span class="sxs-lookup"><span data-stu-id="6e31c-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="6e31c-110">[in] Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="6e31c-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e31c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e31c-111">Return Value</span></span>  
 <span data-ttu-id="6e31c-112">Bu yöntem `true` başarı için ve `false` bir hata oluşursa.</span><span class="sxs-lookup"><span data-stu-id="6e31c-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e31c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e31c-113">Remarks</span></span>  
 <span data-ttu-id="6e31c-114">Bu işlev, DLL derlemeler için işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6e31c-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="6e31c-115">Yürütülebilir derlemeler için yükleyici çağırır [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="6e31c-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="6e31c-116">İşletim sistemi yükleyicisi bağımsız olarak DLL dosyasında belirtilen giriş noktası bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="6e31c-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="6e31c-117">Windows 98, Windows ME, Windows NT ve Windows 2000'de, `_CorDllMain` işlevi çağrıldığında dolaylı olarak fixupin işletim sistemi yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6e31c-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="6e31c-118">Tüm diğer Windows sürümlerinde doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6e31c-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="6e31c-119">Ek bilgi için açıklamalar bölümünde bakın [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="6e31c-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e31c-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e31c-120">Requirements</span></span>  
 <span data-ttu-id="6e31c-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e31c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e31c-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e31c-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e31c-123">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6e31c-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e31c-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e31c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e31c-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e31c-125">See Also</span></span>  
 [<span data-ttu-id="6e31c-126">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6e31c-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
