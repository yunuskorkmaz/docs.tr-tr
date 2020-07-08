---
title: loadFromContext MDA
description: .NET 'teki loadFromContext Managed hata ayıklama Yardımcısı 'nı (MDA), bir derleme LoadFrom bağlamına yüklenirse etkinleştirilir şekilde anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051655"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext`Bağlam içine bir derleme yüklenirse yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir `LoadFrom` . Bu durum, çağırma işleminin <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemlerin sonucu olarak ortaya çıkabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerinin kullanımı, derlemelerin bağlamda yüklenmesine neden olabilir `LoadFrom` . Bu bağlamın kullanılması serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir. Genel olarak, `Load` Bu sorunlardan kaçınmak için derlemelerin bağlamına yüklenmesi önerilir. Bir derlemenin Bu MDA ' dan ne şekilde yüklendiğini belirlemek zordur.  
  
## <a name="cause"></a>Nedeni  
 Genellikle, `LoadFrom` `Load` genel derleme önbelleği veya özelliği gibi bağlam dışındaki bir yoldan yüklenmişse, bir derleme bağlamına yüklenmiştir <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> .  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Reflection.Assembly.LoadFrom%2A>Çağrılara artık gerek duyulmayan uygulamalar için yapılandırma. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
- Derlemeleri genel bütünleştirilmiş kod önbelleğine yükler.  
  
- Derlemeleri <xref:System.AppDomainSetup.ApplicationBase%2A> için dizinine yerleştirin <xref:System.AppDomain> . Varsayılan etki alanı durumunda <xref:System.AppDomainSetup.ApplicationBase%2A> Dizin, işlemi başlatan yürütülebilir dosyayı içeren bir dosyadır. Bu, derlemeyi taşımak uygun değilse yeni bir oluşturma işlemi de gerektirebilir <xref:System.AppDomain> .  
  
- Bağımlı derlemeler çalıştırılabilire göre alt dizinlerde ise, uygulama yapılandırma (. config) dosyanıza veya ikincil uygulama etki alanlarına bir yoklama yolu ekleyin.  
  
 Her durumda, kod yöntemini kullanacak şekilde değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 MDA 'nin CLR üzerinde hiçbir etkisi yoktur. Yükleme isteğinin sonucu olarak kullanılan bağlamı bildirir.  
  
## <a name="output"></a>Çıktı  
 MDA, derlemenin bağlama göre yüklendiğini bildirir `LoadFrom` . Derlemenin basit adını ve yolunu belirtir. Ayrıca, bağlamını kullanmaktan kaçınmak için azaltıcı etkenleri de önerir `LoadFrom` .  
  
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
