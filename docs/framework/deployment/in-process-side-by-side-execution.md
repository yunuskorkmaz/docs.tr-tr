---
title: "Devam Eden Yan Yana Yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa65be2eee481e20231bacb5d0861fa3d2c03f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="243e9-102">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="243e9-102">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="243e9-103">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], işlem içi-tek bir işlemde birden fazla sürümünü ortak dil çalışma zamanı (CLR) çalıştırmak için barındırma yana kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="243e9-103">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="243e9-104">Varsayılan olarak, COM bileşenlerini işlemi için yüklenen .NET Framework sürüm ne olursa olsun bunlar, oluşturulan .NET Framework sürümünü çalıştıran yönetilen.</span><span class="sxs-lookup"><span data-stu-id="243e9-104">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="243e9-105">Arka Plan</span><span class="sxs-lookup"><span data-stu-id="243e9-105">Background</span></span>  
 <span data-ttu-id="243e9-106">Yan yana yönetilen barındırma kodu sağlanan uygulamalar, ancak önce .NET Framework her zaman sahip [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], yönetilen COM bileşenleri bu işlevselliği sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="243e9-106">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="243e9-107">Geçmişte, işlem içine yüklenmiş yönetilen COM bileşenleri zaten yüklendi çalışma zamanı sürümü veya .NET Framework'ün yüklü en son sürümü verdi.</span><span class="sxs-lookup"><span data-stu-id="243e9-107">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="243e9-108">Bu sürüm COM bileşeni ile uyumlu değilse, bileşen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="243e9-108">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="243e9-109">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Aşağıdaki sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:</span><span class="sxs-lookup"><span data-stu-id="243e9-109">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
-   <span data-ttu-id="243e9-110">.NET Framework'ün yeni bir sürümünü yükleme var olan uygulamalar üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="243e9-110">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
-   <span data-ttu-id="243e9-111">Uygulamaları ile oluşturulan .NET Framework sürümünü karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="243e9-111">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="243e9-112">Bunlar, .NET Framework yeni sürümünü açıkça yönlendirilmiş sürece bunu yapmak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="243e9-112">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="243e9-113">Ancak, .NET Framework'ün yeni bir sürümü kullanılarak uygulamaların geçiş kolaydır.</span><span class="sxs-lookup"><span data-stu-id="243e9-113">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="243e9-114">Kullanıcıların ve geliştiricilerin etkileri</span><span class="sxs-lookup"><span data-stu-id="243e9-114">Effects on Users and Developers</span></span>  
  
-   <span data-ttu-id="243e9-115">**Son kullanıcılar ve sistem yöneticileri**.</span><span class="sxs-lookup"><span data-stu-id="243e9-115">**End users and system administrators**.</span></span> <span data-ttu-id="243e9-116">Bu kullanıcılar artık yeni bir çalışma zamanı sürümü bağımsız olarak veya bir uygulamayla yükledikleri zaman, bilgisayarlarında etkisi gerekir güvenle olabilir.</span><span class="sxs-lookup"><span data-stu-id="243e9-116">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="243e9-117">Var olan uygulamalar, önceden olduğu gibi çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="243e9-117">Existing applications will continue to run as they did before.</span></span>  
  
-   <span data-ttu-id="243e9-118">**Uygulama geliştiricilerinin**.</span><span class="sxs-lookup"><span data-stu-id="243e9-118">**Application developers**.</span></span> <span data-ttu-id="243e9-119">Yan yana barındırma uygulama geliştiricileri üzerinde neredeyse hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="243e9-119">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="243e9-120">Varsayılan olarak, bunlar yerleşik .NET Framework sürümünü karşı uygulamalar her zaman çalışır; Bu değişmemiştir.</span><span class="sxs-lookup"><span data-stu-id="243e9-120">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="243e9-121">Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamanın daha yeni bir .NET Framework sürümü altında çalışması için doğrudan (bkz [Senaryo 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="243e9-121">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
-   <span data-ttu-id="243e9-122">**Kitaplık geliştiricileri ve tüketicilerin**.</span><span class="sxs-lookup"><span data-stu-id="243e9-122">**Library developers and consumers**.</span></span> <span data-ttu-id="243e9-123">Yan yana barındırma uyumluluk sorunları bu kitaplığı geliştiriciler yüz çözmez.</span><span class="sxs-lookup"><span data-stu-id="243e9-123">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="243e9-124">Doğrudan--veya doğrudan bir başvuru aracılığıyla bir uygulama tarafından yüklenen bir kitaplık bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrısı--çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> içine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="243e9-124">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="243e9-125">Kitaplıklarınızı desteklemek istediğiniz .NET Framework'ün tüm sürümlerini karşı test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="243e9-125">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="243e9-126">Bir uygulama kullanarak derlenmiş ise [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] çalışma zamanı, ancak bir önceki çalışma zamanı kullanılarak oluşturulan bir kitaplık içerir Bu kitaplık kullanacağı [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] de çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="243e9-126">If an application is compiled using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime but includes a library that was built using an earlier runtime, that library will use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] runtime as well.</span></span> <span data-ttu-id="243e9-127">Ancak, önceki bir çalışma zamanı ve kullanılarak oluşturulan bir kitaplık kullanılarak oluşturulan bir uygulamanız varsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ayrıca kullanmak için uygulamanızı zorlamanız gerekir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (bkz [Senaryo 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="243e9-127">However, if you have an application that was built using an earlier runtime and a library that was built using the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], you must force your application to also use the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (see [scenario 3](#scenarios)).</span></span>  
  
-   <span data-ttu-id="243e9-128">**Yönetilen COM bileşeni geliştiriciler**.</span><span class="sxs-lookup"><span data-stu-id="243e9-128">**Managed COM component developers**.</span></span> <span data-ttu-id="243e9-129">Geçmişte, bilgisayarda yüklü çalışma zamanı en son sürümünü kullanarak yönetilen COM bileşenleri otomatik olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="243e9-129">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="243e9-130">COM bileşenleri ile oluşturulmuş çalışma zamanı sürümü karşı şimdi yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="243e9-130">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="243e9-131">.NET Framework sürüm 1.1 ile oluşturulan bileşenleri tarafından aşağıdaki tabloda gösterildiği gibi yan yana sürüm 4 bileşenleri çalıştırabilirsiniz, ancak yan yana barındırma için kullanılabilir olmadığından sürüm 2.0, 3.0 veya 3.5 bileşenleri çalıştıramadıklarından sürümleri.</span><span class="sxs-lookup"><span data-stu-id="243e9-131">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="243e9-132">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="243e9-132">.NET Framework version</span></span>|<span data-ttu-id="243e9-133">1.1</span><span class="sxs-lookup"><span data-stu-id="243e9-133">1.1</span></span>|<span data-ttu-id="243e9-134">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="243e9-134">2.0 - 3.5</span></span>|<span data-ttu-id="243e9-135">4</span><span class="sxs-lookup"><span data-stu-id="243e9-135">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="243e9-136">1.1</span><span class="sxs-lookup"><span data-stu-id="243e9-136">1.1</span></span>|<span data-ttu-id="243e9-137">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="243e9-137">Not applicable</span></span>|<span data-ttu-id="243e9-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="243e9-138">No</span></span>|<span data-ttu-id="243e9-139">Evet</span><span class="sxs-lookup"><span data-stu-id="243e9-139">Yes</span></span>|  
    |<span data-ttu-id="243e9-140">2.0 - 3.5</span><span class="sxs-lookup"><span data-stu-id="243e9-140">2.0 - 3.5</span></span>|<span data-ttu-id="243e9-141">Hayır</span><span class="sxs-lookup"><span data-stu-id="243e9-141">No</span></span>|<span data-ttu-id="243e9-142">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="243e9-142">Not applicable</span></span>|<span data-ttu-id="243e9-143">Evet</span><span class="sxs-lookup"><span data-stu-id="243e9-143">Yes</span></span>|  
    |<span data-ttu-id="243e9-144">4</span><span class="sxs-lookup"><span data-stu-id="243e9-144">4</span></span>|<span data-ttu-id="243e9-145">Evet</span><span class="sxs-lookup"><span data-stu-id="243e9-145">Yes</span></span>|<span data-ttu-id="243e9-146">Evet</span><span class="sxs-lookup"><span data-stu-id="243e9-146">Yes</span></span>|<span data-ttu-id="243e9-147">Geçerli değil</span><span class="sxs-lookup"><span data-stu-id="243e9-147">Not applicable</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="243e9-148">.NET framework sürüm 3.0 ve 3.5 sürüm 2.0 artımlı olarak oluşturulur ve yan yana çalıştırma gerekmez.</span><span class="sxs-lookup"><span data-stu-id="243e9-148">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="243e9-149">Bunlar temelde aynı sürüme sahip.</span><span class="sxs-lookup"><span data-stu-id="243e9-149">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="243e9-150">Yan yana barındırma yaygın senaryolar</span><span class="sxs-lookup"><span data-stu-id="243e9-150">Common Side-by-Side Hosting Scenarios</span></span>  
  
-   <span data-ttu-id="243e9-151">**Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.</span><span class="sxs-lookup"><span data-stu-id="243e9-151">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="243e9-152">Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve diğer tüm COM bileşenleri tarafından kullanılan .NET Framework sürümleri.</span><span class="sxs-lookup"><span data-stu-id="243e9-152">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="243e9-153">Yapmanız gerekenler: Bu senaryoda, hiçbir şey yapma.</span><span class="sxs-lookup"><span data-stu-id="243e9-153">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="243e9-154">COM bileşenlerini kayıtlı olan .NET Framework sürümü ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="243e9-154">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
-   <span data-ttu-id="243e9-155">**Senaryo 2**: yönetilen ile yerleşik uygulama [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] ile çalıştırmak tercih [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ancak çalıştıracağınız konusunda istekli [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sürüm 2.0 mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="243e9-155">**Scenario 2**: Managed application built with the [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] that you would prefer to run with the [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], but are willing to run on the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="243e9-156">Yüklü .NET framework sürümleri: .NET Framework'ün önceki bir sürümünü ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="243e9-156">.NET Framework versions installed: An earlier version of the .NET Framework and the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="243e9-157">Yapmanız gerekenler: içinde [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) uygulama dizininde kullanmak [ \<başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime > öğe](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="243e9-157">What to do: In the [application configuration file](../../../docs/framework/configure-apps/index.md) in the application directory, use the [\<startup> element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="243e9-158">**Senaryo 3:** ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="243e9-158">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="243e9-159">Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="243e9-159">.NET Framework versions installed: The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].</span></span>  
  
     <span data-ttu-id="243e9-160">Yapmanız gerekenler: uygulama dizinindeki uygulama yapılandırma dosyasını kullanacak `<startup>` öğeyle `useLegacyV2RuntimeActivationPolicy` özniteliğini `true` ve `<supportedRuntime>` öğesi aşağıdaki gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="243e9-160">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="243e9-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="243e9-161">Example</span></span>  
 <span data-ttu-id="243e9-162">Aşağıdaki örnek, yönetilen bir COM bileşeni bileşen için derlenen .NET Framework sürümünü kullanarak çalışan bir yönetilmeyen COM ana gösterir kullanın.</span><span class="sxs-lookup"><span data-stu-id="243e9-162">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="243e9-163">Aşağıdaki örnek çalıştırmak, derleme ve aşağıdaki kaydetmek için Yönetilen COM bileşeni kullanarak [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="243e9-163">To run the following example, compile and register the following managed COM component using the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].</span></span> <span data-ttu-id="243e9-164">Üzerinde bileşen kaydetmek için **proje** menüsünde tıklatın **özellikleri**, tıklatın **yapı** sekmesini tıklatın ve ardından **COMbirlikteçalışmaiçinkaydol**onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="243e9-164">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```  
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
  
 <span data-ttu-id="243e9-165">Önceki örneği tarafından oluşturulan COM nesnesi etkinleştirir aşağıdaki yönetilmeyen C++ uygulama derleyin.</span><span class="sxs-lookup"><span data-stu-id="243e9-165">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="243e9-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="243e9-166">See Also</span></span>  
 [<span data-ttu-id="243e9-167">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="243e9-167">\<startup> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [<span data-ttu-id="243e9-168">\<supportedRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="243e9-168">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
