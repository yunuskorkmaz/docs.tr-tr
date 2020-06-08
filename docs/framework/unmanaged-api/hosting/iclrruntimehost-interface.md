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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504088"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="ce911-102">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce911-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="ce911-103">.NET Framework sürüm 1 ' de sağlanan [ICorRuntimeHost](icorruntimehost-interface.md) arabirimi aşağıdaki değişikliklerle benzer işlevler sağlar:</span><span class="sxs-lookup"><span data-stu-id="ce911-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="ce911-104">Ana bilgisayar denetim arabirimini ayarlamak için [SetHostControl](iclrruntimehost-sethostcontrol-method.md) yönteminin eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="ce911-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="ce911-105">Tarafından sunulan bazı yöntemlerin atlanarak `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="ce911-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce911-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ce911-106">Methods</span></span>  
  
|<span data-ttu-id="ce911-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ce911-107">Method</span></span>|<span data-ttu-id="ce911-108">Description</span><span class="sxs-lookup"><span data-stu-id="ce911-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce911-109">ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="ce911-110">Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce911-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="ce911-111">ExecuteInAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="ce911-112"><xref:System.AppDomain>Belirtilen yönetilen kodun çalıştırılacağı öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce911-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="ce911-113">ExecuteInDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="ce911-114">Belirtilen derlemede belirtilen türde belirtilen metodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="ce911-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="ce911-115">GetCLRControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="ce911-116">Ana bilgisayarlarının ortak dil çalışma zamanının (CLR) yönlerini özelleştirmek için kullanabileceği [ICLRControl](iclrcontrol-interface.md) türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ce911-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="ce911-117">GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="ce911-118"><xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ce911-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="ce911-119">SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="ce911-120">Konak denetim arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce911-120">Sets the host control interface.</span></span> <span data-ttu-id="ce911-121">`SetHostControl`Çağrılmadan önce öğesini çağırmanız gerekir `Start` .</span><span class="sxs-lookup"><span data-stu-id="ce911-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="ce911-122">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="ce911-123">CLR 'yi bir işlem olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="ce911-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="ce911-124">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="ce911-125">Çalışma zamanı tarafından kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="ce911-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="ce911-126">UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce911-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="ce911-127"><xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ce911-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce911-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce911-128">Remarks</span></span>  
 <span data-ttu-id="ce911-129">.NET Framework 4 ' te başlayarak [ICLRMetaHost](iclrmetahost-interface.md) arabirimini kullanarak [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimine bir işaretçi alın ve sonra bir Işaretçi almak Için [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) metodunu çağırın `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="ce911-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="ce911-130">.NET Framework önceki sürümlerinde, konak `ICLRRuntimeHost` [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)çağırarak bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ce911-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="ce911-131">.NET Framework sürüm 2,0 ' de sunulan teknolojilerin herhangi birine yönelik uygulamalar sağlamak için yerine kullanmanız gerekir `ICLRRuntimeHost` `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="ce911-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce911-132">Bildirim tabanlı bir uygulamayı etkinleştirmek için [ExecuteApplication](iclrruntimehost-executeapplication-method.md) metodunu çağırmadan önce [Start](iclrruntimehost-start-method.md) yöntemini çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="ce911-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="ce911-133">`Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ce911-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce911-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce911-134">Requirements</span></span>  
 <span data-ttu-id="ce911-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce911-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce911-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce911-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce911-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ce911-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce911-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce911-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce911-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce911-139">See also</span></span>

- [<span data-ttu-id="ce911-140">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="ce911-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="ce911-141">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="ce911-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="ce911-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce911-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ce911-143">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce911-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="ce911-144">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ce911-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ce911-145">CLRRuntimeHost Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="ce911-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
