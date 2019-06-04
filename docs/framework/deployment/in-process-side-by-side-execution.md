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
# <a name="in-process-side-by-side-execution"></a>Devam Eden Yan Yana Yürütme
.NET Framework 4 ile başlayarak işlem içi yan tek bir işlemde birden çok ortak dil çalışma zamanı (CLR) sürümünü çalıştırmak için barındırma yana kullanabilirsiniz. Varsayılan olarak, COM bileşenlerini .NET Framework sürümüyle birlikte, işlem için yüklenen .NET Framework sürümünden bağımsız olarak oluşturuldukları çalıştırın yönetiliyor.  
  
## <a name="background"></a>Arka Plan  
 .NET Framework için yan yana barındırma yönetilen kod uygulamalarının, ancak önce .NET Framework 4, bu işlevselliği için Yönetilen COM bileşenlerini sağlamadı sağlanan her zaman vardır. Geçmişte, zaten yüklü çalışma zamanı sürümü veya .NET Framework'ün en son yüklenen sürüm işlem içine yüklenmiş yönetilen COM bileşenlerini çalıştı. Bu sürüm COM bileşeni ile uyumlu değilse, bileşenin başarısız olur.  
  
 .NET Framework 4, aşağıdaki sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:  
  
- .NET Framework'ün yeni bir sürümünü yükleme mevcut uygulamalar üzerinde etkisi yoktur.  
  
- Uygulamaları birlikte oluşturuldukları .NET Framework sürümüne karşı çalışır. Bunlar .NET Framework'ün yeni sürüm açıkça yönlendirilmezseniz Bunu yapmak için kullanmayın. Ancak, geçiş için .NET Framework'ün yeni bir sürümünü kullanan uygulamalar için daha kolay olur.  
  
## <a name="effects-on-users-and-developers"></a>Kullanıcılara ve geliştiricilere etkileri  
  
- **Son kullanıcılar ve yöneticilerin**. Bu kullanıcılar artık bunlar bağımsız olarak veya bir uygulama ile yeni bir çalışma zamanı sürümünü yüklediğinizde, kendi bilgisayarlarına herhangi bir etkisi olacağı daha güvenli olabilir. Mevcut uygulamaları önce olduğu gibi çalışmaya devam eder.  
  
- **Uygulama geliştiricileri**. Yan yana barındırma, uygulama geliştiricilerin neredeyse hiçbir etkisi vardır. Varsayılan olarak, uygulamalar her zaman üzerinde oluşturulmuş .NET Framework sürümünü çalıştırın; Bu değişiklik olmadı. Ancak, geliştiricilerin bu davranışı geçersiz kılabilir ve uygulamanın daha yeni bir sürümü .NET Framework'ün altında çalışması için doğrudan (bkz [Senaryo 2](#scenarios)).  
  
- **Kitaplığı geliştiriciler ve tüketiciler**. Yan yana barındırma uyumluluk sorunları bu kitaplığı geliştiriciler yüz çözmez. Doğrudan bir uygulama--veya aracılığıyla bir doğrudan başvuru tarafından yüklenen bir kitaplığı bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> çağrı--çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> içine yüklenir. Desteklemek istediğiniz .NET Framework'ün tüm sürümler karşı Kitaplıklarınızı test etmeniz gerekir. Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenmiş olduğuna, ancak bir önceki çalışma zamanı kullanılarak oluşturulmuş bir kitaplık içerir, bu kitaplık de .NET Framework 4 çalışma zamanını kullanın. Ancak, bir önceki çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa, ayrıca .NET Framework 4 kullanmak için uygulamanızı zorlamanız gerekir (bkz [Senaryo 3](#scenarios)).  
  
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
  
     Yüklü .NET framework sürümleri: .NET Framework 4 ve diğer tüm COM bileşenleri tarafından kullanılan .NET Framework sürümleri.  
  
     Yapmanız gerekenler: Bu senaryoda, hiçbir şey yapmayın. COM bileşenleri kayıtlı olan .NET Framework sürümü ile çalışır.  
  
- **Senaryo 2**: Yönetilen uygulama ile oluşturulmuş [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] çalıştırmak tercih [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)], ancak sürüm 2.0 mevcut değilse .NET Framework 4'te çalıştırmak yararlı olur.  
  
     Yüklü .NET framework sürümleri: Önceki bir sürümünü .NET Framework ve .NET Framework 4.  
  
     Yapmanız gerekenler: İçinde [uygulama yapılandırma dosyası](../../../docs/framework/configure-apps/index.md) uygulama dizininizde [ \<başlangıç > öğesi](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime > öğesi](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulan COM bileşenlerini kullanan yerel uygulama.  
  
     Yüklü .NET framework sürümleri: .NET Framework 4.  
  
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
  
 Aşağıdaki örnek çalıştırmak için derleme ve .NET Framework 3.5 kullanarak aşağıdaki yönetilen COM bileşeni kaydedin. Bileşeni üzerinde kaydetmek için **proje** menüsünde tıklayın **özellikleri**, tıklayın **derleme** sekmesine tıklayın ve ardından **COMbirlikteçalışmasıiçinkaydol**onay kutusu.  
  
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
