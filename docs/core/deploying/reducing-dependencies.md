---
title: project.json ile Paket Bağımlılıklarını Azaltma
description: project.json tabanlı kitaplıkları yazarken paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740831"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>project.json ile Paket Bağımlılıklarını Azaltma

Bu makalede, `project.json` kitaplıklar yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gerekenler yer almaktadır. Bu makalenin sonunda, kitaplığınızı yalnızca gereksinimleri olan bağımlılıkları kullanacak şekilde nasıl oluşturacağınızı öğreneceksiniz.

## <a name="why-its-important"></a>Neden Önemli

.NET Core, NuGet paketlerinden oluşan bir üründür.  Önemli bir paket [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), diğer paketlerden oluşan bir NuGet paketidir. .NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulaması üzerinde çalışması garanti edilen paket kümesini sağlar.

Ancak, kitaplığınuzun içerdiği her paketi kullanmama olasılığı yüksektir.  Bir kitaplık yazarken ve NuGet üzerinden dağıtırken, bağımlılıklarınızı yalnızca kullandığınız paketlere "kırpmak" en iyi yöntemdir.  Bu, NuGet paketleri için daha küçük bir genel ayak izi sağlar.

## <a name="how-to-do-it"></a>Nasıl yapılacağını

Şu anda, `dotnet` paket başvurularını kesen resmi bir komut yoktur.  Bunun yerine, el ile yapmanız gerekir.  Genel süreç aşağıdaki gibi görünür:

1. Bir `NETStandard.Library` `1.6.0` `dependencies` bölümünde referans sürümü `project.json`.
2. Paketleri komut `dotnet restore` satırından[(nota bakınız)](#dotnet-restore-note)geri yükleyin.
3. Dosyayı `project.lock.json` inceleyin `NETStandard.Library` ve bölümü bulun.  Dosyanın başına yakın.
4. Listelenen tüm paketleri aşağıdaki `dependencies`gibi kopyalayın.
5. Başvuruyu `.NETStandard.Library` kaldırın ve kopyalanan paketlerle değiştirin.
6. İhtiyacınız olmayan paketlere yapılan başvuruları kaldırın.

Hangi paketlere ihtiyacınız olmadığını aşağıdaki yollardan biriyle öğrenebilirsiniz:

1. Deneme yanılma. Bu, bir paketi kaldırmayı, geri toplamayı, kitaplığınızın hala derleyip derlemediğini görmeyi ve bu işlemi yinelemeyi içerir.
2. KODUnuzun gerçekte ne kullandığını görmek için referanslara göz atmak için [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflektör](https://www.red-gate.com/products/dotnet-development/reflector) gibi bir araç kullanmak. Ardından, kullandığınız türe uymayan paketleri kaldırabilirsiniz.

## <a name="example"></a>Örnek

Genel koleksiyon türlerine ek işlevsellik sağlayan bir kitaplık yazdığınızı düşünün. Böyle bir kitaplığın `System.Collections`, , ancak hiç de. `System.Net.Http` Bu nedenle, paket bağımlılıklarını yalnızca bu kütüphanenin gerektirdiği şekilde kırpmak iyi olurdu!

Bu kitaplığı kırpmak `project.json` için, dosyayla başlar `NETStandard.Library` `1.6.0`ve sürüme bir başvuru eklersiniz.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

`dotnet restore` Daha sonra, paketleri geri yükleyin ([nota bakınız),](#dotnet-restore-note)dosyayı `project.lock.json` inceler ve tüm paketleri geri `NETStandard.Library`yükleyin.

Dosyadaki `project.lock.json` ilgili bölümün hedefleme yaparken nasıl göründüğü `netstandard1.0`aşağıda veda edin:

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Ardından, paket başvurularının üzerine `dependencies` kitaplığın `project.json` dosyasının bölümüne kopyalayarak başvuruyu değiştirin: `NETStandard.Library`

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

Bu paketler, birçoğu kesinlikle toplama türleri genişletmek için gerekli değildir oldukça çok şey var.  Kodunuzu gerçekte hangi paketleri kullandığını belirlemek için paketleri el ile kaldırabilir veya [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflektör](https://www.red-gate.com/products/dotnet-development/reflector/) gibi bir araç kullanabilirsiniz.

Kesilmiş bir paketin nasıl görünebileceği aşağıda açıklanabilir:

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Metapakete bağlı `NETStandard.Library` olduğundan daha küçük bir ayak izi var.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
