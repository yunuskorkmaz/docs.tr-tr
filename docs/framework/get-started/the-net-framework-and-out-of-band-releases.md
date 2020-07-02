---
title: .NET Framework ve bant dışı yayınlar
description: .NET ve bant dışı sürümler hakkında bilgi edinin. Yeni özellikler, platformlar arası geliştirmeyi geliştirmek veya yeni işlevsellik sunmak için bant dışı (OOB) serbest bırakılır.
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618772"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework ve bant dışı yayınlar

.NET Framework, UWP uygulamaları ve geleneksel masaüstü ve Web uygulamaları gibi farklı platformlara uyum sağlamak ve kod yeniden kullanımını en üst düzeye çıkarmak için geliştirilmiştir. Normal .NET Framework sürümlerinin yanı sıra, platformlar arası geliştirmeyi geliştirmek veya yeni işlevler sunmak için bant dışı (OOB) yeni özellikler de kullanıma sunulacaktır.

## <a name="advantages-of-oob-releases"></a>OOB sürümlerinin avantajları

Yeni bileşenleri veya bant dışı bileşenlere yapılan güncelleştirmelerin dağıtımı, Microsoft 'un .NET Framework için daha sık güncelleştirmeler sağlamasını sağlar. Buna ek olarak, müşteri geri bildirimlerini toplayıp olabildiğince hızlı yanıtlayabiliyoruz.

Uygulamanızda bir OOB özelliği kullandığınızda, OOB derlemeleri uygulama paketinizdeki dağıtımı yaptığından kullanıcılarınızın uygulamanızı çalıştırmak için .NET Framework en son sürümünü yüklemesi gerekmez.

## <a name="how-oob-packages-are-distributed"></a>OOB paketleri nasıl dağıtılır?

Çekirdek ortak dil çalışma zamanı (CLR) bileşenleri için OOB sürümleri, .NET için paket yöneticisi olan [NuGet](https://www.nuget.org/)aracılığıyla dağıtılır. NuGet, Visual Studio içinden kolayca .NET Framework projelerine gözatıp ekleme ve kitaplıklara ekleme yapmanızı sağlar. NuGet Paket Yöneticisi, Visual Studio 2012 ile başlayan tüm Visual Studio sürümlerinde bulunur. Visual Studio 'daki **Araçlar** menüsünde **NuGet Paket Yöneticisi** ' ni arayın. Yüklü değilse, [NuGet 'ı yükleme](/nuget/install-nuget-client-tools)yönergelerini izleyin. NuGet hakkında daha fazla bilgi için bkz. [NuGet belgeleri](/nuget).

## <a name="use-a-nuget-oob-package"></a>NuGet OOB paketini kullanma

NuGet Paket Yöneticisi yüklüyse, Visual Studio 'da Çözüm Gezgini kullanarak NuGet paketlerine gözatıp başvuruları ekleyebilirsiniz:

1. Visual Studio 'da projeniz için kısayol menüsünü açın ve ardından **NuGet Paketlerini Yönet**' i seçin. (Bu seçenek, **Proje** menüsünden de kullanılabilir.)

2. Sol bölmede **çevrimiçi**öğesini seçin.

3. Ön sürüm paketlerini kullanmak istiyorsanız, orta bölmedeki aşağı açılan liste kutusunda **yalnızca kararlı**yerine **ön sürümü dahil et** ' i seçin.

4. Sağ bölmede, kullanmak istediğiniz paketi bulmak için **arama** kutusunu kullanın. Bazı Microsoft paketleri, Microsoft .NET Framework logosu ile tanımlanır ve tümü Microsoft'u yayımcı olarak tanımlar.

![NuGet Paket Yöneticisi.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Daha önce belirtildiği gibi, OOB paketi kullanan bir uygulamayı dağıttığınızda OOB derlemeleri, uygulama paketinizle birlikte sevk edilir.

## <a name="types-of-oob-releases"></a>OOB sürümlerinin türleri

Genellikle, bir OOB paketi bir veya daha fazla yayın öncesi sürüm ve kararlı bir sürüm içerir. Bir ön sürümle birlikte gelen lisans genellikle yeniden dağıtıma izin vermez, ancak bir paketi denemenizi ve geri bildirim sağlamanıza olanak tanır. Geribildirim, pakete yapılan tüm güncelleştirmelere eklenmiştir. Son sürüm NuGet ile bir kararlı paket olarak dağıtılır ve NuGet paketini uygulamanızla yeniden dağıtmanıza olanak sağlayan bir lisans içerir. Kararlı paketler Microsoft tarafından desteklenir. Microsoft, IntelliSense desteğinin yanı sıra tüm paketler için blog gönderileri ve Forum yanıtları gibi diğer belge türlerini de sağlar. Bunlara ek olarak, kaynak kodu bazıları, ancak tüm paketlerle birlikte kullanılabilir olabilir. Yeni ve güncelleştirilmiş paketlerle ilgili duyurular için [.NET Framework bloguna](https://devblogs.microsoft.com/dotnet/)abone olabilirsiniz.

Hem ön sürümü hem de kararlı paketleri bulmak için NuGet Paket Yöneticisi 'nde **ön sürümü dahil et** ' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanmaya başlama](index.md)
