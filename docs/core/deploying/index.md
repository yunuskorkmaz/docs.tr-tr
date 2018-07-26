---
title: .NET core uygulama dağıtımı
description: Bir .NET Core uygulamasını dağıtma.
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: 4a39efdd92cf9c3bb6aadf83949e02ce20960481
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792432"
---
# <a name="net-core-application-deployment"></a>.NET core uygulama dağıtımı

İki .NET Core uygulamaları için dağıtım türleri oluşturabilirsiniz:

- Framework bağımlı dağıtım. Adından da anlaşılacağı gibi .NET Core hedef sistemdeki bir paylaşılan sistem genelinde sürüm varlığını framework bağımlı dağıtım (FDD) kullanır. .NET Core zaten mevcut olduğundan, uygulamanızı de .NET Core yüklemeleri arasında taşınabilir. Uygulamanızı, yalnızca kendi kodunu ve .NET Core kitaplıklar dışında herhangi bir üçüncü taraf bağımlılıkları içerir. FDDs içeren *.dll* kullanılarak başlatılabilen dosyaları [dotnet yardımcı programı](../tools/dotnet.md) komut satırından. Örneğin, `dotnet app.dll` adlı bir uygulamayı çalıştıran `app`.

- Kendi başına dağıtım. FDD, hedef sistemde paylaşılan Bileşenler'in kendi içinde bir dağıtım (SCD) içermez. .NET Core kitaplıkları ve .NET Core çalışma zamanı hem de dahil olmak üzere tüm bileşenlerin uygulama ile birlikte ve diğer .NET Core uygulamalardan yalıtılır. SCDs içeren bir yürütülebilir dosya (gibi *app.exe* adlı bir uygulama için Windows platformlarında `app`), platforma özgü .NET Core konak adı bir sürümü olduğu ve bir *.dll* (örneğin, dosya *app.dll*), gerçek uygulama olduğu.

## <a name="framework-dependent-deployments-fdd"></a>Framework bağımlı dağıtımlar (FDD)

Bir FDD için yalnızca uygulamanız ve üçüncü taraf bağımlılıkları dağıtın. .NET Core uygulamanızı hedef sistemde mevcut .NET Core sürümünü kullanır bu yana dağıtmanız gerekmez. .NET Core uygulamaları için varsayılan dağıtım modeli budur.

### <a name="why-create-a-framework-dependent-deployment"></a>Framework bağımlı dağıtım neden oluşturulsun mu?

Bir FDD dağıtma, çok sayıda avantaj vardır:

- .NET Core uygulamanızı önceden çalışır hedef işletim sistemlerini tanımlamak zorunda değilsiniz. .NET Core yürütülebilir dosyaları ve kitaplıkları işletim sisteminden bağımsız olarak için ortak bir PE dosyası biçimini kullandığından, .NET Core uygulamanızı alttaki işletim sisteminden bağımsız olarak çalıştırabilirsiniz. PE dosyası biçimi hakkında daha fazla bilgi için bkz. [.NET bütünleştirilmiş kodu dosya biçimi](../../standard/assembly-format.md).

- Dağıtım paketinin boyutu küçüktür. Yalnızca uygulamanız ve onun bağımlılıklarını, .NET Core kendisini dağıtırsınız.

- Birden fazla uygulama konak sistemlerinde iki disk alanı ve bellek kullanımını azaltır aynı .NET Core yüklemesini kullanın.

Bazı dezavantajları vardır:

- Yalnızca .NET Core, hedef sürümünü veya sonraki bir sürümü zaten konak sisteminde yüklü değilse, uygulamayı çalıştırabilirsiniz.

- .NET Core çalışma zamanı ve kitaplıklarda bilgi birikiminizi gelecek sürümleri olmadan değiştirmek mümkündür. Nadiren de olsa Bu, uygulamanın davranış şekli değişebilir.

## <a name="self-contained-deployments-scd"></a>Bağımsız dağıtımlar (SCD)

Kendi içinde bir dağıtım için uygulamanızı ve tüm gerekli üçüncü taraf bağımlılıkları sürümü, uygulama oluşturmak için kullanılan bir .NET Core ile birlikte dağıtın. Bir SCD oluşturma içermez [yerel .NET Core bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) çeşitli platformlarda, bu nedenle bu uygulama çalışmadan önce mevcut olmalıdır. Çalışma zamanında sürüm bağlama hakkında daha fazla bilgi için makaleye bakın [.NET core'da sürüm bağlama](../versions/selection.md)

FDD ve SCD dağıtımları ayrı konak yürütülebilir dosyaları, kullandığından, yürütülebilir bir konak için bir SCD yayımcı imza ile oturum açabilirsiniz.

### <a name="why-deploy-a-self-contained-deployment"></a>Neden kendi içinde bir dağıtım dağıtılsın mı?

Müstakil dağıtımının sağladığı iki önemli avantaj vardır:

- Uygulamanızla birlikte dağıtılan bir .NET Core sürümünün tek denetim var. .NET core yalnızca sizin tarafınızdan hizmet verebilir.

- Hedef sistem üzerinde çalışacağı bir .NET Core sürümünü sunuyorsunuz bu yana .NET Core uygulamanızı çalıştırabilirsiniz olabilirsiniz.

Ayrıca, bir dizi dezavantajları vardır:

- .NET Core, dağıtım paketinde bulunduğundan, dağıtım paketleri önceden oluşturduğunuz hedef platformlar seçmeniz gerekir.

- .NET Core yanı sıra, uygulamanızı ve üçüncü taraf bağımlılıkları içerecek şekilde sahip olduğundan, dağıtım paketi görece büyük boyutudur.

- Bir sistem için çok sayıda bağımsız bir .NET Core uygulamaları dağıtma, önemli miktarda disk alanı, her uygulama çoğaltmaları bu yana .NET Core dosyaları kullanabilir.

## <a name="step-by-step-examples"></a>Adım adım örnek

CLI araçları ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [CLI araçları ile .NET Core uygulamaları dağıtma](deploy-with-cli.md). Visual Studio ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md). Her konu, aşağıdaki dağıtımlar örnekleri içerir:

- Framework bağımlı dağıtım
- Framework bağımlı dağıtım üçüncü taraf bağımlılıkları
- Kendi içinde dağıtım
- Üçüncü taraf bağımlılıkları kendi içinde dağıtım

# <a name="see-also"></a>Ayrıca bkz.

[CLI araçları ile .NET Core uygulamaları dağıtma](deploy-with-cli.md)   
[Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md)   
[Paketler, meta paketler ve çerçeveler](../packages.md)   
[.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
