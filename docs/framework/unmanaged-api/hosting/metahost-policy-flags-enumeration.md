---
description: 'Hakkında daha fazla bilgi edinin: METAHOST_POLICY_FLAGS numaralandırması'
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
ms.openlocfilehash: 3a3ebe602c8f048b7f9fc907f5d4741722bd0ed3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679629"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="0db21-103">METAHOST_POLICY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0db21-103">METAHOST_POLICY_FLAGS Enumeration</span></span>

<span data-ttu-id="0db21-104">Çoğu çalışma zamanı ana bilgisayarı için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0db21-104">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="0db21-105">Bu numaralandırma [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0db21-105">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db21-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0db21-106">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0db21-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0db21-107">Members</span></span>  
  
|<span data-ttu-id="0db21-108">Üye</span><span class="sxs-lookup"><span data-stu-id="0db21-108">Member</span></span>|<span data-ttu-id="0db21-109">Description</span><span class="sxs-lookup"><span data-stu-id="0db21-109">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="0db21-110">Geçerli işleme yüklenmiş ortak dil çalışma zamanını (CLR) düşünmez olan yüksek uyumluluk ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0db21-110">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="0db21-111">Bunun yerine, yalnızca yüklü CLRs 'leri ve bileşen tercihlerini, derleme dosyasının kendisinden türetildikleri gibi, derlenen yerleşik sürümü veya yapılandırma dosyası olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0db21-111">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="0db21-112">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftiçeriğine göre tam eşleşme bulunamadığında, sürüm bağlama sonucuna yükseltme ilkesi uygular \\ . Netframework\ilkeupgrades.</span><span class="sxs-lookup"><span data-stu-id="0db21-112">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="0db21-113">Bu, [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)ile aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0db21-113">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="0db21-114">Bağlama sonuçları, çağrıya verilen görüntü yeni bir işlemde başlatılmış gibi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0db21-114">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="0db21-115">Şu anda, `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve yüklü çalışma zamanları kümesine göre bağlar.</span><span class="sxs-lookup"><span data-stu-id="0db21-115">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="0db21-116">Bu bayrak, bir konağın başlatıldığında bir EXE 'nin hangi çalışma zamanına bağlanacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="0db21-116">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="0db21-117">`GetRequestedRuntime`Giriş parametreleriyle uyumlu bir çalışma zamanı bulamazsa bir hata iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0db21-117">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="0db21-118">.NET Framework 4,5 ' den başlayarak bu hata iletişim kutusu, kullanıcının uygun özelliği etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçimini alabilir.</span><span class="sxs-lookup"><span data-stu-id="0db21-118">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="0db21-119">`GetRequestedRuntime` bağlama işlemine ek girdi olarak işlem görüntüsünü (ve ilgili yapılandırma dosyalarını) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0db21-119">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="0db21-120">Varsayılan olarak, `GetRequestedRuntime` bağlanacak çalışma zamanı belirlenirken işlem görüntü yoluna (genellikle işlemi başlatmak için kullanılan exe) geri dönmez.</span><span class="sxs-lookup"><span data-stu-id="0db21-120">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="0db21-121">`GetRequestedRuntime` yapılandırma dosyasında hiçbir bilgi yoksa ilgili SKU 'nun yüklenip yüklenmediğini kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="0db21-121">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="0db21-122">Bu, yapılandırma dosyaları olmayan uygulamaların, .NET Framework varsayılan yüklemesinden daha küçük SKU 'Larda düzgün şekilde başarısız olmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0db21-122">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="0db21-123">Varsayılan olarak, `GetRequestedRuntime` yapılandırma dosyası ÖĞESINDE SKU özniteliği belirtilmediği takdirde uygun SKU 'nun yüklenip yüklenmediğini denetlemez `<supportedRuntime />` .</span><span class="sxs-lookup"><span data-stu-id="0db21-123">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="0db21-124">`GetRequestedRuntime` SEM_FAILCRITICALERRORS göz ardı etmelidir ( [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevi çağırarak ayarlanır) ve hata iletişim kutusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0db21-124">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="0db21-125">Varsayılan olarak, SEM_FAILCRITICALERRORS hata iletişim kutusunu bastırır.</span><span class="sxs-lookup"><span data-stu-id="0db21-125">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="0db21-126">Başka bir işlemden devralınan ve sessiz hata, senaryonuza istenmeyen bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="0db21-126">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0db21-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0db21-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0db21-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0db21-128">Requirements</span></span>  

 <span data-ttu-id="0db21-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0db21-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0db21-130">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="0db21-130">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="0db21-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0db21-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0db21-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0db21-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db21-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0db21-133">See also</span></span>

- [<span data-ttu-id="0db21-134">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="0db21-134">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="0db21-135">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0db21-135">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
