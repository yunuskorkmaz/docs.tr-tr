---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 864367e71f3ed05af87931b2a87f576df42dcbf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390698"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) ya da iki sorunları etkinleştirildi:  
  
-   COM tarafından farklı grup durumu için zaten başlatılmış olan bir iş parçacığı COM grup durumunu değiştirmek için bir deneme yapılır.  
  
-   İş parçacığı COM Grup durumu beklenmedik bir şekilde değiştirir.  
  
## <a name="symptoms"></a>Belirtiler  
  
-   Bir iş parçacığının COM Grup durumu ne değil istendi ' dir. Bu, geçerli olandan farklı bir iş parçacığı modeline sahip COM bileşenleri için kullanılacak proxy neden olabilir. Bu sırayla neden bir <xref:System.InvalidCastException> COM nesnesi arası grup hazırlama için ayarlanmayan arabirimleri aracılığıyla çağrılırken durum için.  
  
-   COM Grup iş parçacığı beklenenden farklı bir durumda. Bu neden bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile yanı sıra bir <xref:System.InvalidCastException> yapma çağırdığında üzerinde bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). Bu da bazı tek iş parçacıklı COM bileşenleri bozulmaya veya veri kaybına yol açabilir aynı anda birden çok iş parçacığı tarafından erişilecek neden olabilir.  
  
## <a name="cause"></a>Sebep  
  
-   İş parçacığı için farklı bir COM Grup durumu daha önce başlatıldı. İş parçacığı Grup durumu açıkça veya örtük ayarlanabilir unutmayın. Açık işlemleri içeren <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Threading.Thread.SetApartmentState%2A> ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemleri. Kullanılarak oluşturulan bir iş parçacığı <xref:System.Threading.Thread.Start%2A> yöntemi örtük olarak ayarlandığında <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.Threading.Thread.SetApartmentState%2A> iş parçacığı başlatılmadan önce çağrılır. Uygulamanın ana iş parçacığına da örtük olarak başlatılıp başlatılmadığı <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.STAThreadAttribute> özniteliği ana yöntemi belirtilen.  
  
-   `CoUninitialize` Yöntemi (veya `CoInitializeEx` yöntemi) ile farklı bir eşzamanlılık modeli iş parçacığı üzerinde olarak adlandırılır.  
  
## <a name="resolution"></a>Çözüm  
 Yürütme başlamadan önce iş parçacığının grup durumu ayarlamak veya ya da geçerli <xref:System.STAThreadAttribute> özniteliği veya <xref:System.MTAThreadAttribute> özniteliği uygulamanın ana yöntem.  
  
 İkinci nedeni için ideal olarak, kod, çağıran `CoUninitialize` yöntemi, iş parçacığının yaklaşık sonlandırmak için ve hiçbir RCWs vardır ve temel alınan COM bileşenleri yine iş parçacığı tarafından kullanımda kadar çağrı gecikme değiştirilmelidir. Ancak, çağıran kodu değiştirmek mümkün değilse, `CoUninitialize` bu şekilde başlatılmadı parçacıklarından yöntemi sonra hiçbir RCWs kullanılmalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçerli iş parçacığının COM Grup durumu ve kod uygulamak için çalışıyordu durumu.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir.  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
