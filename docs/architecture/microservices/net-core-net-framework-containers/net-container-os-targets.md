---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET kapsayıcıları ile hedef işletim sistemi
ms.date: 01/13/2021
ms.openlocfilehash: b128a7b98d7f46034a56314bd8cc6b4f5731f121
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957916"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?

Docker tarafından desteklenen işletim sistemlerinin farklılığının yanı sıra .NET Framework ile .NET 5 arasındaki farklılıklar söz konusu olduğunda, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.

Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz. Bu Windows sürümleri, sırasıyla .NET Framework veya .NET 5 tarafından gerekebilecek, farklı Özellikler (Windows Server Core 'ta IIS, Kestrel gibi şirket içinde barındırılan bir Web sunucusu) sağlar.

Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.

Şekil 3-1 ' de, kullanılan .NET Framework 'e bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Hangi .NET kapsayıcılarıyla kullanılacak işletim sistemini gösteren diyagram.](./media/net-container-os-targets/targeting-operating-systems.png)

**Şekil 3-1.** .NET Framework sürümüne bağlı olarak hedeflenecek işletim sistemleri

Eski .NET Framework uygulamalar dağıtıldığında, eski uygulamalarla ve IIS ile uyumlu olan Windows Server çekirdeğini hedeflemek gerekir, ancak daha büyük bir görüntü içerir. .NET 5 uygulamaları dağıttığınızda, buluta iyileştirilmiş Windows nano Server 'ı hedefleyebilir, Kestrel kullanır ve daha hızlı başlar. Ayrıca, Linux 'u destekleyebilir, alçam ve diğerlerini de kullanabilirsiniz. Ayrıca, Kestrel kullanır, daha küçüktür ve daha hızlı başlar.

Ayrıca, farklı bir Linux veya Microsoft tarafından sağlanmayan sürümlere sahip bir görüntü istediğiniz durumlarda kendi Docker görüntünüzü oluşturabilirsiniz. Örneğin, Docker için olmayan-yaygın bir senaryo olan geleneksel .NET Framework ve Windows Server Core üzerinde çalışan ASP.NET Core bir görüntü oluşturabilirsiniz.

Resim adını Dockerfile dosyanıza eklediğinizde, aşağıdaki örneklerde olduğu gibi, kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:

| Görüntü | Yorumlar |
|-------|----------|
| mcr.microsoft.com/dotnet/runtime:5.0 | .NET 5 çoklu mimari: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler. |
| mcr.microsoft.com/dotnet/aspnet:5.0 | ASP.NET Core 5,0 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler. <br/> Aspnetcore görüntüsünün ASP.NET Core için birkaç iyileştirmesi vardır. |
| mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim | .NET 5 çalışma zamanı-yalnızca Linux 'ta Delinde |
| mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809 | .NET 5 çalışma zamanı-yalnızca Windows nano Server 'da (Windows Server sürüm 1809) |

> [!div class="step-by-step"]
> [Önceki](container-framework-choice-factors.md) 
>  [Sonraki](official-net-docker-images.md)
