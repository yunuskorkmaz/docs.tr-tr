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
ms.openlocfilehash: 89605a119e8251ffd577ff402366dff0fd4af4d7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052512"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
Bağlam içine bir derleme yüklenirse yönetilenhataayıklamaYardımcısı(MDA)etkinleştirilir.`loadFromContext` `LoadFrom` Bu durum, çağırma <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> işleminin veya diğer benzer yöntemlerin sonucu olarak ortaya çıkabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerinin kullanımı, derlemelerin bağlamda `LoadFrom` yüklenmesine neden olabilir. Bu bağlamın kullanılması serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir. Genel olarak, bu sorunlardan kaçınmak için derlemelerin `Load` bağlamına yüklenmesi önerilir. Bir derlemenin Bu MDA ' dan ne şekilde yüklendiğini belirlemek zordur.  
  
## <a name="cause"></a>Sebep  
 Genellikle, `LoadFrom` genelderleme`Load` önbelleği veya özelliğigibibağlamdışındakibiryoldanyüklenmişse,birderlemebağlamınayüklenmiştir.<xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Reflection.Assembly.LoadFrom%2A> Çağrılara artık gerek duyulmayan uygulamalar için yapılandırma. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
- Derlemeleri genel bütünleştirilmiş kod önbelleğine yükler.  
  
- <xref:System.AppDomainSetup.ApplicationBase%2A> Derlemeleri<xref:System.AppDomain>için dizinine yerleştirin. Varsayılan etki alanı <xref:System.AppDomainSetup.ApplicationBase%2A> durumunda Dizin, işlemi başlatan yürütülebilir dosyayı içeren bir dosyadır. Bu, derlemeyi taşımak uygun değilse yeni <xref:System.AppDomain> bir oluşturma işlemi de gerektirebilir.  
  
- Bağımlı derlemeler çalıştırılabilire göre alt dizinlerde ise, uygulama yapılandırma (. config) dosyanıza veya ikincil uygulama etki alanlarına bir yoklama yolu ekleyin.  
  
 Her durumda, kod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullanacak şekilde değiştirilebilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 MDA 'nin CLR üzerinde hiçbir etkisi yoktur. Yükleme isteğinin sonucu olarak kullanılan bağlamı bildirir.  
  
## <a name="output"></a>Çıkış  
 MDA, derlemenin `LoadFrom` bağlama göre yüklendiğini bildirir. Derlemenin basit adını ve yolunu belirtir. Ayrıca, `LoadFrom` bağlamını kullanmaktan kaçınmak için azaltıcı etkenleri de önerir.  
  
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
