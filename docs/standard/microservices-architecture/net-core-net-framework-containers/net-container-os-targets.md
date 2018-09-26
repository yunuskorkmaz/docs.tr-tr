---
title: Hedef .NET kapsayıcıları ile hangi işletim sistemi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Hedef .NET kapsayıcıları ile hangi işletim sistemi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b2ae1d2e732f152133dd8a8757b955e05cdd88eb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970831"
---
# <a name="what-os-to-target-with-net-containers"></a>Hedef .NET kapsayıcıları ile hangi işletim sistemi

Docker ve .NET Framework ve .NET Core arasındaki farklar tarafından desteklenen işletim sistemleri yelpazesi göz önünde bulundurulduğunda, belirli bir işletim sistemi ve kullanmakta olduğunuz framework bağlı olarak belirli sürümlerini hedefleyen.

Windows için Windows Server Core veya Windows Nano sunucu kullanabilirsiniz. Bu Windows sürümleri (Windows Server Core Kestrel Nano Sunucu'da gibi bir şirket içinde barındırılan web sunucusu yerine IIS) .NET Framework veya .NET Core tarafından sırasıyla gerekebilecek farklı özellikleri sağlar.

Linux için birden çok dağıtım paketlerini kullanılabilir ve (Debian gibi) resmi .NET Docker görüntüleri desteklenir.

Şekil 3-1'de kullanılan .NET framework bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Eski .NET Framework uygulamaları, sahip olduğunuz Windows Server Core hede için dağıtırken uyumlu eski uygulamaları ile IIS, daha büyük bir görüntü sahiptir. .NET Core uygulamaları dağıtırken, bulut için iyileştirilmiş, Kestrel kullanır ve daha küçük ve daha hızlı başlatılan Windows Nano sunucu, hedef alabilirsiniz. Ayrıca, Linux, Debian, Alpine ve diğer destekleyici hedefleyebilirsiniz. Ayrıca Kestrel kullanır ve daha küçük ve daha hızlı başlatılır.](./media/image1.png)

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
<td>Microsoft / dotnet:2.1-çalışma zamanı</td>
<td>.NET core 2.1 çok mimari: destekleyen Linux ve Docker konağı bağlı olarak Windows Nano sunucu.</td>
</tr>
<tr class="odd">
<td>Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı</td>
<td><p>ASP.NET Core 2.1 çok mimari: destekleyen Linux ve Docker konağı bağlı olarak Windows Nano sunucu.</p>
<p>ASP.NET Core için birkaç en iyi duruma getirme aspnetcore görüntüsü vardır.</p></td>
</tr>
<tr class="even">
<td>Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı-alpine</td>
<td>.NET core 2.1 çalışma zamanı üzerinde Linux Alpine distro yalnızca</td>
</tr>
<tr class="odd">
<td>Microsoft / dotnet:2.1-aspnetcore-çalışma zamanı-nanoserver-1803</td>
<td>.NET core 2.1 (Windows Server sürümü 1803) Windows Nano Sunucu'da salt çalışma zamanı</td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
[Önceki](container-framework-choice-factors.md)
[İleri](official-net-docker-images.md)
