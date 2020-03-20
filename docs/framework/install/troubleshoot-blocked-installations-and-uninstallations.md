---
title: Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme
description: .NET Framework'ün yüklenmesini engelleyen sorun giderme sorunları. Sorunları çözmek için bilgi için durum iletilerine başvurun.
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
ms.openlocfilehash: 70cefb53d29c7a895a3e242776bae39b7636fd65
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506963"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme

.NET Framework 4.5 veya sonraki sürümleri için [web veya çevrimdışı yükleyiciçalıştırdığınızda,](guide-for-developers.md) .NET Framework'ün yüklenmesini engelleyen veya engelleyen bir sorunla karşılaşabilirsiniz. Aşağıdaki tabloda, olası engelleme sorunları listelenmiş ve sorun giderme bilgilerinin bağlantıları sağlanmıştır.

Windows 8 ve üzeri, .NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz. .NET Framework'deki güncelleştirmeler, Denetim Masası Programları **ve Özellikleri** uygulamasının **Yüklü Güncelleştirmeler** sekmesinde görünür. .NET Framework'ün önceden yüklenmemiş olduğu işletim sistemleri için .NET Framework, Denetim Masası'ndaki **Program ve Özellikler** uygulamasının program sekmesini (veya Program **Ekle/Kaldır** sekmesini) **kaldır veya değiştirin'** de görünür. .NET Framework'ün önceden yüklendiği Windows sürümleri hakkında bilgi için [Bkz. Sistem Gereksinimleri.](../get-started/system-requirements.md)

> [!IMPORTANT]
> .NET Framework'ün 4.x sürümleri yerinde güncelleştirmeler olduğundan, .NET Framework 4.x'in önceki bir sürümünü daha sonraki bir sürümü yüklü olan bir sisteme yükleyemezsiniz. Örneğin, Windows 10 Fall Creators Update'e sahip bir sistemde .NET Framework 4.6.2'yi yükleyemezsiniz, çünkü .NET Framework 4.7.1 işletim sistemiyle önceden yüklenmiştir.

.NET Framework'ün hangi sürümlerinin bir sisteme yüklenmesini belirleyebilirsiniz. Bkz. Nasıl Yapılır: Daha fazla bilgi için [hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](../migration-guide/how-to-determine-which-versions-are-installed.md)

Bu tabloda, 4.5.x .NET Framework 4.5 ve 4.5.1 ve 4.5.2, 4.6.x .NET Framework 4.6 ve 4.6.2, 4.7.x ve 4.7.1 ve 4.7.2 puan sürümlerini ifade eder. ve 4.8 .NET Framework 4.8 anlamına gelir.

|İletiyi engelleme|Daha fazla bilgi veya bu sorunu gidermek için|  
|----------------------|--------------------------------------------------|  
|Microsoft .NET Framework ürününün kaldırılması bazı uygulamaların işlevini durdurmasına neden olabilir.|Genel olarak, kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlı olabileceği için, bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamalısınız. Daha fazla bilgi *için, Başlarken* kılavuzundaki [kullanıcılar için .NET Framework'e](../get-started/index.md#ForUsers) bakın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x (ENU) veya daha sonraki bir sürüm zaten bu bilgisayara yüklenmiş.|Herhangi bir işlem gerekli değil.<br /><br /> .NET Framework'ün hangi sürümlerinin sisteme yüklenerek yükleniyi belirlemek [için bkz: Hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](../migration-guide/how-to-determine-which-versions-are-installed.md)|  
|.NET Çerçevesi 4.5.x/4.6.x/4.7.x/4.8 *(dil)* için .NET Çerçeve 4.5.x/4.6.x/4.7.x/4.8 gerekir. Lütfen .NET Framework 4.5.x/4.6.x/4.7.x/4.8'i Download Center'dan yükleyin ve Kurulumu yeniden yayınlayın.|Bir dil paketi yüklemeden önce belirtilen .NET Framework sürümünü yüklemeniz gerekir. Daha fazla bilgi için yükleme kılavuzuna [dil paketleri yüklemek](guide-for-developers.md#to-install-language-packs) için bölümüne bakın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8'i yükleyemez. Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.<br /><br /> -veya-<br /><br /> Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.|Bu ileti büyük olasılıkla .NET Framework'ün önizleme veya RC sürümünün yüklenmiş olmasından kaynaklanmıştır. Önizlemeveya RC sürümünü kaldırın ve Kurulumu yeniden çalıştırın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8 bu paket kullanılarak kaldırılamaz. .NET Framework 4.5.x/4.6.x/4.7.x/4.8'i bilgisayarınızdan kaldırmak için **Denetim Masası'na**gidin, **Programlar ve Özellikler'i**seçin, **Yüklü Güncelleştirmeleri**Görüntüle'yi seçin, Microsoft Windows için Güncelleştirme 'yi (KB2828152) seçin ve **ardından Kaldır'ı**seçin.|Yüklediğiniz paket,.NET Framework'ün önizlemesini veya RC sürümlerini kaldırmaz.<br /><br /> Denetim Masası'ndan önizlemeyi veya RC yayınını kaldırın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8'i kaldıramaz. Bilgisayarınızdaki diğer uygulamalar bu programa bağımlıdır.|Genel olarak, .NET Framework'ün herhangi bir sürümünü bilgisayarınızdan kaldırmamalısınız, çünkü kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlı olabilir. Daha fazla bilgi *için, Başlarken* kılavuzundaki [kullanıcılar için .NET Framework'e](../get-started/index.md#ForUsers) bakın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8 yeniden dağıtılabilir bu işletim sistemi için geçerli değildir. İşletim sisteminiz için lütfen .NET Framework 4.5.x/4.6.x/4.7.x/4.8'i .NET Framework indirme sayfasından indirin.|.NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8'i desteklenmeyen bir platforma yüklemeye çalışıyor olabilirsiniz veya desteklenen tüm işletim sistemlerinin bileşenlerini içermeyen kurulum paketini seçmiş olabilirsiniz. Yüklemeyi çevrimdışı yükleyiciyi kullanarak yeniden çalıştırın ([4.5.1 için](https://go.microsoft.com/fwlink/p/?LinkId=309493), [4.5.2 için , 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net452) [için](https://dotnet.microsoft.com/download/dotnet-framework/net46), [4.6.1 için](https://dotnet.microsoft.com/download/dotnet-framework/net461), [4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604)için , [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=825306)için ), [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=852090)için , [4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)için , veya [4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)için . Daha fazla bilgi için, desteklenen işletim sistemleri için [kurulum kılavuzuna](guide-for-developers.md) ve [sistem gereksinimlerine](../get-started/system-requirements.md) bakın.|  
|Bu ürünü yükleyemeden önce KB\<*numarasına* karşılık gelen güncelleştirmenin> yüklenmesi gerekir.|.NET Framework'ün yüklenmesi, .NET Framework'ü yüklemeden önce bir KB güncelleştirmesinin yüklenmesini gerektirir. Güncelleştirmeyi yükleyin ve sonra .NET Framework yüklemesini yeniden başlatın.<br /><br /> Örneğin, .NET Framework'ün Windows 8.1, Windows RT 8.1 ve Windows Server 2012 R2'ye güncelleştirilmiş sürümlerinin yüklenmesi, [KB 2919355'e](https://support.microsoft.com/kb/2919355) karşılık gelen güncelleştirmenin yüklenmesini gerektirir.|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5.x işletim sisteminin daha sonra serbest bırakılmasını gerektirir. Lütfen Windows Server 2008 R2 SP1 veya üzerini yükleyin ve .NET Framework 4.5.x kurulumlarını yeniden çalıştırın.|.NET Framework 4.5.1 ve 4.5.2, Windows Server 2008 R2 SP1 veya sonraki sunucu core rolünde desteklenir. [Bkz. Sistem Gereksinimleri](../get-started/system-requirements.md).|  
|Bu bilgisayar üzerinde tüm kullanıcılar için bu işlemi tamamlamak üzere yeterli yetkiniz yok. Yönetici olarak oturum açın ve Kurulumu yeniden **çalıştırın.**|.NET Framework yüklemek için bilgisayarda yönetici olmanız gerekir.|  
|Önceki yükleme bilgisayarınızın yeniden başlatılmasını gerektirdiği için Kurulum devam edemiyor. Lütfen bilgisayarınızı yeniden başlatın ve Kurulumu yeniden çalıştırın.|Yüklemeyi tam olarak tamamlamak için bazen yeniden başlatma gerekir. Bilgisayarınızı yeniden başlatmak ve Kurulum'u yeniden çalıştırmak için yönergeleri izleyin.<br /><br /> Windows bir dizi eksik güncelleştirme algılamışsa ve bir sonraki güncelleştirmeyi kuyruğa yüklemek üzere yeniden başlatıyorsa, nadiren sisteminizi birden çok kez yeniden başlatmanız istenebilir.|  
|.NET Framework Kurulumu Program Uyumluluk modunda çalıştırılamaz.|Bu makalenin ilerleyen bölümlerinde [Program Uyumluluk Sorunları](#compat) bölümüne bakın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8 bileşen deposu bozulduğu için yüklenmemiştir.|Daha fazla bilgi için [DISM veya Sistem Güncelleştirmeye Hazırlık aracını kullanarak Windows Update hatalarını düzelt'e](https://support.microsoft.com/kb/947821) bakın.|  
|Windows Installer Hizmeti bu bilgisayarda kullanılamadığından kurulum çalıştırılamıyor.|Microsoft Destek web sitesinde [Windows 7 veya Windows Vista'da bir program yüklemeye çalıştığınızda "Windows Yükleyici Hizmetine Erişilemedi" hatasına](https://support.microsoft.com/help/2642495/the-windows-installer-service-could-not-be-accessed-error-when-you-try) bakın.|  
|Windows Update Hizmeti bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bilgisayar, Microsoft Windows Update yerine Windows Server Update Services (WSUS) kullanacak şekilde yapılandırılabilir. Daha fazla bilgi için, 0x800F0906 hata kodu için [.NET Framework 3.5 kurulum hatası bölümüne bakın: 0x800F0906, 0x800F081F, 0x800F0907](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906-0x800f081f-0x800f0907).<br /><br /> Ayrıca bkz. Windows Update Aracısı Microsoft Destek web [sitesindeki en son sürüme nasıl güncellenir?](https://support.microsoft.com/help/949104/how-to-update-the-windows-update-agent-to-the-latest-version)|  
|Arka Plan Akıllı Aktarım Hizmeti (BITS) bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bkz. Microsoft Destek web sitesinde [Windows Vista tabanlı bir bilgisayarda arka plan akıllı aktarım hizmeti (BITS) çökmesini düzeltmek için bir güncelleştirme kullanılabilir.](https://support.microsoft.com/help/940520/an-update-is-available-to-fix-a-background-intelligent-transfer-servic)|  
|Windows update bir hatayla karşılaştığıve 0x80070643 veya 0x643 hata kodu görüntülediği için kurulum düzgün şekilde çalışmayabilir.|Microsoft Destek web sitesinde [.NET Framework güncelleştirme yükleme hatasına bakın: "0x80070643" veya "0x643".](https://support.microsoft.com/kb/976982)|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8 zaten bu işletim sisteminin bir parçasıdır. .NET Framework 4.5.x/4.6.x/4.7.x/4.8 yeniden dağıtılabilir yüklemeniz gerekmez.|Eylem yok.<br /><br /> .NET Framework'ün hangi sürümlerinin sisteme yüklenerek yükleniyi belirlemek [için bkz: Hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](../migration-guide/how-to-determine-which-versions-are-installed.md) Desteklenen işletim sistemleri için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md) bakın.|  
|.NET Framework 4.5.x/4.6.x/4.7.x/4.8 bu işletim sisteminde desteklenmez.|Desteklenen işletim sistemleri için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md) bakın.<br /><br /> Windows 7'deki .NET Framework'ün başarısız yüklemeleri için bu ileti genellikle Windows 7 SP1'in yüklü olmadığını gösterir. Windows 7 sistemlerinde ,NET Framework Windows 7 SP1 gerektirir. Windows 7'deyseniz ve henüz Service Pack 1'i yüklemediyseniz, .NET Framework'u yüklemeden önce bunu yapmanız gerekir. Windows 7 SP1'i yükleme hakkında daha fazla bilgi [için](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1)bkz.|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5.x işletim sisteminin veya Server Core 2008 R2 SP1'in tam olarak serbest bırakılmasını gerektirir. Lütfen Windows Server 2008 SP2 veya Windows Server 2008 R2 SP1 veya Server Core 2008 R2 SP1'in tam sürümünü yükleyin ve .NET Framework 4.5.x Kurulumu yeniden çalıştırın.|The .NET Framework , Windows Server 2008 R2 SP1 veya sonrası ile birlikte Sunucu Çekirdeği Rolünde desteklenir. [Bkz. Sistem Gereksinimleri](../get-started/system-requirements.md).|  
|.NET Framework 4.5.x zaten bu işletim sisteminin bir parçasıdır, ancak şu anda kapalıdır (yalnızca Windows Server 2012).| .NET Framework 4.5.x'i açmak için **Denetim Masası'nda** Windows özelliklerini açma **veya kapatma** özelliğini kullanın. |  
|Bu kurulum programı bir x86 bilgisayar gerektiriyor. x64 veya IA64 bilgisayarlara yüklenemez.|[Bkz. Sistem Gereksinimleri](../get-started/system-requirements.md).|  
|Bu kurulum programı bir x64 veya x86 bilgisayar gerektiriyor. IA64 bilgisayarlara yüklenemez.|[Bkz. Sistem Gereksinimleri](../get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Program uyumluluğu sorunları

.NET Framework 4.5 veya nokta sürümlerinin yüklenmesi, Windows Programı Uyumluluk modunda çalışırken 1603 hata koduyla veya bloklarla başarısız olur. **Program Uyumluluk Yardımcısı,.NET** Framework'ün doğru yüklenmemiş olabileceğini belirtir ve önerilen ayarı (Program Uyumluluğu modu) kullanarak yeniden yüklemenizi ister. Program Uyumluluğu modu, başarısız olan veya iptal edilen önceki .NET Framework Kurulumu Programını çalıştırma girişimlerinde Program Uyumluluk Yardımcısı tarafından da ayarlanmış olabilir.

.NET Framework yükleyicisi Program Uyumluluk modunda çalıştırılamaz. Bu engelleme sorununu gidermek için, uyumluluk modu ayarının sistem genelinde etkin olmadığından emin olmak için Kayıt Defteri Düzenleyicisi'ni kullanmanız gerekir:

1. **Başlat** düğmesini seçin ve ardından **Çalıştır'ı**seçin.

1. **Çalıştır** iletişim kutusunda "regedit" yazın ve sonra **Tamam'ı**seçin.

1. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarlara göz atın:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ad sütununda, .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 indirme adlarını, yüklediğiniz sürüye bağlı olarak arayın ve bu girişleri silin. İndirme adları için geliştiriciler makalesi [için .NET Framework'ü](guide-for-developers.md) yükleyin'e bakın.

1. 4.5, 4.5.1, 4.5.2 veya 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 sürüm için .NET Framework yükleyicisini yeniden çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için .NET Framework'u yükleyin](guide-for-developers.md)
- [Nasıl yapılır: Hangi .NET Framework Sürümlerinin Yüklü Olduğunu Belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md)
- [Sürümler ve Bağımlılıklar](../migration-guide/versions-and-dependencies.md)
