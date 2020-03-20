---
title: Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- permission sets, modifying security policy
- security policy [.NET Framework], Code Access Security Policy tool
- enterprise security policy
- referencing code groups and permission sets
- user security policy
- Caspol.exe
- Code Access Security Policy tool
- code groups, modifying security policy
- application development [.NET Framework], security
- machine security policy
- security policy [.NET Framework], modifying
- manually editing security configuration files
ms.assetid: d2bf6123-7b0c-4e60-87ad-a39a1c3eb2e0
ms.openlocfilehash: 792d89351b3759984b085fd8aee9c3ae8e012c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180408"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)
Kod Erişim Güvenliği (CAS) İlkesi aracı (Caspol.exe) kullanıcıların ve yöneticilerin güvenlik ilkesini makine ilkesi düzeyinde, kullanıcı ilkesi düzeyinde ve kuruluş ilkesi düzeyinde değiştirmelerini sağlar.  
  
> [!IMPORTANT]
> .NET Framework 4 ile başlayarak, Caspol.exe [ \<eski CasPolicy> öğesi](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) `true`ayarlanmadıkça CAS ilkesini etkilemez. CasPol.exe tarafından gösterilen veya değiştirilen ayarlar yalnızca CAS ilkesini kullanmayı seçen uygulamaları etkiler. Daha fazla bilgi için [Güvenlik Değişiklikleri'ne](../security/security-changes.md)bakın.  
  
> [!NOTE]
> 64 bit bilgisayarlarda güvenlik ilkesi 64-bit ve 32-bit sürümleri içerir. İlkenizdeki değişikliklerin 32-bit ve 64-bit sürümlerine uygulandığından emin olmak için Caspol.exe'nin 32-bit ve 64-bit sürümlerinin ikisini de çalıştırın.  
  
 Kod Erişimi Güvenlik İlkesi aracı, .NET Framework ve Visual Studio ile otomatik olarak yüklenir. Caspol.exe'yi %windir%\Microsoft.NET\Framework\\*sürümünde* 32 bit sistemlerde veya %windir%\Microsoft.NET\Framework64\\*sürümünde* 64 bit sistemlerde bulabilirsiniz. (Örneğin, 64 bit lik bir sistemde .NET Framework 4 için konum %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe'dir.) Bilgisayarınız .NET Framework'ün birden çok sürümü yan yana çalışıyorsa, aracın birden çok sürümü yüklenmiş olabilir. Aracı yükleme dizininden çalıştırabilirsiniz. Ancak, yükleme klasörüne gezinmenizi gerektirmeyen [Komut İstemleri'ni](developer-command-prompt-for-vs.md)kullanmanızı öneririz.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-af** *assembly_file*|Özel güvenlik nesnesi (örneğin, özel bir izin veya özel üyelik koşulu) uygulayan bir derlemeyi belirli bir ilke düzeyi için tam güven derleme listesine ekler. *assembly_file* bağımsız değişkeni eklemek için derleme belirtir. Bu dosya güçlü bir [adla](../../standard/assembly/strong-named.md)imzalanmalıdır. [Güçlü Ad Aracı'nı (Sn.exe)](sn-exe-strong-name-tool.md)kullanarak güçlü bir ada sahip bir derleme imzalayabilirsiniz.<br /><br /> İlkeye, özel izin içeren bir izin kümesi her eklendiğinde, özel izni uygulayan derleme o ilke düzeyi için tam güven listesine eklenmelidir. Bir güvenlik ilkesinde (makine ilkesi gibi) kullanılan özel güvenlik nesneleri (özel kod grupları veya üyelik koşulları gibi) uygulayan derlemeler her zaman tam güven derleme listesine eklenmelidir. **Dikkat:**  Özel güvenlik nesnesi uygulayan derleme diğer derlemelere başvuruyorsa, önce başvurulan derlemeleri tam güven derleme listesine eklemeniz gerekir. Visual Basic, C++ ve JScript kullanılarak oluşturulan özel güvenlik nesneleri sırasıyla Microsoft.VisualBasic.dll, Microsoft.VisualC.dll veya Microsoft.JScript.dll'ye başvuru yapar. Bu derlemeler varsayılan olarak tam güven derleme listesinde bulunmaz. Özel bir güvenlik nesnesi eklemeden önce uygun derlemeyi tam güven listesine eklemeniz gerekir. Bunun yapılmaması durumunda güvenlik sistemi çalışmaz ve tüm derlemelerin yüklenmesi başarısız olur. Bu durumda, Caspol.exe **-all-reset** seçeneği güvenliği onarmayacaktır. Güvenliği onarmak için, özel güvenlik nesnesini kaldırmak üzere güvenlik dosyalarını el ile düzenlemeniz gerekir.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*bayraklar*]<br /><br /> or<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*bayraklar*]|Kod grubu hiyerarşisine yeni bir kod grubu ekler. *parent_label* veya *parent_name*belirtebilirsiniz. *parent_label* bağımsız değişkeni etiketi belirtir (örneğin 1. veya 1.1.) eklenen kod grubunun üst öğesi olan kod grubunun. *parent_name* bağımsız değişkeni, eklenen kod grubunun üst öğesi olan kod grubunun adını belirtir. *parent_label* ve *parent_name* birbirinin yerine kullanılabildiği için Caspol.exe bunları ayırt edebilmelidir. Bu nedenle, *parent_name* bir sayı ile başlayamaz. Ayrıca, *parent_name* yalnızca A-Z, 0-9 ve alt skor karakteri içerebilir.<br /><br /> Mship bağımsız *değişkeni,* yeni kod grubunun üyelik koşulunu belirtir. Daha fazla bilgi için, daha sonra bu bölümde *mship* bağımsız değişkenleri tablosuna bakın.<br /><br /> *pset_name* bağımsız değişkeni, yeni kod grubuyla ilişkilendirilecek izin kümesinin adıdır. Ayrıca, yeni grup için bir veya daha fazla *bayrak* ayarlayabilirsiniz. Daha fazla bilgi için, bu bölümde daha sonra *bayraklar* bağımsız değişkenleri tablosuna bakın.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> or<br /><br /> **-ap** {*adlı*_*psfile* &#124; *psfile* *pset_name*}|İlkeye yeni bir adlandırılmış izin kümesi ekler. İzin kümesi XML'de yazılmış ve bir .xml dosyasında depolanmış olmalıdır. XML dosyası izin kümesinin adını içeriyorsa, yalnızca bu dosya *(psfile)* belirtilir. XML dosyası izin kümesi adını içermiyorsa, hem XML dosya adını *(psfile)* hem de izin kümesi adını *(pset_name)* belirtmeniz gerekir.<br /><br /> Bir izin kümesinde kullanılan tüm izinlerin genel derleme önbelleğinde bulunan derlemelerde tanımlanması gerektiğini unutmayın.|  
|**-a**[**ll**]|Bunu izleyen tüm seçeneklerin makineye, kullanıcıya ve kuruluş ilkelerine uygulanacağını belirtir. **-tüm** seçenek her zaman şu anda oturum açmış kullanıcının ilkesianlamına gelir. Geçerli kullanıcı dışında bir kullanıcının kullanıcı ilkesine başvurmak için **-customall** seçeneğine bakın.|  
|**-chggroup** {*etiket &#124;adı*} {*mship* &#124; *pset_name* &#124;<br /><br /> *bayraklar* `}`<br /><br /> or<br /><br /> **-cg** {*etiket &#124;adı*} {*mship* &#124; *pset_name* &#124;<br /><br /> *bayraklar* `}`|Kod grubunun üyelik durumunu, izin kümesini veya **özel**, **levelfinal,** **ad**veya **açıklama** bayraklarının ayarlarını değiştirir. *Etiketi* veya *adı*belirtebilirsiniz. *Etiket* bağımsız değişkeni etiketi belirtir (örneğin 1. veya 1.1.) kod grubunun. *Ad* bağımsız değişkeni, değiştirilen kod grubunun adını belirtir. *Etiket* ve *ad* birbirinin yerine kullanılabildiği için, Caspol.exe bunları ayırt edebilmelidir. Bu nedenle, *ad* bir sayı ile başlayamaz. Ayrıca, *ad* yalnızca A-Z, 0-9 ve alt düzey karakter içerebilir.<br /><br /> *pset_name* bağımsız değişkeni, kod grubuyla ilişkilendirmek üzere ayarlanan izin kümesinin adını belirtir. *Mship* ve *bayraklar* bağımsız değişkenleri hakkında bilgi için daha sonra bu bölümde tablolara bakın.|  
|**-chgpset**  *psfile pset_name*<br /><br /> or<br /><br /> **-cp** *psfile pset_name*|Adlandırılmış bir izin kümesini değiştirir. *psfile* bağımsız değişkeni izin kümesi için yeni tanımı sağlar; XML formatında serileştirilmiş bir izin kümesi dosyasıdır. *pset_name* bağımsız değişkeni, değiştirmek istediğiniz izin kümesinin adını belirtir.|  
|**-customall**  *yolu*<br /><br /> or<br /><br /> **-ca**  *yolu*|Bunu izleyen tüm seçeneklerin makineye, kuruluşa ve belirtilen özel kullanıcı ilkelerine uygulanacağını belirtir. Özel kullanıcının güvenlik yapılandırma dosyasının konumunu *yol* bağımsız değişkeniyle belirtmeniz gerekir.|  
|**-cu**[**stomuser**] *yolu*|Adına Caspol.exe çalışmakta olan bir kullanıcıya ait olmayan özel bir kullanıcı ilkesinin yönetilmesine olanak verir. Özel kullanıcının güvenlik yapılandırma dosyasının konumunu *yol* bağımsız değişkeniyle belirtmeniz gerekir.|  
|**-kurumsal**<br /><br /> or<br /><br /> **-en**|Bunu izleyen tüm seçeneklerin kuruluş düzeyinde ilkeye uygulanacağını belirtir. Kurumsal yönetici olmayan kullanıcılar kuruluş ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Kuruluş dışı senaryolarda bu ilke varsayılan olarak makine ve kullanıcı ilkesini engellemez.|  
|**-e**[**xecution**] { kapalı **&#124;****}**|Kod yürütülmeye başlamadan önce çalıştırmak için izni denetleyen mekanizmayı etkinleştirir veya devre dışı bırakır. **Not:**  Bu anahtar .NET Framework 4 ve sonraki sürümlerde kaldırılır. Daha fazla bilgi için [Güvenlik Değişiklikleri'ne](../security/security-changes.md)bakın.|  
|**-f**[**orce**]|Aracın kendini kaldırma testini engeller ve ilkeyi kullanıcı tarafından belirtilen şekilde değiştirir. Normal olarak Caspol.exe, ilke değişikliklerinin Caspol.exe'nin düzgün çalışmasını önleyip önlemeyeceğini denetler; önleyecekse Caspol.exe ilke değişikliğini kaydetmez ve bir hata iletisi yazdırır. Caspol.exe'yi, Caspol.exe'nin çalışmasını engellese bile politikayı değiştirmeye zorlamak için **kuvvet seçeneğini** kullanın.|  
|**-h**[**elp**]|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
|**-l**[**ist**]|Belirtilen makine, kullanıcı, kuruluş veya tüm ilke düzeyleri için kod grubu hiyerarşisini ve izin kümelerini listeler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listdescription**<br /><br /> or<br /><br /> **-ld**|Belirtilen ilke düzeyi için tüm kod grubu açıklamalarını listeler.|  
|**-listfulltrust**<br /><br /> or<br /><br /> **-lf**|Belirtilen ilke düzeyi için tam güven derleme listesinin tüm içeriğini listeler.|  
|**-listgroups**<br /><br /> or<br /><br /> **-lg**|Belirtilen ilke düzeyi veya tüm ilke düzeylerinin kod gruplarını görüntüler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listpset** veya **-lp**|Belirtilen ilke düzeyi veya tüm ilke düzeyleri için izin kümelerini görüntüler.|  
|**-m**[**achine**]|Bunu izleyen tüm seçeneklerin makine düzeyinde ilkeye uygulanacağını belirtir. Yönetici olmayan kullanıcılar makine ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Yöneticiler için **-makine** varsayılandır.|  
|**-polchgprompt** { kapalı **&#124;****}**<br /><br /> or<br /><br /> **-pp** {**kapalı** **&#124;**}|Caspol.exe ilke değişikliklerine neden olan bir seçenek kullanılarak her çalıştırıldığında komut istemini etkinleştirir veya devre dışı bırakır.|  
|**-quiet**<br /><br /> or<br /><br /> **-q**|İlke değişikliklerine neden olan bir seçenek için normal olarak görüntülenen istemi geçici olarak devre dışı bırakır. Genel değişiklik istemi ayarı değişmez. Tüm Caspol.exe komutları için istemin devre dışı bırakılmasından kaçınmak üzere seçeneği yalnızca tek komut temelinde kullanın.|  
|**-r**[**ecover**]|Bir yedek dosyadan ilkeyi kurtarır. Bir ilke değişikliği her yapıldığında, Caspol.exe eski ilkeyi bir yedekleme dosyasına depolar.|  
|**-remfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-rf**  *assembly_file*|Bir derlemeyi ilke düzeyi tam güven listesinden kaldırır. Bu işlem, özel izin içeren bir izin kümesi ilke tarafından artık kullanılmıyorsa gerçekleştirilmelidir. Ancak, yalnızca derleme halen kullanılmakta olan herhangi bir özel izni uygulamıyorsa tam güven listesinden özel izin uygulayan bir derlemeyi kaldırmanız gerekir. Bir derlemeyi listeden kaldırdığınızda, bağımlı olduğu derlemeleri de kaldırmanız gerekir.|  
|**-remgroup** {*etiket &#124;adı*}<br /><br /> or<br /><br /> **-rg** {l*abel &#124; adı*}|Etiketinin veya adının belirttiği kod grubunu kaldırır. Belirtilen kod grubunda alt kod grupları varsa, Caspol.exe tüm alt kod gruplarını da kaldırır.|  
|**-sıfırlama** *pset_name*<br /><br /> or<br /><br /> **-rp** *pset_name*|Belirtilen izin kümesini ilkeden kaldırır. pset_name *pset_name* bağımsız değişkeni, hangi izinlerin kaldırılacağı kümesini gösterir. Caspol.exe izin kümesini yalnızca herhangi bir kod grubu ile ilişkili değilse kaldırır. Varsayılan (yerleşik) izin kümeleri kaldırılamaz.|  
|**-sıfırlama**<br /><br /> or<br /><br /> **-rs**|İlkeyi varsayılan durumuna geri döndürür ve diskte kalıcı kılar. Değiştirilen bir ilke onarılamayacak şekilde görünüyorsa ve siz de yükleme varsayılanları ile baştan başlamak istiyorsanız, bu yararlıdır. Varsayılan ilkeyi özel güvenlik yapılandırma dosyalarında yapılan değişiklikler için bir başlangıç noktası olarak kullanmak istediğinizde sıfırlama da kullanışlı olabilir. Daha fazla bilgi için [bkz.](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1)|  
|**-sıfırlama**<br /><br /> or<br /><br /> **-rsld**|İlkeyi varsayılan durum daha kısıtlayıcı bir sürüme verir ve diskte devam eder; önceki makine ilkesinin bir yedeklemesini oluşturur ve onu `security.config.bac`.  Kilitlenmiş ilke, ilke, `Local Intranet`,, `Trusted Sites` `Internet` ve bölgeler ve ilgili kod gruplarından kod için izin vermemiş olması ve alt kod grupları olmaması dışında varsayılan ilkeyle benzer.|  
|**-çözüm grubu** *assembly_file*<br /><br /> or<br /><br /> **-rsg**  *assembly_file*|Belirli bir derlemenin *(assembly_file)* ait olduğu kod gruplarını gösterir. Varsayılan olarak bu seçenek, derlemenin ait olduğu makine, kullanıcı ve kuruluş ilkesi düzeylerini gösterir. Yalnızca bir ilke düzeyini görüntülemek için bu seçeneği **-machine**, **-user**veya **-enterprise** seçeneğiyle kullanın.|  
|**-resolveperm** *assembly_file*<br /><br /> or<br /><br /> **-rsp** *assembly_file*|Derlemenin çalışmasına izin verilmişse, güvenlik ilkesinin belirtilen (veya varsayılan) düzeyinin derlemeye verdiği tüm izinleri görüntüler. *assembly_file* bağımsız değişkeni derlemeyi belirtir. **-tüm** seçeneğini belirtirseniz, Caspol.exe kullanıcı, makine ve kuruluş ilkesine göre derleme izinlerini hesaplar; aksi takdirde, varsayılan davranış kuralları geçerlidir.|  
|**-s**[**eşitlik**] {**&#124;** **kapalı**}|Kod erişim güvenliğini açar veya kapatır. **-s off** seçeneğini belirtmek rol tabanlı güvenliği devre dışı bırakmıyor. **Not:**  Bu anahtar .NET Framework 4 ve sonraki sürümlerde kaldırılır. Daha fazla bilgi için [Güvenlik Değişiklikleri'ne](../security/security-changes.md)bakın. **Dikkat:**  Kod erişim güvenliği devre dışı bırakıldığında, tüm kod erişim talepleri başarılı dır. Kod erişimi güvenliğini devre dışı bırakmak sistemi virüsler ve solucanlar gibi zararlı kodların saldırılarına açık hale getirir. Güvenliğin devre dışı bırakılması belli oranda performans artışı sağlayabilir ancak bu işlem yalnızca genel sistem güvenliğinin ihlal edilmemesine yardımcı olacak diğer güvenlik önlemleri alındığı zaman yapılmalıdır. Diğer güvenlik önlemlerine ilişkin örnekler arasında ortak ağ bağlantılarını kesme, bilgisayarları fiziksel olarak güvenlik altına alma vb. sayılabilir.|  
|**-u**[**ser**]|Bunu izleyen tüm seçeneklerin, adına Caspol.exe çalıştıran kullanıcı için kullanıcı düzeyi ilkesine uygulanacağını belirtir. Yönetim dışı kullanıcılar için **-kullanıcı** varsayılandır.|  
|**-?**|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Bir kod grubunun üyelik koşulunu belirten *mship* bağımsız **değişkeni,-addgroup** ve **-chggroup** seçenekleriyle kullanılabilir. Her *mship* bağımsız değişkeni bir .NET Framework sınıfı olarak uygulanır. Mship belirtmek için *aşağıdakilerden* birini kullanın.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-allcode**|Tüm kodu belirtir. Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-appdir**|Uygulama dizini belirtir. Üyelik koşulu olarak **-appdir-** belirtirseniz, kodun URL kanıtı, bu kodun uygulama dizini kanıtıyla karşılaştırılır. Her iki kanıt değeri de aynıysa, bu üyelik koşulu gerçekleşmiş demektir. Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-özel**  *xmlfile*|Özel üyelik koşulu ekler. Zorunlu *xmlfile* bağımsız değişkeni, özel üyelik koşulunun XML serileştirmesini içeren .xml dosyasını belirtir.|  
|**-hash** *hashAlg* {**-hex** *hashValue* &#124; **-dosya** *assembly_file* }|Belirtilen derleme karmasına sahip kodu belirtir. Bir karmayı kod grubu üyelik koşulu olarak kullanmak için, karma değerini ya da derleme dosyasını belirtmelisiniz. Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-dosya** *signed_file_name* &#124; **-hex**  *hex_string* }|Belirtilen yazılım yayıncısına sahip kodu (bir sertifika dosyasıyla, bir dosyadaki imzayla veya bir X 509 sertifikasının onaltılı gösterimiyle sunulduğu şekilde) belirtir. Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-site** *web sitesi*|Belirtilen kaynak siteyi içeren kodu belirtir. Örnek:<br /><br /> `-site** www.proseware.com`<br /><br /> Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-güçlü -dosya** *file_name* {*name* &#124; **-noname**} {*sürüm* &#124; **-noversion**}|Dosya adı, derleme adı dize olarak ve biçim *ana*tarafından belirlenen belirli bir güçlü ada sahip kod belirtir. *küçük*. *inşa edin.* *revizyon*. Örnek:<br /><br /> **-güçlü -dosya** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-url** *URL*|Belirtilen URL'den kaynaklanan kodu belirtir. URL gibi bir protokol `http://` içermelidir. `ftp://` Ayrıca, bir joker karakter\*( ) belirli bir URL'den birden çok derlemebelirtmek için kullanılabilir. **Not:**  Bir URL birden çok ad kullanılarak tanımlanadığından, bir URL'yi üyelik koşulu olarak kullanmak kodun kimliğini belirlemenin güvenli bir yolu değildir. Mümkün olan yerlerde, bir tanımlayıcı ad üyelik koşulu, bir yayımcı üyelik koşulu veya karma üyelik koşulu kullanın. <br /><br /> Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>fazla bilgi için bkz.|  
|**-bölge** *bölge adı*|Belirtilen kaynak bölgeyi içeren kodu belirtir. *Bölge adı* bağımsız değişkeni aşağıdaki değerlerden biri olabilir: **MyComputer**, **Intranet**, **Trusted**, **Internet**, veya **Güvenilmez**. Bu üyelik koşulu hakkında daha <xref:System.Security.Policy.ZoneMembershipCondition> fazla bilgi için Sınıf'a bakın.|  
  
 **–addgroup ve –chggroup** seçenekleriyle **–chggroup** kullanılabilen *bayraklar* bağımsız değişkeni aşağıdakilerden biri kullanılarak belirtilir.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-açıklama** "*açıklama*"|**–addgroup** seçeneği yle kullanılırsa, ekleyecek bir kod grubunun açıklamasını belirtir. **–chggroup** seçeneği yle kullanılırsa, bir kod grubunun açıklaması belirtilir. *Açıklama* bağımsız değişkeni çift tırnak içinde eklenmelidir.|  
|**-özel** {**kapalı** **&#124;**}|Ayarlandığında, **on**yalnızca eklediğiniz veya değiştirdiğiniz kod grubuyla ilişkili izin kümesinin, bazı kodlar kod grubunun üyelik durumuna uyduğunda dikkate alındığını gösterir. Bu seçenek **kapatıldığında,** Caspol.exe ilke düzeyindeki tüm eşleşen kod gruplarının izin kümelerini dikkate alır.|  
|**-levelfinal** {**kapalı** **&#124;**}|Ayarlandığında, **on**eklenen veya değiştirilen kod grubunun oluştuğu düzeyin altında hiçbir ilke düzeyinin dikkate alınadığını gösterir. Bu seçenek genellikle makine ilkesi düzeyinde kullanılır. Örneğin, makine düzeyinde bir kod grubu için bu bayrağı ayarlarsanız ve bazı kodlar bu kod grubunun üyelik koşulu ile eşleşirse, Caspol.exe bu kod için kullanıcı düzeyi ilkesini hesaplamaz veya uygulamaz.|  
|**-isim** "*adı*"|**–addgroup** seçeneği yle kullanılırsa, eklenecek bir kod grubunun komut dosyası adını belirtir. **-chggroup** seçeneği yle kullanılırsa, bir kod grubunun kod adını belirtir. *Ad* bağımsız değişkeni çift tırnak içinde eklenmelidir. *Ad* bağımsız değişkeni bir sayıyla başlayamaz ve yalnızca A-Z, 0-9 ve alt düzey karakter içerebilir. Kod grupları sayısal etiketi yerine bu *adla* anılabilir. *Ad,* komut dosyası kullanmak için de son derece yararlıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik ilkesi üç ilke düzeyi kullanılarak ifade edilir: Makine ilkesi, kullanıcı ilkesi ve kuruluş ilkesi. Bir derlemenin aldığı izin kümesi, bu üç ilke düzeyi tarafından izin verilen izin kümelerinin kesişimi ile belirlenir. Her ilke düzey kod gruplarının hiyerarşik bir yapısı ile temsil edilir. Her kod grubunun bir üyelik koşulu vardır ve bu koşul hangi kodun o grubun üyesi olduğunu belirler. Adlandırılmış bir izin kümesi aynı zamanda her kod grubu ile ilişkilidir. Bu izin kümesi, çalışma zamanı tarafından, üyelik koşulunu karşılayan kodun sahip olmasına izin verilen izinleri belirtir. Bir kod grubu hiyerarşisi, ilişkili adlandırılmış izin kümeleriyle birlikte, güvenlik ilkesinin her düzeyini tanımlar ve korur. Güvenlik ilkesi düzeyini ayarlamak için **–kullanıcı**, **-customuser**, **-makine** ve **-kurumsal** seçenekleri kullanabilirsiniz.  
  
 Güvenlik ilkesi ve çalışma zamanının koda hangi izinleri verilebildiğini nasıl belirlediği hakkında daha fazla bilgi için [Güvenlik İlkesi Yönetimi'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))bakın.  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Kod Grupları ve İzin Kümelerine Başvurma  
 Bir hiyerarşideki kod gruplarına başvuruları kolaylaştırmak **için, -liste** seçeneği, sayısal etiketleri (1, 1.1, 1.1.1 vb.) ile birlikte kod gruplarının girintisi listesini görüntüler. Kod gruplarını hedefleyen diğer komut satırı işlemleri belirli kod gruplarına başvuru yapmak için de sayısal etiketleri kullanır.  
  
 Adlandırılmış izin kümelerine, adlarına göre başvuru yapılır. **-liste** seçeneği, kod gruplarının listesini ve ardından bu ilkede bulunan adlandırılmış izin kümelerinin listesini görüntüler.  
  
## <a name="caspolexe-behavior"></a>Caspol.exe Davranışı  
 **-s**[**eşitlik**] {**&#124;** **kapalı**} dışındaki tüm seçenekler Caspol.exe'nin yüklü olduğu .NET Framework sürümünü kullanır. Çalışma zamanının *X* sürümüyle yüklenen Caspol.exe'yi çalıştırırsanız, değişiklikler yalnızca bu sürüm için geçerlidir. Çalışma zamanının, diğer yan yana yüklemeleri varsa etkilenmez. Komut satırından, belirli çalışma zamanı sürümü dizininde olmaksızın Caspol.exe çalıştırırsanız, araç o yoldaki ilk çalışma zamanı sürümü dizininden (genellikle yüklü en son çalışma zamanı sürümü) yürütülür.  
  
 **-s**[**eşitlik**] {**&#124;** **kapalı**} seçeneği bilgisayar çapında bir işlemdir. Kod erişim güvenliği devre dışı bırakmak bilgisayarda tüm kullanıcılar için ve yönetilen tüm kodlar için güvenlik kontrollerini sonlandırır. Yan yana .NET Framework sürümleri yüklüyse, bu komut bilgisayarda yüklü her sürüm için güvenliği kapatır. **Liste** seçeneği güvenliğin kapalı olduğunu gösterse de, başka hiçbir şey diğer kullanıcılar için güvenliğin kapatıldığını açıkça göstermez.  
  
 Yönetim hakkı olmayan bir kullanıcı Caspol.exe'yi çalıştırdığında, **makine** seçeneği belirtilmedikçe tüm seçenekler kullanıcı düzeyi ilkesine başvurur. Bir yönetici Caspol.exe'yi çalıştırdığında, **kullanıcı** seçeneği belirtilmedikçe tüm seçenekler makine ilkesine başvurur.  
  
 Caspol.exe'ye, çalışması için ayarlanmış **Her Şey** izninin eşdeğeri verilmelidir. Araçta, Caspol.exe'in çalışması için gereken izinlerin verilmesini önleyecek biçimlerde ilke üzerinde değişiklik yapılmasını önleyen koruyucu bir mekanizma vardır. Bu tür değişiklikler yapmaya çalışırsanız, Caspol.exe istenen ilke değişikliğinin aracı kesintiye uğratacağını ve ilke değişikliğinin reddedildiğini size bildirir. Bu koruyucu mekanizmayı belirli bir komut için **kuvvet** seçeneğini kullanarak kapatabilirsiniz.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>
## <a name="manually-editing-the-security-configuration-files"></a>Güvenlik Yapılandırma Dosyalarını El İle Düzenleme  
 Üç güvenlik yapılandırması dosyası, Caspol.exe tarafından desteklenen üç ilke düzeyine karşılık gelir: Makine ilkesi için bir dosya, belirli bir kullanıcı ilkesi için bir dosya ve kuruluş ilkesi için bir dosya. Yalnızca makine, kullanıcı veya kuruluş ilkesi Caspol.exe kullanılarak değiştirildiğinde, bu dosyalar disk üzerinde oluşturulur. Gerekirse varsayılan güvenlik ilkesini diske kaydetmek için Caspol.exe'deki **-sıfırlama** seçeneğini kullanabilirsiniz.  
  
 Çoğu durumda, güvenlik yapılandırma dosyalarını el ile düzenlemek önerilmez. Ancak bu dosyalarda değişiklik yapılmasının gerekeceği bazı senaryolar da olabilir (örneğin, bir yönetici belirli bir kullanıcı için güvenlik yapılandırmasını düzenlemek isteyebilir).  
  
## <a name="examples"></a>Örnekler  
 **-addfulltrust**  
  
 Özel izin içeren bir izin kümesinin makine ilkesine eklendiğini varsayalım. Bu özel izin , `MyPerm.exe`ve `MyPerm.exe` 'deki `MyOther.exe`sınıflara başvurur. İki derleme de tam güven derleme listesine eklenmelidir. Aşağıdaki `MyPerm.exe` komut, makine ilkesi için derlemeyi tam güven listesine ekler.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Aşağıdaki `MyOther.exe` komut, makine ilkesi için derlemeyi tam güven listesine ekler.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Aşağıdaki komut, makine ilkesi kod grubu hiyerarşisinin kök dizinine bir alt kod grubu ekler. Yeni kod grubu **Internet** bölgesinin bir üyesidir ve **Yürütme** izni kümesiyle ilişkilidir.  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Aşağıdaki komut, pay \\\netserver\netshare yerel intranet izinleri veren bir alt kod grubu ekler.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Aşağıdaki komut, `Mypset` kullanıcı ilkesine izin kümesini ekler.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Aşağıdaki komut, 1.2 etiketli kod grubunun kullanıcı ilkesinde ayarlanan izin kümesini değiştirir. **Yürütme** izni kümesine.  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Aşağıdaki komut, 1.2.1 etiketli kod grubunun varsayılan ilkesindeki üyelik koşulunu değiştirir. ve **özel** bayrağın ayarını değiştirir. Üyelik **koşulu, Internet** bölgesinden kaynaklanan kod olarak tanımlanır ve **özel** bayrak açık.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Aşağıdaki komut, adı `Mypset` taşıyan izin kümesini ' `newpset.xml`de yer alan izin kümesiyle değiştirir. Geçerli sürümün, kod grubu hiyerarşisi tarafından kullanılan izin kümelerini değiştirmeyi desteklemediğini unutmayın.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-kuvvet**  
  
 Aşağıdaki komut, kullanıcı ilkesinin kök kod grubunun (etiketli 1) **Hiçbir Şey** adlı izin kümesiyle ilişkilendirilmesine neden olur. Bu Caspol.exe'nın çalışmasını engeller.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-kurtarmak**  
  
 Aşağıdaki komut, en son kaydedilen makine ilkesini kurtarır.  
  
```console  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Aşağıdaki komut 1.1 etiketli kod grubunu kaldırır. Bu kod grubunda herhangi bir alt kod grubu varsa, bu gruplar da silinir.  
  
```console  
caspol -remgroup 1.1.  
```  
  
 **-sıfırlama**  
  
 Aşağıdaki komut, kullanıcı ilkesinden **Yürütme** izni kümesini kaldırır.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Aşağıdaki komut kullanıcı `Mypset` ilkesi düzeyinden kaldırır.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-çözüm grubu**  
  
 Aşağıdaki komut, makine ilkesine `myassembly` ait tüm kod gruplarını gösterir.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Aşağıdaki komut, makinenin, işletmenin ve ait olan `myassembly` özel kullanıcı ilkesinin tüm kod gruplarını gösterir.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-çözümleyici**  
  
 Aşağıdaki komut, makine ve `testassembly` kullanıcı ilkesi düzeylerini temel alan izinleri hesaplar.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
