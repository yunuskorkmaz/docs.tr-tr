---
title: loadFromContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acd8291eda97caee72de4632f8715e6211deb7a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
`loadFromContext` Yönetilen hata ayıklama Yardımcısı (MDA), bir derleme halinde yüklenmiş ise etkinleştirilirse `LoadFrom` bağlamı. Çağırma sonucunda bu durum ortaya çıkabilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya benzer diğer yöntemleri.  
  
## <a name="symptoms"></a>Belirtiler  
 Bazı yükleyici yöntemlerinin kullanımını, yüklenmekte olan derlemelerde sonuçlanabilir `LoadFrom` bağlamı. Bu bağlamda kullanımını seri hale getirme, atama ve bağımlılık çözünürlüğü için beklenmeyen davranışlara neden olabilir. Genel olarak, derlemeler halinde yüklenen önerilir `Load` bu sorunları önlemek için bağlam. Hangi bağlamı bir derleme halinde bu MDA yüklendi belirlemek zordur.  
  
## <a name="cause"></a>Sebep  
 Genellikle, bir derleme halinde yüklendi `LoadFrom` dışında bir yoldan yüklerse bağlam `Load` bağlamı, Genel Derleme Önbelleği gibi veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="resolution"></a>Çözüm  
 Uygulamaları yapılandır şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> çağrıları artık gerekli. Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:  
  
-   Derlemeleri genel derleme önbelleğinde yükleyin.  
  
-   Yerleştirin derlemelerde <xref:System.AppDomainSetup.ApplicationBase%2A> için dizin <xref:System.AppDomain>. Varsayılan etki alanı olması durumunda <xref:System.AppDomainSetup.ApplicationBase%2A> işlemi başlatıldı çalıştırılabilir dosyayı içeren bir dizindir. Bu yeni oluşturma gerektirebilir <xref:System.AppDomain> derleme taşımak uygun değilse.  
  
-   Bağımlı derlemeleri yürütülebilir göre alt dizinlerde varsa bir yoklama yolu uygulama yapılandırması (.config) dosyası ya da ikincil uygulama etki alanları ekleyin.  
  
 Her durumda kullanmak için kodu değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 MDA CLR herhangi bir etkisi yok. Bir yük istek kullanılan bağlam bildirir.  
  
## <a name="output"></a>Çıkış  
 MDA derleme içine yüklenmiş olduğunu bildirdiği `LoadFrom` bağlamı. Derleme ve yolun basit adını belirtir. Ayrıca kullanmaktan kaçınmak için Azaltıcı Etkenler öneren `LoadFrom` bağlamı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir:  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
