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
ms.openlocfilehash: 7ff68ce5f612255f41ce3a7c6f2526c3a340cfcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967307"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Yönetilen hata ayıklama Yardımcısı (MDS) iki sorunlardan biri tarafından etkinleştirilir:  
  
- COM tarafından zaten başlatılmış olan bir iş parçacığının COM grup durumunu farklı bir grup durumuna değiştirme girişiminde bulunuldu.  
  
- Bir iş parçacığının COM apartman durumu beklenmedik şekilde değişir.  
  
## <a name="symptoms"></a>Belirtiler  
  
- Bir iş parçacığının COM grubu durumu istenen değildir. Bu durum, mevcut bir iş parçacığı modeline sahip COM bileşenleri için proxy 'lerin kullanılmasına neden olabilir. Bu sırayla, com nesnesi çapraz <xref:System.InvalidCastException> grup sıralaması için ayarlanmamış arabirimler aracılığıyla çağrılırken bir oluşturulmasına neden olabilir.  
  
- İş parçacığının COM apartman durumu beklenenden farklı. Bu, bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde çağrılar <xref:System.InvalidCastException> yaparken bir HRESULT ile birlikte bir <xref:System.Runtime.InteropServices.COMException> RPC_E_WRONG_THREAD ve bir ile oluşmasına neden olabilir. Bu Ayrıca, bazı tek iş parçacıklı COM bileşenlerine aynı anda birden çok iş parçacığı tarafından erişilmesine neden olabilir, bu da bozulmaya veya veri kaybına neden olabilir.  
  
## <a name="cause"></a>Sebep  
  
- İş parçacığı daha önce farklı bir COM grubu durumuna başlatılmıştı. Bir iş parçacığının Grup durumunun açık veya örtük olarak ayarlankullanılamayacağını unutmayın. Açık işlemler, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliğini <xref:System.Threading.Thread.SetApartmentState%2A> ve ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemlerini içerir. <xref:System.Threading.Thread.Start%2A> Yöntemi kullanılarak oluşturulan bir iş parçacığı, iş parçacığı başlatılmadan <xref:System.Threading.ApartmentState.MTA> önce <xref:System.Threading.Thread.SetApartmentState%2A> çağrılmadığı için örtük olarak olarak ayarlanır. Uygulamanın ana iş parçacığı, <xref:System.Threading.ApartmentState.MTA> <xref:System.STAThreadAttribute> özniteliği Main yönteminde belirtilmediği takdirde olarak olarak da başlatılır.  
  
- Farklı bir eşzamanlılık modeliyle `CoInitializeEx` Yöntemi(veyayöntemi)işparçacığındaçağırılır.`CoUninitialize`  
  
## <a name="resolution"></a>Çözüm  
 Yürütmeye başlamadan önce iş parçacığının Grup durumunu ayarlayın veya <xref:System.STAThreadAttribute> özniteliğini <xref:System.MTAThreadAttribute> ya da özniteliğini uygulamanın Main yöntemine uygulayın.  
  
 İkinci nedenle, en ideal olarak, `CoUninitialize` yöntemi çağıran kod, iş parçacığı sonlandırılmaya ve bir RCWs olmadığından ve temel alınan com bileşenleri iş parçacığı tarafından hala kullanımda olana kadar çağrıyı geciktirmek için değiştirilmelidir. Ancak, `CoUninitialize` yöntemi çağıran kodu değiştirmek mümkün değilse, bu şekilde başlatılmamış iş parçacıklarında hiçbir RCWs kullanılmamalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçerli iş parçacığının COM grubu durumu ve kodun uygulanmaya çalışılması gereken durum.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir.  
  
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
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
