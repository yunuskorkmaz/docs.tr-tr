---
title: "Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ccac79516966a6da51d2b590cd22409f0703576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme

Çalıştırdığınızda [web veya çevrimdışı yükleyici](../../../docs/framework/install/guide-for-developers.md) .NET Framework 4.5 veya sonraki sürümler için engeller veya .NET Framework yüklenmesini engelleyen bir sorunla karşılaşabilirsiniz. Aşağıdaki tabloda, olası engelleme sorunları listelenmiş ve sorun giderme bilgilerinin bağlantıları sağlanmıştır.

Windows 8 ve üzeri, .NET Framework bir işletim sistemi bileşenidir ve bağımsız olarak kaldırılamaz. .NET Framework güncelleştirmelerini görünür **yüklü güncelleştirmeler** sekmesi Denetim Masası'ndaki **programlar ve Özellikler** uygulama. .NET Framework üzerinde .NET Framework değil önceden yüklenmiş işletim sistemleri için görünür **Kaldır veya Değiştir bir program** sekmesinde (veya **Program Ekle/Kaldır** sekmesinde),  **Program ve Özellikler** Denetim Masası'ndaki uygulama. .NET Framework önceden Windows sürümleri hakkında daha fazla bilgi için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> .NET Framework 4.x sürümlerinin yerinde güncelleştirmelerinin olduğundan, bir sistemde 4.x zaten daha sonraki bir sürümün yüklü olduğu .NET Framework'ün önceki bir sürümünü yükleyemezsiniz. Örneğin, .NET Framework 4.7.1 işletim sistemi ile önceden yüklenmiş olduğundan Windows 10 sonbaharda oluşturucuları güncelleştirme bir sistemde, .NET Framework 4.6.2, yükleyemezsiniz.

.NET Framework'ün hangi sürümlerinin bir sistemde yüklü olan belirleyebilirsiniz. Bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) daha fazla bilgi için.

Bu tabloda, 4.5. *x* .NET Framework 4.5 ve onun noktası sürümleri başvuruyor 4.5.1 ve 4.5.2, 4.6. *x* .NET Framework 4.6 ve onun noktası sürümleri başvuruyor 4.6.1 ve 4.6.2 ve 4.7. *x* .NET Framework 4.7 hem de 4.7.1, noktası yayınlandığı anlamına gelir.

|İletiyi engelleme|Daha fazla bilgi veya bu sorunu gidermek için|  
|----------------------|--------------------------------------------------|  
|Microsoft .NET Framework ürününün kaldırılması bazı uygulamaların işlevini durdurmasına neden olabilir.|Genel olarak, kullandığınız bir uygulama .NET Framework'ün belirli bir sürümüne bağlı olabileceği için, bilgisayarınıza yüklü olan .NET Framework sürümlerinden hiçbirini kaldırmamalısınız. Daha fazla bilgi için bkz: [kullanıcılar için .NET Framework](../../../docs/framework/get-started/index.md#ForUsers) içinde *Başlarken* Kılavuzu.|  
|.NET framework 4.5*.x*/4.6*.x*  /4.7 (ENU) veya sonraki bir sürümü zaten yüklüyse bu bilgisayara.|Herhangi bir işlem gerekli değil.<br /><br /> Bir sistemde hangi .NET Framework sürümlerinin yüklendiğini belirlemek için bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5*.x*/4.6*.x*/4.7*.x* (*dil*) .NET Framework 4.5 gerektirir*.x*/4.6*.x*/4.7*.x*. Lütfen .NET Framework 4.5 yükleyin*.x*/4.6*.x*/4.7*.x* İndirme Merkezi'nden ve kurulumu yeniden çalıştırın.|Bir dil paketi yüklemeden önce belirtilen .NET Framework sürüm İngilizce sürümünü yüklemeniz gerekir. Daha fazla bilgi için bölümüne bakarak [dil paketlerini yüklemek için](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) Yükleme Kılavuzu'ndaki.|  
|.NET Framework 4.5 yüklenemiyor*.x*/4.6*.x*/4.7*.x*. Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.<br /><br /> veya<br /><br /> Bilgisayarınızdaki diğer uygulamalar bu programla uyumlu değil.|Bu ileti büyük olasılıkla .NET Framework'ün önizleme veya RC sürümünün yüklenmiş olmasından kaynaklanmıştır. Önizleme veya RC sürümünü kaldırın ve kurulumu yeniden çalıştırın.|  
|.NET framework 4.5*.x*/4.6*.x*  /4.7 kullanarak bu paketi kaldırılamıyor. .NET Framework 4.5 kaldırmak için*.x*/4.6*.x* bilgisayarınızdan Git **Denetim Masası**, seçin **programlar ve Özellikler**, seçin **Yüklü güncelleştirmeleri görüntüle**, Microsoft Windows (KB2828152) güncelleştirmesi seçin ve ardından **kaldırma**.|Yüklemekte olduğunuz paketi preview veya .NET Framework'ün RC sürümleri kaldırma değil.<br /><br /> Önizleme veya RC kaldırmak Sürüm Denetim Masası'ndan.|  
|.NET Framework 4.5 kaldıramazsınız*.x*/4.6*.x*/4.7*.x*. Bilgisayarınızdaki diğer uygulamalar bu programa bağımlıdır.|Genel olarak, belirli bir .NET Framework sürümünü kullandığınız bir uygulama bağlı olabilir çünkü bilgisayarınızdan, .NET Framework sürümlerini kaldırın döndürmemelidir. Daha fazla bilgi için bkz: [kullanıcılar için .NET Framework](../../../docs/framework/get-started/index.md#ForUsers) içinde *Başlarken* Kılavuzu.|  
|.NET Framework 4.5*.x*/4.6*.x*/4.7*.x* yeniden dağıtılabilir bu işletim sistemi için geçerli değildir. Lütfen .NET Framework 4.5 indirin*.x*/4.6*.x*/4.7*.x* işletim sisteminizden Microsoft Download Center için.|Yüklemeye çalıştığınız [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, veya desteklenmeyen bir platformda 4.7.1 veya, tüm desteklenen işletim sistemleri için bileşenlerini içermez yükleme paketini seçtiniz. Çevrimdışı yükleyici kullanarak yüklemeyi yeniden çalıştırın ([4.5.1 için](http://go.microsoft.com/fwlink/p/?LinkId=309493), [4.5.2 için](http://go.microsoft.com/fwlink/p/?LinkId=397706), [4.6 için](http://go.microsoft.com/fwlink/p/?LinkId=528233), [4.6.1 için](http://go.microsoft.com/fwlink/p/?LinkId=671744), için [ 4.6.2](http://go.microsoft.com/fwlink/p/?LinkId=780604), için [4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)), veya [4.7.1](http://go.microsoft.com/fwlink/p/?LinkId=852090). Daha fazla bilgi için bkz: [Yükleme Kılavuzu](../../../docs/framework/install/guide-for-developers.md) ve [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) için desteklenen işletim sistemleri.|  
|KB ile ilgili güncelleştirme\<*numarası*> Bu ürünü yüklemeden önce yüklenmesi gerekir.|.NET Framework yüklemesi KB güncelleştirme .NET Framework yüklenmeden önce yüklü olması gerekir. Güncelleştirmeyi yükleyin ve sonra .NET Framework yükleme işlemini yeniden başlatın.<br /><br /> Örneğin, yüklemesi güncelleştirilmiş Windows 8.1, Windows RT 8.1, .NET Framework sürümleri ve Windows Server 2012 R2 gerektirir, karşılık gelen güncelleştirme [KB 2919355](https://support.microsoft.com/kb/2919355) yüklü olmalıdır.|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. *x* işletim sisteminin sonraki bir sürümünü gerektirir. Windows Server 2008 R2 SP1 ya da yeniden çalıştırın ve daha yüksek .NET Framework 4.5 yükleyin. *x* kurulumu.|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Ve 4.5.2, Sunucu Çekirdeği rolü Windows Server 2008 R2 SP1 veya sonraki desteklenir. Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|Bu bilgisayar üzerinde tüm kullanıcılar için bu işlemi tamamlamak üzere yeterli yetkiniz yok. Bir yöneticiyseniz ve yeniden çalıştırın oturum **Kurulum**.|.NET Framework yüklemek için bilgisayarda yönetici olmanız gerekir.|  
|Önceki yükleme bilgisayarınızın yeniden başlatılmasını gerektirdiği için Kurulum devam edemiyor. Lütfen bilgisayarınızı yeniden başlatın ve Kurulumu yeniden çalıştırın.|Yeniden başlatma tam olarak bir yüklemenin tamamlanabilmesi için bazen gereklidir. Bilgisayarınızı yeniden başlatın ve kurulumu yeniden çalıştırın için yönergeleri izleyin.<br /><br /> Nadir durumlarda Windows eksik güncelleştirmeleri sayısı algıladı ve sırasındaki sonraki güncelleştirmeyi yüklemek için yeniden başlatma sisteminizi birden çok kez yeniden başlatmanız istenebilir.|  
|.NET Framework Kurulumu Program Uyumluluk modunda çalıştırılamaz.|Bkz: [Program Uyumluluk sorunlarını](#compat) bu makalenin sonraki bölümlerinde bölümü.|  
|.NET framework 4.5*.x*/4.6*.x*/4.7*.x* bileşen deposu bozuk olduğundan yüklenmedi.|Bkz: [DISM ya da sistem güncelleştirme hazırlığı aracını kullanarak Windows Update düzeltme hatalarını](https://support.microsoft.com/en-us/kb/947821) daha fazla bilgi için.|  
|Windows Installer Hizmeti bu bilgisayarda kullanılamadığından kurulum çalıştırılamıyor.|Bkz: [yükleme ya da programlar güncelleştirilirken Windows Installer hizmeti hata](http://go.microsoft.com/fwlink/p/?LinkId=248684) Microsoft Support Web sitesinde.|  
|Windows Update Hizmeti bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bilgisayar, Microsoft Windows Update yerine Windows Server Update Services (WSUS) kullanacak şekilde yapılandırılabilir. Daha fazla bilgi için hata kodunu 0x800F0906 bölümüne bakın [.NET Framework 3.5 Windows 8 veya Windows Server 2012'deki yüklemeye çalıştığınızda hata kodları](http://support.microsoft.com/kb/2734782).<br /><br /> Ayrıca bkz. [bir bilgisayarda güncelleştirmelerini yönetmenize yardımcı olmak için Windows Update Aracısı'nın en son sürümünü elde etme](http://go.microsoft.com/fwlink/p/?LinkId=248437) Microsoft Support Web sitesinde.|  
|Arka Plan Akıllı Aktarım Hizmeti (BITS) bu bilgisayarda kullanılamadığından kurulum düzgün çalışmayabilir.|Bkz: [Windows Vista tabanlı bir bilgisayarda arka plan Akıllı Aktarım Hizmeti (BITS) kilitlenme önlemek için bir güncelleştirme](http://go.microsoft.com/fwlink/p/?LinkId=248680) Microsoft Support Web sitesinde.|  
|Windows update bir hatayla karşılaştı ve hata kodu 0x80070643 veya 0x643 görüntülenen olduğundan kurulum düzgün çalışmayabilir.|Bkz: [.NET Framework güncelleştirmeyi yükleme hatası: "0x80070643" veya "0x643"](https://support.microsoft.com/kb/976982) Microsoft Support Web sitesinde.|  
|.NET Framework 4.5. *.x*/4.6*.x*/4.7*.x* zaten bu işletim sisteminin bir parçasıdır. .NET Framework 4.5 yüklemek gerekmez*.x*/4.6*.x*/4.7*.x* yeniden dağıtılabilir.|Eylem yok.<br /><br /> Bir sistemde hangi .NET Framework sürümlerinin yüklendiğini belirlemek için bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) için desteklenen işletim sistemleri.|  
|.NET Framework 4.5*.x*/4.6*.x*/4.7*.x* bu işletim sisteminde desteklenmiyor.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md) için desteklenen işletim sistemleri.<br /><br /> Windows 7 .NET Framework'ün başarısız yüklemeler için Windows 7 SP1 yüklü değil Bu ileti genellikle gösterir. Windows 7 sistemlerde, Windows 7 SP1 .NET Framework gerektirir. Windows 7 olan ve henüz Service Pack 1 yüklü olmayan, .NET Framework yüklemeden önce yapmanız gerekir. Windows 7 SP1'i yükleme hakkında daha fazla bilgi için bkz: [Windows 7 Service Pack 1 (SP1) yüklemeyi öğrenin](http://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1).|  
|Bilgisayarınızda şu anda Windows Server 2008 işletim sisteminin Sunucu Çekirdeği yüklemesi çalışıyor. .NET Framework 4.5. *x* işletim sistemi veya Server Core 2008 R2 SP1 tam bir sürümünü gerektirir. Lütfen Windows Server 2008 SP2 veya Windows Server 2008 R2 SP1 veya Server Core 2008 R2 SP1'ın tam sürümünü yükleyin ve .NET Framework 4.5 yeniden çalıştırın. *x* kurulumu.|The .NET Framework , Windows Server 2008 R2 SP1 veya sonrası ile birlikte Sunucu Çekirdeği Rolünde desteklenir. Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|.NET Framework 4.5. *x* zaten bu işletim sisteminin bir parçası olan ancak şu anda devre dışı ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] yalnızca).|Bkz: [kapatma Windows özelliklerini aç veya Kapat](http://go.microsoft.com/fwlink/p/?LinkId=248438) Windows Web sitesinde.|  
|Bu kurulum programı bir x86 bilgisayar gerektiriyor. x64 veya IA64 bilgisayarlara yüklenemez.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  
|Bu kurulum programı bir x64 veya x86 bilgisayar gerektiriyor. IA64 bilgisayarlara yüklenemez.|Bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Program Uyumluluk sorunları

Windows programı uyumluluk modunda çalışırken .NET Framework 4.5 veya kendi noktası sürümleri 1603 hata kodu veya blokları yüklenmesi başarısız olur. **Program Uyumluluk Yardımcısı** .NET Framework düzgün yüklenmemiş ve Önerilen ayar (Program Uyumluluk modu) kullanarak yeniden yüklemenizi ister gösterir. Program Uyumluluğu modu, başarısız olan veya iptal edilen önceki .NET Framework Kurulumu Programını çalıştırma girişimlerinde Program Uyumluluk Yardımcısı tarafından da ayarlanmış olabilir.

.NET Framework yükleyicisi Program Uyumluluk modunda çalıştırılamaz. Bu engelleme sorununu çözmek için, uyumluluk modu ayarının, Kayıt Defteri Düzenleyicisi'nde sistem genelinde etkinleştirilmediğinden emin olmanız gerekir:

1. Seçin **Başlat** düğmesine tıklayın ve ardından **çalıştırmak**.

1. İçinde **çalıştırmak** iletişim kutusu, "regedit" yazın ve ardından **Tamam**.

1. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarlara göz atın:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ad sütununda arayın [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 veya 4.7.1 indirin adları, hangi sürümünde bağlı olarak, yüklemekte olduğunuz ve bu girişleri silin. İndirme adları için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md) makalesi.

1. Sürüm 4.5, 4.5.1, 4.5.2 veya 4.6, 4.6.1, 4.6.2, 4.7 veya 4.7.1 için .NET Framework yükleyiciyi yeniden çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

[Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)   
[Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)
