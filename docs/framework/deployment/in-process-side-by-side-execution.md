---
title: Devam Eden Yan Yana Yürütme
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30d9517c404dc76cdc0f8206599cacdb430a1ae9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613987"
---
# <a name="in-process-side-by-side-execution"></a>Devam Eden Yan Yana Yürütme
İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], işlem içi yan tek bir işlemde birden çok ortak dil çalışma zamanı (CLR) sürümünü çalıştırmak için barındırma yana kullanabilirsiniz. Varsayılan olarak, COM bileşenlerini .NET Framework sürümüyle birlikte, işlem için yüklenen .NET Framework sürümünden bağımsız olarak oluşturuldukları çalıştırın yönetiliyor.  
  
## <a name="background"></a>Arka Plan  
 .NET Framework yönetilen için yan yana barındırma kodu sağlanan uygulamalar, ancak önce her zaman sahip [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], işlevselliği için Yönetilen COM bileşenlerini sağlamadı. Geçmişte, zaten yüklü çalışma zamanı sürümü veya .NET Framework'ün en son yüklenen sürüm işlem içine yüklenmiş yönetilen COM bileşenlerini çalıştı. Bu sürüm COM bileşeni ile uyumlu değilse, bileşenin başarısız olur.  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Aşağıdaki sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:  
  
- .NET Framework'ün yeni bir sürümünü yükleme mevcut uygulamalar üzerinde etkisi yoktur.  
  
- Uygulamaları birlikte oluşturuldukları .NET Framework sürümüne karşı çalışır. Bunlar .NET Framework'ün yeni sürüm açıkça yönlendirilmezseniz Bunu yapmak için kullanmayın. Ancak, geçiş için .NET Framework'ün yeni bir sürümünü kullanan uygulamalar için daha kolay olur.  
  
## <a name="effects-on-users-and-developers"></a>Kullanıcılara ve geliştiricilere etkileri  
  
- **Son kullanıcılar ve yöneticilerin**. Bu kullanıcılar artık bunlar bağımsız olarak veya bir uygulama ile yeni bir çalışma zamanı sürümünü yüklediğinizde, kendi bilgisayarlarına herhangi bir etkisi olacağı daha güvenli olabilir. Mevcut uygulamaları önce olduğu gibi çalışmaya devam eder.  
  
- **Uygulama geliştiricileri**. Yan yana barındırma, uygulama geliştiricilerin neredeyse hiçbir etkisi vardır. Varsayılan olarak, uygulamalar her zaman üzerinde oluşturulmuş .NET Framework sürümünü çalıştırın; Bu değişiklik olmadı. Ancak, geliştiricilerin bu davranışı geçersiz kılabilir ve uygulamanın daha yeni bir sürümü .NET Framework'ün altında çalışması için doğrudan (bkz [Senaryo 2](#scenarios)).  
  
- **Kitaplığı geliştiriciler ve tüketiciler**. Yan yana barındırma uyumluluk sorunları bu kitaplığı geliştiriciler yüz çözmez. Doğrudan bir uygulama--veya aracılığıyla bir doğrudan başvuru tarafından yüklenen bir kitaplığı bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrı--çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> içine yüklenir. Desteklemek istediğiniz .NET Framework'ün tüm sürümler karşı Kitaplıklarınızı test etmeniz gerekir. Bir uygulama kullanarak derlenirse [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] çalışma zamanı, ancak bir önceki çalışma zamanı kullanılarak oluşturulmuş bir kitaplık içerir, kitaplık kullanacak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] de çalışma zamanı. Ancak, bir önceki çalışma zamanı ve kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ayrıca kullanmak için uygulamanızı zorlamanız gerekir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (bkz [Senaryo 3](#scenarios)).  
  
- **COM Bileşen geliştiriciler yönetilen**. Geçmişte, bilgisayarda yüklü olan çalışma zamanı en son sürümünü kullanarak yönetilen COM bileşenlerini otomatik olarak çalıştı. Şimdi, COM bileşenleriyle birlikte oluşturuldukları çalışma zamanı sürümüne karşı çalıştırabilirsiniz.  
  
     Aşağıdaki tabloda gösterildiği gibi .NET Framework sürüm 1.1 ile oluşturulan bileşenler ile yan yana sürüm 4 bileşenlerini çalıştırabilirsiniz, ancak yan yana barındırma için kullanılabilir değil çünkü bunlar ile sürüm 2.0, 3.0 veya 3.5 bileşenleri çalışamaz sürümleri.  
  
    |.NET Framework sürümü|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Geçerli değil|Hayır|Evet|  
    |2.0 - 3.5|Hayır|Geçerli değil|Evet|  
    |4|Evet|Evet|Geçerli değil|  
  
> [!NOTE]
>  .NET framework sürüm 3.0 ve 3.5, sürüm 2.0 üzerinde artımlı olarak oluşturulur ve yan yana çalıştırma gerekmez. Bunlar aynı sürümü temelde aynıdır.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Yan yana barındırma senaryoları  
  
- **Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.  
  
     Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Ve diğer tüm COM bileşenleri tarafından kullanılan .NET Framework sürümleri.  
  
     Yapmanız gerekenler: Bu senaryoda, hiçbir şey yapmayın. COM bileşenleri kayıtlı olan .NET Framework sürümü ile çalışır.  
  
- **Senaryo 2**: Yönetilen uygulama ile oluşturulmuş [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] çalıştırmak tercih [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ancak çalıştırmak istediğiniz [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 2.0 sürümünde mevcut değil.  
  
     Yüklü .NET framework sürümleri: .NET Framework'ün önceki bir sürümünü ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yapmanız gerekenler: İçinde [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) uygulama dizininizde [ \<başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Senaryo 3:** Çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yüklü .NET framework sürümleri: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Yapmanız gerekenler: Uygulama yapılandırma dosyasında uygulama dizinindeki kullanın `<startup>` öğeyle `useLegacyV2RuntimeActivationPolicy` özniteliğini `true` ve `<supportedRuntime>` öğesi aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yönetilen bir COM bileşeni bileşen için derlenmiş .NET Framework sürümünü kullanarak çalışan bir yönetilmeyen COM konak gösterir kullanın.  
  
 Aşağıdaki örnek çalıştırmak, derlemek ve aşağıdaki kaydetmek için COM bileşenini kullanarak yönetilen [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Bileşeni üzerinde kaydetmek için **proje** menüsünde tıklayın **özellikleri**, tıklayın **derleme** sekmesine tıklayın ve ardından **COMbirlikteçalışmasıiçinkaydol**onay kutusu.  
  
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
  
 Önceki örneği tarafından oluşturulan COM nesnesi etkinleştirir aşağıdaki yönetilmeyen C++ uygulama derleyin.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
