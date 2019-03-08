---
title: Project.json ile Paket bağımlılıklarını azaltma
description: Project.json tabanlı kitaplıkları yazma Paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 9d4f9d7f6e7a736b7d07062f3cd31d6f45176cb1
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674971"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Project.json ile Paket bağımlılıklarını azaltma

Bu makale yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gerekenler kapsar `project.json` kitaplıkları. Bu makalenin sonunda, yalnızca gerekli bağımlılıkları kullanır, kitaplığınıza compose öğreneceksiniz.

## <a name="why-its-important"></a>Neden önemli olduğu

.NET core NuGet paketlerini oluşan bir üründür.  Temel bir pakettir [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), bir NuGet paketi diğer paketleri oluşur.  .NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamaları üzerinde çalışacağı garanti paketleri kümesini sağlar.

Ancak, içerdiği her tek bir paket kitaplığınızı kullanmayacaksa şansı yoktur.  Bir kitaplığı yazma ve NuGet dağıtma, "yalnızca paketler aşağı bağımlılıklarınızı kırpmak için" en iyi yöntem olduğunda, gerçekten kullanın.  NuGet paketleri için daha küçük bütün kapladığı alanı sonuçlanır.

## <a name="how-to-do-it"></a>Nasıl yapılır

Şu anda, resmi yoktur `dotnet` paket başvuruları kırpar komutu.  Bunun yerine, el ile yapmanız gerekir.  Genel süreç aşağıdaki gibi görünür:

1. Başvuru `NETStandard.Library` sürüm `1.6.0` içinde bir `dependencies` bölümünü, `project.json`.
2. Paketleri geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut satırı.
3. İnceleme `project.lock.json` dosya ve bulma `NETStandard.Library` bölümü.  Bu, dosyanın başına yakın olur.
4. Tüm altında listelenen paketlerin bir bölümünü kopyalayın `dependencies`.
5. Kaldırma `.NETStandard.Library` başvuru ve kopyalanan paketleri ile değiştirin.
6. İhtiyacınız olmayan paketleri başvuruları kaldırın.

Aşağıdaki yöntemlerden birini kullanarak ihtiyacınız olmayan paketler bulabilirsiniz:

1. Deneme yanılma.  Bu paketi kaldırma, geri yükleme, kitaplığınıza derlenmeye devam eder, görme ve bu süreci tekrarlayarak içerir.
2. Gibi bir araç kullanarak [yetenek](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) ne kodunuzun gerçekte kullanmakta olduğunu görmenizi sağlayan başvurular göz atmak için.  Ardından, kullanmakta olduğunuz türlerine karşılık gelen paketler kaldırabilirsiniz.

## <a name="example"></a>Örnek

Genel koleksiyon türleri için ek işlevler sağlanan kitaplık yazdığınız varsayalım.  Bir tür kitaplığı paketleri gibi bağımlı gerek `System.Collections`, ancak hiç paketleri gibi değişebilir `System.Net.Http`.  Bu nedenle, yalnızca ne bu kitaplığı gerekli aşağı Paket bağımlılıklarını trim yararlı olabilir!

Bu kitaplık kırpmak için ile başlamanız `project.json` bir başvuru ekleyin ve dosya `NETStandard.Library` sürüm `1.6.0`.

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

Ardından, paketleri geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)), inceleme `project.lock.json` dosyasını ve tüm paketleri için geri `NETStandard.Library`.

İlgili bölüme işte `project.lock.json` dosya göründüğüne hedeflenirken `netstandard1.0`:

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

Ardından, paket başvuruları kopyalayabilirsiniz `dependencies` kitaplığın bölümünü `project.json` değiştirerek, dosya `NETStandard.Library` başvurusu:

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

Birçok paketleri, çoğu kesinlikle koleksiyon türlerini genişletmek için gerekli olmayan olmasıdır.  Paketleri el ile kaldırmanız veya gibi bir araç kullanın [yetenek](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) , kodunuzun gerçekte paketleri tanımlamak için kullanır.

İşte kırpılmış paket aşağıdaki gibi görünebilir:

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

Şimdi, bağımlı, daha küçük ayak izine sahip üzerinde `NETStandard.Library` metapackage.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
