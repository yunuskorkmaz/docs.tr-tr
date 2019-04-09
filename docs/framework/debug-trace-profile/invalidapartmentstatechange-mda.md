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
ms.openlocfilehash: c201ab51c1af8a86fc1c2c4f80738007152b3bd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122856"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) ya da iki sorunları tarafından etkinleştirilir:  
  
-   Farklı grup durumuna COM tarafından başlatılmış bir iş parçacığı COM grubu durumunu değiştirmek için bir deneme yapılır.  
  
-   İş parçacığı COM Grup durumu beklenmedik bir şekilde değiştirir.  
  
## <a name="symptoms"></a>Belirtiler  
  
-   Bir iş parçacığının COM Grup durumu ne istenmediğinden ' dir. Bu, geçerli olandan farklı bir iş parçacığı modeline sahip bir COM bileşenleri için kullanılacak proxy neden olabilir. Bu sırayla neden olabilir bir <xref:System.InvalidCastException> COM nesnesi çapraz-grup sıralama için ayarlanmadınız arabirimler üzerinden çağırırken durum.  
  
-   İş parçacığının COM Grup durumu, beklenenden daha farklıdır. Bu neden olabilir bir <xref:System.Runtime.InteropServices.COMException> ile bir HRESULT RPC_E_WRONG_THREAD yanı <xref:System.InvalidCastException> yapma çağırdığında üzerinde bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). Bu da bazı tek iş parçacıklı COM bileşenleri Bozulması veya veri kaybına yol açabilir aynı anda birden çok iş parçacığı tarafından erişilecek neden olabilir.  
  
## <a name="cause"></a>Sebep  
  
-   İş parçacığı için farklı bir COM Grup durumu daha önceden başlatıldı. Bir iş parçacığı grubu durumunu açık veya örtük olarak ayarlanabilir unutmayın. Açık işlemleri <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği ve <xref:System.Threading.Thread.SetApartmentState%2A> ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemleri. Kullanılarak oluşturulan bir iş parçacığı <xref:System.Threading.Thread.Start%2A> yöntemi örtülü olarak ayarlandığında <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.Threading.Thread.SetApartmentState%2A> iş parçacığı başlatılmadan önce çağrılır. Uygulamanın ana iş parçacığı ayrıca açık olarak başlatılır <xref:System.Threading.ApartmentState.MTA> sürece <xref:System.STAThreadAttribute> özniteliği ana yöntemi belirtildi.  
  
-   `CoUninitialize` Yöntemi (veya `CoInitializeEx` yöntemi) ile farklı bir eşzamanlılık modeli iş parçacığı üzerinde çağrılır.  
  
## <a name="resolution"></a>Çözüm  
 Yürütme başlamadan önce iş parçacığı grubu durumunu ayarlamak veya ya da uygulama <xref:System.STAThreadAttribute> özniteliği veya <xref:System.MTAThreadAttribute> uygulamanın main yöntemi için özniteliği.  
  
 İkinci nedeni, ideal olarak, kodu çağırır `CoUninitialize` yöntemi çağrısı yaklaşık sonlandırmak için iş parçacığı olan ve hiçbir RCW vardır ve temel alınan COM bileşenleri yine de iş parçacığı tarafından kullanıma kadar gecikme değiştirilmelidir. Ancak, çağıran kodu değiştirmek mümkün değilse, `CoUninitialize` bu şekilde başlatılmamış parçacıklarından yöntemi, ardından hiçbir RCW kullanılmalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçerli iş parçacığının COM Grup durumu ve kod uygulanmaya çalışılıyor durumu.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu mda'nın etkinleştirebilirsiniz bir durumu gösterir.  
  
```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
