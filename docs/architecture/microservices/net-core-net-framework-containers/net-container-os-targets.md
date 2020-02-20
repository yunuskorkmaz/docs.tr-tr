---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET kapsayıcıları ile hedef işletim sistemi
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501858"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?

Docker tarafından desteklenen işletim sistemlerinin farklılığının yanı sıra .NET Framework ile .NET Core arasındaki farklılıklar söz konusu olduğunda, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.

Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz. Bu Windows sürümleri, sırasıyla .NET Framework veya .NET Core tarafından gerekebilecek, farklı Özellikler (Windows Server çekirdeği 'nde IIS ve Kestrel gibi şirket içinde barındırılan bir Web sunucusu) sağlar.

Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.

Şekil 3-1 ' de, kullanılan .NET Framework 'e bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Hangi .NET kapsayıcılarıyla kullanılacak işletim sistemini gösteren diyagram.](./media/net-container-os-targets/targeting-operating-systems.png)

**Şekil 3-1.** .NET Framework sürümüne bağlı olarak hedeflenecek işletim sistemleri

Eski .NET Framework uygulamalar dağıtıldığında, eski uygulamalarla ve IIS ile uyumlu olan Windows Server çekirdeğini hedeflemek gerekir, ancak daha büyük bir görüntü içerir. .NET Core uygulamaları dağıtıldığında, buluta iyileştirilmiş Windows nano Server 'ı hedefleyebilir, Kestrel kullanır ve daha hızlı başlar. Ayrıca, Linux 'yi desteklemenin yanı sıra alçam ve diğerlerini de kullanabilirsiniz. Ayrıca, Kestrel kullanır, daha küçüktür ve daha hızlı başlar.

Ayrıca, farklı bir Linux veya Microsoft tarafından sağlanmayan sürümlere sahip bir görüntü istediğiniz durumlarda kendi Docker görüntünüzü oluşturabilirsiniz. Örneğin, Docker için olmayan-yaygın bir senaryo olan geleneksel .NET Framework ve Windows Server Core üzerinde çalışan ASP.NET Core bir görüntü oluşturabilirsiniz.

> [!IMPORTANT]
> Windows Server çekirdek görüntülerini kullanırken, tam Windows görüntüleriyle karşılaştırıldığında bazı dll 'Lerin eksik olduğunu fark edebilirsiniz. Bu sorunu, bu [GitHub açıklamasında](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)belirtildiği gibi, görüntü derleme zamanında eksik dosyaları ekleyerek özel bir sunucu çekirdeği görüntüsü oluşturarak çözebilirsiniz.

Resim adını Dockerfile dosyanıza eklediğinizde, aşağıdaki örneklerde olduğu gibi, kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:

| Görüntü | Yorumlar |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3,1 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET Core 3,1 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler. <br/> Aspnetcore görüntüsünün ASP.NET Core için birkaç iyileştirmesi vardır. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3,1 çalışma zamanı-yalnızca Linux 'ta dedıon |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET Core 3,1 çalışma zamanı-yalnızca Windows nano Server 'da (Windows Server sürüm 1809) |

## <a name="additional-resources"></a>Ek kaynaklar

- **BitmapDecoder, eksik WindowsCodecsExt. dll nedeniyle başarısız oluyor (GitHub sorunu)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Önceki](container-framework-choice-factors.md)
> [İleri](official-net-docker-images.md)
