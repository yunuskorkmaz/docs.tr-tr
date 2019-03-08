---
title: _CorDllMain İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679313"
---
# <a name="cordllmain-function"></a><span data-ttu-id="f0117-102">\_CorDllMain işlevi</span><span class="sxs-lookup"><span data-stu-id="f0117-102">\_CorDllMain Function</span></span>

<span data-ttu-id="f0117-103">Ortak dil çalışma zamanı (CLR) başlatır, DLL derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="f0117-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0117-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0117-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0117-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0117-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="f0117-106">[in] Yüklenen bir modülün örneği tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0117-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="f0117-107">[in] DLL giriş noktası işlevini neden çağrılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0117-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="f0117-108">Bu parametre aşağıdaki değerlerden biri olabilir: DLL\__DllMainCRTStartup, DLL\_iş PARÇACIĞI\_ATTACH, DLL\_iş PARÇACIĞI\_Ekle veya DLL\_işlem\_ayırma.</span><span class="sxs-lookup"><span data-stu-id="f0117-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="f0117-109">Bu değerleri açıklamaları için bkz. `DllMain` Platform SDK belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="f0117-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="f0117-110">[in] Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="f0117-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0117-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0117-111">Return Value</span></span>  
 <span data-ttu-id="f0117-112">Bu yöntem döndürür `true` başarı için ve `false` hata oluşması durumunda.</span><span class="sxs-lookup"><span data-stu-id="f0117-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0117-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0117-113">Remarks</span></span>  
 <span data-ttu-id="f0117-114">Bu işlev, DLL derlemeler için işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f0117-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="f0117-115">Yürütülebilir derlemeler için yükleyici çağırır [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini.</span><span class="sxs-lookup"><span data-stu-id="f0117-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="f0117-116">İşletim sistemi yükleyicisi DLL dosyası içinde belirtilen giriş noktası bakılmaksızın bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f0117-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="f0117-117">`_CorDllMain` İşlevi, doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f0117-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="f0117-118">Ek bilgi için bkz açıklamalar bölümünde [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f0117-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0117-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0117-119">Requirements</span></span>  

 <span data-ttu-id="f0117-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0117-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0117-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f0117-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0117-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f0117-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0117-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0117-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0117-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0117-124">See also</span></span>

- [<span data-ttu-id="f0117-125">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f0117-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
