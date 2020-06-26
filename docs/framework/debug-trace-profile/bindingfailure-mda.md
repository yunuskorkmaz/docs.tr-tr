---
title: bindingFailure MDA
description: Bir derlemenin .NET 'te yüklenmemesi durumunda etkinleştirilen bindingFailure yönetilen hata ayıklama Yardımcısı (MDA) hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415634"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA

`bindingFailure`Yönetilen hata ayıklama Yardımcısı (MDA), bir derleme yükleme başarısız olduğunda etkinleştirilir.

## <a name="symptoms"></a>Belirtiler

Kod, statik başvuru veya ya da gibi Loader yöntemlerinden birini kullanarak bir derlemeyi yüklemeyi denedi <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> . Derleme yüklü değil ve bir <xref:System.IO.FileNotFoundException> veya <xref:System.IO.FileLoadException> özel durum oluşturuldu.

## <a name="cause"></a>Nedeni

Çalışma zamanı bir derlemeyi yükleyemediğinde bağlama hatası oluşur. Bir bağlama hatası, aşağıdaki durumlardan birinin sonucu olabilir:

- Ortak dil çalışma zamanı (CLR) istenen derlemeyi bulamıyor. Bunun gerçekleşebileceği, derlemenin yüklü olmadığı veya uygulamanın derlemeyi bulmak için doğru şekilde yapılandırılmadığı birçok nedeni vardır.

- Yaygın bir sorun senaryosu başka bir uygulama etki alanına bir tür geçirilerek, CLR 'nin diğer uygulama etki alanında bu türü içeren derlemeyi yüklemesi gerekir. Diğer uygulama etki alanı orijinal uygulama etki alanından farklı yapılandırılmışsa, çalışma zamanının derlemeyi yüklemesi mümkün olmayabilir. Örneğin, iki uygulama etki alanı farklı <xref:System.AppDomain.BaseDirectory%2A> özellik değerlerine sahip olabilir.

- İstenen derleme bozuk veya bir derleme değil.

- Derlemeyi yüklemeye çalışan kodun, derlemeleri yüklemek için doğru kod erişimi güvenlik izinleri yok.

- Kullanıcı kimlik bilgileri, dosyayı okumak için gerekli izinleri sağlamıyor.

## <a name="resolution"></a>Çözüm

İlk adım, CLR 'nin istenen derlemeye neden bağlanmadığını belirlemektir. Çalışma zamanının istenen derlemeyi (nedeni bölümünde listelenen senaryolar gibi) bulmamasının pek çok nedeni olabilir. Bağlama hatasının nedenini ortadan kaldırmak için aşağıdaki eylemler önerilir:

- MDA tarafından belirtilen verileri kullanarak nedenini belirleme `bindingFailure` :

  - Derleme cildi tarafından üretilen hata günlüklerini okumak için [Fuslogvw.exe (derleme bağlama günlük Görüntüleyicisi)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) çalıştırın.

  - Derlemenin istenen konumda olup olmadığını belirleme. Ve yöntemleri söz konusu olduğunda <xref:System.Reflection.Assembly.LoadFrom%2A> <xref:System.Reflection.Assembly.LoadFile%2A> , istenen konum kolayca belirlenebilir. <xref:System.Reflection.Assembly.Load%2A>Derleme kimliğini kullanarak bağlanan yöntemi söz konusu olduğunda, uygulama etki alanının <xref:System.AppDomain.BaseDirectory%2A> özellik araştırma yolu ve genel derleme önbelleğinde bu kimlikle eşleşen derlemeler için arama yapmanız gerekir.

- Önceki belirleme temelinde nedeni çözün. Olası çözüm seçenekleri şunlardır:

  - İstenen derlemeyi genel derleme önbelleğine yükleyip öğesini çağırın. <xref:System.Reflection.Assembly.Load%2A>derlemeyi kimliğe göre yükleme yöntemi.

  - İstenen derlemeyi uygulama dizinine kopyalayın ve <xref:System.Reflection.Assembly.Load%2A> derlemeyi kimliğe göre yüklemek için yöntemini çağırın.

  - <xref:System.AppDomain.BaseDirectory%2A>Özelliği değiştirerek ya da özel yoklama yolları ekleyerek, derleme yolunu dahil etmek için bağlama hatasının oluştuğu uygulama etki alanını yeniden yapılandırın.

  - Oturum açan kullanıcının dosyayı okumasına izin vermek için dosya için erişim denetim listesini değiştirin.

## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki

Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca bağlama hatalarıyla ilgili verileri raporlar.

## <a name="output"></a>Çıktı

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
