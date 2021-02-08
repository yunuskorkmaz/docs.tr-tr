---
description: ': ICorRuntimeHost arabirimi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: cd50d31668b2dd0718dbe644343bfe314a0afdbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789664"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="433fe-103">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="433fe-103">ICorRuntimeHost Interface</span></span>

<span data-ttu-id="433fe-104">Ana bilgisayarın ortak dil çalışma zamanını (CLR) açık olarak başlatıp durdurmasına, uygulama etki alanlarını oluşturup yapılandırmasına, varsayılan etki alanına erişime ve işlemde çalışan tüm etki alanlarını listelemeye olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="433fe-104">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="433fe-105">.NET Framework sürüm 2,0 ' de, bu arabirimin yerini [ICLRRuntimeHost](iclrruntimehost-interface.md)almıştır.</span><span class="sxs-lookup"><span data-stu-id="433fe-105">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="433fe-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="433fe-106">Methods</span></span>  
  
|<span data-ttu-id="433fe-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="433fe-107">Method</span></span>|<span data-ttu-id="433fe-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="433fe-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="433fe-109">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-109">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="433fe-110">Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="433fe-110">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="433fe-111">CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-111">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="433fe-112">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="433fe-112">Creates an application domain.</span></span> <span data-ttu-id="433fe-113">Çağıran, türünde bir örneğine türünde bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="433fe-113">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="433fe-114">CreateDomainEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-114">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="433fe-115">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="433fe-115">Creates an application domain.</span></span> <span data-ttu-id="433fe-116">Bu yöntem, çağıranın döndürülen örneğin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="433fe-116">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="433fe-117">CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-117">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="433fe-118">Bir örneğe türün arabirim işaretçisini alır `IAppDomainSetup` <xref:System.AppDomainSetup> .</span><span class="sxs-lookup"><span data-stu-id="433fe-118">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="433fe-119">`IAppDomainSetup` , bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="433fe-119">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="433fe-120">CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-120">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="433fe-121"><xref:System.Security.Principal.IIdentity>Konağın, [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md)'e geçiş için güvenlik kanıtı oluşturmasına olanak tanıyan bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-121">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="433fe-122">CreateLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-122">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="433fe-123">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="433fe-123">Do not use.</span></span>|  
|[<span data-ttu-id="433fe-124">CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-124">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="433fe-125"><xref:System._AppDomain>Geçerli iş parçacığında yüklü olan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-125">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="433fe-126">DeleteLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-126">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="433fe-127">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="433fe-127">Do not use.</span></span>|  
|[<span data-ttu-id="433fe-128">EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-128">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="433fe-129">Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-129">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="433fe-130">GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-130">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="433fe-131">Konağın CLR 'nin geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-131">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="433fe-132">GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-132">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="433fe-133"><xref:System._AppDomain>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-133">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="433fe-134">LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-134">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="433fe-135">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="433fe-135">Do not use.</span></span>|  
|[<span data-ttu-id="433fe-136">MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-136">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="433fe-137">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="433fe-137">Maps the specified file into memory.</span></span> <span data-ttu-id="433fe-138">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="433fe-138">This method is obsolete.</span></span>|  
|[<span data-ttu-id="433fe-139">NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-139">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="433fe-140">Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="433fe-140">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="433fe-141">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-141">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="433fe-142">CLR 'yi başlatır.</span><span class="sxs-lookup"><span data-stu-id="433fe-142">Starts the CLR.</span></span>|  
|[<span data-ttu-id="433fe-143">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-143">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="433fe-144">Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="433fe-144">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="433fe-145">SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-145">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="433fe-146">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="433fe-146">Do not use.</span></span>|  
|[<span data-ttu-id="433fe-147">SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-147">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="433fe-148">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="433fe-148">Do not use.</span></span>|  
|[<span data-ttu-id="433fe-149">UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="433fe-149">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="433fe-150">Belirtilen uygulama etki alanını geçerli işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="433fe-150">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="433fe-151">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="433fe-151">Requirements</span></span>  

 <span data-ttu-id="433fe-152">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="433fe-152">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="433fe-153">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="433fe-153">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="433fe-154">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="433fe-154">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="433fe-155">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="433fe-155">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433fe-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="433fe-156">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="433fe-157">Hosting</span><span class="sxs-lookup"><span data-stu-id="433fe-157">Hosting</span></span>](index.md)
- [<span data-ttu-id="433fe-158">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="433fe-158">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="433fe-159">[Çalışma zamanı Konakları](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="433fe-159">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="433fe-160">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="433fe-160">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="433fe-161">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="433fe-161">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
