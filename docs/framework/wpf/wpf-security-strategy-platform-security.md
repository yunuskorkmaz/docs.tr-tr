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
ms.openlocfilehash: 44f98a6d7bf8358baf3b123b2d3b1d13009098a6
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133757"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF Güvenlik Stratejisi - Platform Güvenliği
Windows Presentation Foundation (WPF), çeşitli güvenlik hizmetleri sağladığından, işletim sistemini, CLR 'yi ve Internet Explorer 'ı içeren temel platformun güvenlik özelliklerinden de yararlanır. Bu katmanlar, aşağıdaki şekilde [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] gösterildiği gibi, herhangi bir hata noktasını önlemeye yönelik güçlü, derinlemesine bir güvenlik modeli sağlamak için birleştirilir:  
  
 ![WPF güvenlik modelini gösteren diyagram.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Bu konunun geri kalanında, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] özellikle ilgili olan bu katmanların her birinde bulunan özellikler ele alınmaktadır.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>İşletim sistemi güvenliği  
Windows çekirdeği, WPF ile oluşturulmuş olanlar da dahil olmak üzere tüm Windows uygulamaları için güvenlik temelini oluşturan çeşitli güvenlik özellikleri sağlar. Bu konu, WPF için önemli olan bu güvenlik özelliklerinin kapsamını ele almaktadır ve WPF 'in bunlarla nasıl tümleştirilebildiğinden daha ayrıntılı savunma sağlar.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Genel İnceleme ve Windows 'un güçlendirilemesinin yanı sıra, bu konuda tartışacak üç temel özellik [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] vardır:  
  
- /GS derlemesi  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS derlemesi  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]arabellek taşmalarını azaltmaya yardımcı olmak için, CLR gibi tüm [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bağımlılıklarla birlikte birçok çekirdek sistem kitaplığını yeniden derleyerek koruma sağlar. Bu, C/C++ komut satırı derleyicisi ile/GS parametresi kullanılarak elde edilir. Arabellek taşmalarının açıkça kaçınılması gerekse de,/GS derlemesi, bu, yanlışlıkla veya kötü amaçlı olarak oluşturulan olası güvenlik açıklarına karşı derinlemesine savunma sağlayan bir örnek sağlar.  
  
 Geçmişte, arabellek aşımları birçok yüksek etki güvenliği güvenlik açığından oluşur. Bir saldırgan, bir arabelleğin sınırlarını aşan kötü amaçlı kod eklenmesine izin veren bir kod güvenlik açığından yararlanıyorsa bir arabellek taşması oluşur. Bu daha sonra, saldırganın kodunun yürütülmesine neden olmak için bir işlevin dönüş adresinin üzerine yazarak kodun yürütüldüğü işlemi bir saldırganın almasına izin verir. Sonuç, ele geçirilen işlemle aynı ayrıcalıklarla rastgele kod yürüten kötü amaçlı koddur.  
  
 Yüksek düzeyde,/GS derleyici bayrağı, yerel dize arabelleklerine sahip bir işlevin dönüş adresini korumak için özel bir güvenlik tanımlama bilgisinin ekleme tarafından bazı olası arabellek taşmalarına karşı koruma sağlar. Bir işlev döndüğünde, güvenlik tanımlama bilgisi önceki değeriyle karşılaştırılır. Değer değiştirildiyse, bir arabellek taşması oluşmuş olabilir ve işlem bir hata durumuyla durdurulur. İşlem durdurulduğunda kötü amaçlı olabilecek kodun yürütülmesi önlenir. Daha fazla bilgi için bkz. [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) .  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalara başka bir savunma katmanı eklemek için/GS bayrağıyla derlenir.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Microsoft Windows Update geliştirmeleri  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)], güncelleştirmeleri indirme ve [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] yükleme işlemini basitleştirmek için ' de geliştirilmiştir. Bu değişiklikler, özellikle güvenlik güncelleştirmeleriyle [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ilgili olarak, sistemlerinin güncel olduğundan emin olmaya yardımcı olarak müşteriler için güvenliği önemli ölçüde geliştirir.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
Windows Vista 'daki WPF kullanıcıları, "en az ayrıcalıklı kullanıcı erişimi", kod bütünlüğü denetimleri ve ayrıcalık yalıtımı gibi işletim sisteminin ek güvenlik geliştirmelerinden faydalanır.  
  
#### <a name="user-account-control-uac"></a>Kullanıcı hesabı denetimi (UAC)  
 Günümüzde, çoğu uygulama için yükleme veya yürütme ya da her ikisi için gerekli olduğundan, Windows kullanıcıları yönetici ayrıcalıklarıyla çalışmaya eğilimlidir. Varsayılan uygulama ayarlarını kayıt defterine yazamayacak bir örnektir.  
  
 Yönetici ayrıcalıklarıyla çalıştırmak, uygulamaların yönetici ayrıcalıkları verilen işlemlerden yürütülmesi anlamına gelir. Bunun güvenlik etkisi, yönetici ayrıcalıklarıyla çalışan bir işlemi ele alan herhangi bir kötü amaçlı kodun, kritik sistem kaynaklarına erişim de dahil olmak üzere otomatik olarak bu ayrıcalıkları devralmasını sağlar.  
  
 Bu güvenlik tehditlerine karşı korumanın bir yolu, uygulamaları gereken en az sayıda ayrıcalığa sahip olacak şekilde kullanmaktır. Bu, en az ayrıcalık ilkesi olarak bilinir ve Windows işletim sisteminin temel bir özelliğidir. Bu özellik, Kullanıcı hesabı denetimi (UAC) olarak adlandırılır ve Windows UAC tarafından iki önemli şekilde kullanılır:  
  
- Kullanıcı yönetici olsa bile, çoğu uygulamayı UAC ayrıcalıklarıyla çalıştırmak için; yalnızca yönetici ayrıcalıklarına ihtiyacı olan uygulamalar, yönetici ayrıcalıklarıyla çalışır. Yönetim ayrıcalıklarıyla çalıştırmak için uygulamaların uygulama bildiriminde açıkça veya güvenlik ilkesinde bir giriş olarak işaretlenmesi gerekir.  
  
- Sanallaştırma gibi uyumluluk çözümleri sağlamak için. Örneğin, birçok uygulama C:\Program Files gibi kısıtlı konumlara yazmaya çalışır. UAC altında yürütülen uygulamalar için, yazma için yönetici ayrıcalıkları gerektirmeyen Kullanıcı başına alternatif bir konum vardır. UAC altında çalışan uygulamalar için, UAC 'ler C:\Program Files 'ı sanallaştırır. bu sayede, kendisine yazdıkları uygulamalar aslında alternatif, Kullanıcı başına konuma yazıyor. Bu tür bir uyumluluk çalışması, işletim sisteminin daha önce UAC 'de çalışmayan birçok uygulamayı çalıştırmasına olanak sağlar.  
  
#### <a name="code-integrity-checks"></a>Kod bütünlüğü denetimleri  
 Windows Vista, kötü amaçlı kodun sistem dosyalarına veya yükleme/çalışma zamanında çekirdeğe eklenmesini önlemeye yardımcı olmak için daha derin kod bütünlüğü denetimleri içerir. Bu, sistem dosya korumasının ötesine geçer.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Tarayıcıda barındırılan uygulamalar için sınırlı haklar süreci  
 Tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar Internet bölgesi korumalı alanı içinde yürütülür. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]Microsoft Internet Explorer ile tümleştirme, bu korumayı ek destek ile genişletir.  
  
 Internet [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] bölgesi izin kümesi tarafından genellikle korumalı olduğundan, bu ayrıcalıkların kaldırılması uyumluluk perspektifinden zarar [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] vermez. Bunun yerine, ek bir derinlemesine savunma katmanı oluşturulur; korumalı bir uygulama diğer katmanlardan yararlanabilebiliyor ve süreci hijak, işlem hala yalnızca sınırlı ayrıcalıklara sahip olur.  
  
 Bkz. [en az ayrıcalıklı kullanıcı hesabı kullanma](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Ortak dil çalışma zamanı güvenliği  
 Ortak dil çalışma zamanı (CLR), doğrulama ve doğrulama, kod erişim güvenliği (CAS) ve güvenlik açısından kritik metodolojisini içeren bir dizi anahtar güvenlik avantajı sunar.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Doğrulama ve doğrulama  
 Bütünleştirilmiş kod yalıtımı ve bütünlüğü sağlamak için, CLR doğrulama işlemini kullanır. CLR doğrulaması, derlemenin dışına işaret eden adresler için taşınabilir yürütülebilir (PE) dosya biçimi doğrulayarak derlemelerin yalıtılmasını sağlar. CLR doğrulaması ayrıca bir derleme içine katıştırılmış meta verilerin bütünlüğünü doğrular.  
  
 Tür güvenliğini sağlamak için, yaygın güvenlik sorunlarını önlemeye yardımcı olun (örneğin, arabellek taşmaları) ve alt süreç yalıtımı aracılığıyla korumalı alana alma etkinleştirin, CLR güvenliği doğrulama kavramını kullanır.  
  
 Yönetilen uygulamalar Microsoft ara dil (MSIL) ile derlenir. Yönetilen bir uygulamadaki Yöntemler yürütüldüğünde, MSIL, tam zamanında (JıT) derleme aracılığıyla yerel koda derlenir. JıT derlemesi, kodun olmamasını sağlayan birçok güvenlik ve sağlamlık kuralı uygulayan bir doğrulama işlemi içerir:  
  
- Tür sözleşmelerini ihlal etme  
  
- Arabellek taşmalarını tanıtma  
  
- Bellek erişimi.  
  
 Güvenilen kod kabul edilmediği takdirde, doğrulama kurallarına uymayan yönetilen kodun yürütülmesine izin verilmez.  
  
 Doğrulanabilir kod avantajı, .NET Framework derlemelerin neden [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] olduğunu önemli bir nedendir. Doğrulanabilir kodun kullanıldığı ölçüde, olası güvenlik açıklarını kötüye bir şekilde düşürme olasılığı büyük ölçüde azalır.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 Bir istemci makinesi, yönetilen bir uygulamanın, dosya sistemi, kayıt defteri, yazdırma hizmetleri, Kullanıcı arabirimi, yansıma ve ortam değişkenleri dahil olmak üzere erişebileceği çok çeşitli kaynaklar sunar. Yönetilen bir uygulama, bir istemci makinedeki herhangi bir kaynağa erişebilmeye başlamadan önce, .NET Framework iznine sahip olmalıdır. CAS 'deki bir izin, <xref:System.Security.CodeAccessPermission>öğesinin bir alt sınıfıdır; CAS, yönetilen uygulamaların erişebileceği her kaynak için bir alt sınıf uygular.  
  
 Yönetilen bir uygulamanın,, yürütülmeye başladığı zaman CA 'LAR tarafından verilen izinler kümesi, izin kümesi olarak bilinir ve uygulama tarafından sağlanan kanıt tarafından belirlenir. Uygulamalar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] için, belirtilen kanıt, uygulamaların başlatıldığı konum veya bölgedir. CAS aşağıdaki bölgeleri tanımlar:  
  
- **Bilgisayarım**. İstemci makineden başlatılan uygulamalar (tamamen güvenilir).  
  
- **Yerel Intranet**. İntranetten başlatılan uygulamalar. (Biraz güvenilir).  
  
- **Internet**. Internet 'ten başlatılan uygulamalar. (En az güvenilir).  
  
- **Güvenilen siteler**. Bir kullanıcı tarafından güvenilen olarak tanımlanan uygulamalar. (En az güvenilir).  
  
- **Güvenilmeyen siteler**. Bir kullanıcı tarafından güvenilmeyen olarak tanımlanan uygulamalar. (Güvenilmeyen).  
  
 Bu bölgelerin her biri için CA 'LAR, her biriyle ilişkili güven düzeyiyle eşleşen izinleri içeren önceden tanımlanmış bir izin kümesi sağlar. Bu güncelleştirmeler şunlardır:  
  
- **FullTrust**. **Bilgisayarım** bölgesinden başlatılan uygulamalar için. Olası tüm izinler verilir.  
  
- **LocalIntranet**. **Yerel Intranet** bölgesinden başlatılan uygulamalar için. Yalıtılmış depolama, sınırsız Kullanıcı Arabirimi erişimi, kısıtlanmamış dosya iletişimleri, sınırlı yansıma, ortam değişkenlerine sınırlı erişim dahil olmak üzere bir istemci makinenin kaynaklarına orta erişim sağlamak için izin alt kümesi verilir. Kayıt defteri gibi kritik kaynakların izinleri sağlanmaz.  
  
- **Internet**. **Internet** veya **Güvenilen siteler** bölgesinden başlatılan uygulamalar için. Yalıtılmış depolama, yalnızca dosya açma ve sınırlı kullanıcı arabirimi dahil olmak üzere bir istemci makinenin kaynaklarına sınırlı erişim sağlamak için bir izin alt kümesi verilmiştir. Temelde, bu izin kümesi, uygulamaları istemci makineden ayırır.  
  
 **Güvenilmeyen siteler** bölgesinde olduğu şekilde tanımlanan uygulamalara, CA 'lar tarafından hiçbir izin verilmez. Sonuç olarak, önceden tanımlanmış bir izin kümesi onlar için mevcut değildir.  
  
 Aşağıdaki şekilde bölgeler, izin kümeleri, izinler ve kaynaklar arasındaki ilişki gösterilmektedir:  
  
 ![CAS izin kümelerini gösteren diyagram.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Internet bölgesi güvenlik sanal alanının kısıtlamaları, bir XBAP 'nin bir sistem kitaplığından içeri aktardığı tüm koda eşit olarak uygulanır (dahil [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]). Bu, kodun her bitini de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]kilitli olarak sağlar. Ne yazık ki, yürütebilmek için, bir XBAP 'nin Internet bölgesi güvenlik korumalı alanı tarafından etkinleştirilenden daha fazla izin gerektiren işlevselliği yürütmesi gerekir.  
  
 Aşağıdaki sayfayı içeren bir XBAP uygulaması düşünün:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Bu XBAP 'yi yürütmek için, temel [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] alınan kodun çağıran XBAP tarafından kullanılabilir olandan daha fazla işlevsellik yürütmesi gerekir, örneğin:  
  
- İşleme için pencere tutamacı (HWND) oluşturma  
  
- İletileri dağıtma  
  
- Tahoma yazı tipi yükleniyor  
  
 Bir güvenlik noktasından, korumalı uygulamadan bu işlemlerden herhangi birine doğrudan erişim verilmesi çok zararlı olabilir.  
  
 Neyse ki [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , bu işlemlerin korumalı bir uygulama adına yükseltilmiş ayrıcalıklarla yürütülmesine izin vererek bu duruma karşı koruma sağlar. Tüm [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] işlemler, XBAP 'nin uygulama etki alanının sınırlı Internet bölgesi güvenlik izinlerine (diğer sistem kitaplıklarında olduğu gibi) [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] karşı denetlenirken, olası tüm izinleri içeren bir izin kümesi verilir.
  
 Bunun yapılması, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Bu ayrıcalıkların konak uygulama etki alanının Internet bölgesi izin kümesi tarafından yönetilmesini engelleyen yükseltilmiş ayrıcalıklar almasını gerektirir.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]Bunu, bir iznin **onaylama** yöntemini kullanarak yapar. Aşağıdaki kod bunun nasıl gerçekleştiğini gösterir.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Bu onay aslında, XBAP 'nin Internet bölgesi izinleriyle [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sınırlandırılmalarını gerektiren sınırsız izinleri önler.  
  
 Bir platform perspektifinden doğru onay [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kullanmaktan sorumludur; bir **onaylama** yanlış kullanımı, kötü amaçlı kodun ayrıcalıkların yükseltilmesini sağlar. Sonuç olarak, yalnızca gerektiğinde onay çağrısı yapmak ve korumalı alan kısıtlamalarının bozulmadan kalmasını sağlamak önemlidir. Örneğin, korumalı kodun rastgele dosyaları açmasına izin verilmez, ancak yazı tiplerini kullanmasına izin verilir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]korumalı uygulamaların, **onayı**çağırarak yazı tipi işlevselliğini kullanmasına ve [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] bu yazı tiplerini korumalı uygulama adına içerdiği bilinen dosyaları okumasına olanak sağlar.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 ClickOnce, .NET Framework ile birlikte sunulan kapsamlı bir dağıtım teknolojisidir ve ile [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] tümleştirilir (ayrıntılı bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment) ). Tek [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] başına uygulamalar ClickOnce kullanılarak dağıtılabilir, ancak tarayıcıda barındırılan uygulamalar ClickOnce ile dağıtılmalıdır.  
  
 ClickOnce kullanılarak dağıtılan uygulamalara, kod erişim güvenliği (CAS) üzerinden ek bir güvenlik katmanı verilir; Temelde, ClickOnce tarafından dağıtılan uygulamalar gereksinim duydukları izinleri ister. Yalnızca uygulamanın dağıtıldığı bölge için izin kümesini aşmazsa, bu izinlere izin verilir. İzin kümesini, başlatma bölgesinin izin kümesi tarafından sağlananlardan daha az olsalar bile yalnızca gerekli olanlarla azaltarak, uygulamanın erişimi olan kaynak sayısı en az bir değer olacak şekilde azaltılır. Sonuç olarak, uygulama ele geçirilmiş ise, istemci makinesine zarar verme olasılığı azalır.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Güvenlik açısından kritik metodolojisi  
 XBAP [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamaları için Internet bölgesi korumalı alanını etkinleştirmek üzere izinleri kullanan kod, mümkün olan en yüksek güvenlik denetim ve denetim derecesine sahip olmalıdır. Bu gereksinimi kolaylaştırmak için .NET Framework, ayrıcalıkları destekleyen kodu yönetmek için yeni destek sağlar. CLR, ayrıcalıkları destekleyen kodu tanımlamanızı ve ile <xref:System.Security.SecurityCriticalAttribute>işaretlemenizi sağlar; <xref:System.Security.SecurityCriticalAttribute> işaretli olmayan herhangi bir kod bu metodolojisi kullanılarak *saydam* hale gelir. Buna karşılık, ile <xref:System.Security.SecurityCriticalAttribute> işaretlenmemiş yönetilen kodun ayrıcalık yükseltme işlemi engellenir.  
  
 Güvenlik açısından kritik metodolojisi, ayrıcalıkları bir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] *güvenlik açısından kritik çekirdeğe*yükseltir ve kalanı saydam olacak şekilde sağlar. Güvenlik açısından kritik kodu yalıtmak, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] mühendislik ekibinin, yukarıdaki güvenlik açısından kritik çekirdekte ve standart güvenlik uygulamalarının ötesinde ek bir güvenlik Analizi ve kaynak denetimi odağa izin vermez (bkz. [WPF güvenlik stratejisi-güvenlik Mühendislik](wpf-security-strategy-security-engineering.md)).  
  
 .NET Framework, geliştiricilerin (aptca) ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> işaretlenmiş ve kullanıcının genel derleme önbelleği 'ne (GAC) dağıtılan yönetilen derlemeler yazmasına izin vererek, güvenilen kodun XBAP Internet bölgesi sanal alanını genişletmesine izin verdiğini unutmayın. Derlemeyi APTCA ile işaretlemek, Internet 'ten gelen kötü amaçlı kod dahil olmak üzere herhangi bir kodun bu derlemeyi çağırmasını olanaklı olduğundan, yüksek oranda duyarlı bir güvenlik işlemidir. Bu işlem sırasında çok dikkatli ve en iyi uygulamalar kullanılmalıdır ve kullanıcıların yüklenebilmesi için bu yazılıma güvenmeyi seçmesi gerekir.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer güvenliği  
 Güvenlik sorunlarını azaltmaya ve güvenlik yapılandırmasını basitleştirmeye karşı, Microsoft Internet Explorer 6 (SP2), kullanıcılarının [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]güvenliğini artıran güvenlik geliştirmelerinden oluşan çeşitli özellikler içerir. Bu özelliklerin bu özellikleri, kullanıcıların gözatma deneyimi üzerinde daha fazla denetime izin vermeyi dener.  
  
 IE6 SP2 'den önce, kullanıcılar aşağıdakilerden birine tabi olabilir:  
  
- Rastgele açılan pencereler.  
  
- Kafa karıştırıcı betiği yeniden yönlendirme.  
  
- Bazı web sitelerinde çok sayıda güvenlik iletişim kutusu.  
  
 Bazı durumlarda, güvenilir olmayan Web siteleri, Kullanıcı bunu iptal etmiş olsa bile yüklemeyi [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] yanıltma veya bir Microsoft ActiveX yükleme iletişim kutusunu yeniden göstererek kullanıcıları aldatmaya çalışır. Bu teknikleri kullanarak, casus yazılım uygulamalarının yüklenmesiyle sonuçlanan kötü kararlar almaya çok sayıda kullanıcı daha karmaşık bir şekilde ele alınmış olabilir.  
  
 IE6 SP2, bu tür sorunları hafifletmek için Kullanıcı başlatma kavramını kapsayan çeşitli özellikler içerir. IE6 SP2, bir Kullanıcı *başlatma*olarak bilinen bir eylemden önce bir bağlantı veya sayfa öğesine tıkladığını algılar ve bir sayfada betik tarafından bunun yerine benzer bir eylem olduğu gibi davranır. Örnek olarak, ıE6 SP2 bir kullanıcının açılır pencere oluşturmadan önce bir düğmeye tıkladığını algılayan bir **açılır pencere engelleyicisi** içerir. Bu, ıE6 SP2'NIN çoğu zararsız açılır pencerelere izin vermesini sağlar, ancak kullanıcıların veya istediği açılan pencereleri önler. Engellenen açılır pencereler, kullanıcının engellemeyi el ile geçersiz kılmasını ve açılır pencereyi görüntülemesini sağlayan yeni **bilgi çubuğu**altında yakalanmalıdır.  
  
 Aynı Kullanıcı başlatma mantığı Ayrıca, güvenlik**kaydetme** komut istemlerini **Aç**/' a uygulanır. Daha önce yüklenmiş bir denetimden bir yükseltmeyi temsil etmediği takdirde, ActiveX yükleme iletişim kutuları her zaman bilgi çubuğu altına kaydedilir. Bu ölçümler kullanıcılara daha güvenli, daha denetimli bir kullanıcı deneyimi sağlamak için birleşerek, istenmeyen veya kötü amaçlı yazılım yüklemeleri için bunları tacler eden sitelere karşı koruma sağlar.  
  
 Bu özellikler, IE6 SP2 kullanan müşterileri, uygulamaların indirilmesine ve yüklenmesine [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] izin veren Web sitelerine gözatmaya da karşı korur. Bunun nedeni, bu, ıE6 SP2'NIN, bu sürümü oluşturmak [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]için kullanılan teknolojiden bağımsız olarak kötü amaçlı veya bağımsız uygulamalar yükleyebilme olasılığını azaltan daha iyi bir kullanıcı deneyimi sunmasıdır. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], uygulamalarını Internet üzerinden indirmeyi kolaylaştırmak için ClickOnce kullanarak bu korumaların sonuna ekler. Internet bölgesi güvenlik korumalı alanı içinde yürütülebildiğinden,sorunsuzbirşekildebaşlatılabilir.[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] Öte yandan, tek başına [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uygulamalar yürütmek için tam güven gerektirir. Bu uygulamalar için, ClickOnce, uygulamanın ek güvenlik gereksinimlerinin kullanımını bildirmek üzere başlatma işlemi sırasında bir güvenlik iletişim kutusu görüntüler. Ancak, bu kullanıcı tarafından başlatılmış olması gerekir ve Kullanıcı tarafından başlatılan mantığa göre yönetilir ve iptal edilebilir.  
  
 Internet Explorer 7, güvenlik çabalarının bir parçası olarak ıE6 SP2'NIN güvenlik yeteneklerini içerir ve genişletir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod erişim güvenliği](../misc/code-access-security.md)
- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
