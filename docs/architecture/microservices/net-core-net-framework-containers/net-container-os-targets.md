---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | .NET kapsayıcıları ile hangi işletim sistemi hedef
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501858"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?

Docker tarafından desteklenen işletim sistemlerinin çeşitliliği ve .NET Framework ve .NET Core arasındaki farklar göz önüne alındığında, kullandığınız çerçeveye bağlı olarak belirli bir işletim sistemi ve belirli sürümleri hedeflemeniz gerekir.

Windows için Windows Server Core veya Windows Nano Server'ı kullanabilirsiniz. Bu Windows sürümleri, sırasıyla .NET Framework veya .NET Core tarafından ihtiyaç duyulabilecek farklı özellikler (Windows Server Core'da IIS, Nano Server'da Kestrel gibi kendi kendine barındırılan bir web sunucusuna karşı) sağlar.

Linux için, birden fazla dağıtım mevcuttur ve resmi .NET Docker görüntüleri (Debian gibi) desteklenir.

Şekil 3-1'de kullanılan .NET çerçevesine bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Hangi işletim sistemi yle kullanılacağını gösteren diyagram .NET kapsayıcıları.](./media/net-container-os-targets/targeting-operating-systems.png)

**Şekil 3-1.** .NET çerçevesinin sürümlerine bağlı olarak hedefolacak işletim sistemleri

Eski .NET Framework uygulamalarını dağıtırken, eski uygulamalar ve IIS ile uyumlu olan Windows Server Core'u hedeflemeniz gerekir, ancak daha büyük bir imaja sahiptir. .NET Core uygulamalarını dağıtırken, bulut en iyi duruma getirilmiş, Kerkenez kullanan ve daha küçük olan ve daha hızlı başlayan Windows Nano Server'ı hedefleyebilirsiniz. Debian, Alpine ve diğerlerini destekleyerek Linux'u da hedefleyebilirsiniz. Ayrıca Kerkenez kullanır, daha küçük, ve daha hızlı başlar.

Ayrıca, farklı bir Linux dağıtımını kullanmak istediğiniz veya Microsoft tarafından sağlanmayan sürümlere sahip bir resim istediğiniz durumlarda kendi Docker resminizi de oluşturabilirsiniz. Örneğin, ASP.NET Core'un geleneksel .NET Framework ve Windows Server Core üzerinde çalışan bir görüntü oluşturabilirsiniz, bu da Docker için çok yaygın olmayan bir senaryodur.

> [!IMPORTANT]
> Windows Server Core görüntülerini kullanırken, tam Windows görüntüleriyle karşılaştırıldığında bazı DL'lerin eksik olduğunu görebilirsiniz. Bu [GitHub yorumunda](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)belirtildiği gibi, resim oluşturma zamanında eksik dosyaları ekleyerek, özel bir Server Core görüntü oluşturarak bu sorunu çözmek mümkün olabilir.

Dockerfile dosyanıza görüntü adını eklediğinizde, aşağıdaki örneklerde olduğu gibi kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:

| Görüntü | Yorumlar |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3.1 çoklu mimari: Docker ana bilgisayara bağlı olarak Linux ve Windows Nano Server'ı destekler. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET Core 3.1 çoklu mimari: Docker ana bilgisayara bağlı olarak Linux ve Windows Nano Server'ı destekler. <br/> Aspnetcore görüntü ASP.NET Core için birkaç optimizasyonlar vardır. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3.1 yalnızca Linux Debian dağıtım da |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET Core 3.1 yalnızca Windows Nano Server'da çalışma zamanı (Windows Server sürüm 1809) |

## <a name="additional-resources"></a>Ek kaynaklar

- **BitmapDecoder WindowsCodecsExt.dll (GitHub sorunu) eksik nedeniyle başarısız olur**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Önceki](container-framework-choice-factors.md)
> [Sonraki](official-net-docker-images.md)
