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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e6057d1ce6b5d0e961449ef298b1a50c7a407ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200538"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)
Kod Erişim Güvenliği (CAS) İlkesi aracı (Caspol.exe) kullanıcıların ve yöneticilerin güvenlik ilkesini makine ilkesi düzeyinde, kullanıcı ilkesi düzeyinde ve kuruluş ilkesi düzeyinde değiştirmelerini sağlar.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], sürece Caspol.exe CAS ilkesini etkilemez [ \<legacyCasPolicy > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ayarlanır `true`. CasPol.exe tarafından gösterilen veya değiştirilen ayarlar yalnızca CAS ilkesini kullanmayı seçen uygulamaları etkiler. Daha fazla bilgi için [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  64 bit bilgisayarlarda güvenlik ilkesi 64-bit ve 32-bit sürümleri içerir. İlkenizdeki değişikliklerin 32-bit ve 64-bit sürümlerine uygulandığından emin olmak için Caspol.exe'nin 32-bit ve 64-bit sürümlerinin ikisini de çalıştırın.  
  
 Kod Erişimi Güvenlik İlkesi aracı, .NET Framework ve Visual Studio ile otomatik olarak yüklenir. Caspol.exe %windir%\Microsoft.NET\Framework içinde bulabilirsiniz\\*sürüm* 32-bit sistemlerde veya %windir%\Microsoft.NET\Framework64\\*sürüm* 64-bit sistemlerde. (Örneğin, %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe konumu, 64-bit sistemde .NET Framework 4 içindir.) Bilgisayarınızda .NET Framework'un birden çok sürümü yan yana çalışıyorsa, aracın birden çok sürümü yüklenebilir. Aracı yükleme dizininden çalıştırabilirsiniz. Ancak, kullanmanızı öneririz [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md), gerekli olmadığı, yükleme klasörüne gidin.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
caspol [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> veya<br /><br /> **-af** *assembly_file*|Özel güvenlik nesnesi (örneğin, özel bir izin veya özel üyelik koşulu) uygulayan bir derlemeyi belirli bir ilke düzeyi için tam güven derleme listesine ekler. *Assembly_file* bağımsız değişkeni Eklenecek derlemeyi belirtir. Bu dosya imzalanmalıdır bir [tanımlayıcı ad](../../../docs/framework/app-domains/strong-named-assemblies.md). Bir derlemeyi tanımlayıcı ad kullanarak oturum açabilirsiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> İlkeye, özel izin içeren bir izin kümesi her eklendiğinde, özel izni uygulayan derleme o ilke düzeyi için tam güven listesine eklenmelidir. Bir güvenlik ilkesinde (makine ilkesi gibi) kullanılan özel güvenlik nesneleri (özel kod grupları veya üyelik koşulları gibi) uygulayan derlemeler her zaman tam güven derleme listesine eklenmelidir. **Dikkat:**  Özel güvenlik nesnesi uygulayan derleme başka derlemelere başvuru yapıyorsa, önce başvurulan derlemeleri tam güven derleme listesine eklemeniz gerekir. Visual Basic, C++ ve JScript kullanılarak oluşturulan özel güvenlik nesneleri sırasıyla Microsoft.VisualBasic.dll, Microsoft.VisualC.dll veya Microsoft.JScript.dll'ye başvuru yapar. Bu derlemeler varsayılan olarak tam güven derleme listesinde bulunmaz. Özel bir güvenlik nesnesi eklemeden önce uygun derlemeyi tam güven listesine eklemeniz gerekir. Bunun yapılmaması durumunda güvenlik sistemi çalışmaz ve tüm derlemelerin yüklenmesi başarısız olur. Bu durumda, Caspol.exe **-all - reset** seçeneği güvenlik onarmaz. Güvenliği onarmak için, özel güvenlik nesnesini kaldırmak üzere güvenlik dosyalarını el ile düzenlemeniz gerekir.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*bayrakları*]<br /><br /> veya<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*bayrakları*]|Kod grubu hiyerarşisine yeni bir kod grubu ekler. Belirtebilirsiniz *parent_label* veya *parent_name*. *Parent_label* bağımsız değişkeni belirtir (örneğin, 1 etiket. veya 1.1.) eklenen kod grubunun üst kod grubudur. *Parent_name* bağımsız değişkeni, eklenen kod grubunun üst kod grubunun adını belirtir. Çünkü *parent_label* ve *parent_name* olabilir kullanılabileceğinden, Caspol.exe bunları ayırt edebilmelidir. Bu nedenle, *parent_name* bir sayı ile başlayamaz. Ayrıca, *parent_name* yalnızca A-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Mship* bağımsız değişkeni yeni kod grubu için üyelik koşulunu belirtir. Daha fazla bilgi için tablosuna bakın *mship* bu bölümün sonraki kısımlarında bağımsız değişkenler.<br /><br /> *Pset_name* bağımsız değişkeni yeni kod grubu ile ilişkilendirilecek izin kümesinin adıdır. Ayrıca bir veya daha fazla ayarlayabilirsiniz *bayrakları* yeni grup için. Daha fazla bilgi için tablosuna bakın *bayrakları* bu bölümün sonraki kısımlarında bağımsız değişkenler.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> veya<br /><br /> **-ap** {*adlı*_*psfile* &#124; *psfile* *pset_name*}|İlkeye yeni bir adlandırılmış izin kümesi ekler. İzin kümesi XML'de yazılmış ve bir .xml dosyasında depolanmış olmalıdır. XML dosyası iznin adını içeriyorsa ayarlamak, yalnızca o dosya (*psfile*) belirtilir. XML dosyasında izin kümesinin adı yoksa, hem XML dosya adı belirtmeniz gerekir (*psfile*) ve izin kümesinin adını (*pset_name*).<br /><br /> Bir izin kümesinde kullanılan tüm izinlerin genel derleme önbelleğinde bulunan derlemelerde tanımlanması gerektiğini unutmayın.|  
|**-a**[**ll**]|Bunu izleyen tüm seçeneklerin makineye, kullanıcıya ve kuruluş ilkelerine uygulanacağını belirtir. **-Tüm** seçeneği her zaman şu anda oturum açmış kullanıcının ilkesine başvuruyor. Bkz: **- customall** geçerli kullanıcıdan başka bir kullanıcının kullanıcı ilkesine başvurmak için seçeneği.|  
|**-chggroup** {*etiket &#124;adı*} {*mship* &#124; *pset_name*&#124;<br /><br /> *bayraklar* `}`<br /><br /> veya<br /><br /> **-cg** {*etiket &#124;adı*} {*mship* &#124; *pset_name*&#124;<br /><br /> *bayraklar* `}`|Bir kod grubun üyelik koşulunu, izin kümesi veya ayarlarını değiştirir **özel**, **levelfinal**, **adı**, veya **açıklama**bayrakları. Belirtebilirsiniz *etiket* veya *adı*. *Etiket* bağımsız değişkeni belirtir (örneğin, 1 etiket. veya 1.1.) Kod grubu. *Adı* bağımsız değişkeni değiştirilecek kod grubunun adını belirtir. Çünkü *etiket* ve *adı* olabilir kullanılabileceğinden, Caspol.exe bunları ayırt edebilmelidir. Bu nedenle, *adı* bir sayı ile başlayamaz. Ayrıca, *adı* yalnızca A-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Pset_name* bağımsız değişkeni kod grubu ile ilişkilendirmek için oluşturulan iznin adını belirtir. Hakkında bilgi için bu bölümün sonraki kısımlarında tablolara bakın *mship* ve *bayrakları* bağımsız değişkenler.|  
|**-chgpset**  *psfile pset_name*<br /><br /> veya<br /><br /> **-TP** *psfile pset_name*|Adlandırılmış bir izin kümesini değiştirir. *Psfile* bağımsız değişkeni izin kümesi için yeni tanımı sağlar; her bir XML biçiminde seri hale getirilmiş bir izin kümesi dosyasıdır. *Pset_name* bağımsız değişkeni değiştirmek istediğiniz izin kümesinin adını belirtir.|  
|**-customall**  *yolu*<br /><br /> veya<br /><br /> **-ca**  *yolu*|Bunu izleyen tüm seçeneklerin makineye, kuruluşa ve belirtilen özel kullanıcı ilkelerine uygulanacağını belirtir. İle özel kullanıcının güvenlik yapılandırma dosyasının konumunu belirtmelisiniz *yolu* bağımsız değişken.|  
|**-cu**[**stomuser**] *yolu*|Adına Caspol.exe çalışmakta olan bir kullanıcıya ait olmayan özel bir kullanıcı ilkesinin yönetilmesine olanak verir. İle özel kullanıcının güvenlik yapılandırma dosyasının konumunu belirtmelisiniz *yolu* bağımsız değişken.|  
|**-enterprise**<br /><br /> veya<br /><br /> **-en**|Bunu izleyen tüm seçeneklerin kuruluş düzeyinde ilkeye uygulanacağını belirtir. Kurumsal yönetici olmayan kullanıcılar kuruluş ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Kuruluş dışı senaryolarda bu ilke varsayılan olarak makine ve kullanıcı ilkesini engellemez.|  
|**-e**[**xecution**] {**üzerinde** &#124; **kapalı**}|Kod yürütülmeye başlamadan önce çalıştırmak için izni denetleyen mekanizmayı etkinleştirir veya devre dışı bırakır. **Not:**  Bu anahtarı kaldırılmıştır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Daha fazla bilgi için [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Aracın kendini kaldırma testini engeller ve ilkeyi kullanıcı tarafından belirtilen şekilde değiştirir. Normal olarak Caspol.exe, ilke değişikliklerinin Caspol.exe'nin düzgün çalışmasını önleyip önlemeyeceğini denetler; önleyecekse Caspol.exe ilke değişikliğini kaydetmez ve bir hata iletisi yazdırır. Bu caspol.exe'nin kendisinin çalışmasını engelliyor olsa bile ilkeyi değiştirmek için caspol.exe'yi zorlamak için kullanan **– force** seçeneği.|  
|**-h**[**elp**]|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
|**-l**[**ist**]|Belirtilen makine, kullanıcı, kuruluş veya tüm ilke düzeyleri için kod grubu hiyerarşisini ve izin kümelerini listeler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listdescription**<br /><br /> veya<br /><br /> **-ld**|Belirtilen ilke düzeyi için tüm kod grubu açıklamalarını listeler.|  
|**-listfulltrust**<br /><br /> veya<br /><br /> **-lf**|Belirtilen ilke düzeyi için tam güven derleme listesinin tüm içeriğini listeler.|  
|**-listgroups**<br /><br /> veya<br /><br /> **-lg**|Belirtilen ilke düzeyi veya tüm ilke düzeylerinin kod gruplarını görüntüler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listpset** veya **-lp**|Belirtilen ilke düzeyi veya tüm ilke düzeyleri için izin kümelerini görüntüler.|  
|**-m**[**; achine &**]|Bunu izleyen tüm seçeneklerin makine düzeyinde ilkeye uygulanacağını belirtir. Yönetici olmayan kullanıcılar makine ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Yöneticiler için **-makine** varsayılandır.|  
|**-polchgprompt** {**üzerinde** &#124; **kapalı**}<br /><br /> veya<br /><br /> **-pp** {**üzerinde** &#124; **kapalı**}|Caspol.exe ilke değişikliklerine neden olan bir seçenek kullanılarak her çalıştırıldığında komut istemini etkinleştirir veya devre dışı bırakır.|  
|**-quiet**<br /><br /> veya<br /><br /> **-q**|İlke değişikliklerine neden olan bir seçenek için normal olarak görüntülenen istemi geçici olarak devre dışı bırakır. Genel değişiklik istemi ayarı değişmez. Tüm Caspol.exe komutları için istemin devre dışı bırakılmasından kaçınmak üzere seçeneği yalnızca tek komut temelinde kullanın.|  
|**-r**[**ecover**]|Bir yedek dosyadan ilkeyi kurtarır. Bir ilke değişikliği her yapıldığında, Caspol.exe eski ilkeyi bir yedekleme dosyasına depolar.|  
|**-remfulltrust** *assembly_file*<br /><br /> veya<br /><br /> **-rf**  *assembly_file*|Bir derlemeyi ilke düzeyi tam güven listesinden kaldırır. Bu işlem, özel izin içeren bir izin kümesi ilke tarafından artık kullanılmıyorsa gerçekleştirilmelidir. Ancak, yalnızca derleme halen kullanılmakta olan herhangi bir özel izni uygulamıyorsa tam güven listesinden özel izin uygulayan bir derlemeyi kaldırmanız gerekir. Bir derlemeyi listeden kaldırdığınızda, bağımlı olduğu derlemeleri de kaldırmanız gerekir.|  
|**-remgroup** {*etiket &#124;adı*}<br /><br /> veya<br /><br /> **-rg** {l*abel &#124; adı*}|Etiketinin veya adının belirttiği kod grubunu kaldırır. Belirtilen kod grubunda alt kod grupları varsa, Caspol.exe tüm alt kod gruplarını da kaldırır.|  
|**-rempset** *pset_name*<br /><br /> veya<br /><br /> **-rp** *pset_name*|Belirtilen izin kümesini ilkeden kaldırır. *Pset_name* bağımsız değişkeni hangi izin kümesinin kaldırılacağını belirtir. Caspol.exe izin kümesini yalnızca herhangi bir kod grubu ile ilişkili değilse kaldırır. Varsayılan (yerleşik) izin kümeleri kaldırılamaz.|  
|**-reset**<br /><br /> veya<br /><br /> **-rs**|İlkeyi varsayılan durumuna geri döndürür ve diskte kalıcı kılar. Değiştirilen bir ilke onarılamayacak şekilde görünüyorsa ve siz de yükleme varsayılanları ile baştan başlamak istiyorsanız, bu yararlıdır. Varsayılan ilkeyi özel güvenlik yapılandırma dosyalarında yapılan değişiklikler için bir başlangıç noktası olarak kullanmak istediğinizde sıfırlama da kullanışlı olabilir. Daha fazla bilgi için [güvenlik yapılandırma dosyalarını el ile düzenleme](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> veya<br /><br /> **-rsld**|İlkeyi varsayılan durumun daha kısıtlayıcı bir sürümüne döndürür ve diskte kalıcı kılar; Önceki makine ilkesinin yedeğini oluşturur ve adlı bir dosyaya kalıcı `security.config.bac`.  İlke, koda hiçbir izin verir. kilitli ilke varsayılan ilkeye benzer `Local Intranet`, `Trusted Sites`, ve `Internet` bölgeleri ve karşılık gelen kod gruplarının hiç alt kod grubu vardır.|  
|**-resolvegroup** *assembly_file*<br /><br /> veya<br /><br /> **-rsg**  *assembly_file*|Kod gruplarını gösterir belirli bir derleme (*assembly_file*) ait. Varsayılan olarak bu seçenek, derlemenin ait olduğu makine, kullanıcı ve kuruluş ilkesi düzeylerini gösterir. Yalnızca tek bir ilke düzeyini görüntülemek için bu seçeneği ile birlikte kullanın **-makine**, **-kullanıcı**, veya **-enterprise** seçeneği.|  
|**-resolveperm** *assembly_file*<br /><br /> veya<br /><br /> **-rsp** *assembly_file*|Derlemenin çalışmasına izin verilmişse, güvenlik ilkesinin belirtilen (veya varsayılan) düzeyinin derlemeye verdiği tüm izinleri görüntüler. *Assembly_file* bağımsız değişkeni derlemeyi belirtir. Belirtirseniz **-tüm** seçeneği, Caspol.exe kullanıcı, makine ve kuruluş ilkesine göre derlemenin izinlerini hesaplar; Aksi takdirde varsayılan çalışma biçimi kuralları geçerlidir.|  
|**-s**[**ecurity**] {**üzerinde** &#124; **kapalı**}|Kod erişim güvenliğini açar veya kapatır. Belirtme **-s kapatma** seçeneği devre dışı bırakmaz rol tabanlı güvenlik. **Not:**  Bu anahtarı kaldırılmıştır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Daha fazla bilgi için [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md). **Dikkat:**  Kod erişim güvenliği devre dışı bırakıldığında, tüm kod erişim talepleri başarılı olur. Kod erişimi güvenliğini devre dışı bırakmak sistemi virüsler ve solucanlar gibi zararlı kodların saldırılarına açık hale getirir. Güvenliğin devre dışı bırakılması belli oranda performans artışı sağlayabilir ancak bu işlem yalnızca genel sistem güvenliğinin ihlal edilmemesine yardımcı olacak diğer güvenlik önlemleri alındığı zaman yapılmalıdır. Diğer güvenlik önlemlerine ilişkin örnekler arasında ortak ağ bağlantılarını kesme, bilgisayarları fiziksel olarak güvenlik altına alma vb. sayılabilir.|  
|**-u**[**ser**]|Bunu izleyen tüm seçeneklerin, adına Caspol.exe çalıştıran kullanıcı için kullanıcı düzeyi ilkesine uygulanacağını belirtir. Yönetici olmayan kullanıcılar için **-kullanıcı** varsayılandır.|  
|**-?**|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
  
 *Mship* bir kod grubu için üyelik koşulunu belirtir, bağımsız değişken ile kullanılabilir **- addgroup** ve **- chggroup** seçenekleri. Her *mship* bağımsız bir .NET Framework sınıfı uygulanır. Belirtmek için *mship,* aşağıdakilerden birini kullanın.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-allcode**|Tüm kodu belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>.|  
|**-appdir**|Uygulama dizini belirtir. Belirtirseniz **– appdir** üyelik koşulu olarak URL kanıtı o kodun uygulama dizini kanıt ile karşılaştırılır. Her iki kanıt değeri de aynıysa, bu üyelik koşulu gerçekleşmiş demektir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>.|  
|**-özel**  *xmlfile*|Özel üyelik koşulu ekler. Zorunlu *xmlfile* bağımsız değişkeni özel üyelik koşulu, XML serileştirme içeren .xml dosyasını belirtir.|  
|**-hash** *hashAlg* {**-hex** *hashValue* &#124; **-file** *assembly_file* }|Belirtilen derleme karmasına sahip kodu belirtir. Bir karmayı kod grubu üyelik koşulu olarak kullanmak için, karma değerini ya da derleme dosyasını belirtmelisiniz. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>.|  
|**-pub** { **-cert** *cert_file_name*&#124;<br /><br /> **-file** *signed_file_name* &#124; **-hex**  *hex_string* }|Belirtilen yazılım yayıncısına sahip kodu (bir sertifika dosyasıyla, bir dosyadaki imzayla veya bir X 509 sertifikasının onaltılı gösterimiyle sunulduğu şekilde) belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>.|  
|**-site** *Web sitesi*|Belirtilen kaynak siteyi içeren kodu belirtir. Örneğin:<br /><br /> `-site** www.proseware.com`<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>.|  
|**-strong - dosya** *file_name* {*adı* &#124; **- noname**} {*sürüm* &#124; **- noversion**}|Dosya adı, bir dize ve derleme sürümü olarak derleme adı tarafından atandığı gibi belirli bir tanımlayıcı ad biçiminde sahip kodu belirtir *ana*. *küçük*. *derleme*. *Düzeltme*. Örneğin:<br /><br /> **-strong - dosya** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>.|  
|**-url** *URL'si*|Belirtilen URL'den kaynaklanan kodu belirtir. URL gibi bir protokol içermelidir `http://` veya `ftp://`. Ayrıca, bir joker karakter (\*) belirli bir URL'den birden çok derleme belirtmek için kullanılabilir. **Not:**  Birden çok ad kullanarak bir URL tanımlanabileceğinden, bir üyelik koşulu olarak URL kullanmak kod kimliğini belirlemek için güvenli bir yol değildir. Mümkün olan yerlerde, bir tanımlayıcı ad üyelik koşulu, bir yayımcı üyelik koşulu veya karma üyelik koşulu kullanın. <br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>.|  
|**-Bölge** *zonename*|Belirtilen kaynak bölgeyi içeren kodu belirtir. *Zonename* bağımsız değişkeni aşağıdaki değerlerden biri olabilir: **Bilgisayarım**, **Intranet**, **güvenilen**, **Internet**, veya **güvenilmeyen**. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.ZoneMembershipCondition> sınıfı.|  
  
 *Bayrakları* kullanılabilir bağımsız değişken **– addgroup** ve **– chggroup** seçenekleri, aşağıdakilerden birini kullanarak belirtilir.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-Açıklama** "*açıklama*"|Birlikte kullanılırsa **– addgroup** seçeneğinde, eklenecek bir kod grubunun açıklamasını belirtir. Birlikte kullanılırsa **– chggroup** seçeneği, düzenlenecek bir kod grubunun açıklamasını belirtir. *Açıklama* bağımsız değişkeni çift tırnak içine alınmalıdır.|  
|**-özel** {**üzerinde**&#124;**kapalı**}|Ayarlandığında **üzerinde**, yalnızca kod grubu ile ilişkili izin kümesinin eklediğiniz veya değişiklik olarak kabul edilir, bazı kodlar kod grubunun üyelik koşulu uygun gösterir. Bu seçenek ayarlandığında **kapalı**, Caspol.exe ilke düzeyindeki tüm eşleşen kod gruplarını izin kümesini göz önünde bulundurur.|  
|**-levelfinal** {**üzerinde**&#124;**kapalı**}|Ayarlandığında **üzerinde**, içinde eklenen veya değişiklik yapılan kod grubunun bulunduğu düzeyin altındaki hiçbir ilke düzeyinin dikkate alınmayacağını belirtir. Bu seçenek genellikle makine ilkesi düzeyinde kullanılır. Örneğin, makine düzeyinde bir kod grubu için bu bayrağı ayarlarsanız ve bazı kodlar bu kod grubunun üyelik koşulu ile eşleşirse, Caspol.exe bu kod için kullanıcı düzeyi ilkesini hesaplamaz veya uygulamaz.|  
|**-ad** "*adı*"|Birlikte kullanılırsa **– addgroup** seçeneğinde, eklenecek bir kod grubunun betik adını belirtir. Birlikte kullanılırsa **- chggroup** seçeneği, düzenlenecek bir kod grubunun betik adını belirtir. *Adı* bağımsız değişkeni çift tırnak içine alınmalıdır. *Adı* bağımsız değişken bir sayı ile başlayamaz ve yalnızca A-Z, içerebilir 0-9 ve alt çizgi karakteri. Kod gruplarına başvuru yapılabilir bu *adı* yerine, sayısal etiketleri. *Adı* aynı zamanda betik için kullanımda da çok yararlıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik ilkesi üç ilke düzeyi kullanılarak ifade edilir: Makine ilkesi, kullanıcı ilkesi ve kuruluş ilkesi. Bir derlemenin aldığı izin kümesi, bu üç ilke düzeyi tarafından izin verilen izin kümelerinin kesişimi ile belirlenir. Her ilke düzey kod gruplarının hiyerarşik bir yapısı ile temsil edilir. Her kod grubunun bir üyelik koşulu vardır ve bu koşul hangi kodun o grubun üyesi olduğunu belirler. Adlandırılmış bir izin kümesi aynı zamanda her kod grubu ile ilişkilidir. Bu izin kümesi, çalışma zamanı tarafından, üyelik koşulunu karşılayan kodun sahip olmasına izin verilen izinleri belirtir. Bir kod grubu hiyerarşisi, ilişkili adlandırılmış izin kümeleriyle birlikte, güvenlik ilkesinin her düzeyini tanımlar ve korur. Kullanabileceğiniz **– kullanıcı**, **- customuser**, **– makine** ve **-enterprise** güvenlik ilkesinin düzeyini ayarlamak için Seçenekler.  
  
 Güvenlik İlkesi ve çalışma zamanının koda vereceği izinleri nasıl belirlediği hakkında daha fazla bilgi için bkz: [Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Kod Grupları ve İzin Kümelerine Başvurma  
 Bir hiyerarşideki kod gruplarına başvuru yapılmasını sağlamak için **-liste** seçeneği sayısal etiketleriyle birlikte kod gruplarının girintili bir listesini görüntüler (1, 1.1, 1.1.1 ve benzeri). Kod gruplarını hedefleyen diğer komut satırı işlemleri belirli kod gruplarına başvuru yapmak için de sayısal etiketleri kullanır.  
  
 Adlandırılmış izin kümelerine, adlarına göre başvuru yapılır. **– Liste** seçeneği ayarlar o ilkedeki adlandırılmış izin listesi tarafından izlenen kod gruplarının listesini görüntüler.  
  
## <a name="caspolexe-behavior"></a>Caspol.exe Davranışı  
 Dışındaki tüm seçenekleri **-s**[**ecurity**] {**üzerinde** &#124; **kapalı**} Caspol.exe yüklendiği .NET Framework sürümünü kullanın ile. Sürümüyle birlikte yüklenen caspol.exe'yi çalıştırırsanız *X* çalışma zamanını, değişiklikler yalnızca o sürüme uygulanır. Çalışma zamanının, diğer yan yana yüklemeleri varsa etkilenmez. Komut satırından, belirli çalışma zamanı sürümü dizininde olmaksızın Caspol.exe çalıştırırsanız, araç o yoldaki ilk çalışma zamanı sürümü dizininden (genellikle yüklü en son çalışma zamanı sürümü) yürütülür.  
  
 **-S**[**ecurity**] {**üzerinde** &#124; **kapalı**} seçenektir bilgisayar genelinde bir işlemdir. Kod erişim güvenliği devre dışı bırakmak bilgisayarda tüm kullanıcılar için ve yönetilen tüm kodlar için güvenlik kontrollerini sonlandırır. Yan yana .NET Framework sürümleri yüklüyse, bu komut bilgisayarda yüklü her sürüm için güvenliği kapatır. Ancak **-liste** seçeneği gösterir güvenlik kapalıdır, başka bir şey açıkça güvenlik devre dışı diğer kullanıcılar için gösterir.  
  
 Yönetici hakları olmayan bir kullanıcı caspol.exe'yi çalıştığında, tüm seçenekler kullanıcı düzeyi ilkesine sürece başvuran **– makine** seçeneği belirtildi. Bir yönetici caspol.exe'yi çalıştığında, tüm seçenekler makine ilkesine sürece başvuran **– kullanıcı** seçeneği belirtildi.  
  
 Caspol.exe eşdeğeri verilmelidir **her şeyi** işlevine izin kümesi. Araçta, Caspol.exe'in çalışması için gereken izinlerin verilmesini önleyecek biçimlerde ilke üzerinde değişiklik yapılmasını önleyen koruyucu bir mekanizma vardır. Bu tür değişiklikler yapmaya çalışırsanız, Caspol.exe istenen ilke değişikliğinin aracı kesintiye uğratacağını ve ilke değişikliğinin reddedildiğini size bildirir. Bu koruyucu mekanizmayı için belirli bir komut kullanarak kapatabilirsiniz **– force** seçeneği.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Güvenlik Yapılandırma Dosyalarını El İle Düzenleme  
 Üç güvenlik yapılandırması dosyası, Caspol.exe tarafından desteklenen üç ilke düzeyine karşılık gelir: Makine ilkesi için bir dosya, belirli bir kullanıcı ilkesi için bir dosya ve kuruluş ilkesi için bir dosya. Yalnızca makine, kullanıcı veya kuruluş ilkesi Caspol.exe kullanılarak değiştirildiğinde, bu dosyalar disk üzerinde oluşturulur. Kullanabileceğiniz **– reset** Caspol.exe gerekirse varsayılan güvenlik ilkesini diske kaydetmek için seçeneği.  
  
 Çoğu durumda, güvenlik yapılandırma dosyalarını el ile düzenlemek önerilmez. Ancak bu dosyalarda değişiklik yapılmasının gerekeceği bazı senaryolar da olabilir (örneğin, bir yönetici belirli bir kullanıcı için güvenlik yapılandırmasını düzenlemek isteyebilir).  
  
## <a name="examples"></a>Örnekler  
 **-addfulltrust**  
  
 Özel izin içeren bir izin kümesinin makine ilkesine eklendiğini varsayalım. Bu özel izin uygulanan `MyPerm.exe`, ve `MyPerm.exe` içindeki sınıflara başvurur `MyOther.exe`. İki derleme de tam güven derleme listesine eklenmelidir. Aşağıdaki komut ekler `MyPerm.exe` Makine ilkesi için tam güven listesine derleme.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Aşağıdaki komut ekler `MyOther.exe` Makine ilkesi için tam güven listesine derleme.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Aşağıdaki komut, makine ilkesi kod grubu hiyerarşisinin kök dizinine bir alt kod grubu ekler. Yeni kod grubu üyesi olan **Internet** bölge ve ilişkili olduğu **yürütme** izin kümesi.  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Aşağıdaki komut, paylaşıma izin veren bir alt kod grubu ekler \\\netserver\netshare yerel intranet izinleri.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Aşağıdaki komut ekler `Mypset` izin kümesini kullanıcı ilkesine.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Aşağıdaki komut değişiklikleri 1.2 izin kümesini kullanıcı ilkesine kod grubunun etiketini. için **yürütme** izin kümesi.  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Aşağıdaki komut değişiklikleri kod grubunun varsayılan ilkesindeki üyelik koşulunu 1.2.1 etiketi. ve ayarını değiştirir **özel** bayrağı. Üyelik koşulu kaynaklanan kod olacak şekilde tanımlanır **Internet** bölge ve **özel** bayrağı etkinleştirilir.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Aşağıdaki komutu adıyla değiştirir `Mypset` kümesi içinde bulunan izin `newpset.xml`. Geçerli sürümün, kod grubu hiyerarşisi tarafından kullanılan izin kümelerini değiştirmeyi desteklemediğini unutmayın.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Aşağıdaki komut kullanıcı ilkesinin kök kod grubunun'ilişkilendirilir (1 olarak etiketlenmiştir) neden **hiçbir şey** adlı izin kümesiyle. Bu Caspol.exe'nın çalışmasını engeller.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-recover**  
  
 Aşağıdaki komut, en son kaydedilen makine ilkesini kurtarır.  
  
```console  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Aşağıdaki komut 1.1 etiketli kod grubunu kaldırır. Bu kod grubunda herhangi bir alt kod grubu varsa, bu gruplar da silinir.  
  
```console  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Aşağıdaki komut kaldırır **yürütme** izin kümesini kullanıcı ilkesinden.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Aşağıdaki komut kaldırır `Mypset` kullanıcı ilkesi düzeyinden.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Aşağıdaki komut, makine ilkesinin tüm kod gruplarını gösterir `myassembly` ait.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Aşağıdaki komut, makine, kuruluş ve belirtilen özel kullanıcı ilkesinin tüm kod gruplarını gösterir `myassembly` ait.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Aşağıdaki komutu izinlerini hesaplar `testassembly` makine ve kullanıcı ilkesi düzeylerini temel alarak.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
