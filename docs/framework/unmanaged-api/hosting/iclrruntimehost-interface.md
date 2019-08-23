---
title: ICLRRuntimeHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965987"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="ec970-102">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec970-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="ec970-103">.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="ec970-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="ec970-104">Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="ec970-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="ec970-105">Tarafından sunulan bazı yöntemlerin atlanarak `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="ec970-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec970-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec970-106">Methods</span></span>  
  
|<span data-ttu-id="ec970-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ec970-107">Method</span></span>|<span data-ttu-id="ec970-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec970-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec970-109">ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="ec970-110">Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ec970-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="ec970-111">ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="ec970-112"><xref:System.AppDomain> Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec970-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="ec970-113">ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="ec970-114">Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="ec970-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="ec970-115">GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="ec970-116">Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ec970-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="ec970-117">GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="ec970-118">Şu anda yürütülmekte <xref:System.AppDomain> olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ec970-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="ec970-119">SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="ec970-120">Konak denetim arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec970-120">Sets the host control interface.</span></span> <span data-ttu-id="ec970-121">`SetHostControl` Çağrılmadan`Start`önce öğesini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec970-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="ec970-122">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="ec970-123">CLR 'yi bir işlem olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="ec970-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="ec970-124">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="ec970-125">Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="ec970-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="ec970-126">UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec970-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="ec970-127"><xref:System.AppDomain> Belirtilen sayısal tanımlayıcıya karşılık gelen öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec970-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec970-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec970-128">Remarks</span></span>  
 <span data-ttu-id="ec970-129">.NET Framework 4 `ICLRRuntimeHost`' te başlayarak ICLRMetaHost arabirimini kullanarak [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve sonra bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodunu çağırın. [](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ec970-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="ec970-130">.NET Framework önceki sürümlerinde, konak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)çağırarak `ICLRRuntimeHost` bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ec970-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="ec970-131">.NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için `ICLRRuntimeHost` `ICorRuntimeHost`yerine kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec970-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec970-132">Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemini çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="ec970-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="ec970-133">Yöntemi ilk kez `ExecuteApplication` çağrılırsa Yöntem çağrısı başarısız olur. `Start`</span><span class="sxs-lookup"><span data-stu-id="ec970-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec970-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec970-134">Requirements</span></span>  
 <span data-ttu-id="ec970-135">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec970-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec970-136">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec970-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec970-137">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ec970-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec970-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec970-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec970-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec970-139">See also</span></span>

- [<span data-ttu-id="ec970-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="ec970-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="ec970-141">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="ec970-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="ec970-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec970-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ec970-143">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec970-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="ec970-144">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec970-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ec970-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="ec970-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
