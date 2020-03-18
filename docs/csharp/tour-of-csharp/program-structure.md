---
title: C# Program Yapısı - C# Dili Turu
description: C# programının temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156837"
---
# <a name="program-structure"></a>Program Yapısı

C#'daki temel kuruluş kavramları ***programlar,*** ***ad alanları,*** ***türleri,*** ***üyeler***ve ***derlemelerdir.*** C# programları bir veya daha fazla kaynak dosyadan oluşur. Programlar, üye içeren ve ad boşlukları halinde düzenlenebilecek türleri bildirir. Sınıflar ve arabirimler türleri örnekleridir. Alanlar, yöntemler, özellikler ve olaylar üye örnekleridir. C# programları derlendiğinde, fiziksel olarak derlemelere paketlenirler. Derlemeler genellikle dosya uzantısı `.exe` `.dll`na sahip veya ***sırasıyla uygulamaları*** veya ***kitaplıkları***uygulayıp uygulamadıklarına bağlı olarak.

Komutu kullanarak acme adlı bir kitaplık projesi oluşturabilirsiniz: *acme* `dotnet new`

```console
dotnet new classlib -o acme
```

Bu projede, ad `Stack` alanında adı geçen `Acme.Collections`bir sınıf bildirin:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıfın tam nitelikli `Acme.Collections.Stack`adı . Sınıf birkaç üye içerir: `top`adlı bir `Push` alan, adlı iki yöntem ve `Pop`, adlı iç içe sınıf `Entry`. Sınıf `Entry` daha üç üye içerir: `next`adlı bir `data`alan , adlı bir alan , ve bir oluşturucu. Komut:

```console
dotnet build
```

örneği kitaplık olarak derler `Main` (giriş noktası olmayan kod) `acme.dll`ve adlı bir derleme oluşturur.

Derlemeler, Ara Dil (IL) yönergeleri biçiminde yürütülebilir kod ve meta veri biçiminde sembolik bilgiler içerir. Yürütülmeden önce,.NET Ortak Dil Runtime'ın Just-In-Time (JIT) derleyicisi, bir derlemedeki IL kodunu işlemciye özgü koda dönüştürür.

Derleme, hem kod hem de meta verileri içeren kendi kendini tanımlayan bir `#include` işlevsellik birimi olduğundan, C#'da yönergelere ve üstbilgi dosyalarına gerek yoktur. Belirli bir derlemede yer alan genel türler ve üyeler, yalnızca programı derlerken bu derlemeye başvurarak C# programında kullanılabilir hale getirilir. Örneğin, bu program `Acme.Collections.Stack` `acme.dll` derleme den sınıf kullanır:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Önceki programın projesiiçin *csproj* `acme.dll` dosyası, derlemedeki sınıflara yapılan başvuruları çözmek için C# derleyicisi için bir başvuru düğümü içermelidir:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Bu eklemeden `dotnet build` sonra, çalıştırıldığında `example.exe`çıktıüreten , "çalıştırılabilir" adlı bir yürütülebilir derleme oluşturur:

```console
100
10
1
```

C# bir programın kaynak metninin çeşitli kaynak dosyalarda depolanabına izin verir. Çok dosyalı bir C# programı derlendiğinde, tüm kaynak dosyaları birlikte işlendiğinde ve kaynak dosyaları serbestçe birbirlerine referans verebilirsiniz-kavramsal olarak, tüm kaynak dosyaları işlenmeden önce büyük bir dosyaya entegre edilmiş gibidir. Birkaç istisna dışında bildirim sırası önemsiz olduğundan, C#'da iletme bildirimleri hiçbir zaman gerekli değildir. C# bir kaynak dosyayı yalnızca bir ortak türü bildirmekle sınırlamaz veya kaynak dosyada bildirilen bir türle eşleşecek şekilde kaynak dosyanın adını gerektirmez.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](types-and-variables.md)
