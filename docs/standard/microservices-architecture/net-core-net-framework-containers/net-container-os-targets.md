---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 14a0fb7cd9ecb8dfd5369da6f6bd5b47b4aea37a
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921305"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?

Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri yelpazesi göz önünde bulundurulduğunda, belirli bir işletim sistemi ve kullanmakta olduğunuz framework bağlı olarak belirli sürümlerini hedefleyen.

Windows için Windows Server Core veya Windows Nano sunucu kullanabilirsiniz. Bu Windows sürümleri (Windows Server Core Kestrel Nano Sunucu'da gibi bir şirket içinde barındırılan web sunucusu yerine IIS) .NET Framework veya .NET Core tarafından sırasıyla gerekebilecek farklı özellikleri sağlar.

Linux için birden çok dağıtım paketlerini kullanılabilir ve (Debian gibi) resmi .NET Docker görüntüleri desteklenir.

Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Windows Server Core hedeflemek için sahip olduğunuz eski .NET Framework uygulamaları dağıtırken uyumlu eski uygulamaları ile IIS, daha büyük bir görüntü sahiptir. .NET Core uygulamaları dağıtırken, bulut için iyileştirilmiş, Kestrel kullanır ve daha küçük ve daha hızlı başlatılan Windows Nano sunucu, hedef alabilirsiniz. Ayrıca, Linux, Debian, Alpine ve diğer destekleyici hedefleyebilirsiniz. Ayrıca Kestrel kullanır ve daha küçük ve daha hızlı başlatılır.](./media/image1.png)

**Şekil 3-1.** Bağlı olarak .NET Framework sürümlerini hedeflemek için işletim sistemleri

Farklı bir Linux distro kullanmak istediğiniz veya görüntü Microsoft tarafından sağlanmayan sürümleriyle istediğiniz durumlarda kendi Docker görüntünüzü de oluşturabilirsiniz. Örneğin, geleneksel .NET Framework ve Docker olmayan şekilde yaygın senaryodur Windows Server Core üzerinde çalışan ASP.NET Core ile bir görüntü oluşturabilirsiniz.

Görüntü adı, Dockerfile dosyasına eklediğinizde, işletim sistemi ve sürümüne göre aşağıdaki örneklerde olduğu gibi kullanın etiketi seçebilirsiniz:

<table>
<thead>
<tr class="header">
<th>Görüntü</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr>
<td>MCR.microsoft.com/dotnet/Core/Runtime:2.2</td>
<td>.NET core 2.2 çok mimarisi: Docker konağı bağlı olarak, Linux ve Windows Nano sunucu destekler.</td>
</tr>
<tr class="odd">
<td>MCR.microsoft.com/dotnet/Core/ASPNET:2.2</td>
<td><p>ASP.NET Core 2.2 çok mimarisi: Docker konağı bağlı olarak, Linux ve Windows Nano sunucu destekler.</p>
<p>ASP.NET Core için birkaç en iyi duruma getirme aspnetcore görüntüsü vardır.</p></td>
</tr>
<tr class="even">
<td>MCR.microsoft.com/dotnet/Core/ASPNET:2.2-Alpine</td>
<td>.NET core 2.2 Alpine Linux distro'üzerinde salt çalışma zamanı</td>
</tr>
<tr class="odd">
<td>MCR.microsoft.com/dotnet/Core/ASPNET:2.2-nanoserver-1803</td>
<td>.NET core 2.2 (Windows Server sürümü 1803) Windows Nano Sunucu'da salt çalışma zamanı</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [Önceki](container-framework-choice-factors.md)
> [İleri](official-net-docker-images.md)