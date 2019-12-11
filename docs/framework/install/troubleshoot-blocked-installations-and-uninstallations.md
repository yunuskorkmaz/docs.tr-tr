---
title: Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
ms.openlocfilehash: df7eaf971f3a54057758dc7d974ae00cd4797ad7
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960018"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme

.NET Framework 4,5 veya sonraki sürümler için [Web veya çevrimdışı yükleyiciyi](guide-for-developers.md) çalıştırdığınızda .NET Framework yüklenmesini önleyen veya engelleyen bir sorunla karşılaşabilirsiniz. Aşağıdaki tabloda, olası engelleme sorunları listelenmiş ve sorun giderme bilgilerinin bağlantıları sağlanmıştır.

Windows 8 ve üzeri sürümlerde .NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz. .NET Framework güncelleştirmeleri, Denetim Masası **Programlar ve Özellikler** uygulamasının **yüklü güncelleştirmeler** sekmesinde görüntülenir. .NET Framework önceden yüklü olmadığı işletim sistemleri için, Denetim Masası 'ndaki **program ve Özellikler** uygulamasının **Program Kaldır veya Değiştir** sekmesinde (veya program **ekle/kaldır** sekmesinde) .NET Framework görüntülenir. .NET Framework önceden yüklendiği Windows sürümleri hakkında bilgi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).

> [!IMPORTANT]
> .NET Framework 4. x sürümleri yerinde güncelleştirmeler olduğundan, zaten daha yeni bir sürümü yüklü olan bir sisteme .NET Framework 4. x ' in önceki bir sürümünü yükleyemezsiniz. Örneğin, Windows 10 Fall Creators Update içeren bir sistemde, .NET Framework 4.7.1 işletim sistemiyle önceden yüklenmiş olduğundan .NET Framework 4.6.2 yükleyemezsiniz.

Sistemde hangi .NET Framework sürümlerinin yüklü olduğunu belirleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md) .

Bu tabloda, 4.5. x .NET Framework 4,5 ve Point yayımları, 4.5.1 ve 4.5.2, 4.6. x, .NET Framework 4,6 ve Point yayımları, 4.6.1 ve 4.6.2 .NET Framework 4,7 ve onun nokta sürümleri, 4.7.1 ve 4.7.2 anlamına gelir. ve 4,8 .NET Framework 4,8 ' e başvurur.

|İletiyi engelleme|Daha fazla bilgi veya bu sorunu gidermek için|  
|----------------------|--------------------------------------------------|  
|Microsoft .NET Framework ürününün kaldırılması bazı uygulamaların işlevini durdurmasına neden olabilir.|Genel olarak, kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlı olabileceği için, bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamalısınız. Daha fazla bilgi için *Başlarken* kılavuzundaki [kullanıcılar için .NET Framework](../get-started/index.md#ForUsers) bakın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x (TRK) veya daha sonraki bir sürümü bu bilgisayarda zaten yüklü.|Herhangi bir işlem gerekli değil.<br /><br /> Sistemde hangi .NET Framework sürümlerinin yüklü olduğunu öğrenmek için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 (*Language*), .NET Framework 4.5. x/4.6. x/4.7. x/4.8 gerektirir. Lütfen Indirme merkezi 'nden .NET Framework 4.5. x/4.6. x/4.7. x/4.8 yükleyin ve kurulumu yeniden çalıştırın.|Dil paketini yüklemeden önce belirtilen .NET Framework sürümünün Ingilizce sürümünü yüklemeniz gerekir. Daha fazla bilgi için, yükleme kılavuzunda [dil paketleri yükleme](guide-for-developers.md#to-install-language-packs) bölümüne bakın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 yüklenemiyor. Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.<br /><br /> veya<br /><br /> Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.|Bu ileti büyük olasılıkla .NET Framework'ün önizleme veya RC sürümünün yüklenmiş olmasından kaynaklanmıştır. Önizleme veya RC sürümünü kaldırın ve kurulumu yeniden çalıştırın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 Bu paket kullanılarak kaldırılamaz. .NET Framework 4.5. x/4.6. x/4.7. x/4.8 sürümünü bilgisayarınızdan kaldırmak için **Denetim Masası**' na gidin, **Programlar ve Özellikler**' i seçin, **yüklü güncelleştirmeleri görüntüle**' yi seçin, Microsoft Windows IÇIN Güncelleştir ' i seçin (KB2828152) ve ardından **Kaldır**' ı seçin.|Yüklemekte olduğunuz paket, .NET Framework önizleme veya RC sürümlerini kaldırmaz.<br /><br /> Önizleme veya RC sürümünü Denetim Masası 'ndan kaldırın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 kaldırılamıyor. Bilgisayarınızdaki diğer uygulamalar bu programa bağımlıdır.|Genel olarak, kullandığınız bir uygulama .NET Framework belirli bir sürümüne bağlı olabileceğinden, .NET Framework tüm sürümlerini bilgisayarınızdan kaldırmamanız gerekir. Daha fazla bilgi için *Başlarken* kılavuzundaki [kullanıcılar için .NET Framework](../get-started/index.md#ForUsers) bakın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 Redistributable bu işletim sistemi için geçerlidir. Lütfen Microsoft Indirme merkezinden işletim sisteminiz için 4.5. x/4.6. x/4.7. x/4.8 .NET Framework indirin.|Desteklenmeyen bir platforma .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 yüklemeye çalışıyor veya desteklenen tüm işletim sistemlerine ait bileşenleri içermeyen yükleme paketini seçmiş olabilirsiniz. Çevrimdışı yükleyiciyi kullanarak yüklemeyi yeniden[çalıştırın (](https://go.microsoft.com/fwlink/p/?LinkId=309493) [4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)için [4,6](https://go.microsoft.com/fwlink/p/?LinkId=528233), [4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671744)için 4.6.2, 4,7 için [](https://go.microsoft.com/fwlink/p/?LinkId=780604), [](https://go.microsoft.com/fwlink/p/?LinkId=825306)için için) [, 4.7.1,](https://go.microsoft.com/fwlink/p/?LinkId=852090) [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863265)için veya [4,8](https://go.microsoft.com/fwlink/?linkid=2088631)için. Daha fazla bilgi için bkz. desteklenen işletim sistemleri için [Yükleme Kılavuzu](guide-for-developers.md) ve [sistem gereksinimleri](../get-started/system-requirements.md) .|  
|Bu ürünü yükleyebilmeniz için KB\<*numarası*> karşılık gelen güncelleştirmenin yüklenmesi gerekir.|.NET Framework yüklemesi, .NET Framework yüklenmeden önce bir KB güncelleştirmesi yüklenmesini gerektirir. Güncelleştirmeyi yükleyip .NET Framework yüklemeyi yeniden başlatın.<br /><br /> Örneğin, Windows 8.1, Windows RT 8,1 ve Windows Server 2012 R2 'deki .NET Framework sürümlerinin yüklenmesi, [KB 2919355](https://support.microsoft.com/kb/2919355) ' ye karşılık gelen güncelleştirmenin yüklü olmasını gerektirir.|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. x, işletim sisteminin daha yeni bir sürümünü gerektirir. Lütfen Windows Server 2008 R2 SP1 veya üstünü yükleyip .NET Framework 4.5. x kurulumunu yeniden çalıştırın.|.NET Framework 4.5.1 ve 4.5.2, Windows Server 2008 R2 SP1 veya sonraki sürümleriyle sunucu çekirdeği rolünde desteklenir. Bkz. [sistem gereksinimleri](../get-started/system-requirements.md).|  
|Bu bilgisayar üzerinde tüm kullanıcılar için bu işlemi tamamlamak üzere yeterli yetkiniz yok. Yönetici olarak oturum açın ve **kurulumu**yeniden çalıştırın.|.NET Framework yüklemek için bilgisayarda yönetici olmanız gerekir.|  
|Önceki yükleme bilgisayarınızın yeniden başlatılmasını gerektirdiği için Kurulum devam edemiyor. Lütfen bilgisayarınızı yeniden başlatın ve Kurulumu yeniden çalıştırın.|Yüklemeyi tam olarak tamamlaması için bazen yeniden başlatma gerekir. Bilgisayarınızı yeniden başlatmak ve kurulumu yeniden çalıştırmak için yönergeleri izleyin.<br /><br /> Nadir durumlarda, Windows bir dizi eksik güncelleştirme algıladıysa ve sıradaki bir sonraki güncelleştirmeyi yeniden başlattıktan sonra sistemi yeniden başlatmanız istenebilir.|  
|.NET Framework Kurulumu Program Uyumluluk modunda çalıştırılamaz.|Bu makalenin ilerleyen bölümlerinde [Program uyumluluk sorunları](#compat) bölümüne bakın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8, bileşen deposu bozulduğundan yüklenmedi.|Daha fazla bilgi için bkz. [DISM veya Sistem Güncelleştirmesi Hazırlık Aracı 'nı kullanarak Windows Update hatalarını giderme](https://support.microsoft.com/kb/947821) .|  
|Windows Installer Hizmeti bu bilgisayarda kullanılamadığından kurulum çalıştırılamıyor.|Microsoft Desteği Web sitesinde [Windows 7 veya Windows Vista 'da program yüklemeye çalıştığınızda "Windows Installer hizmetine erişilemedi" hatası](https://support.microsoft.com/help/2642495/the-windows-installer-service-could-not-be-accessed-error-when-you-try) makalesine bakın.|  
|Windows Update Hizmeti bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bilgisayar, Microsoft Windows Update yerine Windows Server Update Services (WSUS) kullanacak şekilde yapılandırılabilir. Daha fazla bilgi için, .NET Framework 3,5 yükleme hatası: 0x800F0906 hata kodu için bölümüne bakın [: 0x800f0906, 0x800F081F, 0x800F0907](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906-0x800f081f-0x800f0907).<br /><br /> Ayrıca [, Windows Update aracısını Microsoft desteği web sitesindeki en son sürüme güncelleştirme](https://support.microsoft.com/help/949104/how-to-update-the-windows-update-agent-to-the-latest-version) bölümüne bakın.|  
|Arka Plan Akıllı Aktarım Hizmeti (BITS) bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Microsoft Desteği Web sitesindeki [Windows Vista tabanlı bir bilgisayarda arka plan Akıllı Aktarım Hizmeti (BITS) kilitlenmesinin giderilmesi için bkz. bir güncelleştirme var](https://support.microsoft.com/help/940520/an-update-is-available-to-fix-a-background-intelligent-transfer-servic) .|  
|Windows Update bir hatayla karşılaştığından ve 0x80070643 veya 0x643 hata kodu görüntülenirken kurulum düzgün çalışmayabilir.|Microsoft Desteği Web sitesinde bkz. [.NET Framework güncelleştirme yükleme hatası: "0x80070643" veya "0x643"](https://support.microsoft.com/kb/976982) .|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 zaten bu işletim sisteminin bir parçasıdır. .NET Framework 4.5. x/4.6. x/4.7. x/4.8 Redistributable yüklemeniz gerekmez.|Eylem yok.<br /><br /> Sistemde hangi .NET Framework sürümlerinin yüklü olduğunu öğrenmek için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md). Desteklenen işletim sistemleri için [sistem gereksinimleri](../get-started/system-requirements.md) bölümüne bakın.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 bu işletim sisteminde desteklenmez.|Desteklenen işletim sistemleri için [sistem gereksinimleri](../get-started/system-requirements.md) bölümüne bakın.<br /><br /> Windows 7 ' de .NET Framework başarısız olan yüklemeleri için, bu ileti genellikle Windows 7 SP1 'in yüklenmediğini belirtir. Windows 7 sistemlerinde, .NET Framework Windows 7 SP1 gerektirir. Windows 7 kullanıyorsanız ve Service Pack 1 ' i henüz yüklemediyseniz, .NET Framework yüklemeden önce bu yapmanız gerekir. Windows 7 SP1 'i yükleme hakkında bilgi için bkz. [Windows 7 Service Pack 1 ' i (SP1) nasıl yükleyeceğinizi öğrenin](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1).|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. x, işletim sisteminin veya sunucu Core 2008 R2 SP1 'in tam bir sürümünü gerektirir. Lütfen Windows Server 2008 SP2 veya Windows Server 2008 R2 SP1 veya Server Core 2008 R2 SP1 'in tam sürümünü yükledikten sonra .NET Framework 4.5. x kurulumunu yeniden çalıştırın.|The .NET Framework , Windows Server 2008 R2 SP1 veya sonrası ile birlikte Sunucu Çekirdeği Rolünde desteklenir. Bkz. [sistem gereksinimleri](../get-started/system-requirements.md).|  
|.NET Framework 4.5. x zaten bu işletim sisteminin bir parçası, ancak şu anda kapalı (yalnızca Windows Server 2012).| .NET Framework 4.5. x ' i açmak için **Denetim Masası** 'ndaki **Windows özelliklerini aç veya kapat** seçeneğini kullanın. |  
|Bu kurulum programı bir x86 bilgisayar gerektiriyor. x64 veya IA64 bilgisayarlara yüklenemez.|Bkz. [sistem gereksinimleri](../get-started/system-requirements.md).|  
|Bu kurulum programı bir x64 veya x86 bilgisayar gerektiriyor. IA64 bilgisayarlara yüklenemez.|Bkz. [sistem gereksinimleri](../get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Program uyumluluğu sorunları

.NET Framework 4,5 veya noktası sürümlerinin yüklenmesi, Windows program uyumluluk modunda çalışırken 1603 hata kodu veya blokları ile başarısız olur. **Program uyumluluk yardımcısı** .NET Framework doğru şekilde yüklenmediğini ve önerilen ayarı (program uyumluluğu modu) kullanarak yeniden yüklemenizi ister. Program Uyumluluğu modu, başarısız olan veya iptal edilen önceki .NET Framework Kurulumu Programını çalıştırma girişimlerinde Program Uyumluluk Yardımcısı tarafından da ayarlanmış olabilir.

.NET Framework yükleyicisi Program Uyumluluk modunda çalıştırılamaz. Bu engelleme sorununu çözmek için, uyumluluk modu ayarının sistem genelinde etkin olmadığından emin olmak için kayıt defteri düzenleyicisini kullanmanız gerekir:

1. **Başlat** düğmesini ve sonra **Çalıştır**' ı seçin.

1. **Çalıştır** iletişim kutusunda "regedit" yazın ve ardından **Tamam**' ı seçin.

1. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarlara göz atın:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ad sütununda, yüklediğiniz sürüme bağlı olarak .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 veya 4.7.2 indirme adlarını arayın ve bu girişleri silin. İndirme adları için bkz. [geliştiriciler için .NET Framework yükleme](guide-for-developers.md) makalesi.

1. Sürüm 4,5, 4.5.1, 4.5.2 veya 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 veya 4.7.2 için .NET Framework yükleyicisini yeniden çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için .NET Framework yüklemesi](guide-for-developers.md)
- [Nasıl yapılır: Hangi .NET Framework Sürümlerinin Yüklü Olduğunu Belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md)
- [Sürümler ve Bağımlılıklar](../migration-guide/versions-and-dependencies.md)
