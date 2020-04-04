---
title: Kendi kendine yeten uygulamaları kırpma
description: Boyutlarını azaltmak için bağımsız uygulamaları nasıl kırptığınızı öğrenin. .NET Core, çalışma süresini kendi kendine çalışan bir uygulamayla paketler ve genellikle çalışma süresinin daha fazlasını içerir ve o zaman gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665637"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Bağımsız dağıtımları ve çalıştırılabilir leri kırpın

Bir uygulama bağımsız yayımlanırken,.NET Core çalışma süresi uygulamayla birlikte paketlenir. Bu birleştirme, paket uygulamanıza önemli miktarda içerik ekler.

Uygulamanızı dağıtma söz konusu olduğunda, boyut genellikle önemli bir faktördür. Paket uygulamasının boyutunu mümkün olduğunca küçük tutmak genellikle uygulama geliştiricileri için bir hedeftir.

Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için yalnızca çalışma zamanının bir alt kümesi gerekir. Çalışma zamanının bu kullanılmayan bölümleri gereksizdir ve paket uygulamadan kesilebilir.

> [!NOTE]
> Kırpma ,NET Core 3.1'de deneysel bir özelliktir ve _yalnızca_ bağımsız olarak yayınlanan uygulamalar için kullanılabilir.

## <a name="trim-your-application"></a>Başvurunuzu kırpın

Aşağıdaki örnek, [dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızın nasıl kırpılabildiğini gösterir:

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

Kırpma özelliği, gerekli çalışma zamanı derlemelerinin bir grafiğini keşfetmek ve oluşturmak için uygulama ikililerini inceleyerek çalışır. Başvurulamayan kalan çalışma zamanı derlemeleri kırpılır.

## <a name="trimming-issues-when-using-reflection"></a>Yansıma kullanırken sorunları kırpma

Kırpma işlevinin başvuruları algılayamadığı senaryolar vardır. Örneğin, yansıma kullanan bir uygulama bu sorunla ilgili olarak, derlemeye bağımlılık yalnızca çalışma zamanında bilinecektir.

Kırpma yalnızca yansıma kullanımı doğrudan başvurulamayan bir çalışma zamanı derlemesi bağlıysa bir sorundur. Uygulama kodunuzu doğrudan yansıtma yı kullanmıyor olabilir, ancak başvuruda bulunduğunuz üçüncü taraf derlemenin bu kodu kullandığını unutmayın.

Kod bir API'ye yansıma yoluyla başvuruyorsa ve bağlayıcının bu API'yi içeren derlemeyi kırpmasını istemiyorsanız, proje dosyanızı derlemeyi kırpma işleminden hariç tutmak için değiştirebilirsiniz. Aşağıdaki örnek, çağrılan `System.Security` bir derlemenin nasıl kırpılmasının önlenişretedildiğini gösterir:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımı](index.md)
