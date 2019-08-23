---
title: Devam Eden Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d9d77ef20090e007e22a0d2f90b29f32ff94b46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911110"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="b7b76-102">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="b7b76-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="b7b76-103">.NET Framework 4 ' te başlayarak, tek bir işlemde ortak dil çalışma zamanının (CLR) birden çok sürümünü çalıştırmak için işlem içi yan yana barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="b7b76-104">Varsayılan olarak, yönetilen COM bileşenleri, işlem için yüklenen .NET Framework sürümden bağımsız olarak, ile derlendikleri .NET Framework sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="b7b76-105">Arka Plan</span><span class="sxs-lookup"><span data-stu-id="b7b76-105">Background</span></span>  
 <span data-ttu-id="b7b76-106">.NET Framework, yönetilen kod uygulamaları için her zaman yan yana barındırma sağlamıştır, ancak .NET Framework 4 ' den önce, yönetilen COM bileşenleri için bu işlevselliği sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="b7b76-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="b7b76-107">Geçmişte, bir işleme yüklenmiş olan yönetilen COM bileşenleri, zaten yüklü olan çalışma zamanının sürümüyle veya .NET Framework en son yüklü sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="b7b76-108">Bu sürüm COM bileşeniyle uyumlu değilse, bileşen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b7b76-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="b7b76-109">.NET Framework 4, aşağıdakileri sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:</span><span class="sxs-lookup"><span data-stu-id="b7b76-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="b7b76-110">.NET Framework yeni bir sürümünün yüklenmesi, mevcut uygulamalar üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="b7b76-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="b7b76-111">Uygulamalar, ile derlendikleri .NET Framework sürümüne karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="b7b76-112">Açıkça yönlendirilmediği takdirde .NET Framework yeni sürümünü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="b7b76-113">Ancak, uygulamaların .NET Framework yeni bir sürümünü kullanarak geçiş yapması kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="b7b76-114">Kullanıcılar ve geliştiriciler üzerindeki etkiler</span><span class="sxs-lookup"><span data-stu-id="b7b76-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="b7b76-115">**Son kullanıcılar ve sistem yöneticileri**.</span><span class="sxs-lookup"><span data-stu-id="b7b76-115">**End users and system administrators**.</span></span> <span data-ttu-id="b7b76-116">Bu kullanıcılar artık bağımsız çalışma zamanının yeni bir sürümünü (bağımsız olarak ya da bir uygulamayla) yüklediklerinde, bilgisayarlarının üzerinde hiçbir etkisi olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="b7b76-117">Mevcut uygulamalar, daha önce olduğu gibi çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="b7b76-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="b7b76-118">**Uygulama geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="b7b76-118">**Application developers**.</span></span> <span data-ttu-id="b7b76-119">Yan yana barındırma, uygulama geliştiricileri üzerinde neredeyse hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="b7b76-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="b7b76-120">Uygulamalar, varsayılan olarak her zaman üzerinde derlendikleri .NET Framework sürümüne karşı çalışır; Bu değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="b7b76-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="b7b76-121">Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamayı .NET Framework daha yeni bir sürümü altında çalışacak şekilde yönlendirebilir (bkz. [Senaryo 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="b7b76-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="b7b76-122">**Kitaplık geliştiricileri ve tüketicileri**.</span><span class="sxs-lookup"><span data-stu-id="b7b76-122">**Library developers and consumers**.</span></span> <span data-ttu-id="b7b76-123">Yan yana barındırma, kitaplık geliştiricilerinin karşılaştığı uyumluluk sorunlarını çözmez.</span><span class="sxs-lookup"><span data-stu-id="b7b76-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="b7b76-124">Doğrudan başvuru aracılığıyla veya bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrı aracılığıyla bir uygulama tarafından doğrudan yüklenen bir kitaplık, ' <xref:System.AppDomain> ın ' a yüklendiği çalışma zamanını kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="b7b76-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="b7b76-125">Kitaplıklarınızı, desteklemek istediğiniz tüm .NET Framework sürümlerine karşı test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="b7b76-126">Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenirse ancak önceki bir çalışma zamanı kullanılarak oluşturulmuş bir kitaplığı içeriyorsa, bu kitaplık .NET Framework 4 çalışma zamanını da kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="b7b76-127">Ancak, önceki bir çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa, uygulamanızı .NET Framework 4 ' ü (bkz. [Senaryo 3](#scenarios)) de kullanacak şekilde zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7b76-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="b7b76-128">**YÖNETILEN com bileşeni geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="b7b76-128">**Managed COM component developers**.</span></span> <span data-ttu-id="b7b76-129">Geçmişte, yönetilen COM bileşenleri, bilgisayarda yüklü olan çalışma zamanının en son sürümü kullanılarak otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="b7b76-130">Artık, yerleşik oldukları çalışma zamanının sürümüne göre COM bileşenlerini yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="b7b76-131">Aşağıdaki tabloda gösterildiği gibi, 1,1 sürümü .NET Framework ile oluşturulmuş bileşenler sürüm 4 bileşenleriyle yan yana çalışabilir, ancak yan yana barındırma bu kişiler için kullanılabilir olmadığından, sürüm 2,0, 3,0 veya 3,5 bileşenleriyle birlikte çalıştırılamaz. ün.</span><span class="sxs-lookup"><span data-stu-id="b7b76-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="b7b76-132">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="b7b76-132">.NET Framework version</span></span>|<span data-ttu-id="b7b76-133">1.1</span><span class="sxs-lookup"><span data-stu-id="b7b76-133">1.1</span></span>|<span data-ttu-id="b7b76-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="b7b76-134">2.0 - 3.5</span></span>|<span data-ttu-id="b7b76-135">4</span><span class="sxs-lookup"><span data-stu-id="b7b76-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="b7b76-136">1.1</span><span class="sxs-lookup"><span data-stu-id="b7b76-136">1.1</span></span>|<span data-ttu-id="b7b76-137">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="b7b76-137">Not applicable</span></span>|<span data-ttu-id="b7b76-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="b7b76-138">No</span></span>|<span data-ttu-id="b7b76-139">Evet</span><span class="sxs-lookup"><span data-stu-id="b7b76-139">Yes</span></span>|  
    |<span data-ttu-id="b7b76-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="b7b76-140">2.0 - 3.5</span></span>|<span data-ttu-id="b7b76-141">Hayır</span><span class="sxs-lookup"><span data-stu-id="b7b76-141">No</span></span>|<span data-ttu-id="b7b76-142">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="b7b76-142">Not applicable</span></span>|<span data-ttu-id="b7b76-143">Evet</span><span class="sxs-lookup"><span data-stu-id="b7b76-143">Yes</span></span>|  
    |<span data-ttu-id="b7b76-144">4</span><span class="sxs-lookup"><span data-stu-id="b7b76-144">4</span></span>|<span data-ttu-id="b7b76-145">Evet</span><span class="sxs-lookup"><span data-stu-id="b7b76-145">Yes</span></span>|<span data-ttu-id="b7b76-146">Evet</span><span class="sxs-lookup"><span data-stu-id="b7b76-146">Yes</span></span>|<span data-ttu-id="b7b76-147">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="b7b76-147">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b7b76-148">3,0 ve 3,5 .NET Framework sürümleri artımlı olarak sürüm 2,0 ' de oluşturulmuştur ve yan yana çalıştırılmasına gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="b7b76-149">Bunlar, doğal olarak aynı sürümdür.</span><span class="sxs-lookup"><span data-stu-id="b7b76-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="b7b76-150">Ortak yan yana barındırma senaryoları</span><span class="sxs-lookup"><span data-stu-id="b7b76-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="b7b76-151">**Senaryo 1:** .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="b7b76-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="b7b76-152">.NET Framework yüklenen sürümler: .NET Framework 4 ve COM bileşenleri tarafından kullanılan .NET Framework diğer tüm sürümleri.</span><span class="sxs-lookup"><span data-stu-id="b7b76-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="b7b76-153">Yapmanız gerekenler: Bu senaryoda hiçbir şey yapmayın.</span><span class="sxs-lookup"><span data-stu-id="b7b76-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="b7b76-154">COM bileşenleri, kayıtlı oldukları .NET Framework sürümüyle çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7b76-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="b7b76-155">**Senaryo 2**: .NET Framework 2,0 ile çalıştırmayı tercih ettiğiniz, ancak sürüm 2,0 mevcut değilse .NET Framework 4 ' te çalışmak üzere .NET Framework 2,0 SP1 ile oluşturulmuş yönetilen uygulama.</span><span class="sxs-lookup"><span data-stu-id="b7b76-155">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="b7b76-156">.NET Framework yüklenen sürümler: .NET Framework önceki bir sürümü ve .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b7b76-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="b7b76-157">Yapmanız gerekenler: Uygulama dizinindeki [uygulama yapılandırma dosyasında](../../../docs/framework/configure-apps/index.md) , [ \<](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) [ \<Başlangıç > öğesini ve supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) kümesini aşağıdaki şekilde kullanın:</span><span class="sxs-lookup"><span data-stu-id="b7b76-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="b7b76-158">**Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="b7b76-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="b7b76-159">.NET Framework yüklenen sürümler: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b7b76-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="b7b76-160">Yapmanız gerekenler: Uygulama dizinindeki `<startup>` uygulama yapılandırma dosyasında, `useLegacyV2RuntimeActivationPolicy` `true` özniteliği olarak ayarlanmış ve öğekümesiaşağıdakişekildeolanöğesinikullanın:`<supportedRuntime>`</span><span class="sxs-lookup"><span data-stu-id="b7b76-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="b7b76-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7b76-161">Example</span></span>  
 <span data-ttu-id="b7b76-162">Aşağıdaki örnek, yönetilen bir COM bileşeni çalıştıran yönetilmeyen bir COM konağını bileşenin kullanmak üzere derlenen .NET Framework sürümünü kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7b76-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="b7b76-163">Aşağıdaki örneği çalıştırmak için .NET Framework 3,5 kullanarak aşağıdaki yönetilen COM bileşenini derleyin ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b7b76-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="b7b76-164">Bileşeni kaydetmek için, **Proje** menüsünde **Özellikler**' e tıklayın, **derleme** sekmesine tıklayın ve ardından **com birlikte çalışması için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b7b76-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="b7b76-165">Önceki örnek tarafından oluşturulan C++ com nesnesini etkinleştiren aşağıdaki yönetilmeyen uygulamayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="b7b76-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7b76-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7b76-166">See also</span></span>

- [<span data-ttu-id="b7b76-167">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="b7b76-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="b7b76-168">\<supportedRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="b7b76-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
