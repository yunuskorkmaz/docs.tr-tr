---
title: METAHOST_POLICY_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f980fb1336adaf43091e41b9e42ea008b00c033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447291"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="b085a-102">METAHOST_POLICY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b085a-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="b085a-103">Çoğu çalışma zamanı konaklar için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="b085a-104">Bu numaralandırma tarafından kullanılan [Iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b085a-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b085a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b085a-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b085a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b085a-106">Members</span></span>  
  
|<span data-ttu-id="b085a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b085a-107">Member</span></span>|<span data-ttu-id="b085a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b085a-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="b085a-109">Geçerli işlemine yüklenen tüm ortak dil çalışma zamanı (CLR) dikkate almaz yüksek uyumluluk İlkesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="b085a-110">Bunun yerine, onu yalnızca yüklü CLRs ve bileşen Tercihler derleme dosyası, bildirilen yerleşik karşı sürümü veya yapılandırma dosyasını türetilmiş olarak göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="b085a-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="b085a-111">Tam bir eşleşme, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft içeriğine göre bulunmadığında, yükseltme ilkesi sürüm bağlama sonucu geçerlidir\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="b085a-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="b085a-112">Bu aynı etkiye sahip [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b085a-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="b085a-113">Bağlama sonuçları çağrısına sağlanan görüntüsünü yeni bir işlemde başlatılan olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b085a-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="b085a-114">Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesi yoksayar ve yüklü çalışma zamanları kümesi karşı bağlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="b085a-115">Bu bayrak başlatıldığında bir EXE bağlanacağı hangi çalışma zamanı belirlemek bir konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="b085a-116">Bir hata iletişim kutusu görüntülenir `GetRequestedRuntime` giriş parametreleri ile uyumlu bir çalışma zamanı bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="b085a-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="b085a-117">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], bu hata iletişim kutusunda kullanıcı uygun özelliğini etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçiminde.</span><span class="sxs-lookup"><span data-stu-id="b085a-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="b085a-118">`GetRequestedRuntime` işlem görüntü (ve karşılık gelen hiçbir yapılandırma dosyası) bağlama işlemi ek giriş olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="b085a-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="b085a-119">Varsayılan olarak, `GetRequestedRuntime` işlem görüntü yolu (genellikle, işlemi başlatmak için kullanılan EXE) için geri dönüş değil bağlamak için çalışma zamanı belirlerken.</span><span class="sxs-lookup"><span data-stu-id="b085a-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="b085a-120">`GetRequestedRuntime` hiçbir bilgi yapılandırma dosyasında kullanılabilir olduğunda uygun SKU yüklü olup olmadığını denetleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="b085a-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="b085a-121">Bu yapılandırma dosyalarını .NET Framework'ün varsayılan yükleme değerinden daha küçük SKU üzerinde düzgün biçimde başarısız olmayan uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="b085a-122">Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyasında belirtilmediği sürece uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b085a-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="b085a-123">`GetRequestedRuntime` hiçbir bilgi yapılandırma dosyasında kullanılabilir olduğunda uygun SKU yüklü olup olmadığını denetleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="b085a-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="b085a-124">Bu yapılandırma dosyalarını .NET Framework'ün varsayılan yükleme değerinden daha küçük SKU üzerinde düzgün biçimde başarısız olmayan uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b085a-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="b085a-125">Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyasında belirtilmediği sürece uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b085a-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="b085a-126">`GetRequestedRuntime` SEM_FAILCRITICALERRORS yok saymanız gerekir (çağırarak ayarlanmış [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi) ve hata iletişim kutusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b085a-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="b085a-127">Varsayılan olarak, hata iletişim kutusu SEM_FAILCRITICALERRORS gizler.</span><span class="sxs-lookup"><span data-stu-id="b085a-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="b085a-128">Başka bir işlemden devralınmış ve sessiz hatası senaryonuzda istenmeyen olabilir.</span><span class="sxs-lookup"><span data-stu-id="b085a-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b085a-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b085a-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b085a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b085a-130">Requirements</span></span>  
 <span data-ttu-id="b085a-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b085a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b085a-132">**Başlık:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="b085a-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="b085a-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b085a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b085a-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b085a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b085a-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b085a-135">See Also</span></span>  
 [<span data-ttu-id="b085a-136">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b085a-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="b085a-137">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b085a-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
