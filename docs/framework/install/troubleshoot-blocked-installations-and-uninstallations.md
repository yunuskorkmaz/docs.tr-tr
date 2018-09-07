---
title: Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme
ms.date: 04/10/2018
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cb33ffbbd735a015b58fe4fd6b9f7f70282cba1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098374"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme

Çalıştırdığınızda [web veya çevrimdışı yükleyiciyi](../../../docs/framework/install/guide-for-developers.md) .NET Framework 4.5 veya sonraki sürümler için .NET Framework'ün yüklemesini engelleyen veya durduran bir sorunla karşılaşabilirsiniz. Aşağıdaki tabloda, olası engelleme sorunları listelenmiş ve sorun giderme bilgilerinin bağlantıları sağlanmıştır.

Windows 8 ve üzeri, .NET Framework, işletim sisteminin bir bileşeni olan ve bağımsız olarak kaldırılamaz. .NET Framework güncelleştirmelerinin görünür **yüklü güncelleştirmeler** Denetim Masası sekmesinde **programlar ve Özellikler** uygulama. .NET Framework, .NET Framework değil önceden işletim sistemleri için görünür **Kaldır veya Değiştir bir program** sekme (veya **Program Ekle/Kaldır** sekmesinde),  **Program ve Özellikler** Denetim Masası'ndaki uygulama. .NET Framework önceden Windows sürümleri hakkında daha fazla bilgi için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> .NET Framework 4.x sürümlerinin yerinde güncelleştirmeyi olduğundan, .NET Framework 4.x bir sistemde zaten daha sonraki bir sürümün yüklü olduğu bir önceki sürümünü yükleyemezsiniz. Örneğin, Windows 10 Fall Creators Update ile bir sistemde, .NET Framework 4.7.1 işletim sistemiyle birlikte önceden yüklenmiş olarak bu yana .NET Framework 4.6.2, yükleyemezsiniz.

Bir sistemde hangi .NET Framework sürümlerinin yüklü olduğunu belirleyebilirsiniz. Bkz: [nasıl yapılır: Determine Which .NET Framework sürümleri Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) daha fazla bilgi için.

Bu tabloda, 4.5. *x* .NET Framework 4.5 ve onun nokta sürümleri için 4.5.1 ve 4.5.2, 4.6. *x* .NET Framework 4.6 ve onun nokta sürümleri başvuruyor 4.6.1 ve 4.6.2 ve 4.7. *x* .NET Framework 4.7 ve onun nokta sürümleri 4.7.1 ve 4.7.2 ifade eder.

|İletiyi engelleme|Daha fazla bilgi veya bu sorunu gidermek için|  
|----------------------|--------------------------------------------------|  
|Microsoft .NET Framework ürününün kaldırılması bazı uygulamaların işlevini durdurmasına neden olabilir.|Genel olarak, kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlı olabileceği için, bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamalısınız. Daha fazla bilgi için [kullanıcılar için .NET Framework](../../../docs/framework/get-started/index.md#ForUsers) içinde *Başlarken* Kılavuzu.|  
|.NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* (trk) veya sonraki bir sürümü bu bilgisayarda zaten yüklü.|Herhangi bir işlem gerekli değil.<br /><br /> Bir sistemde hangi .NET Framework sürümlerinin yüklü olduğunu saptamak için bkz: [nasıl yapılır: Determine Which .NET Framework sürümleri Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* (*dil*) .NET Framework 4.5 gerektirir *.x*/4.6 *.x*/4.7 *.x*. Lütfen .NET Framework 4.5 yükleme *.x*/4.6 *.x*/4.7 *.x* İndirme Merkezi'nden ve kurulumu yeniden çalıştırın.|Dil paketini yüklemeden önce belirtilen .NET Framework sürüm İngilizce sürümünü yüklemeniz gerekir. Daha fazla bilgi için üzerinde bölümüne bakın. [dil paketlerini yüklemek için](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) Yükleme Kılavuzu.|  
|.NET Framework 4.5 yüklenemiyor *.x*/4.6 *.x*/4.7 *.x*. Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.<br /><br /> veya<br /><br /> Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.|Bu ileti büyük olasılıkla .NET Framework'ün önizleme veya RC sürümünün yüklenmiş olmasından kaynaklanmıştır. Önizlemeyi veya RC sürümünü kaldırın ve kurulumu yeniden çalıştırın.|  
|.NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* bu paket kullanılarak kaldırılamaz. .NET Framework 4.5 kaldırmak için *.x*/4.6 *.x*/4.7 *.x* bilgisayarınızdan Git **Denetim Masası**, seçin  **Programlar ve Özellikler**, seçin **yüklü güncelleştirmeleri görüntüle**, (KB2828152) Microsoft Windows Güncelleştirmesi'ni seçin ve ardından **kaldırma**.|Önizleme veya RC sürümlerini .NET Framework'ün kaldırın, yüklemekte olduğunuz paket değil.<br /><br /> Önizlemeyi veya RC kaldırın. Denetim Masası'ndan yayın.|  
|.NET Framework 4.5 kaldıramazsınız *.x*/4.6 *.x*/4.7 *.x*. Bilgisayarınızdaki diğer uygulamalar bu programa bağımlıdır.|Genel olarak, bir uygulama .NET Framework'ün belirli bir sürüme bağlı olabileceği için .NET Framework sürümlerinden hiçbirini bilgisayarınızdan kaldırmanız gerekir. Daha fazla bilgi için [kullanıcılar için .NET Framework](../../../docs/framework/get-started/index.md#ForUsers) içinde *Başlarken* Kılavuzu.|  
|.NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* yeniden dağıtılabilir bu işletim sistemi için geçerli değildir. Lütfen .NET Framework 4.5 karşıdan *.x*/4.6 *.x*/4.7 *.x* işletim sisteminizden Microsoft Download Center için.|Yüklemeye çalıştığınız [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, veya desteklenmeyen bir platformda 4.7.2 veya tüm işletim sistemlerinde desteklenen bileşenlerin bulunmadığı yükleme paketini seçtiniz. Çevrimdışı yükleyiciyi kullanarak yüklemeyi yeniden çalıştırın ([4.5.1 için](https://go.microsoft.com/fwlink/p/?LinkId=309493), [4.5.2 için](https://go.microsoft.com/fwlink/p/?LinkId=397706), [4.6 için](https://go.microsoft.com/fwlink/p/?LinkId=528233), [4.6.1 için](https://go.microsoft.com/fwlink/p/?LinkId=671744), için [ 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604), için [4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)), için [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), veya [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863265). Daha fazla bilgi için [Yükleme Kılavuzu](../../../docs/framework/install/guide-for-developers.md) ve [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) desteklenen işletim sistemleri için.|  
|Güncelleştirme KB olarak karşılık gelen\<*numarası*> Bu ürünü yükleyebilmeniz için önce yüklü olması gerekir.|.NET Framework'ün yüklemesini bir KB güncelleştirmesi .NET Framework'ü yüklemeden önce yüklü olmasını gerektirir. Güncelleştirmeyi yükleyin ve sonra .NET Framework yüklemeyi yeniden başlatın.<br /><br /> Örneğin, yüklenmesini güncelleştirilmiş Windows 8.1, Windows RT 8.1, .NET Framework sürümleri ve Windows Server 2012 R2 gerektirir, karşılık gelen güncelleştirme [KB 2919355](https://support.microsoft.com/kb/2919355) yüklü olmalıdır.|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. *x* işletim sisteminin daha yeni bir sürümünü gerektirir. Lütfen Windows Server 2008 R2 SP1 veya daha yüksek ve yeniden çalıştırma .NET Framework 4.5 yükleyin. *x* kurulumu.|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Ve 4.5.2, Windows Server 2008 R2 SP1 veya daha sonra Sunucu Çekirdeği rolünde desteklenir. Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|Bu bilgisayar üzerinde tüm kullanıcılar için bu işlemi tamamlamak üzere yeterli yetkiniz yok. Yönetici olarak çalıştırıp yeniden oturum **Kurulum**.|.NET Framework yüklemek için bilgisayarda yönetici olmanız gerekir.|  
|Önceki yükleme bilgisayarınızın yeniden başlatılmasını gerektirdiği için Kurulum devam edemiyor. Lütfen bilgisayarınızı yeniden başlatın ve Kurulumu yeniden çalıştırın.|Yeniden başlatma, tam olarak bir yüklemenin tamamlanabilmesi için bazen gereklidir. Bilgisayarınızı yeniden başlatın ve kurulumu yeniden çalıştırın için yönergeleri izleyin.<br /><br /> Nadiren de olsa, sisteminizi Windows eksik güncelleştirmelerin sayısı algıladı ve kuyrukta İleri güncelleştirmeyi yüklemek için yeniden başlatılıyor birden çok kez yeniden başlatmanız istenebilir.|  
|.NET Framework Kurulumu Program Uyumluluk modunda çalıştırılamaz.|Bkz: [Program Uyumluluk sorunları](#compat) bu makalenin devamındaki bölümü.|  
|.NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* bileşen deposu bozuk olduğundan yüklü değil.|Bkz: [DISM ya da sistem güncelleştirme hazırlığı aracını kullanarak Windows güncelleştirme düzeltme hataları](https://support.microsoft.com/en-us/kb/947821) daha fazla bilgi için.|  
|Windows Installer Hizmeti bu bilgisayarda kullanılamadığından kurulum çalıştırılamıyor.|Bkz: [yüklerken veya güncellerken programlar Windows Installer hizmeti hatası](https://go.microsoft.com/fwlink/p/?LinkId=248684) Microsoft Support Web sitesi.|  
|Windows Update Hizmeti bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bilgisayar, Microsoft Windows Update yerine Windows Server Update Services (WSUS) kullanacak şekilde yapılandırılabilir. Daha fazla bilgi için hata kodu 0x800F0906 bölümüne bakın [Windows 8 veya Windows Server 2012 ' .NET Framework 3.5 yüklemeye çalıştığınızda hata kodları](https://support.microsoft.com/kb/2734782).<br /><br /> Ayrıca bkz: [bir bilgisayardaki güncelleştirmeleri yönetmenize yardımcı olmak için Windows Update Aracısı'nın en son sürümünü elde etme](https://go.microsoft.com/fwlink/p/?LinkId=248437) Microsoft Support Web sitesi.|  
|Arka Plan Akıllı Aktarım Hizmeti (BITS) bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bkz: [bir Windows Vista tabanlı bilgisayarlarda bir arka plan Akıllı Aktarım Hizmeti (BITS) kilitlenmesini engellemek için bir güncelleştirme](https://go.microsoft.com/fwlink/p/?LinkId=248680) Microsoft Support Web sitesi.|  
|Windows update bir hatayla karşılaştı ve hata kodu 0x80070643 veya 0x643 görüntülenen olduğundan kurulum düzgün çalışmayabilir.|Bkz: [.NET Framework güncelleştirme yükleme hatası: "0x80070643" veya "0x643"](https://support.microsoft.com/kb/976982) Microsoft Support Web sitesi.|  
|.NET Framework 4.5. *.x*/4.6 *.x*/4.7 *.x* zaten bu işletim sisteminin bir parçasıdır. .NET Framework 4.5 yüklemek gerekmez *.x*/4.6 *.x*/4.7 *.x* yeniden dağıtılabilir.|Eylem yok.<br /><br /> Bir sistemde hangi .NET Framework sürümlerinin yüklü olduğunu saptamak için bkz: [nasıl yapılır: Determine Which .NET Framework sürümleri Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) desteklenen işletim sistemleri için.|  
|.NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* bu işletim sisteminde desteklenmiyor.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) desteklenen işletim sistemleri için.<br /><br /> Windows 7 .NET Framework'ün başarısız yüklemeler için bu ileti genellikle Windows 7 SP1 yüklü olmadığını gösterir. Windows 7 sistemlerde, Windows 7 SP1 .NET Framework gerektirir. Windows 7'de olan ve henüz Service Pack 1 yüklü değilse .NET Framework'ü yüklemeden önce yapmanız gerekir. Windows 7 SP1 yükleme hakkında daha fazla bilgi için bkz. [Windows 7 Service Pack 1 (SP1) yüklemeyi öğrenin](https://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1).|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. *x* işletim sistemi ya da Server Core 2008 R2 SP1 tam bir sürümünü gerektirir. Lütfen Windows Server 2008 SP2 veya Windows Server 2008 R2 SP1 ya da Server Core 2008 R2 SP1'ın tam sürümünü yükleyin ve .NET Framework 4.5 yeniden çalıştırın. *x* kurulumu.|The .NET Framework , Windows Server 2008 R2 SP1 veya sonrası ile birlikte Sunucu Çekirdeği Rolünde desteklenir. Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|.NET Framework 4.5. *x* zaten bu işletim sisteminin bir parçasıdır ancak şu anda kapalı durumdadır ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] yalnızca).|Bkz: [kapatma Windows özelliklerini aç veya Kapat](https://go.microsoft.com/fwlink/p/?LinkId=248438) Windows Web sitesinde.|  
|Bu kurulum programı bir x86 bilgisayar gerektiriyor. x64 veya IA64 bilgisayarlara yüklenemez.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|Bu kurulum programı bir x64 veya x86 bilgisayar gerektiriyor. IA64 bilgisayarlara yüklenemez.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Program Uyumluluk sorunları

.NET Framework 4.5 veya onun nokta sürümleri yüklemesi Windows programı uyumluluk modunda çalışırken 1603 hata kodu veya bloklar ile başarısız oluyor. **Program Uyumluluk Yardımcısı** .NET Framework düzgün yüklenmemiş ve önerilen ayarı (Program uyumluluğu modu) kullanarak yeniden yüklemenizi ister gösterir. Program Uyumluluğu modu, başarısız olan veya iptal edilen önceki .NET Framework Kurulumu Programını çalıştırma girişimlerinde Program Uyumluluk Yardımcısı tarafından da ayarlanmış olabilir.

.NET Framework yükleyicisi Program Uyumluluk modunda çalıştırılamaz. Bu engelleme sorununu çözmek için, uyumluluk modu ayarının, Kayıt Defteri Düzenleyicisi'nde sistem genelinde etkinleştirilmediğinden emin olmanız gerekir:

1. Seçin **Başlat** düğmesine ve ardından **çalıştırma**.

1. İçinde **çalıştırma** iletişim kutusu, "regedit" yazın ve ardından **Tamam**.

1. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarlara göz atın:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ad sütununda aranacak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 indirme adlarını, hangi sürümünde bağlı olarak, yüklemekte olduğunuz ve bu girişleri silin. İndirme adları için bkz. [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md) makalesi.

1. Sürüm 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 için .NET Framework yükleyiciyi yeniden çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

[Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)   
[Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
