---
title: Docker kapsayıcıları için ne zaman .NET 5 seçin
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker kapsayıcıları için ne zaman .NET seçme
ms.date: 02/02/2021
ms.openlocfilehash: d0480ac43c0090b72185bd23bbd11ac7e26001e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653426"
---
# <a name="when-to-choose-net-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET seçilmelidir?

.NET 5 ' in modülerliği ve hafif doğası, kapsayıcılar için mükemmel hale getirir. Bir kapsayıcı dağıttığınızda ve başlattığınızda, görüntü .NET 5 ' ten .NET Framework göre çok daha küçüktür. Buna karşılık, bir kapsayıcı için .NET Framework kullanmak için görüntünüzü, .NET 5 için kullandığınız Windows nano Server veya Linux görüntülerinden çok daha ağır olan Windows Server Core görüntüsüne dayandırmanız gerekir.

Ayrıca, .NET 5 platformlar arası olduğundan, Linux veya Windows kapsayıcı görüntüleriyle sunucu uygulamaları dağıtabilirsiniz. Ancak geleneksel .NET Framework kullanıyorsanız, yalnızca Windows Server Core tabanlı görüntüleri dağıtabilirsiniz.

Aşağıda .NET 5 ' in neden seçmesinin daha ayrıntılı bir açıklaması verilmiştir.

## <a name="developing-and-deploying-cross-platform"></a>Platformlar arası geliştirme ve dağıtma

Açık olarak, amacınız Docker (Linux ve Windows) tarafından desteklenen birden çok platformda çalışabilen bir uygulamaya (Web uygulaması veya hizmet) sahip olmak için, .NET Framework yalnızca Windows 'u desteklediğinden, sağ seçim .NET 5 ' tir.

.NET 5, macOS 'ı bir geliştirme platformu olarak da destekler. Ancak, bir Docker konağına kapsayıcı dağıttığınızda, bu ana bilgisayar Linux veya Windows 'u temel almalıdır (Şu anda). Örneğin, bir geliştirme ortamında, Mac üzerinde çalışan bir Linux sanal makinesini kullanabilirsiniz.

[Visual Studio](https://www.visualstudio.com/vs/) , Windows için tümleşik bir geliştirme ORTAMı (IDE) sağlar ve Docker geliştirmeyi destekler.

[Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/) , MacOS üzerinde çalışan ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio evrimi olan bir IDE 'dir. Bu aracın, güçlü bir IDE kullanmak isteyen Mac makinelerde çalışan geliştiriciler için tercih edilen seçim olması gerekir.

MacOS, Linux ve Windows üzerinde [Visual Studio Code](https://code.visualstudio.com/) de kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil .NET 5 ' ü tam olarak destekler. VS Code basit bir düzenleyici olduğundan, Docker CLı ve [.net CLI](../../../core/tools/index.md)ile birlikte makinede Kapsayıcılı uygulamalar geliştirmek için kullanabilirsiniz. Ayrıca, .NET 5 ' i alt Lime, Emacs, vi gibi birçok üçüncü taraf düzenleyiciyle ve ayrıca IntelliSense desteği sağlayan açık kaynaklı OmniSharp projesi ile de hedefleyebilirsiniz.

Ides ve düzenleyicilere ek olarak, desteklenen tüm platformlar için [.net CLI](../../../core/tools/index.md) kullanabilirsiniz.

## <a name="using-containers-for-new-green-field-projects"></a>Yeni ("yeşil-alan") projeler için kapsayıcıları kullanma

Kapsayıcılar genellikle bir mikro hizmet mimarisi ile birlikte kullanılır, ancak her türlü mimari kalıbı izleyen Web uygulamalarını veya hizmetlerini kapsayıtabilecek de kullanılabilirler. Windows kapsayıcılarında .NET Framework kullanabilirsiniz, ancak .NET 5 ' in modülerliği ve hafif doğası kapsayıcılar ve mikro hizmet mimarileri için mükemmel hale gelir. Bir kapsayıcı oluşturduğunuzda ve dağıttığınızda, bu görüntü .NET 5 ' ten .NET Framework göre çok daha küçüktür.

## <a name="create-and-deploy-microservices-on-containers"></a>Kapsayıcılar üzerinde mikro hizmetler oluşturma ve dağıtma

Düz süreçler kullanarak mikro hizmet tabanlı uygulamalar (kapsayıcılar olmadan) oluşturmak için geleneksel .NET Framework kullanabilirsiniz. Bu şekilde, .NET Framework zaten yüklenmiş ve süreçler genelinde paylaşıldığı için, süreçler hafif ve hızlı bir şekilde başlatılır. Ancak kapsayıcıları kullanıyorsanız, geleneksel .NET Framework görüntüsü de Windows Server Core ' a dayalıdır ve bu, mikro hizmetler arası bir yaklaşım için çok daha ağır hale gelir. Ancak ekipler, .NET Framework kullanıcılara da deneyimi geliştirmek üzere fırsatlar arıyor. Son olarak, [Windows Server çekirdek kapsayıcısı görüntülerinin boyutu %40 oranında daha küçük >](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller).

Diğer yandan, .NET 5 hafif olduğundan, kapsayıcıları temel alan mikro hizmetlere dayalı bir sistem kullanıyorsanız, .NET 5 en iyi adaydır. Ayrıca, Linux veya Windows nano Server için ilgili kapsayıcı görüntüleri yalın ve küçüktür, kapsayıcılar açık ve hızlı bir şekilde başlatılır.

Mikro hizmet mümkün olduğunca küçük olacak şekilde, küçük bir parmak izine sahip olmak, küçük bir [ilgi alanına sahip](https://en.wikipedia.org/wiki/Domain-driven_design)olmak, küçük bir sorun olduğunu göstermek ve hızlı bir şekilde başlayabilmek ve durdurmak için en az bir değer olması gerekir: Bu gereksinimler için, .NET 5 kapsayıcı görüntüsü gibi küçük ve hızlı-örnek oluşturma kapsayıcı görüntülerini kullanmak isteyeceksiniz.

Mikro hizmetler mimarisi Ayrıca bir hizmet sınırı genelinde teknolojileri karıştırabilmeniz için de sağlar. Bu yaklaşım, diğer mikro hizmetlerle birlikte çalışan veya Node.js, Python, Java, GoLang veya diğer teknolojiler ile geliştirilen hizmetlerle birlikte çalışan yeni mikro hizmetler için .NET 5 ' e aşamalı geçiş sağlar.

## <a name="deploying-high-density-in-scalable-systems"></a>Ölçeklenebilir sistemlerde yüksek yoğunluklu dağıtım

Kapsayıcı tabanlı sisteminizin en iyi yoğunluğu, ayrıntı düzeyi ve performansa ihtiyacı olduğunda, .NET ve ASP.NET Core en iyi seçeneklerdir. ASP.NET Core geleneksel .NET Framework en fazla 10 kat daha hızlıdır ve mikro hizmetler için Java servinler, Go ve Node.js gibi diğer popüler sektör teknolojilerini de sağlar.

Bu yaklaşım özellikle, çalışan yüzlerce mikro hizmet (kapsayıcı) olabilecek mikro hizmet mimarileri için geçerlidir. Linux veya Windows nano 'daki ASP.NET Core görüntülerle (.NET çalışma zamanına bağlı olarak), sisteminizi çok daha az sayıda sunucu veya VM ile çalıştırabilirsiniz. böylece, son olarak altyapı ve barındırma ile maliyet tasarrufu yapabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](general-guidance.md) 
> [Sonraki](net-framework-container-scenarios.md)
