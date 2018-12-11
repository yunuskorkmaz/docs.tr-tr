---
title: C#Program yapısı - Turu C# dil
description: Temel yapı taşları hakkında bilgi edinin bir C# programı
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: de10cd000b4028a66ce6dd6f21e39c013e38ecd2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131033"
---
# <a name="program-structure"></a>Program Yapısı

C# anahtar kuruluş kavramlar ***programlar***, ***ad alanları***, ***türleri***, ***üyeleri***, ve ***derlemeleri***. C# programları, bir veya daha fazla kaynak dosyadan oluşur. Programları üyeleri içerir ve ad alanları olarak düzenlenmiş türleri bildirin. Sınıflar ve arabirimler türleri örnekleridir. Alanlar, yöntemler, özellikler ve olaylar üyeleri örnekleridir. C# programları derlendiğinde, bunlar derlemelerine fiziksel olarak paketlenir. Derlemeler genellikle dosya uzantısına sahip `.exe` veya `.dll`uyguladıkları mi bağlı olarak ***uygulamaları*** veya ***kitaplıkları***sırasıyla.

Örnek adlı bir sınıfı bildirir `Stack` adlı bir ad alanında `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıfın tam adı `Acme.Collections.Stack`. Sınıf bazı üyeler içerir: adlı bir alan `top`, adlı iki yöntem `Push` ve `Pop`ve bir iç içe geçmiş sınıf adlı `Entry`. `Entry` Sınıfı daha da içeren üç üye: adlı bir alan `next`, adında bir alan `data`ve bir oluşturucu. Örnek kaynak kodu dosyasında depolanan varsayarak `acme.cs`, komut satırı

```
csc /t:library acme.cs
```

Örnek bir kitaplık olarak derler (olmadan kod bir `Main` giriş noktası) adlı bir derleme oluşturur `acme.dll`.

> [!IMPORTANT]
> Kullanım Yukarıdaki örneklerde `csc` komut satırı olarak C# derleyici. Bir Windows yürütülebilir derleyicisidir. Kullanılacak C# diğer platformlarda için .NET Core Araçları'nı kullanmanız gerekir. .NET Core ekosistemi kullanan `dotnet` komut satırı yapıları yönetmek için CLI. Bu bağımlılıkları yönetmek ve çağırma içerir C# derleyici. Bkz: [Bu öğreticide](../../core/tutorials/using-with-xplat-cli.md) .NET Core tarafından desteklenen platformlarda, araçlarda tam bir açıklaması.

Derlemeleri yürütülebilir kod biçiminde Ara dil (IL) yönergeleri ve simgesel bilgiler meta veri biçiminde içerir. Çalıştırılmadan önce bir derlemede IL kodu işlemciye özgü kodu .NET ortak dil çalışma zamanı tam zamanında (JIT) derleyici tarafından otomatik olarak dönüştürülür.

Bir derleme kendiliğinden açıklayıcı bir işlevsellik hem kod hem de meta verileri içeren birimi olduğundan için gerek yoktur `#include` yönergeleri ve C# üst bilgi dosyaları. Genel türler ve üyeler belirli bir derlemede bulunan program derlerken bu derlemeye yalnızca başvurarak bir C# programı içinde kullanılabilir hale getirilir. Örneğin, bu programın kullandığı `Acme.Collections.Stack` gelen sınıfı `acme.dll` derleme:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Program dosyada saklanıyorsa `example.cs`, `example.cs` olduğundan derlenemiyor; acme.dll derleme derleyicinin /r seçeneği kullanılarak başvurulabilir:

```
csc /r:acme.dll example.cs
```

Bu adında bir yürütülebilir bir derleme oluşturur `example.exe`, çalıştırdığınızda, çıktıyı üretir:

```
100
10
1
```

C# kaynak metni bir programın çeşitli kaynak dosyalarında depolanan izin verir. Çok dosyalı C# programı derlenir, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyaları serbestçe birbirlerine başvurabilir — kavramsal olarak, tüm kaynak dosyalarını tek bir büyük dosyaya işlenmeden önce art arda eklenmiş gibi öyledir. Çok az sayıda özel durum dışında bildirim sırasında Önemsiz olduğundan, iletme bildirimleri hiçbir zaman C# ' de gereklidir. C#, yalnızca bir genel türü bildirmek için bir kaynak dosyası sınırlamaz veya kaynak dosyada bildirilen bir tür ile eşleştirilecek kaynak dosyasının adı gerektirir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](types-and-variables.md)