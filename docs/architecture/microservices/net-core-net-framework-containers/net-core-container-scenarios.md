---
title: Docker kapsayıcıları için ne zaman .NET Core seçilmelidir?
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Docker kapları için .NET Core ne zaman seçilir?
ms.date: 01/30/2020
ms.openlocfilehash: f784512af3f520f96d499ab002eda58071b3c284
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147381"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET Core seçilmelidir?

.NET Core'un modülerliği ve hafif yapısı, konteynerler için mükemmel olmasını sağlar. Bir kapsayıcıyı dağıtıp başlattığınızda, görüntüsü .NET Core ile .NET Framework'e göre çok daha küçüktür. Buna karşılık, bir kapsayıcı için .NET Framework kullanmak için, .NET Core için kullandığınız Windows Nano Server veya Linux görüntülerinden çok daha ağır olan Windows Server Core görüntüsüne resminizi dayandırmalısınız.

Ayrıca, .NET Core çapraz platformdur, böylece sunucu uygulamalarını Linux veya Windows kapsayıcı görüntüleriyle dağıtabilirsiniz. Ancak, geleneksel .NET Framework kullanıyorsanız, görüntüleri yalnızca Windows Server Core'a göre dağıtabilirsiniz.

Aşağıda ,NET Core'un neden seçileceklerine ilişkin daha ayrıntılı bir açıklama yer alamayışyer almakt

## <a name="developing-and-deploying-cross-platform"></a>Çapraz platform geliştirme ve dağıtma

Açıkçası, amacınız Docker (Linux ve Windows) tarafından desteklenen birden çok platformda çalıştırılabilen bir uygulamaya (web uygulaması veya hizmet) sahip olmaksa, doğru seçim .NET Core'dur, çünkü .NET Framework yalnızca Windows'u destekler.

.NET Core, macOS'u geliştirme platformu olarak da destekler. Ancak, kapsayıcıları bir Docker ana bilgisayara dağıttığınızda, bu ana bilgisayar (şu anda) Linux veya Windows'u temel almalıdır. Örneğin, bir geliştirme ortamında, Mac üzerinde çalışan bir Linux VM kullanabilirsiniz.

[Visual Studio,](https://www.visualstudio.com/vs/) Windows için entegre bir geliştirme ortamı (IDE) sağlar ve Docker geliştirmeyi destekler.

[Mac için Visual Studio,](https://www.visualstudio.com/vs/visual-studio-mac/) macOS ile çalışan ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio'nun evrimi olan bir IDE'dir. Bu, güçlü bir IDE kullanmak isteyen Mac makinelerinde çalışan geliştiriciler için tercih edilen seçim olmalıdır.

Visual Studio [Code'u](https://code.visualstudio.com/) macOS, Linux ve Windows'da da kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil olmak üzere .NET Core'u tam olarak destekler. VS Code hafif bir düzenleyici olduğundan, Docker CLI ve [.NET Core CLI](../../../core/tools/index.md)ile birlikte Mac'te kapsayıcı uygulamalar geliştirmek için kullanabilirsiniz. Ayrıca .NET Core'u Sublime, Emacs, vi gibi üçüncü taraf editörlerle ve IntelliSense desteği de sağlayan açık kaynak OmniSharp projesiyle hedefleyebilirsiniz.

II'ler ve editörlere ek olarak, desteklenen tüm platformlar için [.NET Core CLI'yi](../../../core/tools/index.md) kullanabilirsiniz.

## <a name="using-containers-for-new-green-field-projects"></a>Yeni ("yeşil alan") projeler için kapsayıcıkullanma

Kapsayıcılar genellikle bir microservices mimarisi ile birlikte kullanılır, ancak onlar da web uygulamaları veya herhangi bir mimari desen takip hizmetleri konteyner için kullanılabilir. .NET Framework'ü Windows Kapsayıcılarında kullanabilirsiniz, ancak .NET Core'un modülerliği ve hafif yapısı, kapsayıcılar ve mikro hizmetler mimarileri için mükemmel dir. Bir kapsayıcı oluşturup dağıttığınızda, görüntüsü .NET Core ile .NET Framework'e göre çok daha küçüktür.

## <a name="create-and-deploy-microservices-on-containers"></a>Konteynerlerde mikro hizmetler oluşturma ve dağıtma

Basit işlemler kullanarak mikrohizmetlere dayalı uygulamalar (kapsayıcısız) oluşturmak için geleneksel .NET Framework'ü kullanabilirsiniz. Bu şekilde, .NET Framework zaten yüklendiğinden ve süreçler arasında paylaşıldığından, işlemler hafif ve hızlı bir başlangıç olur. Ancak, kapsayıcılar kullanıyorsanız, geleneksel .NET Framework için görüntü de Windows Server Core dayanmaktadır ve bir microservices-on-containers yaklaşım için çok ağır hale getirir. Ancak ekipler, .NET Framework kullanıcılarının deneyimini geliştirmek için de fırsatlar aramıştır. Son zamanlarda, [Windows Server Core kapsayıcı görüntülerinin boyutu >%40 daha küçük bir boyuta düşürüldü.](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller)

Diğer taraftan, .NET Core, .NET Core hafif olduğu için kapsayıcılara dayalı mikrohizmetlere yönelik bir sistemi benimsiyorsanız en iyi adaydır. Buna ek olarak, linux veya Windows Nano Server için ilgili kapsayıcı görüntüleri yalın ve küçüktür, bu da kapsayıcıları hafif ve hızlı bir şekilde başlatmaktadır.

Bir microservice mümkün olduğunca küçük olması içindir: hafif zaman kadar dönerken, küçük bir ayak izi olması, küçük bir Sınırlı Bağlam (DDD, [Etki Alanı Odaklı Tasarım](https://en.wikipedia.org/wiki/Domain-driven_design)kontrol), endişeleri küçük bir alanı temsil etmek ve hızlı başlatmak ve durdurmak edebilmek için. Bu gereksinimler için,.NET Core kapsayıcı görüntüsü gibi küçük ve hızlı ve anlık kapsayıcı görüntüleri kullanmak isteyeceksiniz.

Microservices mimarisi, teknolojileri hizmet sınırı boyunca karıştırmanızı da sağlar. Bu, diğer mikro hizmetlerle birlikte çalışan veya Node.js, Python, Java, GoLang veya diğer teknolojilerle geliştirilen hizmetler için .NET Core'a kademeli bir geçiş sağlar.

## <a name="deploying-high-density-in-scalable-systems"></a>Ölçeklenebilir sistemlerde yüksek yoğunluklu dağıtma

Konteyner tabanlı sisteminizmümkün olan en iyi yoğunluğa, parçalılığa ve performansa ihtiyaç duyduğunda ,NET Core ve ASP.NET Core en iyi seçeneklerinizdir. ASP.NET Core, geleneksel .NET Framework'deki ASP.NET on kata kadar daha hızlıdır ve Java servlets, Go ve Node.js gibi mikro hizmetler için diğer popüler endüstri teknolojilerine liderlik eder.

Bu, özellikle yüzlerce mikro hizmetin (kapsayıcının) çalıştırılabileceği mikro hizmetler mimarileri için önemlidir. Linux veya Windows Nano'daki ASP.NET Core görüntüleriyle (.NET Core çalışma süresine dayalı olarak) sisteminizi çok daha az sayıda sunucu veya VM ile çalıştırarak altyapı ve barındırma maliyetlerinden tasarruf edebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](general-guidance.md)
>[Sonraki](net-framework-container-scenarios.md)
