---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b2cf06a5ab921f5ae89da4856e8164b6f57db5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098617"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir derleme halinde yüklenmiş ise `LoadFrom` bağlamı. Çağırma sonucunda bu durum ortaya çıkabilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemler.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerin kullanımını içinde yüklenen derlemeler sonuçlanabilir `LoadFrom` bağlamı. Bu bağlam kullanımını serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir. Genel olarak, derlemeleri içine yüklenen önerilir `Load` bu sorunları önlemek için bağlam. Hangi bağlamda bir derleme içine bu mda'nın yüklendiğini belirlemek zordur.  
  
## <a name="cause"></a>Sebep  
 Genellikle, bir derleme içine yüklendi `LoadFrom` dışında bir yoldan yüklendiyse bağlam `Load` bağlamı, Genel Derleme Önbelleği gibi veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="resolution"></a>Çözüm  
 Uygulamaları yapılandır şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> çağrıları artık gerekli. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
-   Derlemeleri genel derleme önbelleğine yükleyin.  
  
-   Derlemelerde yerleştirin <xref:System.AppDomainSetup.ApplicationBase%2A> dizinini <xref:System.AppDomain>. Varsayılan etki alanı, söz konusu olduğunda <xref:System.AppDomainSetup.ApplicationBase%2A> işlemi başlatıldı yürütülebilir dosyayı içeren bir dizindir. Bu yeni oluşturma gerektirebilir <xref:System.AppDomain> derleme taşımak uygun değilse.  
  
-   Bağımlı derlemelerin yürütülebilir dosyanın göreli alt dizinlerde varsa araştırma yolu, uygulama (.config) yapılandırma dosyası veya ikincil bir uygulama etki alanları ekleyin.  
  
 Her durumda, kodu kullanmak için değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 MDA CLR üzerinde hiçbir etkisi yok. Bu, yük isteğin sonucu olarak kullanılan bağlam bildirir.  
  
## <a name="output"></a>Çıkış  
 MDA bütünleştirilmiş kod içine yüklenmiş olduğunu bildirdiği `LoadFrom` bağlamı. Bu, derleme ve yolun basit adını belirtir. Ayrıca kullanmaktan kaçınmak için risk azaltma işlemleri önerir `LoadFrom` bağlamı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu mda'nın etkinleştirebilmek için bir durum gösterilmektedir:  
  
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

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
