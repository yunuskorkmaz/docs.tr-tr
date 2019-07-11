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
ms.openlocfilehash: 1d35bd5f8aaa2dc0df0044671414a5a936fed24d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781065"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="a0877-102">METAHOST_POLICY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a0877-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="a0877-103">Çoğu çalışma zamanı konaklar için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0877-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="a0877-104">Bu sabit listesi tarafından kullanılan [Iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a0877-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0877-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0877-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="a0877-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a0877-106">Members</span></span>  
  
|<span data-ttu-id="a0877-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a0877-107">Member</span></span>|<span data-ttu-id="a0877-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0877-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="a0877-109">Geçerli işlem içine yüklenmiş tüm ortak dil çalışma zamanının (CLR) göz önünde bulundurmaz yüksek uyumluluk İlkesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0877-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="a0877-110">Bunun yerine, bunu yalnızca yüklü CLRs ve bileşen tercihleri derleme dosyası, bildirilen yerleşik karşı sürümü veya yapılandırma dosyasını türetildiği haliyle olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a0877-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="a0877-111">Tam bir eşleşme, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft içeriklerine dayanan bulunmadığında, sürüm bağlama sonucu yükseltme İlkesi uygular\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="a0877-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="a0877-112">Bu aynı etkiye sahiptir [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a0877-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="a0877-113">Yeni bir işleme çağrısına sağlanan görüntü Gezginden gibi bağlama sonuçlar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a0877-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="a0877-114">Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve çalışma zamanı kümesini karşı bağlar.</span><span class="sxs-lookup"><span data-stu-id="a0877-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="a0877-115">Bu bayrak başlatıldığında bir EXE bağlanacağı hangi çalışma zamanı belirlemek bir konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0877-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="a0877-116">Bir hata iletişim kutusu görüntülenir `GetRequestedRuntime` giriş parametreleri ile uyumlu olan bir çalışma zamanı bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="a0877-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="a0877-117">.NET Framework 4.5 ile başlayarak, bu hata iletişim kutusunda kullanıcı uygun özelliğini etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçiminde.</span><span class="sxs-lookup"><span data-stu-id="a0877-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="a0877-118">`GetRequestedRuntime` işlem görüntü (ve karşılık gelen herhangi bir yapılandırma dosyası) bağlama işlemi için ek giriş olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0877-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="a0877-119">Varsayılan olarak, `GetRequestedRuntime` geri işlem görüntü yolu (genellikle işlemi başlatmak için kullanılan EXE) düşmüyorsa bağlamak için çalışma zamanı belirlerken.</span><span class="sxs-lookup"><span data-stu-id="a0877-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="a0877-120">`GetRequestedRuntime` yapılandırma dosyasında hiçbir bilgi kullanılabilir olduğunda ve uygun SKU yüklü olup olmadığını denetlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a0877-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="a0877-121">Bu, varsayılan yükleme .NET Framework'ün daha küçük SKU'ları üzerinde düzgün bir şekilde başarısız için yapılandırma dosyalarını olmayan uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0877-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="a0877-122">Varsayılan olarak, `GetRequestedRuntime` SKU öznitelik yapılandırma dosyasında belirtilmediği sürece ve uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0877-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="a0877-123">`GetRequestedRuntime` SEM_FAILCRITICALERRORS sayılmalıdır (çağırarak Hosted [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi) ve hata iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="a0877-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="a0877-124">Varsayılan olarak, hata iletişim kutusu SEM_FAILCRITICALERRORS bastırır.</span><span class="sxs-lookup"><span data-stu-id="a0877-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="a0877-125">Başka bir işlemden devralınmış ve sessiz hata senaryonuzda istenmeyen olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0877-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0877-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0877-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0877-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0877-127">Requirements</span></span>  
 <span data-ttu-id="a0877-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0877-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0877-129">**Üst bilgi:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="a0877-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="a0877-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a0877-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0877-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0877-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0877-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0877-132">See also</span></span>

- [<span data-ttu-id="a0877-133">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a0877-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="a0877-134">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0877-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
