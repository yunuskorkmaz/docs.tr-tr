---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a75efaf6703858fdb48a3f09635da1be4463d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA
`bindingFailure` Yönetilen hata ayıklama Yardımcısı (MDA), bir derlemeyi yüklemek başarısız olduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Kod gibi statik başvuru veya yükleyici yöntemlerden birini kullanarak bir derlemeyi yüklemeye çalıştı <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durumu oluşur.  
  
## <a name="cause"></a>Sebep  
 Çalışma zamanı bütünleştirilmiş yükleyemiyor bağlama hatası oluşur. Bağlama hatası nedeni aşağıdaki durumlardan biri olabilir:  
  
-   Ortak dil çalışma zamanı (CLR) istenen derlemesi bulunamıyor. Bu, yüklenmiyor derleme veya derleme bulmak için düzgün yapılandırılmamış uygulama gibi oluşabilir pek çok neden vardır.  
  
-   Yaygın bir sorun senaryo, başka bir uygulama etki alanında o türünü içeren bütünleştirilmiş CLR gerektiren başka bir uygulama etki alanına bir türü geçiyor. Bu, başka bir uygulama etki alanı özgün uygulama etki alanından farklı şekilde yapılandırılmışsa derlemeyi yüklemeye çalışma zamanı için mümkün olmayabilir. Örneğin, iki uygulama etki alanları farklı olabilir <xref:System.AppDomain.BaseDirectory%2A> özellik değerleri.  
  
-   İstenen derlemeyi bozuk veya bir derleme değil.  
  
-   Derleme yüklenmeye çalışılıyor kod derlemelerini yüklemek için doğru kod erişim güvenliği izinleri yok.  
  
-   Kullanıcı kimlik bilgileri dosyasını okumak için gerekli izinleri sağlamaz.  
  
## <a name="resolution"></a>Çözüm  
 İlk adım, neden CLR istenen derlemeye bağlanamadı belirlemektir. Neden çalışma zamanı bulunamadı veya olabilirsiniz senaryoları gibi istenen derlemeyi neden bölümünde listelenen mümkün yük edilmiş pek çok neden vardır. Aşağıdaki eylemleri bağlama hatanın nedenini ortadan kaldırmak için önerilir:  
  
-   Tarafından sağlanan verileri kullanarak nedenini `bindingFailure` MDA:  
  
    -   Çalıştırma [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) derleme bağlayıcı tarafından üretilen hata günlüklerini okumak için.  
  
    -   Derleme istenen konumda olup olmadığını belirler. Durumunda <xref:System.Reflection.Assembly.LoadFrom%2A> ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri, istenilen konuma kolayca belirlenebilir. Durumunda <xref:System.Reflection.Assembly.Load%2A> derleme kimliğini kullanarak bağlar, yöntem, gerekir Ara uygulama etki alanı içinde bu kimliğiyle eşleşmesi derlemeleri <xref:System.AppDomain.BaseDirectory%2A> özellik araştırma yolu ve genel derleme önbelleği.  
  
-   Önceki belirleme temel nedenini çözümleyin. Olası bir çözüm seçenekleri şunlardır:  
  
    -   İstenen derlemeyi genel derleme önbelleği ve çağrı yükleyin. <xref:System.Reflection.Assembly.Load%2A> derleme kimliği tarafından yükleme yöntemi.  
  
    -   İstenen derlemeyi uygulama dizini ve çağrı kopyalamak <xref:System.Reflection.Assembly.Load%2A> yöntemi kimliği tarafından derlemesi yüklenemedi.  
  
    -   Bağlama hatası oluştuğu ya da değiştirerek derleme yolu eklemek için uygulama etki alanı yeniden <xref:System.AppDomain.BaseDirectory%2A> özelliği veya özel araştırma yollar ekleme.  
  
    -   Oturum açmış kullanıcının dosyayı okuma izni dosya için erişim denetim listesini değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca hataları bağlama hakkında verileri raporlar.  
  
## <a name="output"></a>Çıkış  
 İstenen yol dahil olmak üzere, yükleme ve/veya görüntüleme adı, bağlama bağlamı, yükleme istendi uygulama etki alanı için başarısız olan derlemenin ve hatanın nedenini MDA raporlar.  
  
 Görünen adı ya da istenen yol verileri CLR kullanılabilir değilse boş olabilir. Başarısız olan çağrı yapmak ise <xref:System.Reflection.Assembly.Load%2A> yöntemi, bu olası çalışma zamanı derlemesi için görünen ad belirleyemedi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir:  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
