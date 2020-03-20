---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181804"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
Bir `loadFromContext` derleme `LoadFrom` içeriğe yüklenirse yönetilen hata ayıklama yardımcısı (MDA) etkinleştirilir. Bu durum arama <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemlerin bir sonucu olarak oluşabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerinin kullanımı derlemelerin `LoadFrom` bağlam içinde yüklenmesine neden olabilir. Bu bağlamın kullanımı serileştirme, döküm ve bağımlılık çözümü için beklenmeyen davranışlara neden olabilir. Genel olarak, bu sorunları önlemek için `Load` derlemelerin içeriğe yüklenmesi önerilir. Bu MDA olmadan bir derlemenin hangi içeriğe yüklendiğini belirlemek zordur.  
  
## <a name="cause"></a>Nedeni  
 Genel olarak, bir derleme `LoadFrom` `Load` bağlam dışındaki bir yoldan yüklenmişse, genel derleme önbelleği <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> veya özellik gibi içeriğe yüklenir.  
  
## <a name="resolution"></a>Çözüm  
 Çağrıların artık gerekmeyecek şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> yapılandırıştırın. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
- Derlemeleri genel derleme önbelleğine yükleyin.  
  
- Derlemeleri dizinine <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomain>yerleştirin. Varsayılan etki alanı söz konusu <xref:System.AppDomainSetup.ApplicationBase%2A> olduğunda, dizin işlemi başlatan yürütülebilir dosyayı içeren dizindir. Bu, derlemeyi taşımak <xref:System.AppDomain> için uygun değilse yeni bir oluşturma yı da gerektirebilir.  
  
- Uygulama yapılandırmanıza (.config) dosyanıza veya çalıştırılabilir dosyaya göre alt dizinlerde bağımlı derlemeler varsa ikincil uygulama etki adlarına bir sondalama yolu ekleyin.  
  
 Her durumda, kod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kullanmak için değiştirilebilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 MDA'nın CLR üzerinde herhangi bir etkisi yoktur. Yük isteği nin sonucu olarak kullanılan bağlamı bildirir.  
  
## <a name="output"></a>Çıktı  
 MDA, derlemenin bağlam içine `LoadFrom` yüklendiğini bildirir. Bu derleme ve yol basit adını belirtir. Ayrıca `LoadFrom` bağlamı kullanmaktan kaçınmak için azaltıcı etkenler önerir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu MDA'yı etkinleştirebilecek bir durumu gösterir:  
  
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
