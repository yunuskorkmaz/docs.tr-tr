---
title: C# programı yapısı - C# dili turu
description: C# programının temel yapı taşlarının öğrenin
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: dee24077f9f6287780320d979c44aef5230be81e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="program-structure"></a>Program Yapısı

C# anahtar kuruluş kavramlar ***programları***, ***ad alanları***, ***türleri***, ***üyeleri***, ve ***derlemeleri***. C# programları bir veya daha fazla kaynak dosyalarını oluşur. Programları üyeleri içerir ve ad alanında düzenlenebilir türleri bildirin. Sınıflar ve arabirimler türlerine örnek olarak verilebilir. Alanlar, yöntemleri, özellikleri ve olayları üyeleri gösterilebilir. C# programları derlendiğinde fiziksel olarak derlemelerine paketlenir. Derlemeler, genellikle dosya uzantısına sahip `.exe` veya `.dll`olup uyguladıkları bağlı olarak ***uygulamaları*** veya ***kitaplıkları***sırasıyla.

Adlı bir sınıf örneği bildirir `Stack` adlı bir ad alanındaki `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıf tam adı `Acme.Collections.Stack`. Sınıf birkaç üyeler içerir: adında bir alan `top`, adlı iki yöntem `Push` ve `Pop`ve adlı bir iç içe geçmiş sınıf `Entry`. `Entry` Daha fazla sınıf içerir üç üye: adında bir alan `next`, adında bir alan `data`hem de bir oluşturucu. Örneğin kaynak kodu dosyasına depolanan varsayılarak `acme.cs`, komut satırı

```
csc /t:library acme.cs
```

Örnek bir kitaplık olarak derler (olmadan kod bir `Main` giriş noktası) ve adlı bir derleme üretir `acme.dll`.

> [!IMPORTANT]
> Yukarıdaki kullanım örnekleri `csc` komut satırında C# Derleyici olarak. Bu derleyici yürütülebilir bir windows hizmetidir. C# diğer platformlarda kullanmak için .NET Core araçları kullanmanız gerekir. .NET Core ekosistemi kullanan `dotnet` komut satırı derlemeleri yönetmek için CLI. Bu bağımlılıklar yönetme ve C# derleyicisini çağırma içerir. Bkz: [Bu öğretici](../../core/tutorials/using-with-xplat-cli.md) araçların .NET Core tarafından desteklenen platformlardaki tam bir açıklaması.

Derlemeleri Ara dile (IL) yönergeleri biçiminde yürütülebilir kod ve meta veri biçiminde simgesel bilgilerini içerir. Çalıştırılmadan önce bir bütünleştirilmiş IL kodu işlemciye özgü kodu otomatik olarak .NET ortak dil çalışma zamanı Just-In-Time (JIT) derleyici tarafından dönüştürülür.

Bütünleştirilmiş kod ve meta verileri içeren işlevlerin kendiliğinden açıklayıcı bir birim olduğundan için gerek yoktur `#include` yönergeleri ve C# üstbilgi dosyaları. Genel türler ve belirli bir derlemesinde bulunan üyeleri program derlerken, derleme yalnızca başvurarak bir C# programı içinde kullanılabilir hale getirilir. Örneğin, bu programın kullandığı `Acme.Collections.Stack` sınıfıyla `acme.dll` derleme:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Program dosyada saklanıyorsa `example.cs`, `example.cs` olan derlenmiş, acme.dll derleme derleyicinin /r seçeneğini kullanarak başvurulabilir:

```
csc /r:acme.dll example.cs
```

Bu adlı bir yürütülebilir derleme oluşturur `example.exe`, çalıştırdığınızda, çıktı üretir:

```
100
10
1
```

C# kaynak metni birkaç kaynak dosyalarının depolanacağı bir programın izin verir. Çok dosyalı C# programı derlenmiş, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyaları serbestçe birbirine başvurabilir — kavramsal olarak, tüm kaynak dosyalarını tek bir büyük dosyaya işlenmeden önce art arda eklenmiş gibi değil. Çok az istisnalar bildirim sırasında Önemsiz olduğundan, iletme bildirimleri hiçbir zaman C# ' ta gereklidir. C#, yalnızca bir ortak türü bildirmek için bir kaynak dosyası sınırlamaz Ayrıca kaynak dosyasında bildirilen türüyle eşleşecek şekilde kaynak dosyasının adı gerektirir.

>[!div class="step-by-step"]
[Önceki](index.md)
[sonraki](types-and-variables.md)
