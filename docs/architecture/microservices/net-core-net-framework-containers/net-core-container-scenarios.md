---
title: Docker kapsayıcıları için ne zaman .NET Core seçilmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker kapsayıcıları için ne zaman .NET Core seçme
ms.date: 01/30/2020
ms.openlocfilehash: b3cb1eefe739b4ffdbbdd0bdcb3c74b51862704b
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501844"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET Core seçilmelidir?

.NET Core 'un modülerliği ve hafif doğası, kapsayıcılar için kusursuz hale getirir. Bir kapsayıcı dağıtırken ve başlattığınızda, bu görüntü, .NET Framework .NET Core ile çok daha küçüktür. Buna karşılık, bir kapsayıcı için .NET Framework kullanmak için görüntünüzü, .NET Core için kullandığınız Windows nano Server veya Linux görüntülerinden çok daha ağır olan Windows Server Core görüntüsüne dayandırmanız gerekir.

Ayrıca, .NET Core, Linux veya Windows kapsayıcı görüntüleriyle sunucu uygulamaları dağıtabilmeniz için platformlar arası bir platformdur. Ancak geleneksel .NET Framework kullanıyorsanız, yalnızca Windows Server Core tabanlı görüntüleri dağıtabilirsiniz.

Aşağıda .NET Core 'un neden seçmesinin daha ayrıntılı bir açıklaması verilmiştir.

## <a name="developing-and-deploying-cross-platform"></a>Platformlar arası geliştirme ve dağıtma

Açık olarak, amacınız Docker (Linux ve Windows) tarafından desteklenen birden çok platformda çalışabilen bir uygulamaya (Web uygulaması veya hizmet) sahip olmak için, .NET Framework yalnızca Windows 'u desteklediğinden, sağ tercih edilir.

.NET Core Ayrıca, macOS 'ı bir geliştirme platformu olarak destekler. Ancak, bir Docker konağına kapsayıcı dağıttığınızda, bu ana bilgisayar Linux veya Windows 'u temel almalıdır (Şu anda). Örneğin, bir geliştirme ortamında, Mac üzerinde çalışan bir Linux sanal makinesini kullanabilirsiniz.

[Visual Studio](https://www.visualstudio.com/vs/) , Windows için tümleşik bir geliştirme ORTAMı (IDE) sağlar ve Docker geliştirmeyi destekler.

[Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/) , MacOS üzerinde çalışan ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio evrimi olan bir IDE 'dir. Bu, güçlü bir IDE kullanmak isteyen Mac makinelerde çalışan geliştiriciler için tercih edilen seçim olmalıdır.

MacOS, Linux ve Windows üzerinde [Visual Studio Code](https://code.visualstudio.com/) de kullanabilirsiniz. Visual Studio Code IntelliSense ve hata ayıklama dahil .NET Core 'u tam olarak destekler. VS Code basit bir düzenleyici olduğundan, Docker CLı ve [.NET Core CLI](../../../core/tools/index.md)birlikte Mac üzerinde Kapsayıcılı uygulamalar geliştirmek için kullanabilirsiniz. Ayrıca, IntelliSense desteği sağlayan alt Lime, Emacs, VI ve açık kaynaklı OmniSharp projesi gibi üçüncü taraf düzenleyicilerle de .NET Core 'u hedefleyebilirsiniz.

Ides ve düzenleyicilere ek olarak, desteklenen tüm platformlar için [.NET Core CLI](../../../core/tools/index.md) kullanabilirsiniz.

## <a name="using-containers-for-new-green-field-projects"></a>Yeni ("yeşil-alan") projeler için kapsayıcıları kullanma

Kapsayıcılar genellikle bir mikro hizmet mimarisi ile birlikte kullanılır, ancak her türlü mimari kalıbı izleyen Web uygulamalarını veya hizmetlerini kapsayıtabilecek de kullanılabilirler. Windows kapsayıcılarında .NET Framework kullanabilirsiniz, ancak .NET Core 'un modülerliği ve hafif doğası, kapsayıcılar ve mikro hizmet mimarileri için mükemmel hale getirir. Bir kapsayıcı oluşturduğunuzda ve dağıttığınızda, bu görüntü .NET Core ile .NET Framework göre daha küçüktür.

## <a name="create-and-deploy-microservices-on-containers"></a>Kapsayıcılar üzerinde mikro hizmetler oluşturma ve dağıtma

Düz süreçler kullanarak mikro hizmet tabanlı uygulamalar (kapsayıcılar olmadan) oluşturmak için geleneksel .NET Framework kullanabilirsiniz. Bu şekilde, .NET Framework zaten yüklenmiş ve süreçler genelinde paylaşıldığı için, süreçler hafif ve hızlı bir şekilde başlatılır. Ancak kapsayıcıları kullanıyorsanız, geleneksel .NET Framework görüntüsü de Windows Server Core ' a dayalıdır ve bu, mikro hizmetler arası bir yaklaşım için çok daha ağır hale gelir. Ancak ekipler, .NET Framework kullanıcılara da deneyimi geliştirmek üzere fırsatlar arıyor. Son olarak, [Windows Server çekirdek kapsayıcısı görüntülerinin boyutu %40 daha küçük > kadar azaltılmıştır](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller). 

Diğer yandan, .NET Core basit olduğundan, kapsayıcıları temel alan mikro hizmetlere dayalı bir sistem kullanıyorsanız, .NET Core en iyi adaydır. Ayrıca, Linux veya Windows nano Server için ilgili kapsayıcı görüntüleri yalın ve küçüktür, kapsayıcılar açık ve hızlı bir şekilde başlatılır.

Mikro hizmet mümkün olduğunca küçük olacak şekilde, küçük bir parmak izine sahip olmak, küçük bir [ilgi alanına sahip](https://en.wikipedia.org/wiki/Domain-driven_design)olmak, küçük bir sorun olduğunu göstermek ve hızlı bir şekilde başlayabilmek ve durdurmak için en az bir değer olması gerekir: Bu gereksinimler için, .NET Core kapsayıcı görüntüsü gibi küçük ve hızlı-örnek oluşturma kapsayıcı görüntülerini kullanmak isteyeceksiniz.

Mikro hizmetler mimarisi Ayrıca bir hizmet sınırı genelinde teknolojileri karıştırabilmeniz için de sağlar. Bu, diğer mikro hizmetlerle birlikte çalışan yeni mikro hizmetler veya Node. js, Python, Java, GoLang veya diğer teknolojiler ile geliştirilen hizmetler için aşamalı olarak .NET Core 'a geçiş sağlar.

## <a name="deploying-high-density-in-scalable-systems"></a>Ölçeklenebilir sistemlerde yüksek yoğunluklu dağıtım

Kapsayıcı tabanlı sisteminizin en iyi yoğunluğu, ayrıntı düzeyi ve performansa ihtiyacı olduğunda, .NET Core ve ASP.NET Core en iyi seçenekleriniz vardır. ASP.NET Core geleneksel .NET Framework en fazla on kat daha hızlıdır ve bu, bilinen mikro hizmetler için Java servinler, Go ve Node. js gibi diğer popüler sektör teknolojilerini de sağlar.

Bu özellikle, yüzlerce mikro hizmet (kapsayıcı) çalıştırdığınız mikro hizmet mimarileri için geçerlidir. Linux veya Windows nano 'daki ASP.NET Core görüntülerle (.NET Core çalışma zamanına bağlı olarak), sisteminizi çok daha az sayıda sunucu veya VM ile çalıştırarak, son olarak altyapı ve barındırma halinde maliyet tasarrufu yapabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](general-guidance.md)
>[İleri](net-framework-container-scenarios.md)
