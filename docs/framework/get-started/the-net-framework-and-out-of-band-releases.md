---
title: .NET Framework ve Bant Dışı Yayınlar
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: a2dcd011548df857a1399c5bbdfe6ed33927672e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716397"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>.NET Framework ve Bant Dışı Yayınlar

.NET Framework, Windows Phone ve Windows Mağazası uygulamaları yanı sıra geleneksel masaüstü ve web uygulamaları ve kod tekrar kullanımını en üst düzeye çıkarmak üzere farklı platformlara uyum sağlamak için gelişiyor. Normal .NET Framework yayınlarımızın yanı sıra, platformlar arası geliştirmeyi geliştirmek veya yeni işlevsellikler eklemek için yeni özellikleri bant dışı (OOB) yayınlarız. Bu konu, .NET Framework ve OOB sürümlerinin gelecekteki yönelimlerini tartışır.

## <a name="advantages-of-oob-releases"></a>OOB sürümlerinin avantajları
 Yeni bileşenleri veya bant dışı bileşenlerin güncellemeleri, Microsoft'un .NET Framework'e daha sık güncelleme sağlamasına olanak tanır. Buna ek olarak, müşteri geri bildirimlerini toplayıp olabildiğince hızlı yanıtlayabiliyoruz.

 Uygulamanızda bir OOB özelliğini kullanırsanız, OOB derlemeleri uygulama paketinizle birlikte dağıtıldığından, kullanıcılarınızın uygulamanızı çalıştırmak için .NET Framework'ün son sürümünü yüklemeleri gerekmez.

## <a name="how-oob-packages-are-distributed"></a>OOB paketleri nasıl dağıtılır?
Çekirdek ortak dil çalışma zamanı (CLR) bileşenleri için OOB sürümleri, .NET için bir paket yöneticisi olan [NuGet](https://www.nuget.org/)aracılığıyla dağıtılır. NuGet, Visual Studio'daki Çözüm Gezgini'nden .NET Framework projelerinize kolaylıkla göz atmanıza ve kitaplıklar eklemenize olanak sağlar. NuGet, Visual Studio 2012'den itibaren tüm Visual Studio sürümleriyle birlikte gelir. NuGet 'in yüklü olup olmadığını görmek için, Visual Studio **Araçlar** menüsünde **NuGet Paket Yöneticisi** ' ni arayın. Yüklü değilse:

1. Visual Studio menü çubuğunda **Araçlar**, **Uzantılar ve güncelleştirmeler** ' i seçin (Visual Studio 2010 ' de **Uzantı Yöneticisi**' ni seçin).

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. **Çevrimiçi**, **NuGet Paket Yöneticisi**' ni ve ardından **İndir**' i seçin.

3. Karşıdan yükleme tamamlandıktan sonra Visual Studio'yu yeniden başlatın.

 Ayrıntılı yükleme yönergeleri için NuGet belgeleri Web sitesinde [NuGet yükleme](/nuget/install-nuget-client-tools) bölümüne bakın. NuGet hakkında daha fazla bilgi için bkz. [NuGet belgeleri](/nuget).

## <a name="using-a-nuget-oob-package"></a>NuGet OOB paketini kullanma
 NuGet yükledikten sonra, Visual Studio'da Çözüm Gezgini'ni kullanarak NuGet paketlerine göz atabilir ve başvurular ekleyebilirsiniz:

1. Visual Studio 'da projeniz için kısayol menüsünü açın ve ardından **NuGet Paketlerini Yönet**' i seçin. (Bu seçenek, **Proje** menüsünden de kullanılabilir.)

2. Sol bölmede **çevrimiçi**öğesini seçin.

3. Ön sürüm paketlerini kullanmak istiyorsanız, orta bölmedeki aşağı açılan liste kutusunda **yalnızca kararlı**yerine **ön sürümü dahil et** ' i seçin.

4. Sağ bölmede, kullanmak istediğiniz paketi bulmak için **arama** kutusunu kullanın. Bazı Microsoft paketleri, Microsoft .NET Framework logosu ile tanımlanır ve tümü Microsoft'u yayımcı olarak tanımlar.

 ![NuGet paket yöneticisini gösteren ekran görüntüsü.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

 Daha önce belirtildiği gibi, OOB paketi kullanan bir uygulamayı dağıttığınızda OOB derlemeleri, uygulama paketinizle birlikte sevk edilir.

## <a name="types-of-oob-releases"></a>OOB sürümlerinin türleri
 Genellikle, bir OOB paketi bir veya daha fazla yayın öncesi sürüm ve kararlı bir sürüm içerir. Bir ön sürümle birlikte gelen lisans genellikle yeniden dağıtıma izin vermez, ancak bir paketi denemenizi ve geri bildirim sağlamanıza olanak tanır. Geribildirim, pakete yapılan tüm güncelleştirmelere eklenmiştir. Son sürüm NuGet ile bir kararlı paket olarak dağıtılır ve NuGet paketini uygulamanızla yeniden dağıtmanıza olanak sağlayan bir lisans içerir. Kararlı paketler Microsoft tarafından desteklenir. Microsoft, IntelliSense desteğinin yanı sıra tüm paketler için blog gönderileri ve Forum yanıtları gibi diğer belge türlerini de sağlar. Bunlara ek olarak, kaynak kodu bazıları, ancak tüm paketlerle birlikte kullanılabilir olabilir. Yeni ve güncelleştirilmiş paketlerle ilgili duyurular için [.NET Framework bloguna](https://devblogs.microsoft.com/dotnet/)abone olabilirsiniz.

 Hem ön sürümü hem de kararlı paketleri bulmak için NuGet Paket Yöneticisi ' nde **ön sürümü Ekle** ' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](index.md)
