---
title: C#Program yapısı- C# dilin turu
description: Bir C# programın temel yapı taşlarını öğrenin
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159123"
---
# <a name="program-structure"></a>Program Yapısı

' Deki C# temel kurumsal kavramlar, ***Programlar***, ***ad alanları***, ***türler***, ***Üyeler***ve ***derlemelerdir***. C#programlar bir veya daha fazla kaynak dosyadan oluşur. Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir. Sınıflar ve arabirimler tür örnekleridir. Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir. C# Programlar derlendiğinde, fiziksel olarak derlemeler halinde paketlenir. Derlemeler, sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp uygulamadığına bağlı olarak dosya uzantısına `.exe` veya `.dll`sahiptir.

`dotnet new` komutunu kullanarak *Acme* adlı bir kitaplık projesi oluşturabilirsiniz:

```console
dotnet new classlib -o acme
```

Bu projede, `Acme.Collections`adlı bir ad alanında `Stack` adlı bir sınıf bildirin:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Bu sınıfın tam nitelikli adı `Acme.Collections.Stack`. Sınıf birçok üye içerir: `top`adlı bir alan, `Push` ve `Pop`adlı iki yöntem ve `Entry`adlı bir iç içe sınıf. `Entry` sınıfı üç üye içerir: `next`adlı bir alan, `data`adlı bir alan ve bir Oluşturucu. Komut:

```console
dotnet build 
```

örneği bir kitaplık (`Main` giriş noktası olmayan kod) olarak derler ve `acme.dll`adlı bir derleme oluşturur.

Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir. Yürütülmeden önce, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi, bir derlemedeki Il kodunu işlemciye özel koda dönüştürür.

Bir derleme, hem kodu hem de meta verileri içeren bir işlevsellik birimi olduğundan, içinde C#`#include` yönergeler ve başlık dosyaları gerekmez. Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye C# başvurarak bir programda kullanılabilir hale getirilir. Örneğin, bu program `acme.dll` derlemesinden `Acme.Collections.Stack` sınıfını kullanır:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Önceki programın projesi için *csproj* dosyası, `acme.dll` derlemesindeki sınıfların başvurularını çözümlemek için C# derleyicinin başvuru düğümünü içermelidir:

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Bu eklendikten sonra, `dotnet build` `example.exe`adında bir çalıştırılabilir derleme oluşturur ve bu, çalıştırıldığında çıktıyı üretir:

```console
100
10
1
```

C#bir programın kaynak metninin birkaç kaynak dosyada depolanmasına izin verir. Birden çok dosya C# programı derlendiğinde, tüm kaynak dosyalar birlikte işlenir ve kaynak dosyalar birbirini tamamen başvurabilir — kavramsal olarak, tüm kaynak dosyaları işlenmeden önce bir büyük dosyada birleştirilmiş olur. Bildirim sırası çok önemli olduğundan, C# bazı özel durumlarla birlikte iletme bildirimlerine hiçbir şekilde gerek yoktur. C#kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adının kaynak dosyada belirtilen bir türle eşleşmesi gerekir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](types-and-variables.md)
