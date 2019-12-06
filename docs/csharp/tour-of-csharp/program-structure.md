---
title: C#Program yapısı- C# dilin turu
description: Bir C# programın temel yapı taşlarını öğrenin
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5e095e71549ed3eec6c73e6a134fdb5a64fb63c0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884390"
---
# <a name="program-structure"></a>Program Yapısı

' Deki C# temel kurumsal kavramlar, ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***. C#programlar bir veya daha fazla kaynak dosyadan oluşur. Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir. Sınıflar ve arabirimler tür örnekleridir. Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir. C# Programlar derlendiğinde, fiziksel olarak derlemeler halinde paketlenir. Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp uygulamadığına bağlı olarak dosya uzantısına `.exe` veya `.dll`sahiptir.

Örnek, `Acme.Collections`adlı bir ad alanında `Stack` adlı bir sınıf bildirir:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıfın tam nitelikli adı `Acme.Collections.Stack`. Sınıf birçok üye içerir: `top`adlı bir alan, `Push` ve `Pop`adlı iki yöntem ve `Entry`adlı bir iç içe sınıf. `Entry` sınıfı üç üye içerir: `next`adlı bir alan, `data`adlı bir alan ve bir Oluşturucu. Örneğin kaynak kodunun dosyada `acme.cs`, komut satırının

```console
csc /t:library acme.cs
```

örneği bir kitaplık (`Main` giriş noktası olmayan kod) olarak derler ve `acme.dll`adlı bir derleme oluşturur.

> [!IMPORTANT]
> Yukarıdaki örnekler, komut satırı C# derleyicisi olarak `csc` kullanır. Bu derleyici bir Windows yürütülebiliridir. Diğer platformlarda C# kullanmak Için .NET Core araçlarını kullanmanız gerekir. .NET Core ekosistemi, komut satırı yapılarını yönetmek için `dotnet` CLı kullanır. Buna bağımlılıkları yönetme ve C# derleyicinin çağrılması dahildir. .NET Core tarafından desteklenen platformlarda bu araçların tam açıklaması için [Bu öğreticiye](../../core/tutorials/cli-create-console-app.md) bakın.

Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir. Yürütülmeden önce, bir derlemedeki IL kodu, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi tarafından otomatik olarak işlemciye özgü koda dönüştürülür.

Bir derleme, hem kodu hem de meta verileri içeren bir işlevsellik birimi olduğundan, içinde C#`#include` yönergeler ve üst bilgi dosyaları gerekmez. Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye C# başvurarak bir programda kullanılabilir hale getirilir. Örneğin, bu program `acme.dll` derlemesinden `Acme.Collections.Stack` sınıfını kullanır:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Program dosyada depolanıyorsa, `example.cs` derlendiğinde `example.cs`Acme. dll derlemesine derleyicinin/r seçeneği kullanılarak başvurulabilir:

```console
csc /r:acme.dll example.cs
```

Bu, çalıştırılan `example.exe`adlı bir çalıştırılabilir derleme oluşturur ve bu, çalıştırıldığında çıktıyı üretir:

```console
100
10
1
```

C#bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir. Birden çok dosya C# programı derlendiğinde, tüm kaynak dosyalar birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir — kavramsal olarak, tüm kaynak dosyaları işlenmeden önce bir büyük dosyada birleştirilmiş olur. Bildirim sırası çok önemli olduğundan, C# bazı durumlarda ileri bildirimlere hiçbir şekilde gerek yoktur. C#kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adının kaynak dosyada belirtilen bir türle eşleşmesi gerekir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](types-and-variables.md)
