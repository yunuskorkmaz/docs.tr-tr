---
title: "Ne zaman Docker kapsayıcıları için .NET Core seçin"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ne zaman Docker kapsayıcıları için .NET Core seçin"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7e2322bab7937c41d4659fefef11c8937d5eae7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Ne zaman Docker kapsayıcıları için .NET Core seçin

.NET Core modülerlik ve basit yapısını kapsayıcıları için ideal hale getirir. Dağıtma ve bir kapsayıcı başlatma görüntüsünü .NET çerçevesi ile .NET Core ile çok daha küçük olur. Buna karşılık, .NET Framework için bir kapsayıcı kullanmak için görüntünüzü Windows Nano Server veya .NET Core için kullandığınız Linux görüntüleri daha çok daha ağır Windows Server Core görüntüyü temel gerekir.

Ayrıca, Linux veya Windows kapsayıcı görüntü ile sunucu uygulamaları dağıtabilmek için .NET Core platformlar arası ' dir. Ancak, geleneksel .NET Framework'te kullanıyorsanız, yalnızca Windows Server Core üzerinde görüntülerini dağıtabilirsiniz.

.NET Core seçmek neden daha ayrıntılı bir açıklaması verilmiştir.

## <a name="developing-and-deploying-cross-platform"></a>Geliştirme ve platform dağıtma

Amacınız için .NET Framework yalnızca Windows desteklediğinden Açıkçası, doğru seçim (Linux ve Windows), Docker tarafından desteklenen birden çok platformu üzerinde çalışan bir uygulama (web uygulaması veya hizmeti) .NET Core ise.

.NET core macOS geliştirme platformu olarak da destekler. Kapsayıcıları bir Docker konağına dağıttığınızda, ancak bu ana bilgisayar (şu anda) Linux veya Windows üzerinde temel alması gerekir. Örneğin, bir geliştirme ortamında, Mac'te çalışan bir Linux VM kullanabilirsiniz

[Visual Studio](https://www.visualstudio.com/) için Windows tümleşik geliştirme ortamı (IDE) sağlar ve Docker için geliştirmeyi destekler. 

[Mac için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/) bir IDE içinde macOS çalıştıran Xamarin Studio evrimi ve Docker mid-2017 bu yana destekler.

Aynı zamanda [Visual Studio Code](https://code.visualstudio.com/) (VS Code) macOS, Linux ve Windows üzerinde. VS Code .NET Core ve hata ayıklama IntelliSense dahil olmak üzere, tam olarak destekler. VS Code basit bir düzenleyici olduğundan, Docker CLI ile birlikte Mac kapsayıcılı uygulamaları geliştirmek için kullanabilirsiniz ve [.NET Core komut satırı arabirimi (CLI) araçları](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Ayrıca, Sublime Text, Emacs, VI ve .NET dilleri için IntelliSense desteği sağlayan açık kaynak OmniSharp proje gibi üçüncü taraf en düzenleyicileri ile .NET Core hedefleyebilirsiniz. IDE ve düzenleyiciler ek olarak, .NET Core CLI desteklenen tüm platformlar için kullanabilirsiniz.

## <a name="using-containers-for-new-green-field-projects"></a>Yeni ("alanı yeşil") projeler için kapsayıcıları kullanma

Web uygulamaları veya herhangi bir mimari modeliyle izleyin Hizmetleri containerize için de kullanılabilir olsa da kapsayıcıları genellikle mikro mimarisi ile birlikte kullanılır. .NET Core basit yapısını kapsayıcıları ve mikro mimarileri için mükemmel bir yapar ve .NET Framework Windows kapsayıcıları ancak modülerlik kullanabilirsiniz. Oluşturduğunuzda ve bir kapsayıcıyı dağıtmak görüntüsünü kadar ile .NET çerçevesi ile .NET çekirdek küçüktür.

## <a name="creating-and-deploying-microservices-on-containers"></a>Oluşturma ve mikro kapsayıcılarında dağıtma

Geleneksel .NET Framework düz işlemleri kullanarak mikro tabanlı uygulamaları (olmadan kapsayıcıları) oluşturmak için kullanabilirsiniz. Böylece, .NET Framework zaten yüklü ve süreçler arasında paylaşılan çünkü işlemleri açık olan ve başlatmak için hızlı. Ancak, kapsayıcıları kullanıyorsanız, görüntünün geleneksel .NET Framework için Windows Server Core üzerinde temel alır ve, mikro üzerinde kapsayıcıları yaklaşım için çok yoğun yapar.

Buna karşılık, .NET Core .NET Core basit olduğundan kapsayıcılara göre tabanlı mikro odaklı bir sistem benimsemenin, en iyi adaydır. Ayrıca, Linux veya Windows Nano görüntüsüne ya da kendi ilgili kapsayıcı görüntüleri yalın ve başlatmak için hızlı ve küçük kapsayıcıları açık hale getirme.

Bir mikro hizmet olabildiğince küçük olacak şekilde tasarlanmıştır: Yukarı dönmesini açık olması için bir küçük ilişkisindeki bağlamı, sorunları, küçük bir alanı temsil eder ve hızlı durdurmak ve başlatmak olması için küçük bir yer sağlamak için. Bu gereksinimleri için .NET Core kapsayıcı görüntü gibi küçük ve örneği hızlı kapsayıcı görüntüleri kullanmak istersiniz.

Mikro mimarisi teknolojileri hizmet sınırından karışık sağlar. Bu, .NET Core için aşamalı bir geçiş için diğer mikro veya Node.js, Python, Java, GoLang veya diğer teknolojiler ile geliştirilen Hizmetleri ile birlikte çalışma yeni mikro sağlar.

## <a name="deploying-high-density-in-scalable-systems"></a>Yüksek yoğunluklu ölçeklenebilir sistemleri dağıtma

Kapsayıcı tabanlı sisteminizin en iyi olası yoğunluğu, ayrıntı düzeyi ve performans gerektiğinde, .NET Core ve ASP.NET Core en iyi seçenekleriniz şunlardır. ASP.NET Core en fazla on kez geleneksel .NET Framework ASP.NET hızlıdır ve diğer popüler endüstri teknolojileri Java servlets, Git ve Node.js gibi mikro için yol açar.

Bu özellikle çalıştıran mikro (kapsayıcı) yüzlerce olduğu mikro mimari için geçerlidir. (.NET çekirdeği Çalışma Zamanı Modülü) ASP.NET Core görüntülerini ile Linux veya Windows Nano, çok daha az sayıda sunucular veya VM'ler, sonuçta altyapısında maliyetleri kaydetme ve barındırma sisteminizle çalıştırabilirsiniz.


>[!div class="step-by-step"]
[Önceki] (genel-guidance.md) [sonraki] (net-framework-kapsayıcı-scenarios.md)
