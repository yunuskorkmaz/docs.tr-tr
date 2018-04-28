---
title: Paket bağımlılıkları project.json ile azaltma
description: Paket bağımlılıklarını project.json tabanlı kitaplıkları yazarken azaltın.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 647d850c1629cddc1584a2044174838930b2fb1d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Paket bağımlılıkları project.json ile azaltma

Bu makale, Paket bağımlılıklarını yazarken azaltma hakkında bilmeniz gerekenler kapsamaktadır `project.json` kitaplıkları. Bu makalenin sonundaki tarafından yalnızca gerekli bağımlılıkları kullanır, kitaplığınızı oluşturmak öğreneceksiniz. 

## <a name="why-its-important"></a>Neden önemli olduğunu

.NET core NuGet paketlerini oluşan bir üründür.  Temel bir pakettir [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), hangi bir NuGet paketi diğer paketler halinde oluşur.  .NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamaları üzerinde çalışmak için garanti paket kümesini sağlar.

Ancak, kitaplık içerdiği her tek bir paket kullanmayacaksa şansı yoktur.  Bir kitaplık yazma ve NuGet dağıtma, "yalnızca paketler aşağı kaydırın, bağımlılıkları kırpma için" en iyi yöntem olduğunda, aslında kullanın.  Bu, NuGet paketleri için daha küçük genel ayak izini sonuçlanır.

## <a name="how-to-do-it"></a>Bunu nasıl

Şu anda hiçbir resmi yoktur `dotnet` paket referanslarını kırpar komutu.  Bunun yerine, el ile yapmanız gerekir.  Genel işlem aşağıdaki gibi görünür:

1. Başvuru `NETStandard.Library` sürüm `1.6.0` içinde bir `dependencies` bölümü, `project.json`.
2. Paketlerle geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut satırından.
3. İnceleme `project.lock.json` dosya ve Bul `NETSTandard.Library` bölümü.  Dosya başına yakın olur.
4. Tüm altında listelenen paketler kopyalama `dependencies`.
5. Kaldırma `.NETStandard.Library` başvuru ve kopyalanan paketlerle değiştirin.
6. Gerekmeyen Paketlerine yönelik başvuruları kaldırın.


Aşağıdaki yollardan birini kullanarak gerekmeyen hangi paketlerin bulabilirsiniz:

1. Deneme yanılma.  Bu, bir paketi kaldırma, geri yükleme, kitaplığınızı hala derler, görme ve bu işlem yinelenen içerir.
2. Bir aracı gibi kullanarak [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) ne kodunuzu gerçekte kullandığını görmek için başvurular atmaya.  Sonra kullanmakta olduğunuz türlerine karşılık gelen paketler kaldırabilirsiniz.

## <a name="example"></a>Örnek 

Genel koleksiyon türleri için ek işlevler sağlanan bir kitaplık yazdı düşünün.  Bu tür bir kitaplığı gibi paketlere bağımlı gerek `System.Collections`, ancak hiç paketleri gibi değişebilir `System.Net.Http`.  Bu nedenle, yalnızca ne bu kitaplığı gerekli aşağıya doğru Paket bağımlılıklarını kırpma iyi olur!

Bu kitaplık kırpma için ile başlamanız `project.json` dosyası ve bir başvuru ekleyin `NETStandard.Library` sürüm `1.6.0`.

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

Ardından, paketlerle geri `dotnet restore` ([nota bakın](#dotnet-restore-note)), incelemek `project.lock.json` dosya ve bulmak için geri tüm paketler `NETSTandard.Library`.

İlgili bölümü işte `project.lock.json` dosya görülüyor hedeflerken `netstandard1.0`:

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

Ardından, paket referanslarını üzerinden kopyalama `dependencies` kitaplığın bölümünü `project.json` dosya, değiştirme `NETStandard.Library` başvurusu:

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

Paketler, oldukça çok miktarda olan hangi hangi kesinlikle koleksiyon türleri genişletmek için gerekli olmayan birçoğu.  Paketlerini el ile kaldırın veya gibi bir araç kullanın [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) , kodunuzu gerçekte paketleri tanımlamak için kullanır.

İşte bölünen paketi gibi görünebilir:

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

Şimdi, bağlı, daha küçük bir yer olan üzerinde `NETStandard.Library` metapackage.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]