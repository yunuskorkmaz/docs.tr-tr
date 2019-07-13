---
title: WPF Güvenlik Stratejisi - Platform Güvenliği
ms.date: 03/30/2017
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
ms.openlocfilehash: 5d7b76365178c78d2b20b9541d5e52a605158a77
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859822"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF Güvenlik Stratejisi - Platform Güvenliği
Windows Presentation Foundation (WPF), çeşitli güvenlik hizmetler sağlamasına karşın, bu da işletim sistemini içeren, temel alınan platformu'nın güvenlik özelliklerine yararlanır [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], ve [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Sağlamak üzere bu katmanları birleştirin [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] herhangi tek hata noktası önlemek için aşağıdaki şekilde gösterildiği gibi çalışır bir güçlü, savunma güvenlik modeli:  
  
 ![WPF güvenlik modelini gösteren diyagram.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Bu konunun geri kalanı ilgili bu katmanların her özellikleri anlatılmaktadır [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] özellikle.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>İşletim sistemi güvenlik  
 İşletim sisteminin gerektirdiği en düşük düzey [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] olduğu [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Setinin [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] ile oluşturulmuş dahil olmak üzere tüm Windows uygulamaları için güvenlik temelini çeşitli güvenlik özellikleri sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] güvenlik özelliklerini içerir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ve daha da genişletir. Bu konuda ele alınmıştır için önemli olan bu güvenlik özelliklerinin kapsamını [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], de nasıl [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] daha derinlemesine savunma sağlamak için bunları ile tümleşir.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Genel bir gözden geçirme ve Windows güçlendirme ek olarak, üç anahtar özelliklerinden vardır [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , bu konu başlığında ele alınacaktır:  
  
- /GS derleme  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS derleme  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] Tüm dahil olmak üzere pek çok çekirdek sistem kitaplıkları derleyerek koruma sağlayan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bağımlılıklar gibi [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], arabellek taşmalarına azaltmaya yardımcı olmak için. Bunu, /GS parametresi ile C/C++ komut satırı derleyicisini kullanarak elde edilir. Arabellek taşmaları açıkça kaçınılmalıdır olsa da, /GS derleme bir-savunma yanlışlıkla veya kötü amaçlı olarak bunları tarafından oluşturulan olası güvenlik açıklarına karşı bir örnek sağlar.  
  
 Tarihsel olarak, arabellek taşmalarına çok etkili güvenlik açıklarına neden olmuştur. Bir saldırganın bir arabellek sınırlarını Yazar kötü amaçlı kod eklenmesine izin veren bir kod güvenlik açığından yararlanan bir arabellek taşması oluşur. Bu daha sonra saldırgan, saldırganın kod yürütülmesine neden olacak bir işlevin dönüş adresi üzerine yazarak kod yürütme işlemini ele sağlar. Ele geçirilen bir işlem olarak aynı ayrıcalıklara sahip rastgele kod yürüten kötü amaçlı kod sonucudur.  
  
 Yüksek bir düzeyde /GS derleyici bayrağı, yerel dize arabelleği olan bir işlevin dönüş adresi korumak için bir özel güvenlik tanımlama bilgisi ekleyerek bazı olası arabellek taşması karşı korur. Bir işlev döndürdükten sonra güvenlik tanımlama bilgisi önceki değeriyle karşılaştırılır. Değer değiştiyse, bir arabellek taşması meydana gelebilir ve bir hata koşulu ile işlem durdurulur. İşlem durdurulurken, kötü amaçlı bir kodun yürütülmesini engeller. Bkz: [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) daha fazla ayrıntı için.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] savunma için başka bir katmanı eklemek için /GS bayrağı ile derlenmiş [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Microsoft Windows güncelleştirmesi geliştirmeleri  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] içinde geliştirildi [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] indirme ve güncelleştirmeleri yükleme işlemini basitleştirmek için. Bu değişiklikler güvenliğini önemli ölçüde geliştiren [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] müşterilere göre sistemlerini özellikle güvenlik güncelleştirmeleriyle güncel olduğundan emin olmak için yardımcı olur.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kullanıcıların [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] "En az ayrıcalıklı kullanıcı erişimi" kod bütünlüğü denetimlerini dahil işletim sisteminin ek güvenlik geliştirmelerinden yararlanmak ve ayrıcalık yalıtımı.  
  
#### <a name="user-account-control-uac"></a>Kullanıcı Hesabı Denetimi (UAC)  
 Bugün, çoğu uygulama yükleme veya yürütme veya her ikisi için bunları gerektirdiğinden, yönetici ayrıcalıklarıyla çalıştırmak için Windows kullanıcıları eğilimindedir. Varsayılan uygulama ayarları kayıt defterine yazmak için bir örnek verilebilir.  
  
 Yönetici ayrıcalıklarıyla çalışan uygulamaları yönetici ayrıcalıkları verilmiş işlemlerden yürütme gerçekten anlamına gelir. Güvenlik etkisi, yönetici ayrıcalıklarıyla çalışan bir işlemin ele geçirmeleri herhangi bir kötü amaçlı kod önemli sistem kaynakları dahil olmak üzere, bu ayrıcalıkları otomatik olarak devralır ' dir.  
  
 Bu güvenlik tehditlerine karşı koruma yollarından biri, en az miktarda gerekli ayrıcalıklara uygulamalar çalıştırmaktır. Bu en düşük öncelik ilkesini bilinir ve çekirdek özelliğidir [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] işletim sistemi. Bu özellik, kullanıcı hesabı denetimi (UAC) olarak adlandırılır ve tarafından kullanılan [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] UAC iki önemli şekilde:  
  
- Bir yönetici kullanıcı olsa bile, çoğu uygulama UAC ayrıcalıklarıyla varsayılan olarak, çalıştırılacak; yalnızca yönetici ayrıcalıkları gerekir. uygulamaları yönetici ayrıcalıklarıyla çalıştırın. Yönetici ayrıcalıklarıyla çalıştırmak için uygulamaları açıkça ya da kendi uygulama bildirim veya farklı bir güvenlik ilkesine giriş olarak işaretlenmesi gerekir.  
  
- Uyumluluk sağlamak için gibi sanallaştırma çözümleri. Örneğin, C:\Program Files gibi kısıtlı konumlara yazmak pek çok uygulama deneyin. UAC altında yürütülen uygulamalarda, kullanıcı başına alternatif konum yazmak için yönetici ayrıcalıkları gerektirmez bulunmaktadır. Kendisine yazıyorsanız düşündüğünüz uygulamaların gerçekten alternatif, kullanıcı başına konumuna yazma olacak şekilde UAC altında çalışan uygulamalar için UAC C:\Program Files sanallaştırır. Bu tür bir uyumluluk iş önceden UAC'a çalıştırılamadı birçok uygulamaları çalıştırmak işletim sistemi sağlar.  
  
#### <a name="code-integrity-checks"></a>Kod bütünlüğü denetimleri  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] Sistem dosyalarını veya çekirdek yükleme/çalıştırma zamanında eklenmiş gelen kötü amaçlı kod önlemeye yardımcı olmak için daha ayrıntılı kod bütünlüğü denetimlerini içerir. Bu, sistem dosyası koruma gider.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Tarayıcıda tutulan uygulamalar için sınırlı haklar işlemi  
 Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar Internet bölgesi korumalı alan içinde yürütün. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ile tümleştirme [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] ek destek ile bu koruma genişletir.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 ve XP için Internet Explorer 7  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] işletim sistemi güvenlik için işlem ayrıcalıklarını sınırlayarak yararlanır [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] daha fazla koruma için. Bir tarayıcıda barındırılan önce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında, işletim sistemi gereksiz ayrıcalıkları işlemi belirteçten kaldıran bir ana bilgisayar işlemi oluşturur. Bazı örnekler kaldırılan ayrıcalık makinedeki tüm dosyalara kullanıcının makine, yük sürücüleri ve okuma erişimi kapatma olanağı içerir.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7, Vista  
 İçinde [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları korumalı modda çalışır. Özellikle, [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] orta düzey bütünlüğü ile çalıştırın.  
  
#### <a name="defense-in-depth-layer"></a>Savunma katman  
 Bu yana [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] Internet bölgesi izin kümesi, bu ayrıcalıklarının kaldırılması zarar değil genel korumalı olan [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] uyumluluk açısından. Bunun yerine, ek bir savunma katmanı oluşturulur. korumalı bir uygulama diğer katmanları yararlanma ve işlem ele geçirme olanağına ise, işlem yine de yalnızca ayrıcalıkları sınırlı.  
  
 Bkz: [en az ayrıcalıklı kullanıcı hesabı kullanarak](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Ortak dil çalışma zamanı güvenlik  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Doğrulaması ve kimlik, Ekle anahtar güvenlik avantajları sunar [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]ve güvenlik kritik yöntemleri.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Doğrulama ve doğrulama  
 Derleme yalıtımında ve bütünlüğünü sağlamak için [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] doğrulama işlemi kullanır. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] doğrulama, derlemenin dışından noktası adresleri için taşınabilir yürütülebilir (PE) dosya biçimlerinde doğrulayarak derlemeleri yalıtılır sağlar. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] doğrulama Ayrıca, bir derlemede gömülü olan meta veri bütünlüğünü doğrular.  
  
 Tür güvenliği sağlamak için genel güvenlik sorunları önlemeye yardımcı olmak (örn: arabellek taşmalarını) ve korumalı alana alma alt işlem yalıtımı aracılığıyla etkinleştirme [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] güvenlik doğrulama kavramını kullanır.  
  
 Yönetilen uygulamalar, Microsoft Ara dil (MSIL içine) derlenir. Yönetilen bir uygulamada yöntem yürütüldüğünde, MSIL tam zamanında (JIT) derleme aracılığıyla yerel kod derlenir. JIT derlemesi kod daha önceden emin olmak çok sayıda güvenlik ve sağlamlık kuralları uygulayan bir doğrulama işlemi içerir:  
  
- Tür sözleşmeleri ihlal  
  
- Arabellek taşmaları Ekle  
  
- Çok bellek erişim.  
  
 Güvenilen kod olarak kabul edilir, doğrulama kurallarına uymuyor yönetilen kodu yürütmek için izin verilmez.  
  
 Doğrulanabilen kod avantajlarından bir anahtar olmasının nedenidir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] .NET Framework üzerinde oluşturur. Doğrulanabilen kod kullanılan için toplasa bile, olası güvenlik açıklarını kötüye kullanan olasılığını büyük oranda düşürdü.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 Bir istemci makinesi çok çeşitli kaynakları yönetilen bir uygulamaya erişim için dosya sistemi, kayıt defteri, yazdırma hizmetleri, kullanıcı arabirimi, yansıma ve ortam değişkenleri dahil olduğunu gösterir. Yönetilen bir uygulama istemci makinede kaynaklara erişebilmeniz için önce .NET Framework bunu izni olması gerekir. Bir izin [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] sınıfıdır <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] yönetilen uygulamalar her kaynak erişmek için bir alt sınıf uygular.  
  
 Tarafından yönetilen bir uygulamaya verilen izinler kümesini [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] yürütme başlatıldığında bir izin kümesi bilinir ve uygulama tarafından sağlanan kanıt tarafından belirlenir. İçin [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar, sağlanan kanıt olduğu konum veya uygulamalar, başlatılan bölge. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] Aşağıdaki bölgeler tanımlar:  
  
- **Bilgisayarım**. Uygulamaları İstemci makinesinden (tam güvenilir) başlattı.  
  
- **Yerel Intranet**. İntranetten başlatılan uygulamalar. (Biraz güvenilir).  
  
- **Internet**. Internet'ten başlatılan uygulamalar. (Az güvenli).  
  
- **Güvenilen siteler**. Uygulamaları güvenilir olarak bir kullanıcı tarafından tanımlanmış. (Az güvenli).  
  
- **Güvenilmeyen siteleri**. Güvenilmeyen bir kullanıcı tarafından belirlenen uygulamalar. (Güvenilmeyen).  
  
 Her biri bu bölgeler için [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] eşleşen her ilişkilendirilmiş güven düzeyi izinleri içeren bir önceden tanımlanmış izin kümesi sağlar. Bunlar:  
  
- **FullTrust**. Gelen başlatılan uygulamalara **Bilgisayarım** bölge. Tüm olası izinleri verilir.  
  
- **LocalIntranet**. Gelen başlatılan uygulamalara **yerel Intranet** bölge. İzinler kümesini Orta yalıtılmış depolama, Kısıtlanmamış UI erişimine, sınırsız dosya iletişim kutuları, sınırlı yansıma, ortam değişkenleri sınırlı erişim de dahil olmak üzere bir istemci makine kaynaklarına erişim sağlamak için verilir. Kayıt defteri gibi önemli kaynakları için izinleri sağlanmadı.  
  
- **Internet**. Gelen başlatılan uygulamalara **Internet** veya **Güvenilen siteler** bölge. İzinler kümesini yalıtılmış depolama da dahil olmak üzere bir istemci makine kaynaklarına sınırlı erişimi dosyasını açın. sağlanan yalnızca verilir ve kullanıcı Arabirimi sınırlı. Aslında, yalıtır uygulamaları İstemci makinesinden bu izni ayarlayın.  
  
 Uygulama olacak şekilde tanımlanan **güvenilmeyen siteleri** bölge tarafından izin verilen [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] hiç. Sonuç olarak, önceden tanımlanmış bir izin kümesi için yok.  
  
 Aşağıdaki şekilde, bölgeleri, izin kümeleri, izinleri ve kaynakları arasındaki ilişki gösterilmektedir:  
  
 ![CAS izin kümeleri gösteren diyagram.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Internet bölgesi güvenlik korumalı alan eşit bir sistem Kitaplığı'ndan, bir XBAP aktaran herhangi bir kod için kısıtlamalar dahil olmak üzere [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Bu kodun her bit kilitli, hatta sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Ne yazık ki yürütmek, bir XBAP Internet bölgesi güvenlik korumalı alanı tarafından etkinleştirilmiş daha fazla izin gerektirir işlevi yürütmek gerekir.  
  
 Şu sayfaya içeren bir XBAP uygulamasını göz önünde bulundurun:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Temel, bu XBAP yürütülecek [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kod arama XBAP için kullanılabilir olandan daha fazla işlevsellik yürütmek de dahil olmak üzere:  
  
- İşleme için bir pencere tutucu (HWND) oluşturma  
  
- İleti gönderme  
  
- Tahoma yazı tipi yükleniyor  
  
 Bir güvenlik ile korumalı uygulamadan tüm bu işlemleri doğrudan erişim sağlayan açısından, geri dönülemez olacaktır.  
  
 Neyse ki, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulama korumalı adına yükseltilmiş ayrıcalıklarla yürütmek bu işlemler sağlayarak bu duruma oluşturabilmesine olanak sağlar. Tüm çalışırken [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] işlemleri sınırlı Internet bölgesi güvenlik izinlerini uygulama etki alanının XBAP karşı denetlenir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (diğer sistem kitaplıkları olduğu gibi) tüm olası izinleri içeren bir izin kümesi verilir.
  
 Bunu gerektiren [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] konak uygulama etki alanı tarafından Internet bölgesi izinleri kümesi tabidir, bu ayrıcalıkları sağlarken yükseltilmiş ayrıcalıklar alır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Bunu kullanarak yapar **Assert** iznin yöntemi. Aşağıdaki kod bunu göstermektedir.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** aslında gerektirdiği sınırsız izinleri engeller [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Internet kısıtlı bölge XBAP izinleri.  
  
 Bir platform açısından [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kullanmak için sorumlu **onay** doğru; yanlış kullanımı **onay** ayrıcalıklarını yükseltme kötü amaçlı kod sağlayabilir. Sonuç olarak, yalnızca çağırmak önemli olan **Assert** gerektiğinde ve bu korumalı alan sağlamak için kısıtlamaları değişmeden kalır. Örneğin, korumalı kod rastgele dosyalar açmak için izin verilmez, ancak bu yazı tipleri kullanmasına izin verilir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] yazı tipi işlevini çağırarak kullanmak korumalı uygulamaları etkinleştiren **Assert**ve [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bu yazı tipleri korumalı adına uygulamayı içerecek bilinen dosyaları okumak için.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] .NET Framework ile birlikte ve tümleşik şekilde çalışarak, kapsamlı dağıtım teknolojisi [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (bkz [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment) ayrıntılı bilgi için). Tek başına [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kullanarak uygulamaları dağıtılabilir [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)]tarayıcıda tutulan uygulamalar ile dağıtılmalıdır korurken [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Kullanılarak dağıtılan uygulamalar [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] bir ek güvenlik katmanı verilir [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; aslında [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] dağıtılan uygulamaları, ihtiyaç duydukları izinleri isteyin. Yalnızca izinleri verilen kullanıcılar, uygulamanın dağıtıldığı bölge için izinler kümesini aşarsa değil. Yalnızca gerekli olan izin kümesini azaltarak başlatma bölgenin izni tarafından sağlanan değerinden olsalar bile ayarlayın, uygulama için en az azaltıldı için erişimi olduğunu kaynak sayısı. Sonuç olarak, uygulama geçirilirse, istemci makineye zarar olası azaltılır.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Güvenlik açısından kritik yöntemi  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] XBAP uygulamaları yüksek olası derecede güvenlik denetimi ve denetim için tutulmalıdır Internet bölgesi korumalı alan etkinleştirmek üzere izinleri kullanan kod. Bu gereksinim kolaylaştırmak için .NET Framework ayrıcalık yükseltir kodu yönetmek için yeni destek sağlar. Özellikle, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ayrıcalık yükseltir kodunu tanımlayın ve kendisiyle işaretlemek sağlayan <xref:System.Security.SecurityCriticalAttribute>; herhangi bir kod ile işaretlenmemiş <xref:System.Security.SecurityCriticalAttribute> olur *saydam* bu yöntemi kullanarak. Buna karşılık, yönetilen ile işaretlenmemiş koddan <xref:System.Security.SecurityCriticalAttribute> yükseltme yaptığınıza ayrıcalığı engellenir.  
  
 Güvenlik açısından kritik metodolojiyi organizasyonunu sağlar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ayrıcalık uygulamasına yükseltir kod *güvenlik açısından kritik çekirdek*, saydam olan geri kalanı ile. Güvenlik açısından kritik kodu yalıtma sağlayan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] mühendislik ekibi, güvenlik açısından kritik çekirdeği sunmayan standart güvenlik uygulamaları hakkında ek güvenlik analizi ve kaynak denetim odak (bkz [WPF güvenlik stratejisi -Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)).  
  
 .NET Framework ile işaretlenmiş yönetilen derlemeler yazmak geliştiricilere vererek XBAP Internet bölgesi korumalı alan genişletmek için güvenilen bir kod izin verdiğini unutmayın <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) ve kullanıcının Genel Derleme Önbelleği (GAC) dağıtılır. Internet'ten kötü amaçlı kod dahil olmak üzere bu bütünleştirilmiş kod çağırmak herhangi bir kod verdiğinden APTCA ile bir derlemeyi işaretlemek bir yüksek oranda gizli güvenlik işlemdir. Kullanıcılar bu yazılımı yüklenecek sırayla güven seçmeniz gerekir ve bunu yaparken son derece dikkatli olun ve en iyi kullanılmalıdır.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer güvenlik  
 Güvenlik sorunlarını azaltma ve güvenlik yapılandırması basitleştiriliyor ötesinde [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] güvenliğini kullanıcıları için bu güvenlik geliştirmeleri birçok özellik içeren [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Bu özelliklerin thrust gözatma deneyimlerini üzerinde kullanıcılara daha fazla denetime izin verecek şekilde çalışır.  
  
 Öncesinde [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], kullanıcılar aşağıdaki hiçbirini tabi olabilir:  
  
- Rastgele açılır pencereleri.  
  
- Kafa karıştırıcı betiği yeniden yönlendirme.  
  
- Bazı Web sitelerinde çok sayıda güvenlik iletişim kutuları.  
  
 Bazı durumlarda, kullanıcılar yükleme taklit ederek kandırmaya güvenilmeyen Web sitelerinden isteriz [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] veya kullanıcı bu iptal olsa da Microsoft ActiveX yükleme iletişim kutusunda, tekrar tekrar gösterme. Bu teknikler kullanarak, çok sayıda kullanıcı casus yazılım uygulamaların yüklenmesini ile sonuçlanan kötü kararların içine sağladı, mümkündür.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] Bu tür kullanıcı başlatma kavramı çalışmalarınızı sorunlarını gidermek için çeşitli özellikler içerir. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] bir kullanıcı olarak da bilinen bir eylem önce bir bağlantı veya sayfa öğesinin tıkladığında algılar *kullanıcı başlatma*ve benzer bir eylem bunun yerine bir sayfadaki komut tarafından tetiklendiğinde'den farklı davranır. Örneğin, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] kapsayan bir **açılır pencere Engelleyicisine** bir kullanıcı bir açılır pencere oluşturma sayfasında önce bir düğmeyi tıkladığında algılar. Böylece [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] kullanıcılar için sorun ne istediğiniz açılır pencereleri sağlarken en zararsız açılır pencerelere izin verecek şekilde. Engellenen Açılır pencereleri yakalanan yeni altında **bilgi çubuğu**, el ile blok geçersiz kılmak ve açılır görüntülemek kullanıcının izin verir.  
  
 Aynı kullanıcı başlatma mantığı da uygulanan **açık**/**Kaydet** Güvenlik sorusu. Yükseltme daha önce yüklenen bir denetimi temsil ettikleri sürece ActiveX yükleme iletişim kutusu, her zaman bilgi çubuğunun altında yakalanır. İstenmeyen veya kötü amaçlı yazılım yüklemek için bunları taciz sitelere karşı korunduktan sonra kullanıcılara güvenli, daha denetlenen kullanıcı deneyimi sağlamak için bu ölçümleri birleştirin.  
  
 Bu özellikleri kullanan müşteriler ayrıca koruma [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] yükleyip olanak tanıyan web sitelerine göz atmak için [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. Özellikle, bunun nedeni, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] kullanıcıların hangi teknoloji dahil olmak üzere derlemek için kullanılan bağımsız olarak kötü amaçlı veya devious uygulamaları yüklemek olasılığını düşürür daha iyi bir kullanıcı deneyimi sunar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kullanarak için bu korumalar ekler [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] Internet üzerinden kendi uygulamalarının indirilmesini kolaylaştırmak için. Bu yana [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] bir Internet bölgesi güvenlik korumalı alan içinde yürütün, sorunsuz bir şekilde başlatılabilir. Diğer yandan, tek başına [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları çalıştırmak için tam güven gerektirir. Bu uygulamalar için [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] uygulamanın ek güvenlik gereksinimleri kullanımını bildirmek için başlatma işlemi sırasında bir güvenlik iletişim kutusu görüntülenir. Ancak, bu kullanıcı tarafından başlatılmış olması gerekir, ayrıca kullanıcı tarafından başlatılan mantığı tarafından yönetilecektir ve iptal edilebilir.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] içerir ve güvenlik özelliklerini genişletir [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] çabası güvenlik bir parçası olarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod erişimi güvenliği](../misc/code-access-security.md)
- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
