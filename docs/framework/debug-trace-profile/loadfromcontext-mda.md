---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216168"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext` yönetilen hata ayıklama Yardımcısı (MDA), bir derleme `LoadFrom` bağlamına yüklenirse etkinleştirilir. Bu durum, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya başka benzer yöntemlerin çağrılması sonucu olarak ortaya çıkabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerinin kullanımı, derlemelerin `LoadFrom` bağlamına yüklenmesine neden olabilir. Bu bağlamın kullanılması serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir. Genel olarak, bu sorunlardan kaçınmak için derlemelerin `Load` bağlamına yüklenmesi önerilir. Bir derlemenin Bu MDA ' dan ne şekilde yüklendiğini belirlemek zordur.  
  
## <a name="cause"></a>Nedeni  
 Genellikle, genel derleme önbelleği veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği gibi `Load` bağlamı dışında bir yoldan yüklenmişse, bir derleme `LoadFrom` bağlamına yüklenmiştir.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Reflection.Assembly.LoadFrom%2A> çağrılarına artık gerek duyulmayan uygulamaları yapılandırın. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
- Derlemeleri genel bütünleştirilmiş kod önbelleğine yükler.  
  
- Derlemeleri <xref:System.AppDomain><xref:System.AppDomainSetup.ApplicationBase%2A> dizinine yerleştirin. Varsayılan etki alanı söz konusu olduğunda <xref:System.AppDomainSetup.ApplicationBase%2A> Dizin, işlemi başlatan yürütülebilir dosyayı içeren bir dosyadır. Bu, derlemeyi taşımak uygun değilse yeni bir <xref:System.AppDomain> oluşturulmasını de gerektirebilir.  
  
- Bağımlı derlemeler çalıştırılabilire göre alt dizinlerde ise, uygulama yapılandırma (. config) dosyanıza veya ikincil uygulama etki alanlarına bir yoklama yolu ekleyin.  
  
 Her durumda, kod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullanacak şekilde değiştirilebilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 MDA 'nin CLR üzerinde hiçbir etkisi yoktur. Yükleme isteğinin sonucu olarak kullanılan bağlamı bildirir.  
  
## <a name="output"></a>Çıktı  
 MDA, derlemenin `LoadFrom` bağlamına yüklendiğini bildiriyor. Derlemenin basit adını ve yolunu belirtir. Ayrıca, `LoadFrom` bağlamını kullanmaktan kaçınmak için azaltıcı etkenleri de önerir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
