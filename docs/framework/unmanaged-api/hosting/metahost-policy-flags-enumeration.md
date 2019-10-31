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
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141391"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="8fea7-102">METAHOST_POLICY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8fea7-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="8fea7-103">Çoğu çalışma zamanı ana bilgisayarı için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fea7-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="8fea7-104">Bu numaralandırma [ICLRMetaHostPolicy:: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fea7-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fea7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fea7-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8fea7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8fea7-106">Members</span></span>  
  
|<span data-ttu-id="8fea7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="8fea7-107">Member</span></span>|<span data-ttu-id="8fea7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fea7-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="8fea7-109">Geçerli işleme yüklenmiş ortak dil çalışma zamanını (CLR) düşünmez olan yüksek uyumluluk ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fea7-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="8fea7-110">Bunun yerine, yalnızca yüklü CLRs 'leri ve bileşen tercihlerini, derleme dosyasının kendisinden türetildikleri gibi, derlenen yerleşik sürümü veya yapılandırma dosyası olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="8fea7-111">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\içeriğine göre tam eşleşme bulunamadığında, sürüm bağlama sonucuna yükseltme ilkesi uygular. Netframework\ilkeupgrades.</span><span class="sxs-lookup"><span data-stu-id="8fea7-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="8fea7-112">Bu, [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)ile aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="8fea7-113">Bağlama sonuçları, çağrıya verilen görüntü yeni bir işlemde başlatılmış gibi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8fea7-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="8fea7-114">Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve yüklü çalışma zamanları kümesine göre bağlar.</span><span class="sxs-lookup"><span data-stu-id="8fea7-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="8fea7-115">Bu bayrak, bir konağın başlatıldığında bir EXE 'nin hangi çalışma zamanına bağlanacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="8fea7-116">`GetRequestedRuntime`, giriş parametreleriyle uyumlu bir çalışma zamanı bulamazsa bir hata iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="8fea7-117">.NET Framework 4,5 ' den başlayarak bu hata iletişim kutusu, kullanıcının uygun özelliği etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçimini alabilir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="8fea7-118">`GetRequestedRuntime`, bağlama işlemine ek girdi olarak işlem görüntüsünü (ve ilgili yapılandırma dosyalarını) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8fea7-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="8fea7-119">Varsayılan olarak `GetRequestedRuntime`, bağlanacak çalışma zamanı belirlenirken işlem görüntü yoluna (genellikle işlemi başlatmak için kullanılan EXE) geri dönmemektedir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="8fea7-120">`GetRequestedRuntime`, yapılandırma dosyasında herhangi bir bilgi yoksa ilgili SKU 'nun yüklenip yüklenmediğini denetmelidir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="8fea7-121">Bu, yapılandırma dosyaları olmayan uygulamaların, .NET Framework varsayılan yüklemesinden daha küçük SKU 'Larda düzgün şekilde başarısız olmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fea7-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="8fea7-122">Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyası `<supportedRuntime />` öğesinde belirtilmediği takdirde uygun SKU 'nun yüklenip yüklenmediğini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="8fea7-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="8fea7-123">`GetRequestedRuntime`, SEM_FAILCRITICALERRORS ( [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi çağırarak ayarlanır) öğesini yoksayıp hata iletişim kutusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="8fea7-124">Varsayılan olarak, SEM_FAILCRITICALERRORS hata iletişim kutusunu bastırır.</span><span class="sxs-lookup"><span data-stu-id="8fea7-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="8fea7-125">Başka bir işlemden devralınan ve sessiz hata, senaryonuza istenmeyen bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fea7-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fea7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fea7-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fea7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fea7-127">Requirements</span></span>  
 <span data-ttu-id="8fea7-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fea7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fea7-129">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="8fea7-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="8fea7-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8fea7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fea7-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fea7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fea7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fea7-132">See also</span></span>

- [<span data-ttu-id="8fea7-133">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8fea7-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="8fea7-134">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fea7-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
