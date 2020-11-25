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
ms.openlocfilehash: 16fb112cf5b209091001872567c95bb0b3a8ab61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729999"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="fed2d-102">METAHOST_POLICY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fed2d-102">METAHOST_POLICY_FLAGS Enumeration</span></span>

<span data-ttu-id="fed2d-103">Çoğu çalışma zamanı ana bilgisayarı için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fed2d-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="fed2d-104">Bu numaralandırma [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fed2d-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed2d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fed2d-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fed2d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fed2d-106">Members</span></span>  
  
|<span data-ttu-id="fed2d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="fed2d-107">Member</span></span>|<span data-ttu-id="fed2d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed2d-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="fed2d-109">Geçerli işleme yüklenmiş ortak dil çalışma zamanını (CLR) düşünmez olan yüksek uyumluluk ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed2d-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="fed2d-110">Bunun yerine, yalnızca yüklü CLRs 'leri ve bileşen tercihlerini, derleme dosyasının kendisinden türetildikleri gibi, derlenen yerleşik sürümü veya yapılandırma dosyası olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="fed2d-111">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftiçeriğine göre tam eşleşme bulunamadığında, sürüm bağlama sonucuna yükseltme ilkesi uygular \\ . Netframework\ilkeupgrades.</span><span class="sxs-lookup"><span data-stu-id="fed2d-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="fed2d-112">Bu, [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)ile aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="fed2d-113">Bağlama sonuçları, çağrıya verilen görüntü yeni bir işlemde başlatılmış gibi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fed2d-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="fed2d-114">Şu anda, `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve yüklü çalışma zamanları kümesine göre bağlar.</span><span class="sxs-lookup"><span data-stu-id="fed2d-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="fed2d-115">Bu bayrak, bir konağın başlatıldığında bir EXE 'nin hangi çalışma zamanına bağlanacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="fed2d-116">`GetRequestedRuntime`Giriş parametreleriyle uyumlu bir çalışma zamanı bulamazsa bir hata iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="fed2d-117">.NET Framework 4,5 ' den başlayarak bu hata iletişim kutusu, kullanıcının uygun özelliği etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçimini alabilir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="fed2d-118">`GetRequestedRuntime` bağlama işlemine ek girdi olarak işlem görüntüsünü (ve ilgili yapılandırma dosyalarını) kullanır.</span><span class="sxs-lookup"><span data-stu-id="fed2d-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="fed2d-119">Varsayılan olarak, `GetRequestedRuntime` bağlanacak çalışma zamanı belirlenirken işlem görüntü yoluna (genellikle işlemi başlatmak için kullanılan exe) geri dönmez.</span><span class="sxs-lookup"><span data-stu-id="fed2d-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="fed2d-120">`GetRequestedRuntime` yapılandırma dosyasında hiçbir bilgi yoksa ilgili SKU 'nun yüklenip yüklenmediğini kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="fed2d-121">Bu, yapılandırma dosyaları olmayan uygulamaların, .NET Framework varsayılan yüklemesinden daha küçük SKU 'Larda düzgün şekilde başarısız olmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fed2d-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="fed2d-122">Varsayılan olarak, `GetRequestedRuntime` yapılandırma dosyası ÖĞESINDE SKU özniteliği belirtilmediği takdirde uygun SKU 'nun yüklenip yüklenmediğini denetlemez `<supportedRuntime />` .</span><span class="sxs-lookup"><span data-stu-id="fed2d-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="fed2d-123">`GetRequestedRuntime` SEM_FAILCRITICALERRORS göz ardı etmelidir ( [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevi çağırarak ayarlanır) ve hata iletişim kutusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="fed2d-124">Varsayılan olarak, SEM_FAILCRITICALERRORS hata iletişim kutusunu bastırır.</span><span class="sxs-lookup"><span data-stu-id="fed2d-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="fed2d-125">Başka bir işlemden devralınan ve sessiz hata, senaryonuza istenmeyen bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="fed2d-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fed2d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fed2d-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fed2d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fed2d-127">Requirements</span></span>  

 <span data-ttu-id="fed2d-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fed2d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fed2d-129">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="fed2d-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="fed2d-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fed2d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fed2d-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fed2d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed2d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fed2d-132">See also</span></span>

- [<span data-ttu-id="fed2d-133">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="fed2d-133">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="fed2d-134">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fed2d-134">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
