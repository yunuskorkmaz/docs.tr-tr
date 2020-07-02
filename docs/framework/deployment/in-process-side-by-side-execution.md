---
title: Devam Eden Yan Yana Yürütme
description: Tek bir .NET işleminde ortak dil çalışma zamanının (CLR) birçok sürümünü yürütmek için işlem içi yan yana barındırma kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 078f2eaada8fac57138bef22d46218ef2ccda835
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622607"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="a5729-103">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="a5729-103">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="a5729-104">.NET Framework 4 ' te başlayarak, tek bir işlemde ortak dil çalışma zamanının (CLR) birden çok sürümünü çalıştırmak için işlem içi yan yana barındırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5729-104">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="a5729-105">Varsayılan olarak, yönetilen COM bileşenleri, işlem için yüklenen .NET Framework sürümden bağımsız olarak, ile derlendikleri .NET Framework sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5729-105">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="a5729-106">Arka Plan</span><span class="sxs-lookup"><span data-stu-id="a5729-106">Background</span></span>  
 <span data-ttu-id="a5729-107">.NET Framework, yönetilen kod uygulamaları için her zaman yan yana barındırma sağlamıştır, ancak .NET Framework 4 ' den önce, yönetilen COM bileşenleri için bu işlevselliği sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="a5729-107">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="a5729-108">Geçmişte, bir işleme yüklenmiş olan yönetilen COM bileşenleri, zaten yüklü olan çalışma zamanının sürümüyle veya .NET Framework en son yüklü sürümüyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5729-108">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="a5729-109">Bu sürüm COM bileşeniyle uyumlu değilse, bileşen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a5729-109">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="a5729-110">.NET Framework 4, aşağıdakileri sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:</span><span class="sxs-lookup"><span data-stu-id="a5729-110">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="a5729-111">.NET Framework yeni bir sürümünün yüklenmesi, mevcut uygulamalar üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a5729-111">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="a5729-112">Uygulamalar, ile derlendikleri .NET Framework sürümüne karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5729-112">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="a5729-113">Açıkça yönlendirilmediği takdirde .NET Framework yeni sürümünü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="a5729-113">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="a5729-114">Ancak, uygulamaların .NET Framework yeni bir sürümünü kullanarak geçiş yapması kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="a5729-114">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="a5729-115">Kullanıcılar ve geliştiriciler üzerindeki etkiler</span><span class="sxs-lookup"><span data-stu-id="a5729-115">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="a5729-116">**Son kullanıcılar ve sistem yöneticileri**.</span><span class="sxs-lookup"><span data-stu-id="a5729-116">**End users and system administrators**.</span></span> <span data-ttu-id="a5729-117">Bu kullanıcılar artık bağımsız çalışma zamanının yeni bir sürümünü (bağımsız olarak ya da bir uygulamayla) yüklediklerinde, bilgisayarlarının üzerinde hiçbir etkisi olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5729-117">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="a5729-118">Mevcut uygulamalar, daha önce olduğu gibi çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="a5729-118">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="a5729-119">**Uygulama geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="a5729-119">**Application developers**.</span></span> <span data-ttu-id="a5729-120">Yan yana barındırma, uygulama geliştiricileri üzerinde neredeyse hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a5729-120">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="a5729-121">Uygulamalar, varsayılan olarak her zaman üzerinde derlendikleri .NET Framework sürümüne karşı çalışır; Bu değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="a5729-121">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="a5729-122">Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamayı .NET Framework daha yeni bir sürümü altında çalışacak şekilde yönlendirebilir (bkz. [Senaryo 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="a5729-122">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="a5729-123">**Kitaplık geliştiricileri ve tüketicileri**.</span><span class="sxs-lookup"><span data-stu-id="a5729-123">**Library developers and consumers**.</span></span> <span data-ttu-id="a5729-124">Yan yana barındırma, kitaplık geliştiricilerinin karşılaştığı uyumluluk sorunlarını çözmez.</span><span class="sxs-lookup"><span data-stu-id="a5729-124">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="a5729-125">Doğrudan başvuru aracılığıyla veya bir çağrı aracılığıyla bir uygulama tarafından doğrudan yüklenen bir kitaplık, ' ın ' a <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yüklendiği çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a5729-125">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="a5729-126">Kitaplıklarınızı, desteklemek istediğiniz tüm .NET Framework sürümlerine karşı test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a5729-126">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="a5729-127">Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenirse ancak önceki bir çalışma zamanı kullanılarak oluşturulmuş bir kitaplığı içeriyorsa, bu kitaplık .NET Framework 4 çalışma zamanını da kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5729-127">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="a5729-128">Ancak, önceki bir çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa, uygulamanızı .NET Framework 4 ' ü (bkz. [Senaryo 3](#scenarios)) de kullanacak şekilde zorlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5729-128">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="a5729-129">**YÖNETILEN com bileşeni geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="a5729-129">**Managed COM component developers**.</span></span> <span data-ttu-id="a5729-130">Geçmişte, yönetilen COM bileşenleri, bilgisayarda yüklü olan çalışma zamanının en son sürümü kullanılarak otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5729-130">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="a5729-131">Artık, yerleşik oldukları çalışma zamanının sürümüne göre COM bileşenlerini yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5729-131">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="a5729-132">Aşağıdaki tabloda gösterildiği gibi, 1,1 sürümü .NET Framework ile oluşturulmuş bileşenler sürüm 4 bileşenleriyle yan yana çalıştırılabilir, ancak yan yana barındırma bu sürümler için kullanılabilir olmadığından, sürüm 2,0, 3,0 veya 3,5 bileşenleriyle birlikte çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="a5729-132">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="a5729-133">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="a5729-133">.NET Framework version</span></span>|<span data-ttu-id="a5729-134">1.1</span><span class="sxs-lookup"><span data-stu-id="a5729-134">1.1</span></span>|<span data-ttu-id="a5729-135">2,0-3,5</span><span class="sxs-lookup"><span data-stu-id="a5729-135">2.0 - 3.5</span></span>|<span data-ttu-id="a5729-136">4</span><span class="sxs-lookup"><span data-stu-id="a5729-136">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="a5729-137">1.1</span><span class="sxs-lookup"><span data-stu-id="a5729-137">1.1</span></span>|<span data-ttu-id="a5729-138">Uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="a5729-138">Not applicable</span></span>|<span data-ttu-id="a5729-139">No</span><span class="sxs-lookup"><span data-stu-id="a5729-139">No</span></span>|<span data-ttu-id="a5729-140">Yes</span><span class="sxs-lookup"><span data-stu-id="a5729-140">Yes</span></span>|  
    |<span data-ttu-id="a5729-141">2,0-3,5</span><span class="sxs-lookup"><span data-stu-id="a5729-141">2.0 - 3.5</span></span>|<span data-ttu-id="a5729-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="a5729-142">No</span></span>|<span data-ttu-id="a5729-143">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="a5729-143">Not applicable</span></span>|<span data-ttu-id="a5729-144">Evet</span><span class="sxs-lookup"><span data-stu-id="a5729-144">Yes</span></span>|  
    |<span data-ttu-id="a5729-145">4</span><span class="sxs-lookup"><span data-stu-id="a5729-145">4</span></span>|<span data-ttu-id="a5729-146">Yes</span><span class="sxs-lookup"><span data-stu-id="a5729-146">Yes</span></span>|<span data-ttu-id="a5729-147">Yes</span><span class="sxs-lookup"><span data-stu-id="a5729-147">Yes</span></span>|<span data-ttu-id="a5729-148">Uygulanamaz</span><span class="sxs-lookup"><span data-stu-id="a5729-148">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a5729-149">3,0 ve 3,5 .NET Framework sürümleri artımlı olarak sürüm 2,0 ' de oluşturulmuştur ve yan yana çalıştırılmasına gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="a5729-149">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="a5729-150">Bunlar, doğal olarak aynı sürümdür.</span><span class="sxs-lookup"><span data-stu-id="a5729-150">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="a5729-151">Ortak yan yana barındırma senaryoları</span><span class="sxs-lookup"><span data-stu-id="a5729-151">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="a5729-152">**Senaryo 1:** .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="a5729-152">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="a5729-153">.NET Framework yüklü sürümler: COM bileşenleri tarafından kullanılan .NET Framework .NET Framework 4 ve diğer tüm sürümleri.</span><span class="sxs-lookup"><span data-stu-id="a5729-153">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="a5729-154">Yapılacaklar: Bu senaryoda hiçbir şey yapmayın.</span><span class="sxs-lookup"><span data-stu-id="a5729-154">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="a5729-155">COM bileşenleri, kayıtlı oldukları .NET Framework sürümüyle çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5729-155">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="a5729-156">**Senaryo 2**: .NET Framework 2,0 SP1 ile oluşturulmuş, .NET Framework 2,0 ile çalıştırmayı tercih ettiğiniz, ancak sürüm 2,0 mevcut değilse .NET Framework 4 ' te çalıştırmayı tercih ettiğiniz yönetilen uygulama.</span><span class="sxs-lookup"><span data-stu-id="a5729-156">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="a5729-157">.NET Framework yüklü sürümler: .NET Framework ve .NET Framework 4 ' ün önceki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="a5729-157">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="a5729-158">Yapılacaklar: uygulama dizinindeki [uygulama yapılandırma dosyasında](../configure-apps/index.md) , [ \<startup> öğesini](../configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime> öğesini](../configure-apps/file-schema/startup/supportedruntime-element.md) şu şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="a5729-158">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="a5729-159">**Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="a5729-159">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="a5729-160">.NET Framework yüklü sürümler: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a5729-160">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="a5729-161">Yapılacaklar: uygulama dizinindeki uygulama yapılandırma dosyasında, `<startup>` `useLegacyV2RuntimeActivationPolicy` özniteliği olarak ayarlanmış `true` ve `<supportedRuntime>` öğe kümesi aşağıdaki şekilde olan öğesini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a5729-161">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="a5729-162">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5729-162">Example</span></span>  
 <span data-ttu-id="a5729-163">Aşağıdaki örnek, yönetilen bir COM bileşeni çalıştıran yönetilmeyen bir COM konağını bileşenin kullanmak üzere derlenen .NET Framework sürümünü kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5729-163">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="a5729-164">Aşağıdaki örneği çalıştırmak için .NET Framework 3,5 kullanarak aşağıdaki yönetilen COM bileşenini derleyin ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a5729-164">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="a5729-165">Bileşeni kaydetmek için, **Proje** menüsünde **Özellikler**' e tıklayın, **derleme** sekmesine tıklayın ve ardından **com birlikte çalışması için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="a5729-165">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="a5729-166">Aşağıdaki yönetilmeyen C++ uygulamasını derleyin ve bu, önceki örnek tarafından oluşturulan COM nesnesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a5729-166">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5729-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5729-167">See also</span></span>

- [<span data-ttu-id="a5729-168">\<startup>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="a5729-168">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="a5729-169">\<supportedRuntime>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="a5729-169">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
