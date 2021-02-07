---
description: 'Bu konuda daha fazla bilgi edinin: ICLRRuntimeHost arabirimi'
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
ms.openlocfilehash: 92bab42fa1cf2cca5caa0eb039c88fec3e65390c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753893"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="52db5-103">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52db5-103">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="52db5-104">.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="52db5-104">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="52db5-105">Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="52db5-105">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="52db5-106">Tarafından sunulan bazı yöntemlerin atlanarak `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="52db5-106">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52db5-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="52db5-107">Methods</span></span>  
  
|<span data-ttu-id="52db5-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="52db5-108">Method</span></span>|<span data-ttu-id="52db5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52db5-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52db5-110">ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-110">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="52db5-111">Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52db5-111">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="52db5-112">ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-112">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="52db5-113"><xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52db5-113">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="52db5-114">ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-114">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="52db5-115">Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="52db5-115">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="52db5-116">GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-116">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="52db5-117">Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52db5-117">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="52db5-118">GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-118">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="52db5-119"><xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="52db5-119">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="52db5-120">SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-120">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="52db5-121">Konak denetim arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52db5-121">Sets the host control interface.</span></span> <span data-ttu-id="52db5-122">`SetHostControl`Çağrılmadan önce öğesini çağırmanız gerekir `Start` .</span><span class="sxs-lookup"><span data-stu-id="52db5-122">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="52db5-123">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-123">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="52db5-124">CLR 'yi bir işlem olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="52db5-124">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="52db5-125">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-125">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="52db5-126">Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="52db5-126">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="52db5-127">UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52db5-127">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="52db5-128"><xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="52db5-128">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52db5-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52db5-129">Remarks</span></span>  

 <span data-ttu-id="52db5-130">.NET Framework 4 ' te başlayarak [ICLRMetaHost](iclrmetahost-interface.md) arabirimini kullanarak [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve sonra bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) metodunu çağırın `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="52db5-130">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="52db5-131">.NET Framework önceki sürümlerinde, konak `ICLRRuntimeHost` [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)çağırarak bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="52db5-131">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="52db5-132">.NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için yerine kullanmanız gerekir `ICLRRuntimeHost` `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="52db5-132">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52db5-133">Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](iclrruntimehost-start-method.md) yöntemini çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="52db5-133">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="52db5-134">`Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="52db5-134">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52db5-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52db5-135">Requirements</span></span>  

 <span data-ttu-id="52db5-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52db5-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52db5-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52db5-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52db5-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="52db5-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52db5-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52db5-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52db5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52db5-140">See also</span></span>

- [<span data-ttu-id="52db5-141">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="52db5-141">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="52db5-142">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="52db5-142">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="52db5-143">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52db5-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="52db5-144">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52db5-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="52db5-145">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52db5-145">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="52db5-146">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="52db5-146">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
