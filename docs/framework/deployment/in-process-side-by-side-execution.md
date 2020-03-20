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
# <a name="in-process-side-by-side-execution"></a>Devam Eden Yan Yana Yürütme
.NET Framework 4'ten başlayarak, ortak dil çalışma zamanının (CLR) birden çok sürümüne tek bir işlemde çalıştırmak için süreç içi yan yana barındırma yı kullanabilirsiniz. Varsayılan olarak, yönetilen COM bileşenleri, işlem için yüklenen .NET Framework sürümünden bağımsız olarak, birlikte üretildikleri .NET Framework sürümüyle çalışır.  
  
## <a name="background"></a>Arka plan  
 .NET Framework her zaman yönetilen kod uygulamaları için yan yana barındırma sağlamıştır, ancak .NET Framework 4'ten önce yönetilen COM bileşenleri için bu işlevselliği sağlamamıştır. Geçmişte, bir işleme yüklenen yönetilen COM bileşenleri, zaten yüklenmiş olan çalışma zamanının sürümüyle veya .NET Framework'ün en son yüklü sürümüyle çalıştırılırdı. Bu sürüm COM bileşeni ile uyumlu değilse, bileşen başarısız olur.  
  
 .NET Framework 4, yan yana barındırma için yeni bir yaklaşım sağlar ve aşağıdakileri sağlar:  
  
- .NET Framework'ün yeni bir sürümünün yüklenmesinin varolan uygulamalar üzerinde hiçbir etkisi yoktur.  
  
- Uygulamalar, .NET Framework'ün birlikte inşa edildikleri sürümüne karşı çalışır. Açıkça yönlendirilmedikçe .NET Framework'ün yeni sürümünü kullanmaz. Ancak, uygulamaların .NET Framework'ün yeni bir sürümünü kullanması daha kolaydır.  
  
## <a name="effects-on-users-and-developers"></a>Kullanıcılar ve Geliştiriciler Üzerindeki Etkileri  
  
- **Son kullanıcılar ve sistem yöneticileri.** Bu kullanıcılar artık çalışma zamanının yeni bir sürümünü bağımsız olarak veya bir uygulamayla yüklediklerinde, bunun bilgisayarları üzerinde hiçbir etkisi olmayacağından daha fazla güvenebilirler. Varolan uygulamalar daha önce olduğu gibi çalışmaya devam edecektir.  
  
- **Uygulama geliştiricileri**. Yan yana barındırma uygulama geliştiricileri üzerinde hemen hemen hiçbir etkisi yoktur. Varsayılan olarak, uygulamalar her zaman üzerine inşa edildi .NET Framework sürümüne karşı çalışır; bu değişmedi. Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamayı .NET Framework'ün daha yeni bir sürümü altında çalıştırmaya yönlendirebilir [(bkz. senaryo 2).](#scenarios)  
  
- **Kütüphane geliştiricileri ve tüketiciler.** Yan yana barındırma, kitaplık geliştiricilerinkarşılaştığı uyumluluk sorunlarını çözmez. Doğrudan bir uygulama tarafından doğrudan yüklenen bir kitaplık - <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> doğrudan bir başvuru yoluyla veya <xref:System.AppDomain> bir çağrı yoluyla - yüklendiği zaman ları kullanmaya devam ediyor. Kitaplıklarınızı desteklemek istediğiniz .NET Framework'ün tüm sürümlerine göre test etmeniz gerekir. Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenmişse, ancak daha önceki bir çalışma zamanı kullanılarak oluşturulmuş bir kitaplık içeriyorsa, bu kitaplık .NET Framework 4 çalışma zamanını da kullanır. Ancak, daha önceki bir çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplığını kullanarak oluşturulmuş bir uygulamanız varsa, uygulamanızı .NET Framework 4'ü de kullanmaya zorlamalısınız (bkz. [senaryo 3).](#scenarios)  
  
- **Yönetilen COM bileşen geliştiricileri.** Geçmişte, yönetilen COM bileşenleri bilgisayarda yüklü çalışma zamanının en son sürümünü kullanarak otomatik olarak çalışırdı. Artık COM bileşenlerini, birlikte üretildikleri çalışma zamanının sürümüne karşı çalıştırabilirsiniz.  
  
     Aşağıdaki tabloda gösterildiği gibi, .NET Framework sürüm 1.1 ile oluşturulmuş bileşenler sürüm 4 bileşenleriyle yan yana çalıştırılabilir, ancak sürüm 2.0, 3.0 veya 3.5 bileşenleriyle çalıştırılamazlar, çünkü yan yana barındırma bu bileşenler için kullanılamaz Sürüm.  
  
    |.NET Framework sürümü|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Uygulanamaz|Hayır|Evet|  
    |2.0 - 3.5|Hayır|Uygulanamaz|Evet|  
    |4|Evet|Evet|Uygulanamaz|  
  
> [!NOTE]
> .NET Framework sürümleri 3.0 ve 3.5 sürüm 2.0 üzerine kademeli olarak oluşturulur ve yan yana çalışması gerekmez. Bunlar doğal olarak aynı sürüm.  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a>Ortak Yan Yana Barındırma Senaryoları  
  
- **Senaryo 1:** .NET Framework'ün önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.  
  
     .NET Framework sürümleri yüklendi: .NET Framework 4 ve COM bileşenleri tarafından kullanılan .NET Framework'ün diğer tüm sürümleri.  
  
     Ne yapmalı: Bu senaryoda, hiçbir şey yapmayın. COM bileşenleri, kayıtlı oldukları .NET Framework sürümüyle çalışır.  
  
- **Senaryo 2**: .NET Framework 2.0 ile çalıştırmayı tercih ettiğiniz ,ancak sürüm 2.0 yoksa .NET Framework 4 üzerinde çalıştırmak istediğiniz .NET Framework 2.0 SP1 ile oluşturulmuş yönetilen uygulama.  
  
     .NET Framework sürümleri yüklü: .NET Framework ve .NET Framework 4'ün önceki bir sürümü.  
  
     Ne yapmalı: Uygulama dizinindeki [uygulama yapılandırma dosyasında](../configure-apps/index.md) [ \<başlangıç> öğesini](../configure-apps/file-schema/startup/startup-element.md) ve [ \<desteklenen Runtime> öğesini](../configure-apps/file-schema/startup/supportedruntime-element.md) aşağıdaki gibi kullanın:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework'ün önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.  
  
     .NET Framework sürümleri yüklendi: .NET Framework 4.  
  
     Ne yapmalı: Uygulama dizinindeki uygulama yapılandırma dosyasında, `<startup>` öznitelik `useLegacyV2RuntimeActivationPolicy` ayarlı `true` öğeyi `<supportedRuntime>` ve öğeyi aşağıdaki gibi ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bileşenin kullanmak üzere derlenen .NET Framework sürümünü kullanarak yönetilen bir COM bileşeni çalıştıran yönetilmeyen bir COM ana bilgisayarını gösterir.  
  
 Aşağıdaki örneği çalıştırmak için .NET Framework 3.5'i kullanarak aşağıdaki yönetilen COM bileşenini derleyip kaydedin. Bileşeni kaydetmek için **Proje** menüsünde **Özellikler'i**, **Yapı** sekmesini tıklatın ve ardından COM interop onay kutusunu **kaydet'i** seçin.  
  
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
  
 Önceki örnekte oluşturulan COM nesnesini etkinleştiren aşağıdaki yönetilmemiş C++ uygulamasını derle.  
  
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

- [\<başlangıç> Öğesi](../configure-apps/file-schema/startup/startup-element.md)
- [\<desteklenenRuntime> Öğesi](../configure-apps/file-schema/startup/supportedruntime-element.md)
