---
title: Platform güvenlik stratejisi
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
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174608"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF Güvenlik Stratejisi - Platform Güvenliği
Windows Sunu Temeli (WPF) çeşitli güvenlik hizmetleri sağlarken, işletim sistemi, CLR ve Internet Explorer'ı içeren temel platformun güvenlik özelliklerinden de yararlanır. Bu katmanlar, WPF'ye aşağıdaki şekilde gösterildiği gibi, tek bir hata noktasından kaçınmaya çalışan güçlü, derinlemesine bir güvenlik modeli sağlamak için biraraya gelir:  
  
 ![WPF güvenlik modelini gösteren diyagram.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Bu konunun geri kalanı, özellikle WPF ile ilgili bu katmanların her birinde özellikleri tartışır.  

## <a name="operating-system-security"></a>İşletim Sistemi Güvenliği  
Windows'un çekirdeği, WPF ile oluşturulmuş olanlar da dahil olmak üzere tüm Windows uygulamaları için güvenlik temelini oluşturan çeşitli güvenlik özellikleri sağlar. Bu konu, WPF için önemli olan bu güvenlik özelliklerinin genişliğini ve WPF'nin derinlemesine daha fazla savunma sağlamak için onlarla nasıl entegre olduğunu tartışır.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Windows'un genel bir incelemesi ve güçlendirilmesine ek olarak, Windows XP SP2'nin bu konuda tartışacağız üç temel özelliği vardır:  
  
- /GS derlemesi  
  
- Microsoft Windows Update.  
  
#### <a name="gs-compilation"></a>/GS Derleme  
 Windows XP SP2, arabellek taşmaları azaltmaya yardımcı olmak için CLR gibi Tüm WPF bağımlılıkları da dahil olmak üzere birçok temel sistem kitaplıklarını yeniden derleyerek koruma sağlar. Bu, C/C++ komut satırı derleyicisi ile /GS parametresi kullanılarak elde edilir. Arabellek taşmaları açıkça kaçınılmalıdır rağmen, / GS derleme yanlışlıkla veya kötü niyetli onlar tarafından oluşturulan olası güvenlik açıklarına karşı derinlemesine bir savunma örneği sağlar.  
  
 Tarihsel olarak, arabellek taşmaları birçok yüksek etkili güvenlik açıkları neden olmuştur. Arabellek taşma, bir saldırgan arabellek sınırlarını geçmiş yazıyor kötü amaçlı kod enjeksiyonu sağlayan bir kod güvenlik açığı yararlanmak oluşur. Bu, saldırganın bir işlevin iade adresini üzerine yazarak kodun yürütüldettiği işlemi ele geçirerek saldırganın kodunun yürütülmesine neden olmasını sağlar. Sonuç, kaçırılan işlemle aynı ayrıcalıklara sahip rasgele kod yürüten kötü amaçlı koddur.  
  
 Yüksek düzeyde, -GS derleyici bayrağı, yerel dize arabelleklerine sahip bir işlevin dönüş adresini korumak için özel bir güvenlik çerezi enjekte ederek bazı olası arabellek taşmaları karşı korur. Bir işlev döndükten sonra, güvenlik çerezi önceki değeriyle karşılaştırılır. Değer değiştiyse, arabellek taşma oluştu ve işlem bir hata koşuluyla durdurulur. İşlemin durdurulması, kötü amaçlı olabilecek kodun yürütülmesini engeller. Daha fazla bilgi için [bkz: -GS (Arabellek Güvenlik Kontrolü).](/cpp/build/reference/gs-buffer-security-check)  
  
 WPF, WPF uygulamalarına başka bir savunma katmanı eklemek için /GS bayrağı yla derlenmiştir.  
  
### <a name="windows-vista"></a>Windows Vista  
Windows Vista'daki WPF kullanıcıları, işletim sisteminin "En Az Ayrıcalıklı Kullanıcı Erişimi", kod bütünlüğü denetimleri ve ayrıcalık yalıtımı gibi ek güvenlik geliştirmelerinden yararlanır.  
  
#### <a name="user-account-control-uac"></a>Kullanıcı Hesabı Denetimi (UAC)  
 Günümüzde, birçok uygulama yükleme veya yürütme veya her ikisi için bunları gerektirdiğinden, Windows kullanıcıları yönetici ayrıcalıklarıyla çalışma eğilimindedir. Kayıt Defteri'ne varsayılan uygulama ayarlarını yazabilmek bir örnektir.  
  
 Yönetici ayrıcalıklarıyla çalışan, uygulamaların yönetici ayrıcalıkları verilen işlemlerden yürütülmesi anlamına gelir. Bunun güvenlik etkisi, yönetici ayrıcalıklarıyla çalışan bir işlemi ele kaçıran herhangi bir kötü amaçlı kodun, kritik sistem kaynaklarına erişim de dahil olmak üzere bu ayrıcalıkları otomatik olarak devralmasıdır.  
  
 Bu güvenlik tehdidine karşı korumanın bir yolu, gerekli olan en az ayrıcalıkla uygulamaları çalıştırmaktır. Bu, en az ayrıcalık ilkesi olarak bilinir ve Windows işletim sisteminin temel bir özelliğidir. Bu özellik Kullanıcı Hesabı Denetimi (UAC) olarak adlandırılır ve Windows UAC tarafından iki anahtar şekilde kullanılır:  
  
- Kullanıcı yönetici olsa bile, varsayılan olarak UAC ayrıcalıklarına sahip çoğu uygulamayı çalıştırmak için; yalnızca yönetici ayrıcalıkları gerektiren uygulamalar yönetici ayrıcalıklarıyla birlikte çalışır. İdari ayrıcalıklarla çalışmak için, uygulamaların uygulama bildiriminde veya güvenlik ilkesine giriş olarak açıkça işaretlemesi gerekir.  
  
- Sanallaştırma gibi uyumluluk çözümleri sunmak. Örneğin, birçok uygulama C:\Program Dosyaları gibi kısıtlı konumlara yazmaya çalışır. UAC altında çalıştırılabilen uygulamalar için, kullanıcı başına yönetici ayrıcalıkları gerektirmeyen bir alternatif konum vardır. UAC altında çalışan uygulamalar için, UAC C:\Program Dosyalarını sanallaştırır, böylece ona yazdıklarını düşünen uygulamalar aslında alternatif kullanıcı başına konuma yazıyorlar. Bu tür uyumluluk çalışmaları, işletim sisteminin daha önce UAC'de çalıştırılamamış birçok uygulamayı çalıştırmasını sağlar.  
  
#### <a name="code-integrity-checks"></a>Kod Bütünlüğü Denetimleri  
 Windows Vista, kötü amaçlı kodun sistem dosyalarına veya yük/çalışma zamanında çekirdek içine enjekte edilebünden korunmaya yardımcı olmak için daha derin kod bütünlüğü denetimleri içerir. Bu sistem dosya koruması ötesine geçer.  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>Tarayıcı Barındırılan Uygulamalar için Sınırlı Haklar Süreci  
 Tarayıcı tarafından barındırılan WPF uygulamaları Internet bölgesi sandbox içinde yürütülür. Microsoft Internet Explorer ile WPF tümleştirmesi bu korumayı ek destekle genişletir.  
  
 XAML tarayıcı uygulamaları (XBAP'ler) genellikle Internet bölgesi izin kümesi tarafından sandboxed olduğundan, bu ayrıcalıkların kaldırılması XAML tarayıcı uygulamalarına (XBAP' ler) uyumluluk açısından zarar vermez. Bunun yerine, ek bir savunma-in-derinlemesine katman oluşturulur; Kumlanmış bir uygulama diğer katmanları sömürebilir ve işlemi ele geçirebiliyorsa, işlem yine de yalnızca sınırlı ayrıcalıklara sahip olur.  
  
 Bkz. [En Az Ayrıcalıklı Kullanıcı Hesabı Kullanma](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Ortak Dil Çalışma Süresi Güvenliği  
 Ortak dil çalışma süresi (CLR), doğrulama ve doğrulama, Kod Erişim Güvenliği (CAS) ve Güvenlik Açısından Kritik Metodoloji gibi bir dizi önemli güvenlik avantajı sunar.  

### <a name="validation-and-verification"></a>Doğrulama ve Doğrulama  
 Derleme yalıtımı ve bütünlüğü sağlamak için CLR bir doğrulama işlemi kullanır. CLR doğrulama, derlemenin dışındaki adresler için Taşınabilir Çalıştırılabilir (PE) dosya biçimini doğrulayarak derlemelerin yalıtılmış olmasını sağlar. CLR doğrulaması, derlemenin içine katıştırılmış meta verilerin bütünlüğünü de doğrular.  
  
 Tür güvenliğini sağlamak, sık karşılaşılan güvenlik sorunlarını önlemeye yardımcı olmak (örn. arabellek taşmaları) ve alt proses yalıtımı yoluyla kum kutulamasını etkinleştirmek için CLR security doğrulama kavramını kullanır.  
  
 Yönetilen uygulamalar Microsoft Ara Dili (MSIL) olarak derlenir. Yönetilen bir uygulamadaki yöntemler yürütüldüğünde, MSIL'i Just-In-Time (JIT) derlemesi aracılığıyla yerel kod olarak derlenir. JIT derlemesi, kodun aşağıdakileri yapmamasını sağlayan birçok güvenlik ve sağlamlık kuralını uygulayan bir doğrulama işlemi içerir:  
  
- Tür sözleşmelerini ihlal  
  
- Arabellek taşmaları tanıtın  
  
- Belleğe çılgınca erişin.  
  
 Denetim kurallarına uymayan yönetilen kodun, güvenilir kod olarak kabul edilmedikçe yürütülmesine izin verilmez.  
  
 Doğrulanabilir kodun avantajı, WPF'nin .NET Framework üzerinde oluşturmasının önemli bir nedenidir. Doğrulanabilir kod kullanıldığı ölçüde, olası güvenlik açıklarından yararlanma olasılığı büyük ölçüde azaltılır.  
  
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 İstemci makinesi, dosya sistemi, Kayıt Defteri, yazdırma hizmetleri, kullanıcı arabirimi, yansıma ve ortam değişkenleri de dahil olmak üzere yönetilen bir uygulamanın erişebileceği çok çeşitli kaynakları ortaya çıkarır. Yönetilen bir uygulamaistemci makinesindeki kaynaklardan herhangi biri sine erişebilmek için bunu yapmak için .NET Framework iznine sahip olması gerekir. CAS'ta bir izin bir <xref:System.Security.CodeAccessPermission>alt sınıftır; CAS, yönetilen uygulamaların erişebileceği her kaynak için bir alt sınıf uygular.  
  
 Yönetilen bir uygulamanın yürütmeye başladığında CAS tarafından verildiği izinler kümesi, izin kümesi olarak bilinir ve uygulama tarafından sağlanan kanıtlarla belirlenir. WPF uygulamaları için sağlanan kanıt, uygulamaların başlatıldığı konum veya bölgedir. CAS aşağıdaki bölgeleri tanımlar:  
  
- **Benim Bilgisayar**. İstemci makinesinden başlatılan uygulamalar (Tam Güvenilir).  
  
- **Yerel Intranet**. Uygulamalar intranetten başlatılır. (Biraz Güvenilir).  
  
- **İnternet**. Uygulamalar Internet'ten başlatıldı. (En Az Güvenilir).  
  
- **Güvenilir Siteler**. Kullanıcı tarafından güvenilir olarak tanımlanan uygulamalar. (En Az Güvenilir).  
  
- **Güvenilmeyen Siteler**. Kullanıcı tarafından güvenilmeyen olarak tanımlanan uygulamalar. (Güvenilmez).  
  
 Bu bölgelerin her biri için CAS, her biriyle ilişkili güven düzeyiyle eşleşen izinleri içeren önceden tanımlanmış bir izin kümesi sağlar. Bunlar:  
  
- **FullTrust**. **Bilgisayarım** bölgesinden başlatılan uygulamalar için. Tüm olası izinler verilir.  
  
- **LocalIntranet**. **Yerel Intranet** bölgesinden başlatılan uygulamalar için. İzole depolama, sınırsız Kullanıcı Bira erişimi, sınırsız dosya iletişim bilgileri, sınırlı yansıma, ortam değişkenlerine sınırlı erişim gibi istemci makinesinin kaynaklarına orta düzeyde erişim sağlamak için izinlerin bir alt kümesi verilir. Kayıt Defteri gibi kritik kaynaklar için izinler sağlanmaz.  
  
- **İnternet**. **Internet** veya **Trusted Sites** bölgesinden başlatılan uygulamalar için. İzlenme, yalnızca dosya açık ve sınırlı kullanıcı arama bilgileri de dahil olmak üzere istemci makinenin kaynaklarına sınırlı erişim sağlamak için izinlerin bir alt kümesi verilir. Esasen, bu izin kümesi uygulamaları istemci makineden yalıtır.  
  
 **Güvenilmeyen Siteler** bölgesinden olduğu belirlenen başvurulara CAS tarafından hiçbir izin verilmez. Sonuç olarak, onlar için önceden tanımlanmış bir izin kümesi yok.  
  
 Aşağıdaki şekilde bölgeler, izin kümeleri, izinler ve kaynaklar arasındaki ilişki gösteriş verecektir:  
  
 ![CAS izin kümelerini gösteren diyagram.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Internet bölgesi güvenlik alanı kısıtlamaları, XBAP'ın WPF de dahil olmak üzere bir sistem kitaplığından aldığı tüm kodlar için eşit olarak uygulanır. Bu, kodun her bitinin WPF tarafından bile kilitaltında olmasını sağlar. Ne yazık ki, yürütebilmek için, bir XBAP'Nin Internet bölgesi güvenlik alanı tarafından etkinleştirilenlerden daha fazla izin gerektiren işlevleri yürütmesi gerekir.  
  
 Aşağıdaki sayfayı içeren bir XBAP uygulamasını düşünün:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Bu XBAP'ı yürütmek için, temel WPF kodu, aşağıdakiler de dahil olmak üzere, aşağıdakiler de dahil olmak üzere, xbap çağıran için kullanılabilir olandan daha fazla işlevsellik yürütmelidir:  
  
- Oluşturma için bir pencere tutamacı (HWND) oluşturma  
  
- İletileri gönderme  
  
- Tahoma yazı tipini yükleme  
  
 Güvenlik açısından bakıldığında, bu işlemlerden herhangi biri için kum havuzu uygulamasından doğrudan erişime izin vermek felaket olur.  
  
 Neyse ki, WPF bu işlemleri kumhavuzu uygulaması adına yüksek ayrıcalıklarla yürütülmesine izin vererek bu duruma hitap eder. Tüm WPF işlemleri XBAP uygulama etki alanının sınırlı Internet bölgesi güvenlik izinleri karşı kontrol edilirken, WPF (diğer sistem kitaplıklarında olduğu gibi) tüm olası izinleri içeren bir izin kümesi verilir.
  
 Bu, WPF'nin yüksek ayrıcalıklar almasını ve bu ayrıcalıkların ana bilgisayar uygulama etki alanının Internet bölgesi izin kümesi tarafından yönetilmesini engellemesini gerektirir.  
  
 WPF bunu, bir izin **alma** yöntemini kullanarak yapar. Aşağıdaki kod bunun nasıl olduğunu gösterir.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert,** WPF tarafından gerekli olan sınırsız izinlerin XBAP'ın Internet bölgesi izinleri tarafından kısıtlanmasını engeller.  
  
 Platform açısından Bakıldığında, WPF **Assert'ı** doğru kullanmaktan sorumludur; **Assert'in** yanlış kullanımı, kötü amaçlı kodun ayrıcalıkları yükseltmesine olanak sağlayabilir. Sonuç olarak, yalnızca gerektiğinde **Assert'ı** aramak ve kum havuzu kısıtlamalarının bozulmadan kalmasını sağlamak önemlidir. Örneğin, sandboxed kodu rasgele dosyaları açmak için izin verilmez, ancak yazı tipleri kullanmak için izin verilir. WPF, kumlanmış uygulamaların **Assert'ı**arayarak yazı tipi işlevselliğini kullanmasını ve WPF'nin bu yazı tiplerini kumlanmış uygulama adına içerdiği bilinen dosyaları okumasını sağlar.  
  
### <a name="clickonce-deployment"></a>ClickOnce Dağıtım  
 ClickOnce, .NET Framework ile birlikte verilen ve Visual Studio ile entegre olan kapsamlı bir dağıtım teknolojisidir (ayrıntılı bilgi için [ClickOnce güvenlik ve dağıtıma](/visualstudio/deployment/clickonce-security-and-deployment) bakın). Bağımsız WPF uygulamaları ClickOnce kullanılarak dağıtılabilirken, tarayıcı tarafından barındırılan uygulamaların ClickOnce ile dağıtılması gerekir.  
  
 ClickOnce kullanılarak dağıtılan uygulamalara Code Access Security (CAS) üzerinden ek bir güvenlik katmanı verilir; esasen, ClickOnce dağıtılan uygulamalar gereksinim duydukları izinleri isteyin. Yalnızca uygulamanın dağıtıldığı bölge için izin kümesini aşmadıkları takdirde bu izinler verilir. İzin kümesini yalnızca gerekli olanlara indirgeyerek, başlatma bölgesinin izin kümesi tarafından sağlananlardan daha az olsalar bile, uygulamanın erişediği kaynak sayısı en aza indirgenir. Sonuç olarak, uygulama kaçırılırsa, istemci makineye zarar verme potansiyeli azalır.  
  
### <a name="security-critical-methodology"></a>Güvenlik Açısından Kritik Metodoloji  
 XBAP uygulamaları için Internet bölgesi kum havuzunu etkinleştirmek için izinleri kullanan WPF kodu, mümkün olan en yüksek düzeyde güvenlik denetimi ve denetimine sahip olmalıdır. Bu gereksinimi kolaylaştırmak için ,NET Framework ayrıcalığı artıran kodu yönetmek için yeni destek sağlar. Özellikle, CLR ayrıcalık yükseltir kodu tanımlamak ve onu işaretlemek <xref:System.Security.SecurityCriticalAttribute>sağlar ; işaretlenmemiş <xref:System.Security.SecurityCriticalAttribute> herhangi bir kod bu metodoloji kullanılarak *saydam* hale gelir. Tersine, işaretlenmemiş <xref:System.Security.SecurityCriticalAttribute> yönetilen kodun ayrıcalığı yükseltmesi engellenir.  
  
 Güvenlik Açısından Kritik Metodoloji, gizliliği güvenlik açısından kritik çekirdek haline yükselten WPF *kodunun*düzenlenmesine izin verir ve geri kalanı saydamdır. Güvenlik açısından kritik kodun yalıtılmasını, WPF mühendislik ekibinin standart güvenlik uygulamalarının üstündeve ötesinde ki güvenlik açısından kritik çekirdek üzerinde ek bir güvenlik analizi ve kaynak denetimine odaklanmasını sağlar [(bkz.](wpf-security-strategy-security-engineering.md)  
  
 .NET Framework'ün, geliştiricilerin (APTCA) ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> işaretlenmiş ve kullanıcının Genel Derleme Önbelleğine (GAC) dağıtılan yönetilen derlemeler yazmasına izin vererek, güvenilir kodun XBAP Internet bölgesi kum havuzunu genişletmesine izin verdiğini unutmayın. Bir derlemeyi APTCA ile işaretleme, herhangi bir kodun Internet'ten gelen kötü amaçlı kod da dahil olmak üzere bu derlemeyi çağırmasına izin verdiği için son derece hassas bir güvenlik işlemidir. Bunu yaparken çok dikkatli ve en iyi uygulamalar kullanılmalıdır ve kullanıcıların bu yazılımın yüklenmesi için bu yazılıma güvenmeyi seçmeleri gerekir.  
  
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer Güvenliği  
 Microsoft Internet Explorer 6 (SP2), güvenlik sorunlarını azaltmanın ve güvenlik yapılandırmalarını basitleştirmenin ötesinde, XAML tarayıcı uygulamaları (XBAPs) kullanıcılarıiçin güvenliği artıran güvenlik geliştirmeleri içeren çeşitli özellikler içerir. Bu özelliklerin itme kullanıcıların tarama deneyimi üzerinde daha fazla kontrol sağlamak için çalışır.  
  
 IE6 SP2'den önce, kullanıcılar aşağıdakilerden herhangi biri olabilir:  
  
- Rastgele açılır pencereler.  
  
- Kafa karıştırıcı komut dosyası yeniden yönlendirmesi.  
  
- Bazı Web sitelerinde çok sayıda güvenlik iletişim ilerler.  
  
 Bazı durumlarda, güvenilmez Web siteleri, kullanıcı yüklemeyi iptal etmiş [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] olsa bile, yüklemeyi taklit ederek veya microsoft ActiveX yükleme iletişim kutusunu tekrar tekrar göstererek kullanıcıları kandırmaya çalışır. Bu teknikleri kullanarak, kullanıcıların önemli bir kısmı casus yazılım uygulamalarının kurulumu ile sonuçlanan kötü kararlar almak için kandırılmış olabilir.  
  
 IE6 SP2, kullanıcı başlatma kavramı etrafında dönen bu tür sorunları azaltmak için çeşitli özellikler içerir. IE6 SP2, kullanıcı *başlatma*olarak bilinen bir eylemden önce bir bağlantıyı veya sayfa öğesini tıklattığında algılar ve benzer bir eylemin bir sayfadaki komut dosyası tarafından tetiklendiğinden farklı davranır. Örnek olarak, IE6 SP2, bir kullanıcının sayfaaçılır pencere oluşturmadan önce bir düğmeyi tıklattığında algıladığını algılayan bir **Açılır Pencere Engelleyici** içerir. Bu, IE6 SP2'nin en zararsız açılır pencerelere izin verirken, kullanıcıların ne istediği ne de istediği açılır pencereleri önlemesini sağlar. Engellenen açılır pencereler, kullanıcının bloğu el ile geçersiz kılmasına ve açılır pencereyi görüntülemesine olanak tanıyan yeni **Bilgi Çubuğu'nun**altında sıkışıp kalır.  
  
 Aynı kullanıcı başlatma mantığı,/**Kaydet** **Open**güvenlik istemlerine de uygulanır. ActiveX yükleme iletişim kutuları, önceden yüklenmiş bir denetimden bir yükseltmeyi temsil etmediği sürece her zaman Bilgi Çubuğu'nun altında sıkışıp kalır. Bu önlemler, kullanıcılara istenmeyen veya kötü amaçlı yazılım yüklemeleri için onları rahatsız eden sitelere karşı korundukları için daha güvenli ve daha kontrollü bir kullanıcı deneyimi sağlamak için biraraya gelir.  
  
 Bu özellikler, WPF uygulamalarını indirmelerine ve yüklemelerine izin veren web sitelerine göz atmak için IE6 SP2 kullanan müşterileri de korur. Bunun nedeni, IE6 SP2'nin wpf dahil olmak üzere, hangi teknolojinin kullanıldığına bakılmaksızın kullanıcıların kötü amaçlı veya dolambaçlı uygulamalar yükleme şansını azaltan daha iyi bir kullanıcı deneyimi sunmasıdır. WPF, internet üzerinden uygulamalarının karşıdan yüklenmesini kolaylaştırmak için ClickOnce'yi kullanarak bu korumaları ekler. XAML tarayıcı uygulamaları (XBAP'ler) Internet bölgesi güvenlik alanı içinde yürütüldünden, sorunsuz bir şekilde başlatılabilir. Diğer taraftan, bağımsız WPF uygulamaları yürütmek için tam güven gerektirir. Bu uygulamalar için ClickOnce, başlatma işlemi sırasında uygulamanın ek güvenlik gereksinimlerinin kullanımını bildirmek için bir güvenlik iletişim kutusu görüntüler. Ancak, bu kullanıcı tarafından başlatılmalıdır, ayrıca kullanıcı başlatılan mantığı tarafından yönetilir ve iptal edilebilir.  
  
 Internet Explorer 7, iE6 SP2'nin güvenlik yeteneklerini sürekli güvenlik taahhüdünün bir parçası olarak birleştirir ve genişletir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod Erişimi Güvenliği](../misc/code-access-security.md)
- [Güvenlik](security-wpf.md)
- [WPF Kısmi Güven Güvenliği](wpf-partial-trust-security.md)
- [WPF Güvenlik Stratejisi - Güvenlik Mühendisliği](wpf-security-strategy-security-engineering.md)
