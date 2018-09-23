---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 74b3749077fdb375f84ddacd98221aa4afcf2f67
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577854"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: Docker için kullanılacak .NET çerçeveleri

Aşağıdaki tabloda karar .NET Framework veya .NET Core kullanıp kullanmayacağınızı özetler. Linux kapsayıcıları için Linux tabanlı Docker konakları (VM'ler veya sunucular) gerekir ve Docker ana bilgisayarları (VM'ler veya sunucular) tabanlı Windows kapsayıcıları için Windows Server ihtiyacınız olduğunu unutmayın.

> [!IMPORTANT]
> Geliştirme makineleriniz bir Docker konağı, Linux veya Windows çalıştırılır. İlgili mikro hizmetler ve birlikte bir çözümde test çalıştırmak istediğiniz tüm aynı kapsayıcı platformu üzerinde çalıştırmanız gerekir.

<table>
<thead>
<tr class="header">
<th><strong>Mimari / uygulama yazın</strong></th>
<th><strong>Linux kapsayıcıları</strong></th>
<th><strong>Windows kapsayıcıları</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Kapsayıcıları çalıştırma</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Tek parçalı uygulama</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Sınıfının en iyi performans ve ölçeklenebilirlik</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Windows Server kapsayıcıları için eski uygulama ("alanı brown") geçiş</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Yeni kapsayıcı tabanlı geliştirme ("alanı yeşil")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET core (önerilir)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, Web API 2 ve Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>SignalR Hizmetleri</td>
<td>.NET core 2.1 veya üzeri bir sürüm</td>
<td><p>.NET Framework</p>
<p>.NET core 2.1 veya üzeri bir sürüm</p></td>
</tr>
<tr class="odd">
<td>WCF, WF ve diğer eski çerçeveleri</td>
<td>WCF .NET core'da (yalnızca WCF istemci kitaplığı)</td>
<td><p>.NET Framework</p>
<p>WCF .NET core'da (yalnızca WCF istemci kitaplığı)</p></td>
</tr>
<tr class="even">
<td>Azure hizmetlerinin tüketiminin</td>
<td><p>.NET Core</p>
<p>(sonunda tüm Azure Hizmetleri İstemci SDK'ları için .NET Core sağlar)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(sonunda tüm Azure Hizmetleri İstemci SDK'ları için .NET Core sağlar)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
[Önceki](net-framework-container-scenarios.md)
[İleri](net-container-os-targets.md)
