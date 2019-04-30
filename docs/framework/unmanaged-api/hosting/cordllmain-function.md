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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666927"
---
# <a name="cordllmain-function"></a><span data-ttu-id="f83b9-102">\_CorDllMain işlevi</span><span class="sxs-lookup"><span data-stu-id="f83b9-102">\_CorDllMain Function</span></span>

<span data-ttu-id="f83b9-103">Ortak dil çalışma zamanı (CLR) başlatır, DLL derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="f83b9-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f83b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f83b9-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f83b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f83b9-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="f83b9-106">[in] Yüklenen bir modülün örneği tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f83b9-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="f83b9-107">[in] DLL giriş noktası işlevini neden çağrılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="f83b9-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="f83b9-108">Bu parametre aşağıdaki değerlerden biri olabilir: DLL\__DllMainCRTStartup, DLL\_iş PARÇACIĞI\_ATTACH, DLL\_iş PARÇACIĞI\_Ekle veya DLL\_işlem\_ayırma.</span><span class="sxs-lookup"><span data-stu-id="f83b9-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="f83b9-109">Bu değerleri açıklamaları için bkz. `DllMain` Platform SDK belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="f83b9-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="f83b9-110">[in] Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="f83b9-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f83b9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f83b9-111">Return Value</span></span>  
 <span data-ttu-id="f83b9-112">Bu yöntem döndürür `true` başarı için ve `false` hata oluşması durumunda.</span><span class="sxs-lookup"><span data-stu-id="f83b9-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f83b9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f83b9-113">Remarks</span></span>  
 <span data-ttu-id="f83b9-114">Bu işlev, DLL derlemeler için işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f83b9-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="f83b9-115">Yürütülebilir derlemeler için yükleyici çağırır [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini.</span><span class="sxs-lookup"><span data-stu-id="f83b9-115">For executable assemblies, the loader calls the [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="f83b9-116">İşletim sistemi yükleyicisi DLL dosyası içinde belirtilen giriş noktası bakılmaksızın bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f83b9-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="f83b9-117">`_CorDllMain` İşlevi, doğrudan işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f83b9-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="f83b9-118">Ek bilgi için bkz açıklamalar bölümünde [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f83b9-118">For additional information, see the Remarks section in the [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f83b9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f83b9-119">Requirements</span></span>  

 <span data-ttu-id="f83b9-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f83b9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f83b9-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f83b9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f83b9-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f83b9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f83b9-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f83b9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83b9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f83b9-124">See also</span></span>

- [<span data-ttu-id="f83b9-125">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f83b9-125">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
