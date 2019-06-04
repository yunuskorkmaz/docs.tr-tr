---
title: Devam Eden Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86d735bf84cdb33736701410d365ec90e6177e0e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489771"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="8a800-102">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="8a800-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="8a800-103">.NET Framework 4 ile başlayarak işlem içi yan tek bir işlemde birden çok ortak dil çalışma zamanı (CLR) sürümünü çalıştırmak için barındırma yana kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a800-103">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="8a800-104">Varsayılan olarak, COM bileşenlerini .NET Framework sürümüyle birlikte, işlem için yüklenen .NET Framework sürümünden bağımsız olarak oluşturuldukları çalıştırın yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="8a800-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="8a800-105">Arka Plan</span><span class="sxs-lookup"><span data-stu-id="8a800-105">Background</span></span>  
 <span data-ttu-id="8a800-106">.NET Framework için yan yana barındırma yönetilen kod uygulamalarının, ancak önce .NET Framework 4, bu işlevselliği için Yönetilen COM bileşenlerini sağlamadı sağlanan her zaman vardır.</span><span class="sxs-lookup"><span data-stu-id="8a800-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="8a800-107">Geçmişte, zaten yüklü çalışma zamanı sürümü veya .NET Framework'ün en son yüklenen sürüm işlem içine yüklenmiş yönetilen COM bileşenlerini çalıştı.</span><span class="sxs-lookup"><span data-stu-id="8a800-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="8a800-108">Bu sürüm COM bileşeni ile uyumlu değilse, bileşenin başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8a800-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="8a800-109">.NET Framework 4, aşağıdaki sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:</span><span class="sxs-lookup"><span data-stu-id="8a800-109">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="8a800-110">.NET Framework'ün yeni bir sürümünü yükleme mevcut uygulamalar üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8a800-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="8a800-111">Uygulamaları birlikte oluşturuldukları .NET Framework sürümüne karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="8a800-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="8a800-112">Bunlar .NET Framework'ün yeni sürüm açıkça yönlendirilmezseniz Bunu yapmak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8a800-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="8a800-113">Ancak, geçiş için .NET Framework'ün yeni bir sürümünü kullanan uygulamalar için daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="8a800-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="8a800-114">Kullanıcılara ve geliştiricilere etkileri</span><span class="sxs-lookup"><span data-stu-id="8a800-114">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="8a800-115">**Son kullanıcılar ve yöneticilerin**.</span><span class="sxs-lookup"><span data-stu-id="8a800-115">**End users and system administrators**.</span></span> <span data-ttu-id="8a800-116">Bu kullanıcılar artık bunlar bağımsız olarak veya bir uygulama ile yeni bir çalışma zamanı sürümünü yüklediğinizde, kendi bilgisayarlarına herhangi bir etkisi olacağı daha güvenli olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a800-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="8a800-117">Mevcut uygulamaları önce olduğu gibi çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8a800-117">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="8a800-118">**Uygulama geliştiricileri**.</span><span class="sxs-lookup"><span data-stu-id="8a800-118">**Application developers**.</span></span> <span data-ttu-id="8a800-119">Yan yana barındırma, uygulama geliştiricilerin neredeyse hiçbir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="8a800-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="8a800-120">Varsayılan olarak, uygulamalar her zaman üzerinde oluşturulmuş .NET Framework sürümünü çalıştırın; Bu değişiklik olmadı.</span><span class="sxs-lookup"><span data-stu-id="8a800-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="8a800-121">Ancak, geliştiricilerin bu davranışı geçersiz kılabilir ve uygulamanın daha yeni bir sürümü .NET Framework'ün altında çalışması için doğrudan (bkz [Senaryo 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="8a800-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="8a800-122">**Kitaplığı geliştiriciler ve tüketiciler**.</span><span class="sxs-lookup"><span data-stu-id="8a800-122">**Library developers and consumers**.</span></span> <span data-ttu-id="8a800-123">Yan yana barındırma uyumluluk sorunları bu kitaplığı geliştiriciler yüz çözmez.</span><span class="sxs-lookup"><span data-stu-id="8a800-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="8a800-124">Doğrudan bir uygulama--veya aracılığıyla bir doğrudan başvuru tarafından yüklenen bir kitaplığı bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrı--çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> içine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8a800-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="8a800-125">Desteklemek istediğiniz .NET Framework'ün tüm sürümler karşı Kitaplıklarınızı test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a800-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="8a800-126">Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenmiş olduğuna, ancak bir önceki çalışma zamanı kullanılarak oluşturulmuş bir kitaplık içerir, bu kitaplık de .NET Framework 4 çalışma zamanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a800-126">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="8a800-127">Ancak, bir önceki çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa, ayrıca .NET Framework 4 kullanmak için uygulamanızı zorlamanız gerekir (bkz [Senaryo 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="8a800-127">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="8a800-128">**COM Bileşen geliştiriciler yönetilen**.</span><span class="sxs-lookup"><span data-stu-id="8a800-128">**Managed COM component developers**.</span></span> <span data-ttu-id="8a800-129">Geçmişte, bilgisayarda yüklü olan çalışma zamanı en son sürümünü kullanarak yönetilen COM bileşenlerini otomatik olarak çalıştı.</span><span class="sxs-lookup"><span data-stu-id="8a800-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="8a800-130">Şimdi, COM bileşenleriyle birlikte oluşturuldukları çalışma zamanı sürümüne karşı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a800-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="8a800-131">Aşağıdaki tabloda gösterildiği gibi .NET Framework sürüm 1.1 ile oluşturulan bileşenler ile yan yana sürüm 4 bileşenlerini çalıştırabilirsiniz, ancak yan yana barındırma için kullanılabilir değil çünkü bunlar ile sürüm 2.0, 3.0 veya 3.5 bileşenleri çalışamaz sürümleri.</span><span class="sxs-lookup"><span data-stu-id="8a800-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="8a800-132">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="8a800-132">.NET Framework version</span></span>|<span data-ttu-id="8a800-133">1.1</span><span class="sxs-lookup"><span data-stu-id="8a800-133">1.1</span></span>|<span data-ttu-id="8a800-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="8a800-134">2.0 - 3.5</span></span>|<span data-ttu-id="8a800-135">4</span><span class="sxs-lookup"><span data-stu-id="8a800-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="8a800-136">1.1</span><span class="sxs-lookup"><span data-stu-id="8a800-136">1.1</span></span>|<span data-ttu-id="8a800-137">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="8a800-137">Not applicable</span></span>|<span data-ttu-id="8a800-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="8a800-138">No</span></span>|<span data-ttu-id="8a800-139">Evet</span><span class="sxs-lookup"><span data-stu-id="8a800-139">Yes</span></span>|  
    |<span data-ttu-id="8a800-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="8a800-140">2.0 - 3.5</span></span>|<span data-ttu-id="8a800-141">Hayır</span><span class="sxs-lookup"><span data-stu-id="8a800-141">No</span></span>|<span data-ttu-id="8a800-142">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="8a800-142">Not applicable</span></span>|<span data-ttu-id="8a800-143">Evet</span><span class="sxs-lookup"><span data-stu-id="8a800-143">Yes</span></span>|  
    |<span data-ttu-id="8a800-144">4</span><span class="sxs-lookup"><span data-stu-id="8a800-144">4</span></span>|<span data-ttu-id="8a800-145">Evet</span><span class="sxs-lookup"><span data-stu-id="8a800-145">Yes</span></span>|<span data-ttu-id="8a800-146">Evet</span><span class="sxs-lookup"><span data-stu-id="8a800-146">Yes</span></span>|<span data-ttu-id="8a800-147">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="8a800-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8a800-148">.NET framework sürüm 3.0 ve 3.5, sürüm 2.0 üzerinde artımlı olarak oluşturulur ve yan yana çalıştırma gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8a800-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="8a800-149">Bunlar aynı sürümü temelde aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8a800-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="8a800-150">Yan yana barındırma senaryoları</span><span class="sxs-lookup"><span data-stu-id="8a800-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="8a800-151">**Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="8a800-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="8a800-152">Yüklü .NET framework sürümleri: .NET Framework 4 ve diğer tüm COM bileşenleri tarafından kullanılan .NET Framework sürümleri.</span><span class="sxs-lookup"><span data-stu-id="8a800-152">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="8a800-153">Yapmanız gerekenler: Bu senaryoda, hiçbir şey yapmayın.</span><span class="sxs-lookup"><span data-stu-id="8a800-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="8a800-154">COM bileşenleri kayıtlı olan .NET Framework sürümü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="8a800-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="8a800-155">**Senaryo 2**: Yönetilen uygulama ile oluşturulmuş [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] çalıştırmak tercih [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ancak sürüm 2.0 mevcut değilse .NET Framework 4'te çalıştırmak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="8a800-155">**Scenario 2**: Managed application built with the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="8a800-156">Yüklü .NET framework sürümleri: Önceki bir sürümünü .NET Framework ve .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8a800-156">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8a800-157">Yapmanız gerekenler: İçinde [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) uygulama dizininizde [ \<başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8a800-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="8a800-158">**Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="8a800-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8a800-159">Yüklü .NET framework sürümleri: .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8a800-159">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8a800-160">Yapmanız gerekenler: Uygulama yapılandırma dosyasında uygulama dizinindeki kullanın `<startup>` öğeyle `useLegacyV2RuntimeActivationPolicy` özniteliğini `true` ve `<supportedRuntime>` öğesi aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8a800-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="8a800-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a800-161">Example</span></span>  
 <span data-ttu-id="8a800-162">Aşağıdaki örnek, yönetilen bir COM bileşeni bileşen için derlenmiş .NET Framework sürümünü kullanarak çalışan bir yönetilmeyen COM konak gösterir kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a800-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="8a800-163">Aşağıdaki örnek çalıştırmak için derleme ve .NET Framework 3.5 kullanarak aşağıdaki yönetilen COM bileşeni kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8a800-163">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="8a800-164">Bileşeni üzerinde kaydetmek için **proje** menüsünde tıklayın **özellikleri**, tıklayın **derleme** sekmesine tıklayın ve ardından **COMbirlikteçalışmasıiçinkaydol**onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="8a800-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
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
  
 <span data-ttu-id="8a800-165">Önceki örneği tarafından oluşturulan COM nesnesi etkinleştirir aşağıdaki yönetilmeyen C++ uygulama derleyin.</span><span class="sxs-lookup"><span data-stu-id="8a800-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a800-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a800-166">See also</span></span>

- [<span data-ttu-id="8a800-167">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="8a800-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="8a800-168">\<supportedRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="8a800-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
