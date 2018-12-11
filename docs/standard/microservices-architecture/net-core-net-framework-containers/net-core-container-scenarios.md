---
title: .NET Core için Docker kapsayıcıları ne zaman
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET Core için Docker kapsayıcıları ne zaman
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b283916d6ae4d19fdc6a4f7976a3adbb66d26b2c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143416"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>.NET Core için Docker kapsayıcıları ne zaman

.NET Core modüler ve hafif yapısını kapsayıcılar için mükemmel bir hale getirir. Bir kapsayıcı başlatma dağıtırken, .NET Framework ile .NET Core çok daha küçük bir görüntüsüdür. Buna karşılık, .NET Framework için bir kapsayıcı kullanmak için görüntünüzü Windows Nano sunucu veya .NET Core için kullandığınız Linux görüntüleri daha çok daha ağır Windows Server Core görüntüyü temel gerekir.

Ayrıca, Linux veya Windows kapsayıcı görüntüleri ile sunucu uygulamaları dağıtabilirsiniz böylece .NET Core platformlar arası. Bununla birlikte, geleneksel .NET Framework kullanıyorsa, yalnızca Windows Server Core'da temelinde görüntülerini dağıtabilirsiniz.

.NET Core seçmek neden daha ayrıntılı bir açıklaması verilmiştir.

## <a name="developing-and-deploying-cross-platform"></a>Geliştirme ve platformlar arası dağıtma

Amacınız için .NET Framework yalnızca Windows desteklediğinden NET bir şekilde, doğru seçim (Linux ve Windows), Docker tarafından desteklenen çeşitli platformlarda çalışabilen bir uygulama (web uygulaması veya hizmeti) .NET Core ise.

.NET core, macOS geliştirme platformu olarak da destekler. Kapsayıcıları bir Docker konağına dağıttığınızda, ancak bu ana bilgisayar (şu anda) Linux veya Windows üzerinde temel alması gerekir. Örneğin, bir geliştirme ortamında, bir Mac üzerinde çalışan bir Linux VM kullanabilirsiniz

[Visual Studio](https://www.visualstudio.com/vs/) Windows için bir tümleşik geliştirme ortamı (IDE) sağlar ve Docker için geliştirmeyi destekler.

[Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/) macOS üzerinde çalışır ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio evrimi bir IDE. Bu da güçlü bir IDE kullanmak isteyen Mac makinelerinizde çalışan geliştiriciler için tercih edilen seçenek olmalıdır.

Ayrıca [Visual Studio Code](https://code.visualstudio.com/) (VS Code) macOS, Linux ve Windows. VS Code, .NET Core hata ayıklama ve IntelliSense dahil olmak üzere, tam olarak destekler. VS Code basit Düzenleyici olduğundan, kapsayıcılı uygulamaları Docker CLI ile birlikte Mac'te geliştirin olarak da kullanabilirsiniz ve [.NET Core komut satırı arabirimi (CLI)](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Ayrıca, Sublime, Emacs, VI ve IntelliSense desteği sağlayan açık kaynaklı OmniSharp proje gibi üçüncü taraf en düzenleyicileri ile .NET Core hedefleyebilirsiniz.

IDE'ler ve düzenleyicilerden ek olarak kullanabileceğiniz [.NET Core CLI](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) desteklenen tüm platformlar için Araçlar.

## <a name="using-containers-for-new-green-field-projects"></a>Yeni ("alanı yeşil") projeler için kapsayıcıları kullanma

Web uygulamaları veya herhangi bir mimari deseni izleyen Hizmetleri kapsayıcılı hale getirme için de kullanılabilir olsa da kapsayıcılar, mikro hizmet mimarisi ile birlikte sık kullanılan bloblardır. .NET Framework Windows kapsayıcıları ancak modülerlik kullanabilirsiniz ve .NET Core basit doğasını kapsayıcıları ve mikro hizmet mimarileri için mükemmel yapar. Bir kapsayıcı oluşturup görüntüsünü .NET Framework ile .NET Core çok daha küçük olur.

## <a name="creating-and-deploying-microservices-on-containers"></a>Oluşturma ve mikro hizmetler kapsayıcılarına dağıtma

Geleneksel .NET Framework düz işlemleri kullanarak mikro hizmet tabanlı uygulamalar (kapsayıcılar) olmadan oluşturmak için kullanabilirsiniz. Böylece, .NET Framework yüklü ve süreçler arasında paylaşılan işlemleri açık olan ve başlamak için hızlı. Ancak, kapsayıcıları kullanıyorsanız, görüntü geleneksel .NET Framework için de Windows Server Core'da dayalıdır ve, bir kapsayıcı üzerinde mikro hizmetler yaklaşımı çok ağır yapar.

Buna karşılık, .NET Core, .NET Core basit olduğu için kapsayıcılarında, temel bir mikro hizmet odaklı bir sistemi benimsemektedir en iyi adaydır. Ayrıca, ilgili kapsayıcı görüntülerini, Linux görüntüsü ya da Windows Nano görüntü yalın ve küçük kapsayıcıları açık hale getirme ve başlamak için hızlı.

Bir mikro hizmet, olabildiğince az olacak şekilde tasarlanmıştır: yedekleme dönen açık olması, küçük bir sınırlanmış bağlam sağlamak için küçük bir boyut için (DDD, kontrol [etki alanı Odaklı Tasarım](https://en.wikipedia.org/wiki/Domain-driven_design)), ilgilenilecek alanların küçük bir alanı temsil etmek için ve başlatabilmeniz için ve hızlı durdurun. Bu gereksinimleri için .NET Core kapsayıcı görüntüsü gibi küçük ve örneği hızlı kapsayıcı görüntülerini kullanmak isteyebilirsiniz.

Bir mikro hizmet mimarisi hizmet sınırında teknolojilerinin karışımı sağlar. Bu, aşamalı bir geçiş .NET Core, Node.js, Python, Java, GoLang veya diğer teknolojiler ile geliştirilen Hizmetleri veya diğer mikro hizmetler ile birlikte çalışan yeni mikro hizmetler için sağlar.

## <a name="deploying-high-density-in-scalable-systems"></a>Yüksek yoğunluklu ölçeklenebilir sistemlerini dağıtma

.NET Core ve ASP.NET Core, kapsayıcı tabanlı sisteminizi en iyi olası yoğunluğu, ayrıntı düzeyi ve performans gerektiğinde, en iyi seçenekleriniz şunlardır. ASP.NET Core on kata kadar daha hızlı bir şekilde ASP.NET geleneksel .NET Framework ve mikro hizmetler, Java servlet'ler, Git ve Node.js gibi diğer popüler sektör teknolojiler gidiyor.

Bu özellikle burada çalışan mikro hizmetler (kapsayıcılar) yüzlerce olabilir, mikro hizmet mimarileri için geçerlidir. (.NET Core çalışma zamanına göre) ASP.NET Core görüntülerinde ile Linux veya Windows Nano çok daha az sayıda sunucular veya VM'ler, sonuçta maliyetleri altyapısında kaydetme ve barındırma sisteminizle çalıştırabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](general-guidance.md)
>[İleri](net-framework-container-scenarios.md)