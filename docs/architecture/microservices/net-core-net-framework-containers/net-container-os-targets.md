---
title: .NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | .NET kapsayıcıları ile hedef işletim sistemi
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296511"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET kapsayıcıları ile hangi işletim sistemi hedeflenmelidir?

Docker tarafından desteklenen işletim sistemlerinin farklılığının yanı sıra .NET Framework ile .NET Core arasındaki farklılıklar söz konusu olduğunda, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.

Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz. Bu Windows sürümleri, sırasıyla .NET Framework veya .NET Core tarafından gerekebilecek, farklı Özellikler (Windows Server çekirdeği 'nde IIS ve Kestrel gibi şirket içinde barındırılan bir Web sunucusu) sağlar.

Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.

Şekil 3-1 ' de, kullanılan .NET Framework 'e bağlı olarak olası işletim sistemi sürümünü görebilirsiniz.

![Eski .NET Framework uygulamalar dağıtıldığında, eski uygulamalarla ve IIS ile uyumlu Windows Server çekirdeğini hedeflemek için daha büyük bir görüntü vardır. .NET Core uygulamaları dağıtıldığında, buluta iyileştirilmiş Windows nano Server 'ı hedefleyebilir, Kestrel kullanır ve daha hızlı başlar. Ayrıca, Linux 'yi desteklemenin yanı sıra alçam ve diğerlerini de kullanabilirsiniz. Ayrıca Kestrel kullanır ve daha hızlı başlatılır.](./media/image1.png)

**Şekil 3-1.** .NET Framework sürümüne bağlı olarak hedeflenecek işletim sistemleri

Ayrıca, farklı bir Linux veya Microsoft tarafından sağlanmayan sürümlere sahip bir görüntü istediğiniz durumlarda kendi Docker görüntünüzü oluşturabilirsiniz. Örneğin, Docker için olmayan-yaygın bir senaryo olan geleneksel .NET Framework ve Windows Server Core üzerinde çalışan ASP.NET Core bir görüntü oluşturabilirsiniz.

Resim adını Dockerfile dosyanıza eklediğinizde, aşağıdaki örneklerde olduğu gibi, kullandığınız etikete bağlı olarak işletim sistemini ve sürümü seçebilirsiniz:

<table>
<thead>
<tr class="header">
<th>Görüntü</th>
<th>Açıklamalar</th>
</tr>
</thead>
<tbody>
<tr>
<td>mcr.microsoft.com/dotnet/core/runtime:2.2</td>
<td>.NET Core 2,2 Multi-Architecture: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2</td>
<td><p>ASP.NET Core 2,2 çoklu mimari: Docker konağına bağlı olarak Linux ve Windows nano Server 'ı destekler.</p>
<p>Aspnetcore görüntüsünün ASP.NET Core için birkaç iyileştirmesi vardır.</p></td>
</tr>
<tr class="even">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</td>
<td>.NET Core 2,2 çalışma zamanı-yalnızca Linux alp Deon</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</td>
<td>.NET Core 2,2 çalışma zamanı-yalnızca Windows nano Server 'da (Windows Server sürüm 1803)</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [Önceki](container-framework-choice-factors.md)İleri
> [](official-net-docker-images.md)
