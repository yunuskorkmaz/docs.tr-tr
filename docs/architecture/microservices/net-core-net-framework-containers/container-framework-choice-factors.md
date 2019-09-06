---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296536"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: Docker için kullanılacak .NET çerçeveleri

Aşağıdaki karar tablosu .NET Framework veya .NET Core 'un kullanılıp kullanılmayacağını özetler. Linux kapsayıcılarında, Linux tabanlı Docker konakları (VM 'Ler veya sunucular) gerektiğini ve Windows kapsayıcıları için Windows Server tabanlı Docker konaklarının (VM 'Ler veya sunucular) gerekli olduğunu unutmayın.

> [!IMPORTANT]
> Geliştirme makineleriniz, Linux veya Windows 'un bulunduğu bir Docker ana bilgisayarı çalıştırır. Çalıştırmak ve tek bir çözümde birlikte test etmek istediğiniz ilgili mikro hizmetler, tümünün aynı kapsayıcı platformunda çalıştırılması gerekir.

<table>
<thead>
<tr class="header">
<th><strong>Mimari/uygulama türü</strong></th>
<th><strong>Linux kapsayıcıları</strong></th>
<th><strong>Windows kapsayıcıları</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Kapsayıcılar üzerinde mikro hizmetler</td>
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
<td>Sınıfının en iyisi performansı ve ölçeklenebilirliği</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Windows Server eski uygulaması ("kahverengi-Field") kapsayıcılara geçiş</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Yeni kapsayıcı tabanlı geliştirme ("yeşil-alan")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (önerilir)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, Web API 2 ve Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>SignalR Hizmetleri</td>
<td>.NET Core 2,1 veya üzeri sürümü</td>
<td><p>.NET Framework</p>
<p>.NET Core 2,1 veya üzeri sürümü</p></td>
</tr>
<tr class="odd">
<td>WCF, WF ve diğer eski çerçeveler</td>
<td>.NET Core 'da WCF (yalnızca WCF istemci kitaplığı)</td>
<td><p>.NET Framework</p>
<p>.NET Core 'da WCF (yalnızca WCF istemci kitaplığı)</p></td>
</tr>
<tr class="even">
<td>Azure hizmetleri kullanımı</td>
<td><p>.NET Core</p>
<p>(sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Önceki](net-framework-container-scenarios.md)İleri
>[](net-container-os-targets.md)
