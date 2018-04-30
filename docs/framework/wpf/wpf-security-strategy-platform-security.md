---
title: WPF Güvenlik Stratejisi - Platform Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d4606023c1a9f3252e9039da547f384d27b7ecd
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-security-strategy---platform-security"></a>WPF Güvenlik Stratejisi - Platform Güvenliği
Windows Presentation Foundation (WPF) güvenlik hizmetleri, çeşitli sağlarken, bu da işletim sistemi içeren bir temel platform güvenlik özelliklerini yararlanır [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], ve [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Sağlamak üzere bu Katmanlar birleştirilmiştir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] herhangi tek hata noktası, önlemek için aşağıdaki resimde gösterildiği gibi çalışır bir güçlü, savunma güvenlik modeli:  
  
 ![WPF Güvenliği çizimi](../../../docs/framework/wpf/media/windowplatformsecurity.PNG "windowplatformsecurity")  
  
 Bu konunun geri kalanında ait bu katmanların her özellikleri ele alır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] özellikle.  
  

  
<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>İşletim sistemi güvenliği  
 Gerekli işletim sistemi en düşük düzeyde [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] olan [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Çekirdeği [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] ile oluşturulan dahil olmak üzere tüm Windows uygulamaları için güvenlik temelini çeşitli güvenlik özellikleri sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] güvenlik özelliklerini içerir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ve daha fazla genişletir. Bu konu en önemli olan bu güvenlik özellikleri derecesini açıklar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], de nasıl [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] daha derinlemesine savunma sağlamak için onlarla tümleştirir.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Genel bir gözden geçirme ve Windows'un güçlendirme ek olarak, üç anahtar özelliklerinden vardır [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , bu konuda ele alınacaktır:  
  
-   /GS derleme  
  
-   [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS derleme  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] Tüm de dahil olmak üzere pek çok çekirdek sistem kitaplıkları derleyerek koruma sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] gibi bağımlılıkları [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], arabellek taşmaları azaltmaya yardımcı olmak için. C/C++ komut satırı derleyicisi ile /GS parametresini kullanarak elde edilir. Arabellek aşırı çalıştırmaları açıkça kaçınılmalıdır rağmen /GS derleme bir-savunma yanlışlıkla veya kötü amaçlı olarak bunları tarafından oluşturulan olası güvenlik açıklarına karşı ilişkin bir örnek sağlar.  
  
 Geçmişte, arabellek taşmaları pek çok yüksek etkili güvenlik açıklarına neden olmuştur. Bir saldırganın bir arabellek sınırları Yazar kötü amaçlı kod eklenmesine izin veren bir kod güvenlik açığı yararlanan bir arabellek taşması oluşur. Bu, bir saldırgan, saldırganın kodunun yürütülmesini neden bir işlevin dönüş adresi yazarak kodu yürütme işlemi çalabilir sonra sağlar. Ele geçirilen bir işlem olarak aynı ayrıcalıklarıyla rastgele kod yürüten kötü amaçlı kod sonucudur.  
  
 Yüksek bir düzeyde /GS derleyici bayrağı yerel dize arabellekleri sahip bir işlevin dönüş adresi korumak için bir özel güvenlik tanımlama bilgisi ekleyerek bazı olası arabellek taşmaları karşı korur. Bir işlev döndürür sonra güvenlik tanımlama bilgisi önceki değeriyle karşılaştırılır. Değer değiştiyse, bir arabellek taşması oluşmuş olabilir ve işlem bir hata durumu durdurulur. İşlem durdurulması, kötü amaçlı kod yürütülmesini engeller. Bkz: [/GS (arabellek güvenlik denetimi)](http://msdn.microsoft.com/library/8dbf701c.aspx) daha fazla ayrıntı için.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] /GS bayrağıyla için savunma henüz başka bir katman ekleyin derlenmiş [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Microsoft Windows Update geliştirmeleri  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] Ayrıca, geliştirildi [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] indirme ve güncelleştirmeleri yükleme işlemini basitleştirmek için. Bu değişiklikler önemli ölçüde güvenliği [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] müşterilere göre sistemlerini özellikle güvenlik güncelleştirmeleriyle güncel olduğundan emin olmak için yardımcı olma.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kullanıcıların [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] yararlı "En az ayrıcalıklı kullanıcı erişimi" kod bütünlüğü denetimler de dahil olmak üzere işletim sisteminin ek güvenlik iyileştirmeleriyle ve ayrıcalık yalıtım.  
  
#### <a name="user-account-control-uac"></a>Kullanıcı Hesabı Denetimi (UAC)  
 Günümüzde, Windows kullanıcıları birçok uygulama yükleme veya yürütme ya da her ikisi için bunları gerektirdiğinden yönetici ayrıcalıklarıyla çalıştırın eğilimindedir. Varsayılan uygulama ayarları kayıt defterine yazma için bir örnektir.  
  
 Yönetici ayrıcalıklarıyla çalıştığından, uygulamalar, yönetici ayrıcalıkları verilmiş işlemlerini yürütmek gerçekten anlamına gelir. Güvenlik Bu yönetici ayrıcalıklarına sahip çalışan bir işlemi ele geçirilmesini herhangi bir kötü amaçlı kod önemli sistem kaynaklarına erişim de dahil olmak üzere, o ayrıcalıkları otomatik olarak devralır etkisidir.  
  
 Bu güvenlik tehdidi karşı korumak için bir en az sayıda gerekli ayrıcalığa uygulamaları çalıştırmak için yoludur. Bu en az ayrıcalık prensibi bilinir ve çekirdek özelliğidir [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] işletim sistemi. Bu özellik, kullanıcı hesabı denetimi (UAC) olarak adlandırılır ve tarafından kullanılan [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] iki anahtar yolla UAC:  
  
-   Bir yönetici kullanıcı olsa bile, uygulamaların çoğu UAC ayrıcalıklarıyla varsayılan olarak, çalıştırılacak; Yönetici ayrıcalıkları gerektiren uygulamalar yönetici ayrıcalıklarıyla çalıştırın. Yönetici ayrıcalıklarıyla çalıştırmak için uygulamaları açıkça ya da kendi uygulama bildirim ya da Güvenlik İlkesi'nde bir girdi olarak işaretlenmesi gerekir.  
  
-   Uyumluluk sağlamak üzere Sanallaştırma Çözümleri ister. Örneğin, C:\Program Files gibi sınırlı konumlara yazmak birçok uygulamayı deneyin. UAC altında yürütme uygulamalar için bir kullanıcı başına alternatif konum yazmak için yönetici ayrıcalıkları gerektirmez bulunmaktadır. Gerçekte alternatif, kullanıcı başına konum yazmak için yazıyorsanız düşündüğünüz uygulamaların; böylece UAC altında çalışan uygulamalar için UAC C:\Program Files sanallaştırır. Bu tür bir uyumluluk iş UAC içinde daha önce çalışamadı birçok uygulamaları çalıştırmak işletim sisteminin sağlar.  
  
#### <a name="code-integrity-checks"></a>Kod bütünlüğü denetimleri  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] Sistem dosyalarını veya çekirdek yük/çalışma zamanında eklenmiş gelen kötü amaçlı kod önlemeye yardımcı olmak için daha derin kod bütünlüğü denetimlerini içerir. Bu, sistem dosyası koruma gider.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Tarayıcıda barındırılan uygulamalar için sınırlı haklar işlemi  
 Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları Internet bölgesi sandbox içinde yürütün. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ile tümleştirme [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] bu ek destek korumasıyla genişletir.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 ve XP için Internet Explorer 7  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] işletim sistemi güvenliği için işlem ayrıcalıkları sınırlayarak yararlanır [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] daha fazla koruma için. Tarayıcıda barındırılan önce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında, işletim sistemi işlem belirtecinden gereksiz ayrıcalıklarını kaldırır bir ana bilgisayar işlemi oluşturur. Bazı örnekleri kaldırılır ayrıcalıkları makinedeki tüm dosyalara kullanıcının makine, yük sürücüleri ve okuma erişimi kapatmaya özelliği içerir.  
  
#### <a name="internet-explorer-7-for-vista"></a>Vista için Internet Explorer 7  
 İçinde [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları korumalı modda çalışır. Özellikle, [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] orta düzey bütünlüğüyle çalıştırın.  
  
#### <a name="defense-in-depth-layer"></a>Savunma katman  
 Bu yana [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] bu ayrıcalıklarının kaldırılması bölgesi izin kümesi zarar değil Internet tarafından genellikle korumalı olan [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] uyumluluk açısından. Bunun yerine, ek bir savunma katman oluşturulur; korumalı bir uygulama diğer katmanları yararlanma ve işlem çalabilir mümkün ise, işlem hala yalnızca ayrıcalıkları sınırlı.  
  
 Bkz: [en az ayrıcalıklı kullanıcı hesabı kullanarak](http://technet.microsoft.com/library/cc700846.aspx).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Ortak dil çalışma zamanı güvenlik  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Doğrulama ve doğrulama içeren anahtar güvenlik avantajları sunar [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]ve güvenlik kritik Metodoloji.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Doğrulama ve doğrulama  
 Derleme yalıtım ve bütünlüğünü sağlamak için [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] doğrulama işlemi kullanır. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] Taşınabilir yürütülebilir (PE) dosya biçimlerinde derlemenin dışından noktası adresleri doğrulayarak derlemeleri yalıtılır doğrulama sağlar. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] doğrulama ayrıca bir derlemenin içinde ekli meta veri bütünlüğünü doğrular.  
  
 Tür güvenliği sağlamak için genel güvenlik sorunları önlemeye yardımcı olmak (örn. arabellek taşmaları) ve korumalı alan alt işlem yalıtım aracılığıyla etkinleştirin [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] güvenlik doğrulama kavramı kullanır.  
  
 Yönetilen uygulamalar, Microsoft Ara dili (MSIL içine) derlenir. Yönetilen bir uygulamada yöntemleri çalıştırıldığında, kendi MSIL Just-In-Time (JIT) derleme aracılığıyla yerel koda derlenir. JIT derleme kodu desteklemez olun çok sayıda güvenlik ve sağlamlık kurallarını uygular doğrulama işlemi aşağıdakileri içerir:  
  
-   Türü sözleşmeleri ihlal  
  
-   Arabellek aşırı çalıştırmaları tanıtır  
  
-   Müthiş bir başarı bellek erişin.  
  
 Güvenilen kod kabul sürece doğrulama kurallarına uymuyor yönetilen kod yürütmek için izin verilmiyor.  
  
 Doğrulanabilen kod avantajlarından bir anahtar neden nedeni [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] .NET Framework üzerinde oluşturur. Doğrulanabilen kod kullanılan toplasa bile, olası güvenlik açıklarını yararlanmasını olasılığını önemli ölçüde düşürdü.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 Bir istemci makine çok çeşitli kaynakları yönetilen bir uygulamaya erişim dosya sistemi, kayıt defteri, yazdırma hizmetleri, kullanıcı arabirimi, yansıma ve ortam değişkenleri dahil olduğunu gösterir. Bir yönetilen uygulamayı herhangi bir istemci makine üzerindeki kaynaklara erişebilmeniz için önce bunu yapmak için .NET Framework izni olmalıdır. Bir izin [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] sınıfıdır <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] uygulamaları yönetilen her bir kaynağın erişim için bir alt kümesi uygular.  
  
 Yönetilen bir uygulama tarafından verilen izinler kümesini [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] yürütme başladığında bir izin kümesi olarak bilinir ve uygulama tarafından sağlanan bulgu göre belirlenir. İçin [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar, sağlanan kanıt olduğu konumu veya bölge, kendisinden uygulamaları başlattı. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] Aşağıdaki bölgeler tanımlar:  
  
-   **Bilgisayarım**. Uygulamaları istemci makineden (tam olarak güvenilir) başlattı.  
  
-   **Yerel Intranet**. İntranetten başlatılan uygulamalara. (Biraz güvenilir).  
  
-   **Internet**. Internet'ten başlatılan uygulamalara. (Az güvenli).  
  
-   **Güvenilen siteler**. Güvenilir olarak bir kullanıcı tarafından tanımlanan uygulamalar. (Az güvenli).  
  
-   **Güvenilmeyen siteleri**. Güvenilmeyen gibi bir kullanıcı tarafından tanımlanan uygulamalar. (Güvenilmeyen).  
  
 Bu bölgeler her [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] her ilişkilendirilmiş güven düzeyi eşleşen izinleri içeren önceden tanımlanmış izin kümesi sağlar. Bu güncelleştirmeler şunlardır:  
  
-   **FullTrust**. Gelen başlatılan uygulamalara **Bilgisayarım** bölgesi. Tüm olası izinleri verilir.  
  
-   **LocalIntranet**. Gelen başlatılan uygulamalara **yerel Intranet** bölgesi. İzinler kümesini yalıtılmış depolama, sınırsız UI erişim, sınırsız dosya iletişim kutularını, sınırlı yansıma, ortam değişkenleri sınırlı erişim dahil olmak üzere bir istemci makinenin kaynaklarına Orta erişim sağlamak için verilmiştir. Kayıt defteri gibi kritik kaynaklara izinlerini sağlanmadı.  
  
-   **Internet**. Gelen başlatılan uygulamalara **Internet** veya **Güvenilen siteler** bölgesi. İzinler kümesini yalıtılmış depolama da dahil olmak üzere bir istemci makinenin kaynaklarına sınırlı erişimi dosyasını açın sağlanan yalnızca verilir ve kullanıcı Arabirimi sınırlıdır. Esas olarak, bu izni istemci makine yalıtır uygulamalardan ayarlar.  
  
 Gelen olarak tanımlanmasından uygulamaları **güvenilmeyen siteleri** bölge tarafından izin verilen [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] hiç. Sonuç olarak, önceden tanımlanmış izin kümesi için yok.  
  
 Aşağıdaki şekilde bölgeleri, izin kümeleri, izinleri ve kaynakları arasındaki ilişki gösterilmektedir.  
  
 ![CAS izin kümeleri](../../../docs/framework/wpf/media/caspermissionsets.png "CASPermissionSets")  
  
 Bölge güvenlik sandbox uygulamak eşit herhangi Internet kısıtlamalarını kod bir [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] bir sistem kitaplığından alır dahil olmak üzere [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Bu kodu her bit kilitli, hatta sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ne yazık ki, yürütmek için bir [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] execute Internet bölgesi güvenlik korumalı alanı tarafından etkinleştirilmiş olandan daha fazla izinleri gerektiren işlevselliğini gerekiyor.  
  
 Göz önünde bulundurun bir [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aşağıdaki sayfayı içeren uygulama:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Bu yürütmek için [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], arka plandaki [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod arama bulunandan daha fazla işlevsellik yürütmek [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)]dahil:  
  
-   İşleme için bir pencere tanıtıcının (hWnd) oluşturma  
  
-   İleti gönderme  
  
-   Tahoma yazı tipi yükleniyor  
  
 Bir güvenlik bakış açısından bakıldığında, doğrudan bu işlemlerin herhangi biri için korumalı uygulamadan erişimine yıkıcı olacaktır.  
  
 Neyse ki, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] korumalı uygulama adına yükseltilmiş ayrıcalıklarla yürütmek bu işlemler sağlayarak bu duruma caters. Tüm sırasında [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] işlemleri sınırlı Internet bölgesi güvenlik izinlerini uygulama etki alanının karşı denetlenir [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (diğer sistem kitaplıkları olduğu gibi) tüm olası içeren bir izin kümesi verildi izinleri  
  
 Bu gerektiren [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Internet bölgesi izin kümesi ana uygulama etki alanı tarafından yönetilen Bu ayrıcalıkları önlerken yükseltilmiş ayrıcalıklar alır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Bunu kullanarak yapar **Assert** izin yöntemi. Aşağıdaki kod bu nasıl gerçekleştiğini gösterir.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** temelde gerektirdiği sınırsız izinleri engeller [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Internet ile sınırlanmış bölge izinlerini [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)].  
  
 Bir platform açısından [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kullanımından sorumludur **Assert** doğru; yanlış bir kullanımı **Assert** ayrıcalık yükseltmesine kötü amaçlı kod sağlayabilir. Sonuç olarak, yalnızca çağırmak önemli olan **Assert** gerekli olduğunda ve bu korumalı alan emin olmak için kısıtlamaları değişmeden kalır. Örneğin, korumalı kod rastgele dosyaları açmaya izin verilmez, ancak yazı tiplerini kullanmasına izin verilir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yazı tipi işlevini çağırarak kullanmak korumalı uygulamalar sağlayan **Assert**ve [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] korumalı uygulama adına bu yazı tipleri içeren bilinen dosyaları okumak için.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] .NET Framework ile birlikte ve tümleşir kapsamlı dağıtım teknolojisi [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (bkz [ClickOnce dağıtımına genel bakış](http://msdn.microsoft.com/library/142dbbz4.aspx) ayrıntılı bilgi için). Tek başına [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar kullanılarak dağıtılabilir [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)]tarayıcıda barındırılan uygulamalar ile dağıtılmalıdır yaparken [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Kullanılarak dağıtılan uygulamalar [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] bir ek güvenlik katmanı verilen [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; esas olarak, [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] dağıtılan uygulamalar ihtiyaç duydukları izinleri isteyin. Yalnızca bu izinlerin verildiğini bunlar, uygulamanın dağıtıldığı bölge için izinler kümesini aşarsa değil. Uygulama erişimi kaynakların sayısını başlatma bölgenin izin kümesi tarafından sağlanan olandan daha az olsalar bile, yalnızca gerekli olan izinler kümesi azaltarak tam minimumda azaltın. Sonuç olarak, uygulama geçirilirse, istemci makine zarar potansiyeli daha azdır.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Güvenlik açısından kritik yöntemi  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Internet bölgesi korumalı alanı etkinleştirmek için izinleri kullanan kodu [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] yüksek olası derecede güvenlik denetim ve denetim için uygulamaları tutulur. Bu gereksinim kolaylaştırmak için ayrıcalık yükseltir kodu yönetmek için .NET Framework yeni destek sağlar. Özellikle, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ayrıcalık yükseltir kodunu belirleyin ve onunla işaretlemek sağlar <xref:System.Security.SecurityCriticalAttribute>; herhangi bir kod ile işaretlenmemiş <xref:System.Security.SecurityCriticalAttribute> hale *saydam* bu yöntemi kullanarak. Buna karşılık, yönetilen ile işaretli olmayan kod <xref:System.Security.SecurityCriticalAttribute> yükseltme yaptığınıza ayrıcalığını engellenir.  
  
 Güvenlik açısından kritik Metodoloji organizasyonu sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ayrıcalık içine yükseltir kod *güvenlik açısından kritik çekirdek*, saydam olan geri kalan. Güvenlik açısından kritik kod yalıtma etkinleştirir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] mühendislik ekibi odaklanmak standart güvenlik uygulamaları özellik güvenlik açısından kritik çekirdek bir ek güvenlik analizi ve kaynak denetimi (bkz [WPF güvenlik stratejisi -Güvenlik mühendislik](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)).  
  
 .NET Framework genişletmek için güvenilen kod izin verdiğini unutmayın [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] işaretlenir Yönetilen derlemeler yazmak geliştiricilere sağlayarak Internet bölgesi sandbox <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) ve kullanıcının Genel Derleme Önbelleği (GAC) dağıtılır. Internet'ten kötü amaçlı kod dahil olmak üzere bu derleme çağırmak herhangi bir kod verdiğinden APTCA ile bir derlemeyi işaretleme bir yüksek oranda gizli güvenlik işlemdir. Bunu yaparken çok dikkatli ve en iyi yöntemler kullanılmalıdır ve kullanıcılar için bu yüklenecek yazılım güvenmeyi seçmeniz gerekir.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer güvenliği  
 Güvenlik sorunları azaltır ve güvenlik yapılandırması, basitleştirme ötesinde [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] çeşitli özellikler kullanıcılarının güvenliği, güvenlik geliştirmelerini içerir [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Bu özelliklerin thrust daha geniş bir denetim kullanıcılar kendi gözatma deneyimi üzerinde çalışır.  
  
 Öncesinde [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], kullanıcıların aşağıdakilerden herhangi birini tabi olabilir:  
  
-   Rastgele açılır pencereleri.  
  
-   Kafa karıştırıcı betik yönlendirmesi.  
  
-   Bazı Web sitelerinde çok sayıda güvenlik iletişim kutuları.  
  
 Bazı durumlarda, kullanıcılar yükleme yanıltma tarafından kandırarak güvenilmez Web siteleri isteriz [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] veya tekrar tekrar gösterme bir [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] yükleme iletişim kutusu, kullanıcı iptal olsa bile. Bu teknikler kullanarak, çok sayıda kullanıcı casus yazılım uygulamaların yüklenmesini sonuçlanan zayıf kararları içine sağladı olduğunu mümkün değildir.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] Bu türdeki bir kullanıcı başlatma kavramı Uzayda Döndür sorunlarını azaltmak için çeşitli özellikler içerir. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] bir kullanıcı olarak bilinen bir eylem önce bir bağlantı veya sayfa öğesinde tıklamıştır algılar *kullanıcı başlatma*ve farklı bir şekilde ne zaman benzer bir eylem bunun yerine bir sayfadaki komut tarafından tetiklenir değerlendirir. Örneğin, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] içerir bir **Açılır Pencere Engelleyicisi** bir kullanıcı bir açılır pencere oluşturma sayfasında önce düğmesine tıkladığında algılar. Böylece [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] kullanıcılar için sorun ne istediğiniz açılır pencereleri önlerken en zararsız açılır pencerelere izin vermek için. Engellenen Açılır pencereleri yakalanan yeni altında **bilgi çubuğu**, el ile engellemeyi geçersiz ve açılır görüntülemek kullanıcı izin verir.  
  
 Aynı kullanıcı başlatma mantığı da uygulanan **açık**/**kaydetmek** güvenlik ister. [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] bir yükseltme önceden yüklenmiş bir denetimden temsil ettikleri sürece yükleme iletişim kutuları her zaman bilgi çubuğunun altında yakalanır. Bunları istenmeyen veya kötü amaçlı yazılım yüklemek için taciz sitelere karşı korumalı olduğundan güvenli, daha denetlenen kullanıcı deneyimi kullanıcılara vermek için bu ölçüleri birleştirin.  
  
 Bu özellikleri kullanan müşteriler de koruma [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] izin vermeniz indirmek ve yüklemek web sitelerine göz atmak için [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. Özellikle, bunun nedeni, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] kullanıcıların hangi teknolojisi dahil olmak üzere, oluşturmak için kullanılan yedeklemiş kötü amaçlı veya devious uygulamaları yüklemek olasılığını azaltır daha iyi bir kullanıcı deneyimi sunar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Bu korumalar kullanarak ekler [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] Internet üzerinden kendi uygulamaları indirme kolaylaştırmak için. Bu yana [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] Internet bölgesi güvenlik sandbox içinde yürütün, sorunsuz bir şekilde başlatılabilir. Diğer yandan, tek başına [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları çalıştırmak için tam güven gerektirir. Bu uygulamalar için [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] uygulamanın ek güvenlik gereksinimleri kullanımını bildirmek için başlatma işlemi sırasında bir güvenlik iletişim kutusu görüntülenir. Ancak, bu kullanıcı tarafından başlatılan olması gerekir, ayrıca kullanıcı tarafından başlatılan mantığı tarafından yönetilir ve iptal edilemez.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] bir araya getirir ve güvenlik özelliklerini genişletir [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] çabası güvenlik parçası olarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows XP SP2'de Microsoft Internet Explorer 6'deki güvenlik anlama](http://www.microsoft.com/downloads/details.aspx?FamilyId=E550F940-37A0-4541-B5E2-704AB386C3ED&displaylang=en)  
 [Anlama ve korumalı mod Internet Explorer'da çalışma](http://msdn.microsoft.com/library/bb250462.aspx)  
 [Windows XP Service Pack 3](http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)  
 [Windows Vista Güvenlik Kılavuzu](http://www.microsoft.com/downloads/details.aspx?familyid=a3d1bbed-7f35-4e72-bfb5-b84a526c1565&displaylang=en)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)  
 [Güvenlik](../../../docs/framework/wpf/security-wpf.md)  
 [WPF Kısmi Güven Güvenliği](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
