---
title: .NET core uygulama dağıtımı
description: .NET Core uygulama dağıtma.
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5b8d49fd70b6e6b136a00aa0f7d7070bdd5a401a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-application-deployment"></a>.NET core uygulama dağıtımı

Dağıtımları .NET Core uygulamaları için iki tür oluşturabilirsiniz:

- Framework bağımlı dağıtım. Adından da anlaşılacağı gibi framework bağımlı dağıtım (FDD) .NET Core hedef sistemdeki bir paylaşılan sistem genelinde sürümünün varlığına bağımlıdır. .NET Core zaten mevcut olduğundan, uygulamanız da .NET Core yüklemeler arasında taşınabilir. Uygulamanızı yalnızca kendi kodunu ve .NET Core kitaplıkları dışında olan üçüncü taraf bağımlılıkları içerir. FDDs içeren *.dll* kullanarak başlatılabilir dosyaları [dotnet yardımcı programı](../tools/dotnet.md) komut satırından. Örneğin, `dotnet app.dll` adlı bir uygulamayı çalıştıran `app`.

- Kendi içinde bulunan dağıtım. FDD farklı olarak, hedef sistemde paylaşılan bileşenler varlığına kendi içinde bulunan bir dağıtım (SCD) kullanmaz. .NET Core kitaplıkları ve .NET çekirdeği çalışma zamanı dahil olmak üzere tüm bileşenler uygulama ile birlikte ve diğer .NET Core uygulamalardan yalıtılır. SCDs içeren bir yürütülebilir dosya (gibi *app.exe* adlı bir uygulama için Windows platformlarında `app`), platforma özgü .NET Core ana bilgisayar yeniden adlandırılmış bir sürümünü olduğu ve *.dll* (örneğin, dosya *app.dll*), gerçek uygulama olduğu.

## <a name="framework-dependent-deployments-fdd"></a>Framework bağımlı dağıtımları (FDD)

Bir FDD için yalnızca uygulamanızı ve üçüncü taraf bağımlılıkları dağıtın. Uygulamanızı hedef sistemde mevcut .NET Core sürümünü kullanacak beri .NET Core dağıtmak zorunda değilsiniz. .NET Core uygulamaları için varsayılan dağıtım modeli budur.

### <a name="why-create-a-framework-dependent-deployment"></a>Neden framework bağımlı dağıtım oluşturulsun mu?

Bir FDD dağıtma, çok sayıda avantaj vardır:

- .NET Core uygulamanızı önceden çalışacak hedef işletim sistemleri tanımlamanız gerekmez. .NET Core yürütülebilir dosyaları ve kitaplıkları bakılmaksızın işletim sistemi için ortak bir PE dosya biçimi kullandığından, .NET Core uygulamanızı temel işletim sistemini bağımsız olarak çalıştırabilirsiniz. PE dosya biçimi hakkında daha fazla bilgi için bkz: [.NET derleme dosyası biçimi](../../standard/assembly-format.md).

- Dağıtım paketi boyutu küçüktür. Yalnızca uygulamanızı ve bağımlılıklarını, .NET Core kendisini dağıttığınız.

- Birden fazla uygulama ana bilgisayar sistemlerinde her iki disk alanı ve bellek kullanımını azaltır aynı .NET Core yüklemesi kullanın.

Birkaç dezavantajları vardır:

- Yalnızca hedef .NET Core sürümü veya sonraki bir sürümü zaten ana bilgisayar sisteminde yüklü değilse, uygulamanızın çalıştırabilirsiniz.

- .NET çekirdeği çalışma zamanı ve bilginiz gelecekteki Sunumlarda olmadan değiştirmek için kitaplıklar için mümkündür. Nadir durumlarda bu, uygulamanızın davranışını değiştirebilir.

## <a name="self-contained-deployments-scd"></a>Kendi içinde bulunan dağıtımları (SCD)

Kendi içinde bulunan bir dağıtım için uygulamanızı ve uygulama oluşturmak için kullanılan .NET Core sürümü ile birlikte gerekli üçüncü taraf bağımlılıkları dağıtın. Bir SCD oluşturma içermez [.NET Core yerel bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) çeşitli platformlarda, bu nedenle bu uygulama çalışmadan önce mevcut olmalı.

Yayımcı imza ile yürütülebilir bir ana bilgisayar için bir SCD oturum şekilde FDD ve SCD dağıtımları ayrı konak yürütülebilir dosyaları, kullanın.

### <a name="why-deploy-a-self-contained-deployment"></a>Neden bir müstakil dağıtım?

Kendi içinde bulunan bir dağıtım dağıtma iki ana avantajları vardır:

- Uygulamanız ile dağıtılan .NET Core sürümü tek denetime sahiptir. .NET core yalnızca sizin tarafınızdan hizmet verebilir.

- Üzerinde çalışacağı .NET Core sürümü sağlama hedef sistem .NET Core uygulamanızı çalışabilir emin olabilirsiniz.

Ayrıca, bir dizi dezavantajları vardır:

- .NET Core dağıtım paketinde yer aldığından, kendisi için dağıtım paketleri önceden oluşturduğunuz hedef platformlar seçmeniz gerekir.

- .NET Core yanı sıra, uygulamanızı ve üçüncü taraf bağımlılıkları içerecek şekilde sahip olduğundan, dağıtım paketi görece büyük boyutudur.

- Çok sayıda müstakil .NET Core uygulamaları bir sisteme dağıtmaya önemli miktarda disk alanı, her uygulama çoğaltmaları .NET Core dosyaları bu yana kullanabilir.

## <a name="step-by-step-examples"></a>Adım adım örnekler

CLI araçlarını ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [CLI araçlarını ile .NET Core uygulamaları dağıtma](deploy-with-cli.md). Visual Studio ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md). Her konunun aşağıdaki dağıtımları örnekleri içerir:

- Framework bağımlı dağıtım
- Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım
- Kendi içinde bulunan dağıtım
- Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım

# <a name="see-also"></a>Ayrıca bkz.

[CLI araçlarını ile .NET Core uygulamaları dağıtma](deploy-with-cli.md)   
[Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md)   
[Paketler, Metapackages ve çerçeveleri](../packages.md)   
[.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
