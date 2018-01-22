---
title: "Geliştiriciler için .NET Framework'ü yükleme"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: get-started-article
helpviewer_keywords:
- .NET Framework redistributable package, downloading
- .NET Framework, installing
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: daf9d9d5-84ac-4bd9-a864-27665ffd0f5c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4be70c047566416b40da3fd34d1e8b8f479af7c5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="install-the-net-framework-for-developers"></a>Geliştiriciler için .NET Framework'ü yükleme

.NET Windows üzerinde çalışan birçok uygulama ayrılmaz bir parçasıdır ve bu uygulamaların çalışması ortak işlevsellik sağlar. Geliştiriciler, uygulamaları oluşturmak için tutarlı programlama modeline sahip kullanıcı deneyimleri ve sorunsuz ve güvenli iletişim şaşırtıcı ve kapsamlı bir .NET Framework sağlar.  

Bu makalede, .NET Framework'ün tüm sürümleri için .NET Framework 4.5 yükleme için bağlantılar sağlar [!INCLUDE[net_current](../../../includes/net-current-version.md)] bilgisayarınızda. Bir geliştirici değilseniz, bu bağlantıları indirmek ve .NET Framework uygulamalarınızı ile yeniden dağıtmak için de kullanabilirsiniz. Uygulamanız ile .NET Framework sürümü dağıtma hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework Dağıtım Kılavuzu](../deployment/deployment-guide-for-developers.md).

> [!NOTE]
> Bu konu, ya da kendi sistemde .NET Framework'ü yüklemek isteyen veya bunların uygulamalarla kurmak isteyen geliştiriciler için tasarlanmıştır. .NET Framework yükleme kullanıcıları görmek için .NET Framework gibi belirli işletim sistemlerine yükleyerek ele konularıyla [Windows 10 ve Windows Server 2016 .NET Framework'ü yüklemek](on-windows-10.md).  
  
.NET Framework'ün yeni bir sürümünü yükleme her zaman önceki bir sürümü yenisiyle değiştirmez olduğunu unutmayın. .NET Framework sürümleri ve hangi sürümlerinin bir bilgisayarda yüklü olduğunu belirleme hakkında daha fazla bilgi için bkz: [sürümleri ve bağımlılıkları](~/docs/framework/migration-guide/versions-and-dependencies.md) ve [nasıl yapılır: belirlemek, .NET Framework sürümleri Yüklü](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Aşağıdaki tabloda listelenen .NET Framework sürümlerini .NET Framework 4 yerinde güncelleştirmelerinin tümü. .NET Framework 4.6 gibi sonraki bir sürümünü yüklerseniz, diğer bir deyişle, önce .NET Framework 4.5, 4.5.1 veya 4.5.2 gibi önceki sürümlerini yüklemek gerekmez. .NET Framework 4.6 gibi sonraki bir sürümünü yüklerseniz, benzer şekilde, ilk .NET Framework 4.5, 4.5.1 veya 4.5.2 gibi önceki sürümlerini kaldırmanız gerekmez. 

.NET Framework 4.x üstünü yerinde bulunmasına önceki sürümleri anlamına gelir güncelleştirmeleri *olamaz* sonraki bir sürümü zaten yüklüyse tabloda listelenen önceki bir sürümünü yükleyin. Örneğin, .NET Framework 4.6.1 üzerinde önceden yüklenmiş olarak bu yana bir Windows 10 Kasım güncelleştirme sistemde .NET Framework 4.6 yükleyemezsiniz.    

> [!NOTE]
> .NET Framework 3.5 hakkında daha fazla bilgi için bkz: [Windows 10, Windows 8.1 ve Windows 8 .NET Framework 3.5 yüklemek](~/docs/framework/install/dotnet-35-windows-10.md).  
  
Hızlı bağlantılar ya da daha fazla ayrıntı için okuma için aşağıdaki tabloyu kullanın. Yüklemeden önce .NET Framework sistem gereksinimleri görüntülemek için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md). Sorun giderme ile ilgili daha fazla yardım için bkz: [sorun giderme](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md).  
  
|.NET Framework sürümü|Geliştirici yükleme|Yeniden dağıtılabilir yükleme|Platform desteği|  
|----------------------------|----------------------------|----------------------------------|----------------------|  
|**4.7.1**|[NET Framework 4.7.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=852105)|[İndirme sayfasının 4.7.1 için web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=852095)<br /><br /> [İndirme sayfasının 4.7.1 için çevrimdışı yükleyici](http://go.microsoft.com/fwlink/?LinkId=852107)|Dahil: <br/>Windows 10 sonbaharda oluşturucuları güncelleştir<br/>Windows Server, sürüm 1709<br /><br /> Üzerinde yükleyebilirsiniz:<br/> Windows 10 oluşturucuları güncelleştir <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))||
|**4.7**|[NET Framework 4.7 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=825319)|[4.7 web Yükleyicisi için indirme](http://go.microsoft.com/fwlink/?LinkId=825299)<br /><br /> [Sayfa için 4.7 çevrimdışı yükleyiciyi karşıdan yükleme](http://go.microsoft.com/fwlink/?LinkId=825303)|Dahil: <br/>Windows 10 oluşturucuları güncelleştir<br /><br /> Üzerinde yükleyebilirsiniz:<br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))||
|**4.6.2**|[NET Framework 4.6.2 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=780617)|[İndirme sayfasının 4.6.2 için web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=780597)<br /><br /> [İndirme sayfasının 4.6.2 için çevrimdışı yükleyici](http://go.microsoft.com/fwlink/?LinkId=780601)|Dahil: <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /><br /> Üzerinde yükleyebilirsiniz:<br /> Windows 10 Kasım güncelleştirme <br/> Windows 10 <br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|
|**4.6.1**|[NET Framework 4.6.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=690706)|[İndirme sayfasının 4.6.1 için web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=671729)<br /><br /> [İndirme sayfasının 4.6.1 için çevrimdışı yükleyici](http://go.microsoft.com/fwlink/?LinkId=671744)|Üzerinde yükleyebilirsiniz:<br /> Windows 10 <br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|
|**4.6**|Dahil [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]. Daha fazla bilgi için bkz: [Visual Studio 2015'na Hoş](http://msdn.microsoft.com/library/dd831853\(v=vs.140\).aspx).<br /><br /> [Microsoft .NET Framework 4.6 hedefleme paketi](http://go.microsoft.com/fwlink/?LinkId=528261)|[4.6 web Yükleyicisi için indirme](http://go.microsoft.com/fwlink/?LinkId=528259)<br /><br /> [Sayfa için 4.6 çevrimdışı yükleyiciyi karşıdan yükleme](http://go.microsoft.com/fwlink/?LinkId=528233)|Dahil: <br /> Windows 10 <br />[!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]<br /><br /> Üzerinde yükleyebilirsiniz:<br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|  
|**4.5.2**|[Microsoft .NET Framework 4.5.2 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=397702)<br /><br /> İle kullanılmak üzere [Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=325532), Visual Studio 2012 ya da diğer IDE|[Sayfayı 4.5.2 için Yükle web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=397703)<br /><br /> [Sayfayı 4.5.2 için Yükle çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=397706)|Üzerinde yükleyebilirsiniz:<br /> Windows 8.1 ve önceki sürümleri<br /> Windows Server 2012 R2 ve önceki sürümleri<br /> (tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|  
|**4.5.1**|[Microsoft .NET Framework 4.5.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=324213)<br /><br /> Visual Studio 2012 ya da diğer IDE ile kullanmak için|[4.5.1 için indirme web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br /><br /> [4.5.1 için indirme çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=310159)|Dahil:<br /> [!INCLUDE[win81](../../../includes/win81-md.md)]<br /> Windows Server 2012 R2<br /> [Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=325532)<br /><br /> Üzerinde yükleyebilirsiniz:<br /> [!INCLUDE[win8](../../../includes/win8-md.md)]ve önceki sürümleri<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]ve önceki sürümleri<br />(tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|  
|**4.5**|Visual Studio 2012'de bulunan<br /><br /> Ayrıca kullanılabilir olarak parçası [Windows 8 SDK'sı](http://msdn.microsoft.com/windows/hardware/hh852363)|[4.5 web Yükleyicisi için indirme](http://go.microsoft.com/fwlink/p/?LinkId=245484)|Dahil: <br /> [!INCLUDE[win8](../../../includes/win8-md.md)]<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]<br /> Visual Studio 2012<br /><br /> Üzerinde yükleyebilirsiniz:<br /> Windows 7 ve önceki<br /> Windows Server 2008 SP2 ve önceki sürümleri<br />(tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md))|  

Yükleyebileceğiniz **Geliştirici paketi** belirli tüm desteklenen platformlarda, varsa, .NET Framework sürümü için.  
  
Yükleyebileceğiniz **Web veya çevrimdışı yükleyici** üzerinde:  
  
- Windows 8.1 ve önceki sürümleri  
  
- Windows Server 2012 R2 ve önceki sürümleri  
  
Tam listesi için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md).  

Kullanıcılar ve geliştiriciler için .NET Framework genel bir giriş için bkz: [Başlarken](../get-started/index.md). Uygulamanız ile .NET Framework dağıtma hakkında daha fazla bilgi için bkz: [Dağıtım Kılavuzu'na](~/docs/framework/deployment/deployment-guide-for-developers.md). Mimari ve .NET Framework'ün temel özellikleri hakkında bilgi için bkz: [genel bakış](~/docs/framework/get-started/overview.md).  

<a name="choices"></a>
## <a name="installation-choices"></a>Yükleme Seçenekleri

En son Visual Studio ya da başka bir geliştirme ortamı .NET Framework sürümünü karşı geliştirmek için paketi hedefleyen bir geliştirici yükleyin veya .NET Framework uygulama veya denetim ile dağıtım için yeniden dağıtılabilir indirin.  
  
## <a name="to-install-the-net-framework-developer-or-targeting-pack"></a>.NET Framework Geliştirici veya paketi hedefleme yüklemek için

Geliştirici paketi için .NET Framework 4.5.1 veya hedefleme 4.5.2 paketi [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]ve geliştirici paketi [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], 4.6.2, 4.7 veya 4.7.1 sağlar .NET Framework 4.5.1 veya 4.5.2 veya [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1 veya 4.6.2 ya da .NET Framework 4.7 veya 4.7.1 başvuru derlemeleri, dil paketlerini ve Visual Studio gibi bir tümleşik geliştirme ortamında kullanılması için IntelliSense dosyaları.  Ayrıca, Visual Studio, geliştirici paketi kullanarak veya paketi hedefleme yeni bir proje oluşturduğunuzda, .NET Framework'ün yüklü olan sürüm hedef seçenekleri ekler.  Bu Geliştirici paketleri ya da hedefleme paketi birini seçin:  

- [Microsoft .NET Framework 4.7.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=852105)

- [Microsoft .NET Framework 4.7 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=825319)
  
- [Microsoft .NET Framework 4.6.2 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=780617)  
  
- [Microsoft .NET Framework 4.6.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=690706)  
  
- [Microsoft .NET Framework 4.6 hedefleme paketi](http://go.microsoft.com/fwlink/?LinkId=528261)  
  
- [.NET framework 4.5.2 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=397702) sürüm 4.5.2 Windows 8.1 veya önceki sürümlerde, Visual Studio 2013, Visual Studio 2012 veya diğer IDE yüklemek için.  
  
- [.NET framework 4.5.1 Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=324213) Visual Studio 2012 veya diğer IDE 4.5.1 sürümünü yüklemek için.  
  
Geliştirici paketi indirme sayfasından seçin **karşıdan**. Sonraki seçin **çalıştırmak** veya **kaydetmek**ve istendiğinde yönergeleri izleyin.  
  
## <a name="to-install-or-download-the-net-framework-redistributable"></a>Yükleme veya .NET Framework yeniden dağıtılabilir indirmek için

Bu yükleyiciler bir uygulama ya da .NET Framework'ın bu sürümlerini hedefleyen denetimi için .NET Framework bileşenlerini yükleyin. Bu bileşenler uygulama veya denetim çalıştığı her bilgisayara yüklenmesi gerekir. Her iki yükleyiciler yeniden dağıtılabilir, olduğundan bunları uygulamanız için Kurulum programını içerebilir.  
  
İndirme sayfasına çeşitli dillerde sağlanır, ancak çoğu indirme yalnızca İngilizce olarak sağlanmıştır. Ek dil desteği için bir dil paketini yüklemeniz gerekir.  
  
İki yeniden dağıtılabilir yükleme türü mevcuttur:  
  
- **Web yükleyicisi** gerekli bileşenleri ve Web yükleme bilgisayarın işletim sistemine eşleşen dil paketi (web önyükleyici) yükler. Bu paket, çevrimdışı yükleyici çok daha küçüktür ancak tutarlı bir Internet bağlantısı gerektirir. İndirebilirsiniz [tek başına dil paketlerini](#standalone_language_packs) ek dil desteği yüklemek için.  
  
- **Çevrimdışı yükleyici** (tek başına yeniden dağıtılabilir) .NET Framework yükleme için gereken tüm bileşenleri içerir ancak dil paketlerini içermiyor. Bu yükleme, web yükleyicisi büyüktür. Çevrimdışı yükleyici Internet bağlantısı olmasını gerektirmez. Çevrimdışı yükleyici çalıştırdıktan sonra indirebilirsiniz [tek başına dil paketlerini](#standalone_language_packs) dil desteği yüklemek için. Tutarlı bir Internet bağlantısına sahip bağlı olamaz, çevrimdışı yükleyiciyi kullanın.  
  
Hem web hem de çevrimdışı yükleyicileri x86 ve x64 tabanlı bilgisayarlar için tasarlanmıştır (bkz [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md)), ancak Itanium tabanlı bilgisayarlar desteklemez.  
  
1.  Yüklemek istediğiniz .NET Framework sürümü için yükleme sayfasını açın:  

   - .NET framework 4.7.1 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=852095) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=852107))

   - .NET framework 4.7 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=825299) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=825303))

    - .NET framework 4.6.2 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=780597) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=780601))  
    
    - .NET framework 4.6.1 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=671729) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=671744))  
  
    - .NET framework 4.6 ([web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=528259) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=528233))  
  
    - .NET framework 4.5.2 ([web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=397703) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=397706))  
  
    - .NET framework 4.5.1 ([web yükleyicisi](http://go.microsoft.com/fwlink/p/?LinkId=310158) veya [çevrimdışı yükleyici](http://go.microsoft.com/fwlink/p/?LinkId=310159))  
  
    - [.NET framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)  
  
1. İndirme sayfasına dilini seçin. Bu seçenek, .NET Framework'ün yerelleştirilmiş kaynaklar indirmez; yalnızca indirme sayfasında görüntülenen metni de etkiler.  
  
1. Seçin **karşıdan**.  
  
1. İstenirse, sistem mimarisi ile eşleşen indirme seçin ve ardından **sonraki**.  
  
1. Yükleme istemi belirdiğinde yapmak **bir** aşağıdaki:
  
   - .NET Framework bilgisayarınıza yüklemek istiyorsanız, tercih **çalıştırmak**ve ardından ekrandaki yönergeleri izleyin.   
  
   - .NET Framework yeniden dağıtımı için karşıdan yüklemek isterseniz, seçin **kaydetmek**ve ardından ekrandaki yönergeleri izleyin.  
  
1. Ek dil için kaynak karşıdan yüklemek isterseniz, bir veya daha fazla dil paketlerini yüklemek için sonraki bölümünde yer alan yönergeleri izleyin.  
  
> [!NOTE]
> Yükleme sırasında herhangi bir sorunla karşılaşırsanız, bkz: [sorun giderme](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md).  
  
 **Yükleme Notlar:**  
  
- [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Ve 4.5.2 yanı sıra [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, 4.7 ve 4.7.1 olan yerinde güncelleştirmeleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Kendi noktası sürümler, [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve sürümler ve .NET Framework 4.7 ve kendi noktası yayın Değiştir noktasını [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Bu sürümleri sahip bir sistemde yüklediğinizde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] yüklü derlemelerin değiştirilir.
  
- Kaldırma [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kendi noktası sürümler, [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve sürümler, veya .NET Framework 4.7 kendi noktası sürüm ve aynı zamanda önceden varolan kaldırır noktasını [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] dosyaları. Geri dönüp istiyorsanız [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]ve bunu herhangi bir güncelleştirme yeniden yüklemeniz gerekir. (Bkz [.NET Framework 4 yükleme](http://go.microsoft.com/fwlink/p/?LinkId=230665).)  
  
- Yüklemek için yönetici kimlik bilgilerine sahip [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kendi noktası sürümleri, .NET Framework 4.6 ve kendi noktası serbest bırakır ve .NET Framework 4.7 ve noktası sürüm.
  
- .NET Framework 4.5 yeniden dağıtılabilir 9 Ekim, dijital imza üretilen ve erken sona Microsoft tarafından imzalanmış dosyalarını neden bir dijital sertifika yanlış bir zaman damgasını ilgili bir sorunu gidermek için 2012 güncelleştirildi. .NET Framework 4.5 tarihli 16 Ağustos 2012 yeniden dağıtılabilir paketi daha önce yüklediyseniz en son yeniden dağıtılabilir ile kopyanızı güncelleştirmenizi öneririz [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=245484). Bu sorun hakkında daha fazla bilgi için bkz: [Microsoft güvenlik önerisi 2749655](http://technet.microsoft.com/security/advisory/2749655) ve [Bilgi Bankası makalesi 2770445](http://support.microsoft.com/kb/2770445).  
  
<a name="standalone_language_packs"></a>   
## <a name="to-install-language-packs"></a>Dil paketlerini yüklemek için

 Dil paketleri, desteklenen diller için yerelleştirilen kaynaklar (örneğin, çevrilmiş hata iletileri ve UI metin) içeren yürütülebilir dosyalarıdır. Bir dil paketi yüklemezse, .NET Framework hata iletileri ve başka bir metin İngilizce dilinde görüntülenir.  Web yükleyicisi işletim sistemleriyle eşleşen dil paketi otomatik olarak yükler, ancak ek dil paketlerini bilgisayarınıza indirebilirsiniz unutmayın. Çevrimdışı yükleyici herhangi bir dil paketi eklemeyin. 
  
> [!IMPORTANT]
> Dil paketlerini bir dil paketi yüklemeden önce web veya çevrimdışı yükleyici çalıştırmanız gerekir böylece bir uygulamayı çalıştırmak için gerekli olan .NET Framework bileşenlerini hiçbirini içeremez. Bir dil paketi yüklediyseniz kaldırmak, .NET Framework'ü yüklemek ve dil paketini yeniden yükleyin.  
  
1.  Yüklediğiniz .NET Framework sürümü için dil paketi yükleme sayfasını açın:  
  
    - [.NET framework 4.7.1 dil paketleri](http://go.microsoft.com/fwlink/?LinkID=852090) 

    - [.NET framework 4.7 Dil paketleri](http://go.microsoft.com/fwlink/?LinkID=825306) 

    - [.NET framework 4.6.2 dil paketleri](http://go.microsoft.com/fwlink/?LinkID=780604)  
  
    - [.NET framework 4.6.1 dil paketleri](http://go.microsoft.com/fwlink/?LinkID=671747)  
  
    - [.NET framework 4.6 dil paketleri](http://go.microsoft.com/fwlink/?LinkID=528314)  
  
    - [.NET framework 4.5.2 dil paketleri](http://go.microsoft.com/fwlink/?LinkId=397701)  
  
    - [.NET framework 4.5.1 dil paketleri](http://go.microsoft.com/fwlink/?LinkId=322101)  
  
    - [.NET framework 4.5 dil paketleri](http://go.microsoft.com/fwlink/p/?LinkId=245451)  
  
2.  Dil listesinde indirmek istediğiniz dili seçin ve sayfanın o dilde yeniden yüklemek için birkaç saniye bekleyin.  
  
3.  Seçin **karşıdan**.  
  
Aşağıdaki tabloda, desteklenen dilleri listeler.  
  
| Dil              | Kültür |
| --------------------- | :-----: |
| Arapça                | ar      |
| Çekçe                 | cs      |
| Danca                | da      |
| Hollanda dili                 | nl      |
| Fince               | fi      |
| Fransızca                | fr      |
| Almanca                | de      |
| Yunanca                 | el      |
| İbranice                | Müşterinizle      |
| Macarca             | hu      |
| İtalyanca               | it      |
| Japonca              | ja      |
| Kore Dili                | Ko      |
| Norveççe             | Yok      |
| Lehçe                | pl      |
| Portekizce (Brezilya)   | pt-BR   |
| Portekizce (Portekiz) | pt-PT   |
| Rusça               | ru      |
| Basitleştirilmiş Çince    | zh-CHS  |
| İspanyolca               | ES      |
| İsveç dili               | sv      |
| Geleneksel Çince   | zh-CHT  |
| Türkçe               | tr      |
| İngilizce (ABD)            | en-US   |
  
## <a name="next-steps"></a>Sonraki adımlar  
  
- .NET Framework yeniyseniz, bkz: [genel bakış](~/docs/framework/get-started/overview.md) giriş temel kavramları ve bileşenleri için.  
  
- Yeni özellikler ve geliştirmeler .NET Framework 4.5 ve tüm sonraki sürümler için bkz: [yenilikler](../../../docs/framework/whats-new/index.md).  
  
- Uygulamanız ile .NET Framework dağıtma hakkında ayrıntılı bilgi için bkz: [geliştiriciler için Dağıtım Kılavuzu](~/docs/framework/deployment/deployment-guide-for-developers.md).  
  
- .NET Framework ile uygulamanızı dağıtımını etkileyen değişiklikleri görmek [azaltma sistemi yeniden sırasında .NET Framework 4.5 yüklemeleri](~/docs/framework/deployment/reducing-system-restarts.md).  
  
- Uygulamanız .NET Framework 4'e geçiş hakkında bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya kendi noktası sürümlerden birini [Geçiş Kılavuzu](~/docs/framework/migration-guide/index.md). 

- Bkz: [.NET Framework başvuru kaynağı](http://referencesource.microsoft.com/) .NET Framework kaynak kodu çevrimiçi gidin. Başvuru kaynağı da kullanılabilir [GitHub](https://github.com/Microsoft/referencesource). Yapabilecekleriniz [başvuru kaynağı karşıdan](http://referencesource.microsoft.com/download.html) çevrimdışı izleme ve hata ayıklama sırasında (düzeltme eklerini ve güncelleştirmeleri dahil) kaynakları ilerleyebilirsiniz. Daha fazla bilgi için blog girişine bakın [.NET başvuru kaynağı için yeni bir görünüm](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx).  
  
## <a name="see-also"></a>Ayrıca bkz.

[Geliştiriciler için Dağıtım Kılavuzu](~/docs/framework/deployment/deployment-guide-for-developers.md)   
[Yöneticiler için Dağıtım Kılavuzu](~/docs/framework/deployment/guide-for-administrators.md)   
[.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme](~/docs/framework/install/dotnet-35-windows-10.md)   
[Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
