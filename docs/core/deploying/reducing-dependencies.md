---
title: Project. JSON ile paket bağımlılıklarını azaltma
description: Project. JSON tabanlı kitaplıklar yazarken paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740831"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Project. JSON ile paket bağımlılıklarını azaltma

Bu makalede, `project.json` kitaplıklarını yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gereken özellikler ele alınmaktadır. Bu makalenin sonuna kadar, kitaplığınızı yalnızca ihtiyaç duyduğunuz bağımlılıkları kullanacak şekilde oluşturmayı öğreneceksiniz.

## <a name="why-its-important"></a>Neden önemli

.NET Core, NuGet paketlerinden oluşan bir üründür.  Temel bir paket [. ](https://www.nuget.org/packages/NETStandard.Library)Diğer paketlerden oluşan bir NuGet paketi olan Netstandart. Library meta paketi. Bu, .NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamasında çalışmak için garanti edilen paket kümesini sağlar.

Ancak, kitaplığınızın içerdiği her bir paketi kullanması iyi bir şansınız vardır.  Bir kitaplığı yazarken ve NuGet üzerinden dağıtırken, bağımlılıklarınızı yalnızca gerçekten kullandığınız paketlere göre "kırpmak" en iyi uygulamadır.  Bu, NuGet paketleri için daha küçük bir genel parmak izine neden olur.

## <a name="how-to-do-it"></a>Nasıl yapılır

Şu anda paket başvurularını kırpan resmi bir `dotnet` komutu yoktur.  Bunun yerine, el ile yapmanız gerekir.  Genel işlem aşağıdaki gibi görünür:

1. `project.json`bir `dependencies` bölümünde sürüm `1.6.0` başvuru `NETStandard.Library`.
2. Paketleri, komut satırından `dotnet restore` ([bkz. nota](#dotnet-restore-note)) geri yükleyin.
3. `project.lock.json` dosyasını inceleyin ve `NETStandard.Library` bölümünü bulun.  Bu, dosyanın başlangıcına yakıntı.
4. Listelenen tüm paketleri `dependencies`altına kopyalayın.
5. `.NETStandard.Library` başvurusunu kaldırın ve kopyalanmış paketlerle değiştirin.
6. İhtiyacınız olmayan paketlere yönelik başvuruları kaldırın.

Aşağıdaki yollarla ihtiyacınız olmayan paketleri öğrenebilirsiniz:

1. Deneme ve hata. Bu, bir paketi kaldırmayı, geri yüklemeyi, kitaplığınızın hala derlendiğini görmenizi ve bu işlemi tekrarlamayı içerir.
2. Kodunuzun gerçekten kullandığını görmek için başvurularda göz atmayı sağlamak üzere [ılspy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.net yansıtıcısı](https://www.red-gate.com/products/dotnet-development/reflector) gibi bir araç kullanma. Daha sonra, kullanmakta olduğunuz türlere karşılık gelen paketleri kaldırabilirsiniz.

## <a name="example"></a>Örnek

Genel koleksiyon türlerine ek işlevsellik sağlayan bir kitaplık yazdığınızı düşünelim. Bu tür bir kitaplığın `System.Collections`gibi paketlere bağlı olması gerekir, ancak tümü `System.Net.Http`gibi paketlere bağlı olmayabilir. Bu nedenle, paket bağımlılıklarını yalnızca bu kitaplıkta gerekli olacak şekilde kırpmak iyi olacaktır!

Bu kitaplığı kırpmak için `project.json` dosyası ile başlar ve `NETStandard.Library` sürümü `1.6.0`başvurusunu ekleyin.

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

Ardından, paketleri `dotnet restore` ([bkz. nota](#dotnet-restore-note)) geri yükler, `project.lock.json` dosyasını inceleyin ve `NETStandard.Library`için geri yüklenen tüm paketleri bulabilirsiniz.

`project.lock.json` dosyadaki ilgili bölüm, `netstandard1.0`hedefleme sırasında şöyle görünür:

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

Sonra, `NETStandard.Library` başvurusunu değiştirerek kitaplığın `project.json` dosyasının `dependencies` bölümüne paket başvurularını kopyalayın:

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

Bu çok sayıda paket, büyük ölçüde koleksiyon türlerini genişletmek için gerekli değildir.  Kodlarınızın gerçekten hangi paketleri kullandığını belirlemek için paketleri el ile kaldırabilir veya [ılspy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.net yansıtıcısı](https://www.red-gate.com/products/dotnet-development/reflector/) gibi bir araç kullanabilirsiniz.

Kırpılmış bir paket şöyle görünebilir:

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

Şimdi, `NETStandard.Library` metapackage 'e bağımlı olsa da daha küçük bir ayak izine sahiptir.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
