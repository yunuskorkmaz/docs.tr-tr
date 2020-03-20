---
title: .NET Framework ve Out-of-Band Bültenleri
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181572"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework ve bant dışı sürümler

.NET Framework, UWP uygulamaları ve geleneksel masaüstü ve web uygulamaları gibi farklı platformları barındıracak ve kodun yeniden kullanımını en üst düzeye çıkarmak için gelişmiştir. Düzenli .NET Framework sürümlerine ek olarak, platformlar arası geliştirmeyi geliştirmek veya yeni işlevsellik sağlamak için bant (OOB) dışında yeni özellikler serbest bırakılır.

## <a name="advantages-of-oob-releases"></a>OOB sürümlerinin avantajları

Yeni bileşenlerin veya bileşenlerin bant dışına güncelleştirmeler gönderme, Microsoft'un .NET Framework'de daha sık güncelleştirmeler sağlamasına olanak tanır. Buna ek olarak, müşteri geri bildirimlerini toplayıp olabildiğince hızlı yanıtlayabiliyoruz.

Uygulamanızda bir OOB özelliği kullandığınızda, oob derlemeleri uygulama paketinizle dağıtıldığı için uygulamanızı çalıştırmak için kullanıcılarınızın .NET Framework'ün en son sürümünü yüklemesi gerekmez.

## <a name="how-oob-packages-are-distributed"></a>OOB paketleri nasıl dağıtılır?

Çekirdek ortak dil çalışma zamanı (CLR) bileşenleri için OOB sürümleri [NuGet](https://www.nuget.org/)aracılığıyla teslim edilir , hangi .NET için paket yöneticisidir. NuGet, .NET Framework projelerinize Visual Studio içinden kolayca kitaplıklar eklemenizi ve göz atmanızı sağlar. NuGet Package Manager Visual Studio 2012 ile başlayan Visual Studio tüm sürümleri ile birlikte. Visual Studio'daki **Araçlar** menüsünde **NuGet Paket Yöneticisi'ni** arayın. Yüklü değilse, [NuGet'i yükleme](/nuget/install-nuget-client-tools)yönergelerini izleyin. NuGet hakkında daha fazla bilgi için [NuGet dokümanlarına](/nuget)bakın.

## <a name="use-a-nuget-oob-package"></a>NuGet OOB paketi kullanın

NuGet Paket Yöneticisi yüklüyse, Visual Studio'da Solution Explorer'ı kullanarak NuGet paketlerine göz atabilir ve referans ekleyebilirsiniz:

1. Visual Studio'da projenizin kısayol menüsünü açın ve ardından **NuGet Paketlerini Yönet'i**seçin. (Bu seçenek **Proje** menüsünden de kullanılabilir.)

2. Sol **bölmede, Çevrimiçi'yi**seçin.

3. Yayın öncesi paketleri kullanmak istiyorsanız, orta bölmedeki açılır liste kutusunda Yalnızca **Kararlı**yerine **Ön Sürüm'ü ekle'yi** seçin.

4. Sağ bölmede, kullanmak istediğiniz paketi bulmak için **Arama** kutusunu kullanın. Bazı Microsoft paketleri, Microsoft .NET Framework logosu ile tanımlanır ve tümü Microsoft'u yayımcı olarak tanımlar.

![Nuget Paket Yöneticisi.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Daha önce belirtildiği gibi, OOB paketi kullanan bir uygulamayı dağıttığınızda OOB derlemeleri, uygulama paketinizle birlikte sevk edilir.

## <a name="types-of-oob-releases"></a>OOB sürümlerinin türleri

Genellikle, bir OOB paketi bir veya daha fazla yayın öncesi sürüm ve kararlı bir sürüm içerir. Ön sürümle birlikte olan lisans genellikle yeniden dağıtıma izin vermez, ancak bir paketi denemenize ve geri bildirim sağlamanıza olanak tanır. Geribildirim, pakete yapılan tüm güncelleştirmelere eklenmiştir. Son sürüm NuGet ile bir kararlı paket olarak dağıtılır ve NuGet paketini uygulamanızla yeniden dağıtmanıza olanak sağlayan bir lisans içerir. Kararlı paketler Microsoft tarafından desteklenir. Microsoft, Tüm paketler için intelliSense desteğinin yanı sıra blog gönderileri ve forum yanıtları gibi diğer belge türlerini de sağlar. Buna ek olarak, kaynak kodu bazı, ancak tüm paketleri ile kullanılabilir. Yeni ve güncellenmiş paketlerle ilgili duyurular için [.NET Framework Blog'a](https://devblogs.microsoft.com/dotnet/)abone olabilirsiniz.

Hem ön sürüm hem de kararlı paketleri bulmak için NuGet Paket Yöneticisi'nde **Ön Sürüm Ekle'yi** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](index.md)
