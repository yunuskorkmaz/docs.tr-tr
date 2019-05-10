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
ms.openlocfilehash: da22cbfe06245d915bed6db9cba220fc32b38942
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627136"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="4a9a4-102">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="4a9a4-103">Benzer işlevlere [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework sürüm 1'i aşağıdaki değişikliklerle birlikte sağlanan arabirim:</span><span class="sxs-lookup"><span data-stu-id="4a9a4-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="4a9a4-104">Ek [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) konak denetimi arabirimi ayarlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="4a9a4-105">Tarafından sağlanan bazı yöntemler Java'daki `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a9a4-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4a9a4-106">Methods</span></span>  
  
|<span data-ttu-id="4a9a4-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4a9a4-107">Method</span></span>|<span data-ttu-id="4a9a4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a9a4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a9a4-109">ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="4a9a4-110">ClickOnce dağıtım senaryolarında bildirim tabanlı yeni bir etki alanı etkinleştirilmesi için uygulamayı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="4a9a4-111">ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="4a9a4-112">Belirtir <xref:System.AppDomain> burada belirtilen yönetilen kodu yürütmek.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="4a9a4-113">ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="4a9a4-114">Belirtilen bütünleştirilmiş kod içinde belirtilen türün belirtilen yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="4a9a4-115">GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="4a9a4-116">Türü bir arabirim işaretçisi alır [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="4a9a4-117">GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="4a9a4-118">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="4a9a4-119">SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="4a9a4-120">Konak denetimi arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-120">Sets the host control interface.</span></span> <span data-ttu-id="4a9a4-121">Çağırmalısınız `SetHostControl` çağırmadan önce `Start`.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="4a9a4-122">Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="4a9a4-123">CLR'yi bir işleme başlatır.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="4a9a4-124">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="4a9a4-125">Çalışma zamanı tarafından kodun yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="4a9a4-126">UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="4a9a4-127">Bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a9a4-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a9a4-128">Remarks</span></span>  
 <span data-ttu-id="4a9a4-129">İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], kullanın [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) işaretçisi almak için arabirimi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirim ve sonra çağrı [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) işaretçisi almak için yöntemi `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="4a9a4-130">Önceki .NET Framework sürümlerinde, konak için bir işaretçi alır. bir `ICLRRuntimeHost` çağırarak örneği [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="4a9a4-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="4a9a4-131">.NET Framework 2.0 sürümünde sağlanan teknolojilerin hiçbiri uygulamaları sağlamak için kullanmanız gerekir `ICLRRuntimeHost` yerine `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a9a4-132">Çağırmayın [Başlat](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="4a9a4-133">Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a9a4-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a9a4-134">Requirements</span></span>  
 <span data-ttu-id="4a9a4-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a9a4-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a9a4-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a9a4-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a9a4-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a9a4-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a9a4-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a9a4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9a4-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a9a4-139">See also</span></span>

- [<span data-ttu-id="4a9a4-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="4a9a4-141">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="4a9a4-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4a9a4-143">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9a4-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="4a9a4-144">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a9a4-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4a9a4-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="4a9a4-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
