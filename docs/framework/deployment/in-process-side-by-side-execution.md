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
# <a name="in-process-side-by-side-execution"></a>Devam Eden Yan Yana Yürütme
İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], işlem içi-tek bir işlemde birden fazla sürümünü ortak dil çalışma zamanı (CLR) çalıştırmak için barındırma yana kullanabilirsiniz. Varsayılan olarak, COM bileşenlerini işlemi için yüklenen .NET Framework sürüm ne olursa olsun bunlar, oluşturulan .NET Framework sürümünü çalıştıran yönetilen.  
  
## <a name="background"></a>Arka Plan  
 Yan yana yönetilen barındırma kodu sağlanan uygulamalar, ancak önce .NET Framework her zaman sahip [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], yönetilen COM bileşenleri bu işlevselliği sağlamadı. Geçmişte, işlem içine yüklenmiş yönetilen COM bileşenleri zaten yüklendi çalışma zamanı sürümü veya .NET Framework'ün yüklü en son sürümü verdi. Bu sürüm COM bileşeni ile uyumlu değilse, bileşen başarısız olur.  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Aşağıdaki sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:  
  
-   .NET Framework'ün yeni bir sürümünü yükleme var olan uygulamalar üzerinde etkisi yoktur.  
  
-   Uygulamaları ile oluşturulan .NET Framework sürümünü karşı çalışır. Bunlar, .NET Framework yeni sürümünü açıkça yönlendirilmiş sürece bunu yapmak için kullanmayın. Ancak, .NET Framework'ün yeni bir sürümü kullanılarak uygulamaların geçiş kolaydır.  
  
## <a name="effects-on-users-and-developers"></a>Kullanıcıların ve geliştiricilerin etkileri  
  
-   **Son kullanıcılar ve sistem yöneticileri**. Bu kullanıcılar artık yeni bir çalışma zamanı sürümü bağımsız olarak veya bir uygulamayla yükledikleri zaman, bilgisayarlarında etkisi gerekir güvenle olabilir. Var olan uygulamalar, önceden olduğu gibi çalışmaya devam eder.  
  
-   **Uygulama geliştiricilerinin**. Yan yana barındırma uygulama geliştiricileri üzerinde neredeyse hiçbir etkisi yoktur. Varsayılan olarak, bunlar yerleşik .NET Framework sürümünü karşı uygulamalar her zaman çalışır; Bu değişmemiştir. Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamanın daha yeni bir .NET Framework sürümü altında çalışması için doğrudan (bkz [Senaryo 2](#scenarios)).  
  
-   **Kitaplık geliştiricileri ve tüketicilerin**. Yan yana barındırma uyumluluk sorunları bu kitaplığı geliştiriciler yüz çözmez. Doğrudan--veya doğrudan bir başvuru aracılığıyla bir uygulama tarafından yüklenen bir kitaplık bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrısı--çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> içine yüklenir. Kitaplıklarınızı desteklemek istediğiniz .NET Framework'ün tüm sürümlerini karşı test etmeniz gerekir. Bir uygulama kullanarak derlenmiş ise [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] çalışma zamanı, ancak bir önceki çalışma zamanı kullanılarak oluşturulan bir kitaplık içerir Bu kitaplık kullanacağı [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] de çalışma zamanı. Ancak, önceki bir çalışma zamanı ve kullanılarak oluşturulan bir kitaplık kullanılarak oluşturulan bir uygulamanız varsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ayrıca kullanmak için uygulamanızı zorlamanız gerekir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (bkz [Senaryo 3](#scenarios)).  
  
-   **Yönetilen COM bileşeni geliştiriciler**. Geçmişte, bilgisayarda yüklü çalışma zamanı en son sürümünü kullanarak yönetilen COM bileşenleri otomatik olarak çalıştırılır. COM bileşenleri ile oluşturulmuş çalışma zamanı sürümü karşı şimdi yürütebilir.  
  
     .NET Framework sürüm 1.1 ile oluşturulan bileşenleri tarafından aşağıdaki tabloda gösterildiği gibi yan yana sürüm 4 bileşenleri çalıştırabilirsiniz, ancak yan yana barındırma için kullanılabilir olmadığından sürüm 2.0, 3.0 veya 3.5 bileşenleri çalıştıramadıklarından sürümleri.  
  
    |.NET Framework sürümü|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Geçerli değil|Hayır|Evet|  
    |2.0 - 3.5|Hayır|Geçerli değil|Evet|  
    |4|Evet|Evet|Geçerli değil|  
  
> [!NOTE]
>  .NET framework sürüm 3.0 ve 3.5 sürüm 2.0 artımlı olarak oluşturulur ve yan yana çalıştırma gerekmez. Bunlar temelde aynı sürüme sahip.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Yan yana barındırma yaygın senaryolar  
  
-   **Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.  
  
     Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve diğer tüm COM bileşenleri tarafından kullanılan .NET Framework sürümleri.  
  
     Yapmanız gerekenler: Bu senaryoda, hiçbir şey yapma. COM bileşenlerini kayıtlı olan .NET Framework sürümü ile çalışır.  
  
-   **Senaryo 2**: yönetilen ile yerleşik uygulama [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] ile çalıştırmak tercih [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ancak çalıştıracağınız konusunda istekli [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sürüm 2.0 mevcut değilse.  
  
     Yüklü .NET framework sürümleri: .NET Framework'ün önceki bir sürümünü ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yapmanız gerekenler: içinde [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) uygulama dizininde kullanmak [ \<başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime > öğe](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **Senaryo 3:** ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yapmanız gerekenler: uygulama dizinindeki uygulama yapılandırma dosyasını kullanacak `<startup>` öğeyle `useLegacyV2RuntimeActivationPolicy` özniteliğini `true` ve `<supportedRuntime>` öğesi aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yönetilen bir COM bileşeni bileşen için derlenen .NET Framework sürümünü kullanarak çalışan bir yönetilmeyen COM ana gösterir kullanın.  
  
 Aşağıdaki örnek çalıştırmak, derleme ve aşağıdaki kaydetmek için Yönetilen COM bileşeni kullanarak [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Üzerinde bileşen kaydetmek için **proje** menüsünde tıklatın **özellikleri**, tıklatın **yapı** sekmesini tıklatın ve ardından **COMbirlikteçalışmaiçinkaydol**onay kutusu.  
  
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
  
 Önceki örneği tarafından oluşturulan COM nesnesi etkinleştirir aşağıdaki yönetilmeyen C++ uygulama derleyin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
 [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
