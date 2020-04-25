---
title: C# Program yapısı-C# dilinin turu
description: C# programının temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141022"
---
# <a name="program-structure"></a>Program Yapısı

C# ' deki temel kurumsal kavramlar ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***. C# programları bir veya daha fazla kaynak dosyadan oluşur. Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir. Sınıflar ve arabirimler tür örnekleridir. Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir. C# programları derlendiğinde, fiziksel olarak derlemeler halinde paketlenir. Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp `.dll`uygulamadığına bağlı olarak, genellikle dosya uzantısına `.exe` sahiptir.

Komutunu kullanarak Acme adlı bir kitaplık projesi oluşturabilirsiniz: *acme* `dotnet new`

```dotnetcli
dotnet new classlib -o acme
```

Bu projede adlı bir ad alanında adında `Stack` bir sınıf bildirin: `Acme.Collections`

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıfın tam adı `Acme.Collections.Stack`. Sınıf birçok üye `top`içerir: adlı bir alan, `Push` ve `Pop`adlı iki yöntem ve adlı `Entry`bir iç içe sınıf. `Entry` Sınıf daha fazla üç üye içerir: adlı `next`alan, adlı `data`alan ve Oluşturucu. Komut:

```dotnetcli
dotnet build
```

örneği bir kitaplık (bir `Main` giriş noktası olmayan kod) olarak derler ve adında `acme.dll`bir derleme oluşturur.

Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir. Yürütülmeden önce, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi, bir derlemedeki Il kodunu işlemciye özel koda dönüştürür.

Bir derleme, hem kodu hem de meta verileri içeren işlevsellikten oluşan bir birim olduğundan, C# dilinde `#include` yönergeler ve başlık dosyaları gerekmez. Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye başvurarak bir C# programında kullanılabilir hale getirilir. Örneğin, bu program `Acme.Collections.Stack` `acme.dll` derlemeden sınıfını kullanır:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Önceki programın projesi için *csproj* dosyası, `acme.dll` derlemede bulunan sınıflara yönelik başvuruları çözümlemek üzere C# derleyicisi için bir başvuru düğümü içermelidir:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Bu eklemeyi tamamladıktan sonra `dotnet build` adlı `example.exe`bir çalıştırılabilir derleme oluşturur, bu, çalıştırıldığında çıktıyı üretir:

```dotnetcli
100
10
1
```

C#, bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir. Çok sayfalı bir C# programı derlendiğinde, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir. kavramsal olarak, tüm kaynak dosyaları işlenmek üzere bir büyük dosyada birleştirilmiş olur. Birkaç özel durum dışında, bildirim sırası çok önemli olduğundan, C# ' ta ileri bildirimlere hiçbir şekilde gerek yoktur. C#, kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adını kaynak dosyada belirtilen bir türle eşleşecek şekilde gerektirmez.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](types-and-variables.md)
