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
ms.openlocfilehash: 663ceda1c0621e1152e795db79c3953be0090d5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681800"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA
`bindingFailure` Yönetilen hata ayıklama Yardımcısı (MDA) yüklemek bir derleme başarısız olduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Kod gibi statik başvuru veya yükleyici yöntemlerden birini kullanarak bir derlemeyi yüklemek denediğini <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durumu oluşturulur.  
  
## <a name="cause"></a>Sebep  
 Çalışma zamanının bir derlemeyi yükleyemedi bağlama hatası gerçekleşir. Bağlama hatası sonucu aşağıdaki durumlardan biri olabilir:  
  
-   Ortak dil çalışma zamanı (CLR), istenen derlemesi bulunamıyor. Bu, yüklü derleme veya derleme bulmak için düzgün yapılandırılmamış uygulama gibi oluşabilir birçok neden vardır.  
  
-   Ortak bir sorunu senaryosu, diğer uygulama etki alanında bu türü içeren derlemenin yüklenecek CLR gerektiren başka bir uygulama etki alanına bir tür geçiyor. Bu, diğer uygulama etki alanı özgün uygulama etki alanından farklı şekilde yapılandırılmışsa, derlemeyi yüklemeye çalışma zamanı için mümkün olmayabilir. Örneğin, iki uygulama etki alanları farklı olabilir <xref:System.AppDomain.BaseDirectory%2A> özellik değerleri.  
  
-   İstenen derleme bozuk veya bir derleme değil.  
  
-   Bütünleştirilmiş kod yüklemeye çalışan kod derlemeleri yüklemek için doğru kod erişimi güvenliği izinleri yok.  
  
-   Kullanıcı kimlik bilgileri, dosyayı okumak için gerekli izinlere sağlamaz.  
  
## <a name="resolution"></a>Çözüm  
 İlk adım, neden CLR istenen derlemeye bağlanamadı belirlemektir. Neden çalışma zamanı bulunamadı veya olabilirsiniz senaryoları gibi istenen derleme nedeni bölümünde listelenen mümkün yük olan birçok neden vardır. Bağlama hatanın nedenini ortadan kaldırmak için aşağıdaki eylemleri önerilir:  
  
-   Tarafından sağlanan verileri kullanarak nedenini `bindingFailure` MDA:  
  
    -   Çalıştırma [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) derleme cildiyle üretilen hata günlüklerini okumak için.  
  
    -   Derleme için istenen konumu olup olmadığını belirler. Durumunda, <xref:System.Reflection.Assembly.LoadFrom%2A> ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri, istenen konumu kolayca belirlenebilir. Durumunda, <xref:System.Reflection.Assembly.Load%2A> derleme kimliği kullanarak bağlanan, yöntem, gerekir arayın uygulama etki alanının içinde bu kimlikle eşleşen derlemeleri <xref:System.AppDomain.BaseDirectory%2A> özellik araştırma yolu ve genel derleme önbelleği.  
  
-   Önceki belirlemeye dayalı nedenini çözümleyin. Olası çözüm seçenekleri şunlardır:  
  
    -   İstenen derlemeyi genel bütünleştirilmiş kod önbelleğine ve çağrı yükleyin. <xref:System.Reflection.Assembly.Load%2A> derleme kimliği tarafından yükleme yöntemi.  
  
    -   İstenen derleme arama ve uygulama dizini kopyalamak <xref:System.Reflection.Assembly.Load%2A> yöntemi tarafından kimlik derlemesi yüklenemiyor.  
  
    -   Uygulama etki bağlama hatası oluştuğu derleme yolu ya da değiştirerek içerecek şekilde yeniden <xref:System.AppDomain.BaseDirectory%2A> özelliği veya özel bir yoklama yolu ekleme.  
  
    -   Dosyayı okumak oturum açan kullanıcının izin vermek bir dosya için erişim denetim listesini değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca hataları bağlama hakkında veri bildirir.  
  
## <a name="output"></a>Çıkış  
 İstenen yol dahil olmak üzere, yük ve/veya görünen adı, bağlama bağlamı, yükü istenen uygulama etki alanı için başarısız olan derlemenin ve hatanın nedenini MDA bildirir.  
  
 Görünen ad veya istenen yol verileri CLR için kullanılabilir değilse boş olabilir. Başarısız olan çağrı ise <xref:System.Reflection.Assembly.Load%2A> yöntemi, bu büyük olasılıkla çalışma zamanı derlemenin görünen adı belirleyemedi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu mda'nın etkinleştirebilmek için bir durum gösterilmektedir:  
  
```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
