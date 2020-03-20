---
title: Devam Eden Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 5ca2f03576946a23b3133bbe7532d46c4ad758ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181656"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="67609-102">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="67609-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="67609-103">.NET Framework 4'ten başlayarak, ortak dil çalışma zamanının (CLR) birden çok sürümüne tek bir işlemde çalıştırmak için süreç içi yan yana barındırma yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67609-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="67609-104">Varsayılan olarak, yönetilen COM bileşenleri, işlem için yüklenen .NET Framework sürümünden bağımsız olarak, birlikte üretildikleri .NET Framework sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="67609-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="67609-105">Arka plan</span><span class="sxs-lookup"><span data-stu-id="67609-105">Background</span></span>  
 <span data-ttu-id="67609-106">.NET Framework her zaman yönetilen kod uygulamaları için yan yana barındırma sağlamıştır, ancak .NET Framework 4'ten önce yönetilen COM bileşenleri için bu işlevselliği sağlamamıştır.</span><span class="sxs-lookup"><span data-stu-id="67609-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="67609-107">Geçmişte, bir işleme yüklenen yönetilen COM bileşenleri, zaten yüklenmiş olan çalışma zamanının sürümüyle veya .NET Framework'ün en son yüklü sürümüyle çalıştırılırdı.</span><span class="sxs-lookup"><span data-stu-id="67609-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="67609-108">Bu sürüm COM bileşeni ile uyumlu değilse, bileşen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="67609-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="67609-109">.NET Framework 4, yan yana barındırma için yeni bir yaklaşım sağlar ve aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="67609-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="67609-110">.NET Framework'ün yeni bir sürümünün yüklenmesinin varolan uygulamalar üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="67609-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="67609-111">Uygulamalar, .NET Framework'ün birlikte inşa edildikleri sürümüne karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="67609-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="67609-112">Açıkça yönlendirilmedikçe .NET Framework'ün yeni sürümünü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="67609-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="67609-113">Ancak, uygulamaların .NET Framework'ün yeni bir sürümünü kullanması daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="67609-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="67609-114">Kullanıcılar ve Geliştiriciler Üzerindeki Etkileri</span><span class="sxs-lookup"><span data-stu-id="67609-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="67609-115">**Son kullanıcılar ve sistem yöneticileri.**</span><span class="sxs-lookup"><span data-stu-id="67609-115">**End users and system administrators**.</span></span> <span data-ttu-id="67609-116">Bu kullanıcılar artık çalışma zamanının yeni bir sürümünü bağımsız olarak veya bir uygulamayla yüklediklerinde, bunun bilgisayarları üzerinde hiçbir etkisi olmayacağından daha fazla güvenebilirler.</span><span class="sxs-lookup"><span data-stu-id="67609-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="67609-117">Varolan uygulamalar daha önce olduğu gibi çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="67609-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="67609-118">**Uygulama geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="67609-118">**Application developers**.</span></span> <span data-ttu-id="67609-119">Yan yana barındırma uygulama geliştiricileri üzerinde hemen hemen hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="67609-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="67609-120">Varsayılan olarak, uygulamalar her zaman üzerine inşa edildi .NET Framework sürümüne karşı çalışır; bu değişmedi.</span><span class="sxs-lookup"><span data-stu-id="67609-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="67609-121">Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamayı .NET Framework'ün daha yeni bir sürümü altında çalıştırmaya yönlendirebilir [(bkz. senaryo 2).](#scenarios)</span><span class="sxs-lookup"><span data-stu-id="67609-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="67609-122">**Kütüphane geliştiricileri ve tüketiciler.**</span><span class="sxs-lookup"><span data-stu-id="67609-122">**Library developers and consumers**.</span></span> <span data-ttu-id="67609-123">Yan yana barındırma, kitaplık geliştiricilerinkarşılaştığı uyumluluk sorunlarını çözmez.</span><span class="sxs-lookup"><span data-stu-id="67609-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="67609-124">Doğrudan bir uygulama tarafından doğrudan yüklenen bir kitaplık - <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> doğrudan bir başvuru yoluyla veya <xref:System.AppDomain> bir çağrı yoluyla - yüklendiği zaman ları kullanmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="67609-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="67609-125">Kitaplıklarınızı desteklemek istediğiniz .NET Framework'ün tüm sürümlerine göre test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67609-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="67609-126">Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenmişse, ancak daha önceki bir çalışma zamanı kullanılarak oluşturulmuş bir kitaplık içeriyorsa, bu kitaplık .NET Framework 4 çalışma zamanını da kullanır.</span><span class="sxs-lookup"><span data-stu-id="67609-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="67609-127">Ancak, daha önceki bir çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplığını kullanarak oluşturulmuş bir uygulamanız varsa, uygulamanızı .NET Framework 4'ü de kullanmaya zorlamalısınız (bkz. [senaryo 3).](#scenarios)</span><span class="sxs-lookup"><span data-stu-id="67609-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="67609-128">**Yönetilen COM bileşen geliştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="67609-128">**Managed COM component developers**.</span></span> <span data-ttu-id="67609-129">Geçmişte, yönetilen COM bileşenleri bilgisayarda yüklü çalışma zamanının en son sürümünü kullanarak otomatik olarak çalışırdı.</span><span class="sxs-lookup"><span data-stu-id="67609-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="67609-130">Artık COM bileşenlerini, birlikte üretildikleri çalışma zamanının sürümüne karşı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67609-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="67609-131">Aşağıdaki tabloda gösterildiği gibi, .NET Framework sürüm 1.1 ile oluşturulmuş bileşenler sürüm 4 bileşenleriyle yan yana çalıştırılabilir, ancak sürüm 2.0, 3.0 veya 3.5 bileşenleriyle çalıştırılamazlar, çünkü yan yana barındırma bu bileşenler için kullanılamaz Sürüm.</span><span class="sxs-lookup"><span data-stu-id="67609-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="67609-132">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="67609-132">.NET Framework version</span></span>|<span data-ttu-id="67609-133">1.1</span><span class="sxs-lookup"><span data-stu-id="67609-133">1.1</span></span>|<span data-ttu-id="67609-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="67609-134">2.0 - 3.5</span></span>|<span data-ttu-id="67609-135">4</span><span class="sxs-lookup"><span data-stu-id="67609-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="67609-136">1.1</span><span class="sxs-lookup"><span data-stu-id="67609-136">1.1</span></span>|<span data-ttu-id="67609-137">Uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="67609-137">Not applicable</span></span>|<span data-ttu-id="67609-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="67609-138">No</span></span>|<span data-ttu-id="67609-139">Evet</span><span class="sxs-lookup"><span data-stu-id="67609-139">Yes</span></span>|  
    |<span data-ttu-id="67609-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="67609-140">2.0 - 3.5</span></span>|<span data-ttu-id="67609-141">Hayır</span><span class="sxs-lookup"><span data-stu-id="67609-141">No</span></span>|<span data-ttu-id="67609-142">Uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="67609-142">Not applicable</span></span>|<span data-ttu-id="67609-143">Evet</span><span class="sxs-lookup"><span data-stu-id="67609-143">Yes</span></span>|  
    |<span data-ttu-id="67609-144">4</span><span class="sxs-lookup"><span data-stu-id="67609-144">4</span></span>|<span data-ttu-id="67609-145">Evet</span><span class="sxs-lookup"><span data-stu-id="67609-145">Yes</span></span>|<span data-ttu-id="67609-146">Evet</span><span class="sxs-lookup"><span data-stu-id="67609-146">Yes</span></span>|<span data-ttu-id="67609-147">Uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="67609-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="67609-148">.NET Framework sürümleri 3.0 ve 3.5 sürüm 2.0 üzerine kademeli olarak oluşturulur ve yan yana çalışması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="67609-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="67609-149">Bunlar doğal olarak aynı sürüm.</span><span class="sxs-lookup"><span data-stu-id="67609-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="67609-150">Ortak Yan Yana Barındırma Senaryoları</span><span class="sxs-lookup"><span data-stu-id="67609-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="67609-151">**Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="67609-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="67609-152">.NET Framework sürümleri yüklendi: .NET Framework 4 ve COM bileşenleri tarafından kullanılan .NET Framework'ün diğer tüm sürümleri.</span><span class="sxs-lookup"><span data-stu-id="67609-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="67609-153">Ne yapmalı: Bu senaryoda, hiçbir şey yapmayın.</span><span class="sxs-lookup"><span data-stu-id="67609-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="67609-154">COM bileşenleri, kayıtlı oldukları .NET Framework sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="67609-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="67609-155">**Senaryo 2**: .NET Framework 2.0 ile çalıştırmayı tercih ettiğiniz ,ancak sürüm 2.0 yoksa .NET Framework 4 üzerinde çalıştırmak istediğiniz .NET Framework 2.0 SP1 ile oluşturulmuş yönetilen uygulama.</span><span class="sxs-lookup"><span data-stu-id="67609-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="67609-156">.NET Framework sürümleri yüklü: .NET Framework ve .NET Framework 4'ün önceki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="67609-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67609-157">Ne yapmalı: Uygulama dizinindeki [uygulama yapılandırma dosyasında](../configure-apps/index.md) [ \<başlangıç> öğesini](../configure-apps/file-schema/startup/startup-element.md) ve [ \<desteklenen Runtime> öğesini](../configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="67609-157">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="67609-158">**Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="67609-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67609-159">.NET Framework sürümleri yüklendi: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67609-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="67609-160">Ne yapmalı: Uygulama dizinindeki uygulama yapılandırma dosyasında, `<startup>` öznitelik `useLegacyV2RuntimeActivationPolicy` ayarlı `true` öğeyi `<supportedRuntime>` ve öğeyi aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="67609-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="67609-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="67609-161">Example</span></span>  
 <span data-ttu-id="67609-162">Aşağıdaki örnek, bileşenin kullanmak üzere derlenen .NET Framework sürümünü kullanarak yönetilen bir COM bileşeni çalıştıran yönetilmeyen bir COM ana bilgisayarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67609-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="67609-163">Aşağıdaki örneği çalıştırmak için .NET Framework 3.5'i kullanarak aşağıdaki yönetilen COM bileşenini derleyip kaydedin.</span><span class="sxs-lookup"><span data-stu-id="67609-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="67609-164">Bileşeni kaydetmek için **Proje** menüsünde **Özellikler'i**, **Yapı** sekmesini tıklatın ve ardından COM interop onay kutusunu **kaydet'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="67609-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="67609-165">Önceki örnekte oluşturulan COM nesnesini etkinleştiren aşağıdaki yönetilmemiş C++ uygulamasını derle.</span><span class="sxs-lookup"><span data-stu-id="67609-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="67609-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67609-166">See also</span></span>

- [<span data-ttu-id="67609-167">\<başlangıç> Öğesi</span><span class="sxs-lookup"><span data-stu-id="67609-167">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="67609-168">\<desteklenenRuntime> Öğesi</span><span class="sxs-lookup"><span data-stu-id="67609-168">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
