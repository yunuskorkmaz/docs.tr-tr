---
title: ".NET Framework ve Bant Dışı Yayınlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c79326634a24ddcc9aed71fca018c69c36c94db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="the-net-framework-and-out-of-band-releases"></a>.NET Framework ve Bant Dışı Yayınlar
.NET Framework, Windows Phone ve Windows Mağazası uygulamaları yanı sıra geleneksel masaüstü ve web uygulamaları ve kod tekrar kullanımını en üst düzeye çıkarmak üzere farklı platformlara uyum sağlamak için gelişiyor. Normal .NET Framework yayınlarımızın yanı sıra, platformlar arası geliştirmeyi geliştirmek veya yeni işlevsellikler eklemek için yeni özellikleri bant dışı (OOB) yayınlarız. Bu konu, .NET Framework ve OOB sürümlerinin gelecekteki yönelimlerini tartışır.  
  
## <a name="advantages-of-oob-releases"></a>OOB sürümlerinin avantajları  
 Yeni bileşenleri veya bant dışı bileşenlerin güncellemeleri, Microsoft'un .NET Framework'e daha sık güncelleme sağlamasına olanak tanır. Buna ek olarak, müşteri geri bildirimlerini toplayıp olabildiğince hızlı yanıtlayabiliyoruz.  
  
 Uygulamanızda bir OOB özelliğini kullanırsanız, OOB derlemeleri uygulama paketinizle birlikte dağıtıldığından, kullanıcılarınızın uygulamanızı çalıştırmak için .NET Framework'ün son sürümünü yüklemeleri gerekmez.  
  
## <a name="how-oob-packages-are-distributed"></a>OOB paketleri nasıl dağıtılır?  
Çekirdek ortak dil çalışma zamanı (CLR) bileşenlerini OOB sürümleri aracılığıyla teslim edilir [NuGet](https://www.nuget.org/), .NET için bir paket Yöneticisi olduğu. NuGet, Visual Studio'daki Çözüm Gezgini'nden .NET Framework projelerinize kolaylıkla göz atmanıza ve kitaplıklar eklemenize olanak sağlar. NuGet, Visual Studio 2012'den itibaren tüm Visual Studio sürümleriyle birlikte gelir. NuGet'ın yüklü olup olmadığını görmek için Ara **kitaplık Paket Yöneticisi** Visual Studio üzerinde **Araçları** menüsü. Yüklü değilse:  
  
1.  Visual Studio menü çubuğunda seçin **Araçları**, **Uzantılar ve güncelleştirmeler** (Visual Studio 2010'da seçin **Uzantı Yöneticisi**).  
  
     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.  
  
2.  Seçin **çevrimiçi**, **NuGet Paket Yöneticisi**ve ardından **karşıdan**.  
  
3.  Karşıdan yükleme tamamlandıktan sonra Visual Studio'yu yeniden başlatın.  
  
 Ayrıntılı yükleme yönergeleri için bkz: [yükleme NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) NuGet belgeleri Web üzerinde. NuGet hakkında daha fazla bilgi için bkz: [NuGet belgelerine](http://docs.nuget.org/).  
  
## <a name="using-a-nuget-oob-package"></a>NuGet OOB paketini kullanma  
 NuGet yükledikten sonra, Visual Studio'da Çözüm Gezgini'ni kullanarak NuGet paketlerine göz atabilir ve başvurular ekleyebilirsiniz:  
  
1.  Visual Studio'da projeniz için kısayol menüsünü açın ve ardından **NuGet paketlerini Yönet**. (Bu seçenek ayrıca kullanılabilir **proje** menü.)  
  
2.  Sol bölmede seçin **çevrimiçi**.  
  
3.  Orta bölmede aşağı açılan liste kutusunda ön sürüm paketlerini kullanmak istiyorsanız, seçin **dahil ön** yerine **yalnızca kararlı**.  
  
4.  Sağ bölmede, kullanmak **arama** kutusunu kullanmak istediğiniz paketi bulun. Bazı Microsoft paketleri, Microsoft .NET Framework logosu ile tanımlanır ve tümü Microsoft'u yayımcı olarak tanımlar.  
  
 ![NuGet Paket Yöneticisi](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")  
  
 Daha önce belirtildiği gibi, OOB paketi kullanan bir uygulamayı dağıttığınızda OOB derlemeleri, uygulama paketinizle birlikte sevk edilir.  
  
## <a name="types-of-oob-releases"></a>OOB sürümlerinin türleri  
 Genellikle, bir OOB paketi bir veya daha fazla yayın öncesi sürüm ve kararlı bir sürüm içerir. Bir yayın öncesi eşlik lisans yeniden dağıtımı genellikle izin vermez ancak bu bir paket deneyin ve geri bildirim sağlar. Geribildirim, pakete yapılan tüm güncelleştirmelere eklenmiştir. Son sürüm NuGet ile bir kararlı paket olarak dağıtılır ve NuGet paketini uygulamanızla yeniden dağıtmanıza olanak sağlayan bir lisans içerir. Kalıcı paketler, Microsoft tarafından desteklenir. Microsoft diğer türleri blog gönderileri gibi belgelerin yanı sıra IntelliSense desteği sağlar ve forum tüm paketler için yanıtlar. Ayrıca, kaynak kodu, ancak bazı değil tüm paketleri ile kullanılabilir. Yeni ve güncelleştirilmiş paketleri ile ilgili daha fazla duyuruları için için abone olabilirsiniz [.NET Framework Blog](http://blogs.msdn.com/b/dotnet/).  
  
 Yayın öncesi ve kararlı paketleri bulmak için tercih **dahil ön** NuGet Paket Yöneticisi'nde.  
  
 Kararlı paketi sürümleri bildirim almak istiyorsanız, abone [akış .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/get-started/index.md)
