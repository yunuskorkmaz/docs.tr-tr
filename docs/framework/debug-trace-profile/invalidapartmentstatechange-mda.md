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
ms.openlocfilehash: 8acafcc2fba9a7d30cc77f25f06adaca7c79db32
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217411"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` yönetilen hata ayıklama Yardımcısı (MDS) iki sorunlardan biri tarafından etkinleştirilir:  
  
- COM tarafından zaten başlatılmış olan bir iş parçacığının COM grup durumunu farklı bir grup durumuna değiştirme girişiminde bulunuldu.  
  
- Bir iş parçacığının COM apartman durumu beklenmedik şekilde değişir.  
  
## <a name="symptoms"></a>Belirtiler  
  
- Bir iş parçacığının COM grubu durumu istenen değildir. Bu durum, mevcut bir iş parçacığı modeline sahip COM bileşenleri için proxy 'lerin kullanılmasına neden olabilir. Bu sırayla, COM nesnesi çapraz grup sıralaması için ayarlanmamış arabirimler aracılığıyla çağrılırken bir <xref:System.InvalidCastException> oluşturulmasına neden olabilir.  
  
- İş parçacığının COM apartman durumu beklenenden farklı. Bu, bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde çağrılar yaparken bır <xref:System.Runtime.InteropServices.COMException> hresult rpc_e_wrong_thread ve bir <xref:System.InvalidCastException> olan bir neden olabilir. Bu Ayrıca, bazı tek iş parçacıklı COM bileşenlerine aynı anda birden çok iş parçacığı tarafından erişilmesine neden olabilir, bu da bozulmaya veya veri kaybına neden olabilir.  
  
## <a name="cause"></a>Nedeni  
  
- İş parçacığı daha önce farklı bir COM grubu durumuna başlatılmıştı. Bir iş parçacığının Grup durumunun açık veya örtük olarak ayarlankullanılamayacağını unutmayın. Açık işlemler <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliğini ve <xref:System.Threading.Thread.SetApartmentState%2A> ve <xref:System.Threading.Thread.TrySetApartmentState%2A> yöntemlerini içerir. <xref:System.Threading.Thread.Start%2A> yöntemi kullanılarak oluşturulan bir iş parçacığı, <xref:System.Threading.Thread.SetApartmentState%2A> iş parçacığı başlatılmadan önce çağrılmadığı müddetçe örtük olarak <xref:System.Threading.ApartmentState.MTA> olarak ayarlanır. Uygulamanın ana iş parçacığı Ayrıca, ana yöntemde <xref:System.STAThreadAttribute> özniteliği belirtilmedikçe <xref:System.Threading.ApartmentState.MTA> için de örtülü olarak başlatılır.  
  
- Farklı bir eşzamanlılık modeliyle `CoUninitialize` yöntemi (veya `CoInitializeEx` yöntemi) iş parçacığında çağırılır.  
  
## <a name="resolution"></a>Çözüm  
 Yürütmeye başlamadan önce iş parçacığının Grup durumunu ayarlayın veya <xref:System.STAThreadAttribute> özniteliğini ya da <xref:System.MTAThreadAttribute> özniteliğini uygulamanın Main yöntemine uygulayın.  
  
 İkinci neden için `CoUninitialize` yöntemi çağıran kod, iş parçacığı sonlandırılmaya ve bir RCWs olmadığından ve temel alınan COM bileşenleri iş parçacığı tarafından hala kullanımda olana kadar çağrıyı geciktirmek için değiştirilmelidir. Ancak, `CoUninitialize` yöntemini çağıran kodu değiştirmek mümkün değilse, bu şekilde başlatılmamış iş parçacıklarında hiçbir RCWs kullanılmamalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
