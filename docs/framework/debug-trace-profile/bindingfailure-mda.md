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
ms.openlocfilehash: 93c426cce792c8f30a3551e2d4626736dd67278f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052952"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA

Yönetilen `bindingFailure` hata ayıklama Yardımcısı (MDA), bir derleme yükleme başarısız olduğunda etkinleştirilir.

## <a name="symptoms"></a>Belirtiler

Kod, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> statik başvuru veya ya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>da gibi Loader yöntemlerinden birini kullanarak bir derlemeyi yüklemeyi denedi. Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durum oluşturuldu.

## <a name="cause"></a>Sebep

Çalışma zamanı bir derlemeyi yükleyemediğinde bağlama hatası oluşur. Bir bağlama hatası, aşağıdaki durumlardan birinin sonucu olabilir:

- Ortak dil çalışma zamanı (CLR) istenen derlemeyi bulamıyor. Bunun gerçekleşebileceği, derlemenin yüklü olmadığı veya uygulamanın derlemeyi bulmak için doğru şekilde yapılandırılmadığı birçok nedeni vardır.

- Yaygın bir sorun senaryosu başka bir uygulama etki alanına bir tür geçirilerek, CLR 'nin diğer uygulama etki alanında bu türü içeren derlemeyi yüklemesi gerekir. Diğer uygulama etki alanı orijinal uygulama etki alanından farklı yapılandırılmışsa, çalışma zamanının derlemeyi yüklemesi mümkün olmayabilir. Örneğin, iki uygulama etki alanı farklı <xref:System.AppDomain.BaseDirectory%2A> özellik değerlerine sahip olabilir.

- İstenen derleme bozuk veya bir derleme değil.

- Derlemeyi yüklemeye çalışan kodun, derlemeleri yüklemek için doğru kod erişimi güvenlik izinleri yok.

- Kullanıcı kimlik bilgileri, dosyayı okumak için gerekli izinleri sağlamıyor.

## <a name="resolution"></a>Çözüm

İlk adım, CLR 'nin istenen derlemeye neden bağlanmadığını belirlemektir. Çalışma zamanının istenen derlemeyi (nedeni bölümünde listelenen senaryolar gibi) bulmamasının pek çok nedeni olabilir. Bağlama hatasının nedenini ortadan kaldırmak için aşağıdaki eylemler önerilir:

- `bindingFailure` Mda tarafından belirtilen verileri kullanarak nedenini belirleme:

  - Derleme cildi tarafından üretilen hata günlüklerini okumak için [Fuslogvw. exe ' yi (derleme bağlama günlük Görüntüleyici)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) çalıştırın.

  - Derlemenin istenen konumda olup olmadığını belirleme. <xref:System.Reflection.Assembly.LoadFrom%2A> Ve<xref:System.Reflection.Assembly.LoadFile%2A> yöntemleri söz konusu olduğunda, istenen konum kolayca belirlenebilir. Derleme kimliğini kullanarak bağlanan <xref:System.Reflection.Assembly.Load%2A> yöntemi söz konusu olduğunda, uygulama <xref:System.AppDomain.BaseDirectory%2A> etki alanının özellik araştırma yolu ve genel derleme önbelleğinde bu kimlikle eşleşen derlemeler için arama yapmanız gerekir.

- Önceki belirleme temelinde nedeni çözün. Olası çözüm seçenekleri şunlardır:

  - İstenen derlemeyi genel derleme önbelleğine yükleyip öğesini çağırın. <xref:System.Reflection.Assembly.Load%2A>derlemeyi kimliğe göre yükleme yöntemi.

  - İstenen derlemeyi uygulama dizinine kopyalayın ve derlemeyi kimliğe göre yüklemek için <xref:System.Reflection.Assembly.Load%2A> yöntemini çağırın.

  - <xref:System.AppDomain.BaseDirectory%2A> Özelliği değiştirerek ya da özel yoklama yolları ekleyerek, derleme yolunu dahil etmek için bağlama hatasının oluştuğu uygulama etki alanını yeniden yapılandırın.

  - Oturum açan kullanıcının dosyayı okumasına izin vermek için dosya için erişim denetim listesini değiştirin.

## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki

Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca bağlama hatalarıyla ilgili verileri raporlar.

## <a name="output"></a>Çıkış

MDA, istenen yol ve/veya görünen ad, bağlama bağlamı, yükün istendiği uygulama etki alanı ve hatanın nedeni dahil olmak üzere, yükleme başarısız olan derlemeyi rapor ediyor.

Görünen ad veya istenen yol, verilerin CLR tarafından kullanılamadığı durumlarda boş olabilir. Başarısız olan çağrı <xref:System.Reflection.Assembly.Load%2A> yöntemi ise, çalışma zamanının derleme için görünen adı belirleyememe olasıdır.

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:

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

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
