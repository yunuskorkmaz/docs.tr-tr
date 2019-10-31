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
ms.openlocfilehash: b5b5e1872af89417fbad6e95b7a8bee5e9b68925
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129899"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)
Kod Erişim Güvenliği (CAS) İlkesi aracı (Caspol.exe) kullanıcıların ve yöneticilerin güvenlik ilkesini makine ilkesi düzeyinde, kullanıcı ilkesi düzeyinde ve kuruluş ilkesi düzeyinde değiştirmelerini sağlar.  
  
> [!IMPORTANT]
> .NET Framework 4 ' te başlayarak, [\<legacyCasPolicy > öğesi](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) `true`olarak ayarlanmadığı takdirde Caspol. exe CAS ilkesini etkilemez. CasPol.exe tarafından gösterilen veya değiştirilen ayarlar yalnızca CAS ilkesini kullanmayı seçen uygulamaları etkiler. Daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md).  
  
> [!NOTE]
> 64 bit bilgisayarlarda güvenlik ilkesi 64-bit ve 32-bit sürümleri içerir. İlkenizdeki değişikliklerin 32-bit ve 64-bit sürümlerine uygulandığından emin olmak için Caspol.exe'nin 32-bit ve 64-bit sürümlerinin ikisini de çalıştırın.  
  
 Kod Erişimi Güvenlik İlkesi aracı, .NET Framework ve Visual Studio ile otomatik olarak yüklenir. Caspol. exe ' yi, 32 bitlik sistemlerde%windir%\Microsoft.NET\Framework\\*sürümünde* veya 64 bit sistemlerde%windir%\Microsoft.NET\Framework64\\*sürümünde* bulabilirsiniz. (Örneğin, konum 64 bitlik bir sistemde .NET Framework 4 için%windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe.) Bilgisayarınız .NET Framework birden çok sürümünü yan yana çalıştırıyorsa aracın birden çok sürümü yüklü olabilir. Aracı yükleme dizininden çalıştırabilirsiniz. Ancak, yükleme klasörüne gitmenizi gerektirmeyen [komut istemlerini](developer-command-prompt-for-vs.md)kullanmanızı öneririz.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-addfulltrust** *Assembly_file*<br /><br /> veya<br /><br /> **-AF** *Assembly_file*|Özel güvenlik nesnesi (örneğin, özel bir izin veya özel üyelik koşulu) uygulayan bir derlemeyi belirli bir ilke düzeyi için tam güven derleme listesine ekler. *Assembly_file* bağımsız değişkeni eklenecek derlemeyi belirtir. Bu dosyanın bir [tanımlayıcı ad](../../standard/assembly/strong-named.md)ile imzalanması gerekir. Tanımlayıcı [Ad Aracı (sn. exe)](sn-exe-strong-name-tool.md)kullanarak, bir derlemeyi tanımlayıcı ad ile imzalayabilirsiniz.<br /><br /> İlkeye, özel izin içeren bir izin kümesi her eklendiğinde, özel izni uygulayan derleme o ilke düzeyi için tam güven listesine eklenmelidir. Bir güvenlik ilkesinde (makine ilkesi gibi) kullanılan özel güvenlik nesneleri (özel kod grupları veya üyelik koşulları gibi) uygulayan derlemeler her zaman tam güven derleme listesine eklenmelidir. **Dikkat:**  Özel güvenlik nesnesini uygulayan derleme diğer derlemelere başvuruyorsa, önce başvurulan derlemeleri tam güven derleme listesine eklemeniz gerekir. Visual Basic, C++ ve JScript kullanılarak oluşturulan özel güvenlik nesneleri sırasıyla Microsoft.VisualBasic.dll, Microsoft.VisualC.dll veya Microsoft.JScript.dll'ye başvuru yapar. Bu derlemeler varsayılan olarak tam güven derleme listesinde bulunmaz. Özel bir güvenlik nesnesi eklemeden önce uygun derlemeyi tam güven listesine eklemeniz gerekir. Bunun yapılmaması durumunda güvenlik sistemi çalışmaz ve tüm derlemelerin yüklenmesi başarısız olur. Bu durumda, Caspol. exe **-All-Reset** seçeneği güvenliği onarmaz. Güvenliği onarmak için, özel güvenlik nesnesini kaldırmak üzere güvenlik dosyalarını el ile düzenlemeniz gerekir.|  
|**-addgroup** {*parent_label &#124; parent_name*} *msevkiyat Pset_name* [*Flags*]<br /><br /> veya<br /><br /> **-AG** {*parent_label &#124; parent_name*} *msevkiyat Pset_name* [*Flags*]|Kod grubu hiyerarşisine yeni bir kod grubu ekler. *Parent_label* veya *parent_name*seçeneklerinden birini belirtebilirsiniz. *Parent_label* bağımsız değişkeni etiketi belirtir (örneğin, 1. veya 1,1.) eklenen kod grubunun üst öğesi olan kod grubu. *Parent_name* bağımsız değişkeni, eklenmekte olan kod grubunun üst öğesi olan kod grubunun adını belirtir. *Parent_label* ve *parent_name* birbirinin yerine kullanılabileceği için, Caspol. exe ile aralarında ayrım yapabilmelidir. Bu nedenle, *parent_name* bir sayıyla başlayamaz. Ayrıca, *parent_name* yalnızca A-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Msevkiyat* bağımsız değişkeni, yeni kod grubu için üyelik koşulunu belirtir. Daha fazla bilgi için bu bölümün ilerleyen kısımlarında yer alan *mgönderim* bağımsız değişkenlerinin tablosuna bakın.<br /><br /> *Pset_name* bağımsız değişkeni, yeni kod grubuyla ilişkilendirilecek izin kümesinin adıdır. Yeni grup için bir veya daha fazla *bayrak* de ayarlayabilirsiniz. Daha fazla bilgi için bu bölümün ilerleyen kısımlarında bulunan *Flags* bağımsız değişkenlerinin tablosuna bakın.|  
|**-addpset** {*psfile* &#124; *psfile* p*SET_NAME*}<br /><br /> veya<br /><br /> **-AP** {*adlandırılmış*_*psfile* &#124; *psfile* *Pset_name*}|İlkeye yeni bir adlandırılmış izin kümesi ekler. İzin kümesi XML'de yazılmış ve bir .xml dosyasında depolanmış olmalıdır. XML dosyası izin kümesinin adını içeriyorsa, yalnızca bu dosya (*psfile*) belirtilir. XML dosyası izin kümesi adını içermiyorsa, hem XML dosya adını (*psfile*) hem de izin kümesi adını (*Pset_name*) belirtmeniz gerekir.<br /><br /> Bir izin kümesinde kullanılan tüm izinlerin genel derleme önbelleğinde bulunan derlemelerde tanımlanması gerektiğini unutmayın.|  
|**-a**[**ll**]|Bunu izleyen tüm seçeneklerin makineye, kullanıcıya ve kuruluş ilkelerine uygulanacağını belirtir. **-All** seçeneği her zaman şu anda oturum açmış olan kullanıcının ilkesine başvurur. Geçerli Kullanıcı dışında bir kullanıcının Kullanıcı ilkesine başvurmak için **-customall** seçeneğine bakın.|  
|**-chggroup** {*etiket &#124;adı*} {*msevkiyat* &#124; *Pset_name*&#124;<br /><br /> *bayraklar* `}`<br /><br /> veya<br /><br /> **-CG** {*etiket &#124;adı*} {*msevk* &#124; *Pset_name*&#124;<br /><br /> *bayraklar* `}`|Bir kod grubunun üyelik koşulunu, izin kümesini veya **dışlamalı**, **LevelFinal**, **Name**ya da **Description** bayraklarının ayarlarını değiştirir. *Etiketi* ya da *adı*belirtebilirsiniz. *Etiket* bağımsız değişkeni etiketi belirtir (örneğin, 1. veya 1,1.) bir kod grubu. *Name* bağımsız değişkeni, değiştirilecek kod grubunun adını belirtir. *Etiket* ve *ad* birbirinin yerine kullanılabildiğinden, Caspol. exe bunları aralarında ayırt edebilmelidir. Bu nedenle, *ad* bir sayıyla başlayamaz. Ayrıca, *ad* yalnızca a-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Pset_name* bağımsız değişkeni, kod grubuyla ilişkilendirilecek izin kümesi adını belirtir. *Msevkıyat* ve *bayraklar* bağımsız değişkenleri hakkında bilgi için bu bölümün ilerleyen kısımlarında yer alan tablolara bakın.|  
|**-chgpset**  *psfile Pset_name*<br /><br /> veya<br /><br /> **-CP** *psfile Pset_name*|Adlandırılmış bir izin kümesini değiştirir. *Psfile* bağımsız değişkeni, izin kümesi için yeni tanımı sağlar; XML biçiminde serileştirilmiş bir izin kümesi dosyasıdır. *Pset_name* bağımsız değişkeni, değiştirmek istediğiniz izin kümesinin adını belirtir.|  
|**-customall**  *yolu*<br /><br /> veya<br /><br /> **-CA**  *yolu*|Bunu izleyen tüm seçeneklerin makineye, kuruluşa ve belirtilen özel kullanıcı ilkelerine uygulanacağını belirtir. Özel kullanıcının güvenlik yapılandırma dosyasının konumunu *yol* bağımsız değişkeniyle belirtmeniz gerekir.|  
|**-cu**[**stomuser**] *yolu*|Adına Caspol.exe çalışmakta olan bir kullanıcıya ait olmayan özel bir kullanıcı ilkesinin yönetilmesine olanak verir. Özel kullanıcının güvenlik yapılandırma dosyasının konumunu *yol* bağımsız değişkeniyle belirtmeniz gerekir.|  
|**-kuruluş**<br /><br /> veya<br /><br /> **-En**|Bunu izleyen tüm seçeneklerin kuruluş düzeyinde ilkeye uygulanacağını belirtir. Kurumsal yönetici olmayan kullanıcılar kuruluş ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Kuruluş dışı senaryolarda bu ilke varsayılan olarak makine ve kullanıcı ilkesini engellemez.|  
|**-e**[**xecution**] {**on** &#124; **off**}|Kod yürütülmeye başlamadan önce çalıştırmak için izni denetleyen mekanizmayı etkinleştirir veya devre dışı bırakır. **Note:**  Bu anahtar .NET Framework 4 ve sonraki sürümlerinde kaldırılır. Daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md).|  
|**-f**[**Orce**]|Aracın kendini kaldırma testini engeller ve ilkeyi kullanıcı tarafından belirtilen şekilde değiştirir. Normal olarak Caspol.exe, ilke değişikliklerinin Caspol.exe'nin düzgün çalışmasını önleyip önlemeyeceğini denetler; önleyecekse Caspol.exe ilke değişikliğini kaydetmez ve bir hata iletisi yazdırır. Caspol. exe ' nin kendi çalışmasını önlüyor olsa bile ilkeyi değiştirmek için Caspol. exe ' yi zorlamak için **– zorlama** seçeneğini kullanın.|  
|**-h**[**ELP**]|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
|**-l**[**ist**]|Belirtilen makine, kullanıcı, kuruluş veya tüm ilke düzeyleri için kod grubu hiyerarşisini ve izin kümelerini listeler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listdescription**<br /><br /> veya<br /><br /> **-ld**|Belirtilen ilke düzeyi için tüm kod grubu açıklamalarını listeler.|  
|**-listfulltrust**<br /><br /> veya<br /><br /> **-LF**|Belirtilen ilke düzeyi için tam güven derleme listesinin tüm içeriğini listeler.|  
|**-ListGroups**<br /><br /> veya<br /><br /> **-LG**|Belirtilen ilke düzeyi veya tüm ilke düzeylerinin kod gruplarını görüntüler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listpset** veya **-LP**|Belirtilen ilke düzeyi veya tüm ilke düzeyleri için izin kümelerini görüntüler.|  
|**-d**[**achine**]|Bunu izleyen tüm seçeneklerin makine düzeyinde ilkeye uygulanacağını belirtir. Yönetici olmayan kullanıcılar makine ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Yöneticiler için **-makine** varsayılandır.|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> veya<br /><br /> **-PP** {**on** &#124; **off**}|Caspol.exe ilke değişikliklerine neden olan bir seçenek kullanılarak her çalıştırıldığında komut istemini etkinleştirir veya devre dışı bırakır.|  
|**-quiet**<br /><br /> veya<br /><br /> **-q**|İlke değişikliklerine neden olan bir seçenek için normal olarak görüntülenen istemi geçici olarak devre dışı bırakır. Genel değişiklik istemi ayarı değişmez. Tüm Caspol.exe komutları için istemin devre dışı bırakılmasından kaçınmak üzere seçeneği yalnızca tek komut temelinde kullanın.|  
|**-r**[**eCover**]|Bir yedek dosyadan ilkeyi kurtarır. Bir ilke değişikliği her yapıldığında, Caspol.exe eski ilkeyi bir yedekleme dosyasına depolar.|  
|**-remfulltrust** *Assembly_file*<br /><br /> veya<br /><br /> **-RF**  *Assembly_file*|Bir derlemeyi ilke düzeyi tam güven listesinden kaldırır. Bu işlem, özel izin içeren bir izin kümesi ilke tarafından artık kullanılmıyorsa gerçekleştirilmelidir. Ancak, yalnızca derleme halen kullanılmakta olan herhangi bir özel izni uygulamıyorsa tam güven listesinden özel izin uygulayan bir derlemeyi kaldırmanız gerekir. Bir derlemeyi listeden kaldırdığınızda, bağımlı olduğu derlemeleri de kaldırmanız gerekir.|  
|**-remgroup** {*etiket &#124;adı*}<br /><br /> veya<br /><br /> **-RG** {l*Abel &#124; Name*}|Etiketinin veya adının belirttiği kod grubunu kaldırır. Belirtilen kod grubunda alt kod grupları varsa, Caspol.exe tüm alt kod gruplarını da kaldırır.|  
|**-rempset** *Pset_name*<br /><br /> veya<br /><br /> **-RP** *Pset_name*|Belirtilen izin kümesini ilkeden kaldırır. *Pset_name* bağımsız değişkeni, hangi iznin kaldırılacağını belirtir. Caspol.exe izin kümesini yalnızca herhangi bir kod grubu ile ilişkili değilse kaldırır. Varsayılan (yerleşik) izin kümeleri kaldırılamaz.|  
|**-Sıfırla**<br /><br /> veya<br /><br /> **-RS**|İlkeyi varsayılan durumuna geri döndürür ve diskte kalıcı kılar. Değiştirilen bir ilke onarılamayacak şekilde görünüyorsa ve siz de yükleme varsayılanları ile baştan başlamak istiyorsanız, bu yararlıdır. Varsayılan ilkeyi özel güvenlik yapılandırma dosyalarında yapılan değişiklikler için bir başlangıç noktası olarak kullanmak istediğinizde sıfırlama da kullanışlı olabilir. Daha fazla bilgi için, [güvenlik yapılandırma dosyalarını el Ile düzenlemeyle](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1)ilgili bölümüne bakın.|  
|**-resetlockdown**<br /><br /> veya<br /><br /> **-rsld**|İlkeyi varsayılan durumun daha kısıtlayıcı bir sürümüne döndürür ve diski diske devam ettirir; önceki makine ilkesinin bir yedeğini oluşturur ve `security.config.bac`adlı bir dosyaya devam ettirir.  Kilitli ilke, ilkenin `Local Intranet`, `Trusted Sites`ve `Internet` bölgelerinden kod için izin vermediği ve karşılık gelen kod gruplarının hiç alt kod grubu olmadığı durumlar dışında varsayılan ilkeye benzer.|  
|**-resolvegroup** *Assembly_file*<br /><br /> veya<br /><br /> **-RSG**  *Assembly_file*|Belirli bir derlemenin (*Assembly_file*) ait olduğu kod gruplarını gösterir. Varsayılan olarak bu seçenek, derlemenin ait olduğu makine, kullanıcı ve kuruluş ilkesi düzeylerini gösterir. Yalnızca bir ilke düzeyini görüntülemek için, bu seçeneği **-Machine**, **-User**veya **-Enterprise** seçeneğiyle kullanın.|  
|**-resolveizin** *Assembly_file*<br /><br /> veya<br /><br /> **-RSP** *Assembly_file*|Derlemenin çalışmasına izin verilmişse, güvenlik ilkesinin belirtilen (veya varsayılan) düzeyinin derlemeye verdiği tüm izinleri görüntüler. *Assembly_file* bağımsız değişkeni derlemeyi belirtir. **-All** seçeneğini belirtirseniz, Caspol. exe, Kullanıcı, makine ve kurumsal ilkeye göre derlemenin izinlerini hesaplar; Aksi takdirde, varsayılan davranış kuralları uygulanır.|  
|**-s**[**ecurity & lt**] {**on** &#124; **off**}|Kod erişim güvenliğini açar veya kapatır. **-S kapalı** seçeneğinin belirtilmesi rol tabanlı güvenliği devre dışı bırakır. **Note:**  Bu anahtar .NET Framework 4 ve sonraki sürümlerinde kaldırılır. Daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md). **Dikkat:**  Kod erişimi güvenliği devre dışı bırakıldığında, tüm kod erişimi istekleri başarılı olur. Kod erişimi güvenliğini devre dışı bırakmak sistemi virüsler ve solucanlar gibi zararlı kodların saldırılarına açık hale getirir. Güvenliğin devre dışı bırakılması belli oranda performans artışı sağlayabilir ancak bu işlem yalnızca genel sistem güvenliğinin ihlal edilmemesine yardımcı olacak diğer güvenlik önlemleri alındığı zaman yapılmalıdır. Diğer güvenlik önlemlerine ilişkin örnekler arasında ortak ağ bağlantılarını kesme, bilgisayarları fiziksel olarak güvenlik altına alma vb. sayılabilir.|  
|**-u**[**ser**]|Bunu izleyen tüm seçeneklerin, adına Caspol.exe çalıştıran kullanıcı için kullanıcı düzeyi ilkesine uygulanacağını belirtir. Yönetici olmayan kullanıcılar için **-Kullanıcı** varsayılandır.|  
|**-?**|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Bir kod grubu için üyelik koşulunu belirten *msevk* bağımsız değişkeni **-addgroup** ve **-chggroup** seçenekleriyle kullanılabilir. Her *msevkıyat* bağımsız değişkeni bir .NET Framework sınıfı olarak uygulanır. *Msevkiyat* belirtmek için aşağıdakilerden birini kullanın.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-allcode**|Tüm kodu belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>.|  
|**-Appdir**|Uygulama dizini belirtir. Üyelik koşulu olarak **– Appdir** belirtirseniz, kodun URL kanıtı bu kodun uygulama dizini kanıtını ile karşılaştırılır. Her iki kanıt değeri de aynıysa, bu üyelik koşulu gerçekleşmiş demektir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>.|  
|**-özel**  *xmlfile*|Özel üyelik koşulu ekler. Zorunlu *xmlfile* bağımsız değişkeni, özel ÜYELIK koşulunun XML serileştirmesini içeren. xml dosyasını belirtir.|  
|**-hash** *HashAlg* { **-onaltılı** *diyez değeri* &#124; **-File** *Assembly_file* }|Belirtilen derleme karmasına sahip kodu belirtir. Bir karmayı kod grubu üyelik koşulu olarak kullanmak için, karma değerini ya da derleme dosyasını belirtmelisiniz. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>.|  
|**-pub** { **-CERT** *cert_file_name*&#124;<br /><br /> **-File** *signed_file_name* &#124; **-onaltılı**  *hex_string* }|Belirtilen yazılım yayıncısına sahip kodu (bir sertifika dosyasıyla, bir dosyadaki imzayla veya bir X 509 sertifikasının onaltılı gösterimiyle sunulduğu şekilde) belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>.|  
|**-site** *Web sitesi*|Belirtilen kaynak siteyi içeren kodu belirtir. Örneğin:<br /><br /> `-site** www.proseware.com`<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>.|  
|**-strong-file** *dosya_adı* {*Name* &#124; **-noname**} {*Sürüm* &#124; **-noversion**}|Dosya adı, derleme adı ve *birincil*biçimdeki derleme sürümü ile belirlenen belirli bir tanımlayıcı ada sahip kodu belirtir. *küçük*. *oluşturun*. *Düzeltme*. Örneğin:<br /><br /> **-strong-file** MyAssembly. exe MyAssembly 1.2.3.4<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>.|  
|**-URL** *URL 'si*|Belirtilen URL'den kaynaklanan kodu belirtir. URL, `http://` veya `ftp://`gibi bir protokol içermelidir. Ayrıca, belirli bir URL 'den birden fazla derlemeyi belirtmek için bir joker karakter (\*) kullanılabilir. **Note:**  Bir URL birden çok ad kullanılarak belirlenebildiğinden, üyelik koşulu olarak bir URL kullanılması kodun kimliğini belirlemek için güvenli bir yol değildir. Mümkün olan yerlerde, bir tanımlayıcı ad üyelik koşulu, bir yayımcı üyelik koşulu veya karma üyelik koşulu kullanın. <br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz. <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>.|  
|**-Zone** *BölgeAdı*|Belirtilen kaynak bölgeyi içeren kodu belirtir. *BölgeAdı* bağımsız değişkeni şu değerlerden biri olabilir: **Bilgisayarım**, **Intranet**, **Güvenilen**, **Internet**veya **Güvenilmeyen**. Bu üyelik koşulu hakkında daha fazla bilgi için <xref:System.Security.Policy.ZoneMembershipCondition> sınıfına bakın.|  
  
 **– Addgroup** ve **– chggroup** seçenekleriyle kullanılabilecek *Flags* bağımsız değişkeni, aşağıdakilerden biri kullanılarak belirtilir.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-Açıklama** "*Açıklama*"|**– Addgroup** seçeneğiyle birlikte kullanılırsa, eklenecek bir kod grubunun açıklamasını belirtir. **– Chggroup** seçeneğiyle birlikte kullanılırsa, düzenlenecek bir kod grubunun açıklamasını belirtir. *Açıklama* bağımsız değişkeni çift tırnak içine alınmalıdır.|  
|**-dışlamalı** {**on**&#124;**off**}|**Açık**olarak ayarlandığında, yalnızca eklediğiniz veya değiştirdiğiniz kod grubuyla ilişkili izin kümesinin, kod grubunun üyelik koşuluna uygun olduğu durumlarda dikkate alındığını gösterir. Bu seçenek **off**olarak ayarlandığında, Caspol. exe ilke düzeyindeki tüm eşleşen kod gruplarının izin kümelerini dikkate alır.|  
|**-LevelFinal** {**on**&#124;**off**}|**Açık**olarak ayarlandığında, eklenen veya değiştirilen kod grubunun gerçekleştiği düzeyin altında hiçbir ilke düzeyinin kabul edileceğini gösterir. Bu seçenek genellikle makine ilkesi düzeyinde kullanılır. Örneğin, makine düzeyinde bir kod grubu için bu bayrağı ayarlarsanız ve bazı kodlar bu kod grubunun üyelik koşulu ile eşleşirse, Caspol.exe bu kod için kullanıcı düzeyi ilkesini hesaplamaz veya uygulamaz.|  
|**-ad** "*ad*"|**– Addgroup** seçeneğiyle birlikte kullanılırsa, eklenecek bir kod grubunun betik adını belirtir. **-Chggroup** seçeneğiyle birlikte kullanılırsa, düzenlenecek bir kod grubunun betik adını belirtir. *Ad* bağımsız değişkeni çift tırnak içine alınmalıdır. *Ad* bağımsız değişkeni bir sayıyla başlayamaz ve yalnızca a-Z, 0-9 ve alt çizgi karakterini içerebilir. Kod gruplarına, sayısal etiketleri yerine bu *ad* tarafından başvurulabilir. *Ad* , komut dosyası amaçları için de oldukça kullanışlıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik ilkesi üç ilke düzeyi kullanılarak ifade edilir: Makine ilkesi, kullanıcı ilkesi ve kuruluş ilkesi. Bir derlemenin aldığı izin kümesi, bu üç ilke düzeyi tarafından izin verilen izin kümelerinin kesişimi ile belirlenir. Her ilke düzey kod gruplarının hiyerarşik bir yapısı ile temsil edilir. Her kod grubunun bir üyelik koşulu vardır ve bu koşul hangi kodun o grubun üyesi olduğunu belirler. Adlandırılmış bir izin kümesi aynı zamanda her kod grubu ile ilişkilidir. Bu izin kümesi, çalışma zamanı tarafından, üyelik koşulunu karşılayan kodun sahip olmasına izin verilen izinleri belirtir. Bir kod grubu hiyerarşisi, ilişkili adlandırılmış izin kümeleriyle birlikte, güvenlik ilkesinin her düzeyini tanımlar ve korur. Güvenlik ilkesi düzeyini ayarlamak için **– User**, **-customuser**, **– Machine** ve **-Enterprise** seçeneklerini kullanabilirsiniz.  
  
 Güvenlik ilkesi ve çalışma zamanının hangi izinlerin koda verileceğini belirleme hakkında daha fazla bilgi için bkz. [Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Kod Grupları ve İzin Kümelerine Başvurma  
 Bir hiyerarşideki kod gruplarının başvurularını kolaylaştırmak için, **-list** seçeneği, sayısal etiketleriyle birlikte (1, 1,1, 1.1.1, vb.) bir dizi kod grubunun girintili listesini görüntüler. Kod gruplarını hedefleyen diğer komut satırı işlemleri belirli kod gruplarına başvuru yapmak için de sayısal etiketleri kullanır.  
  
 Adlandırılmış izin kümelerine, adlarına göre başvuru yapılır. **– List** seçeneği, kod gruplarının listesini ve ardından bu ilkede bulunan adlandırılmış izin kümelerinin bir listesini görüntüler.  
  
## <a name="caspolexe-behavior"></a>Caspol.exe Davranışı  
 **-S**[**ecurity & lt**] {**on** &#124; **off**} dışındaki tüm seçenekler, Caspol. exe ' nin yüklü olduğu .NET Framework sürümünü kullanır. Çalışma zamanının *X* sürümü Ile yüklenmiş Caspol. exe ' yi çalıştırırsanız, değişiklikler yalnızca bu sürüm için geçerlidir. Çalışma zamanının, diğer yan yana yüklemeleri varsa etkilenmez. Komut satırından, belirli çalışma zamanı sürümü dizininde olmaksızın Caspol.exe çalıştırırsanız, araç o yoldaki ilk çalışma zamanı sürümü dizininden (genellikle yüklü en son çalışma zamanı sürümü) yürütülür.  
  
 **-S**[**ecurity & lt**] {**on** &#124; **off**} seçeneği, bilgisayar genelindeki bir işlemdir. Kod erişim güvenliği devre dışı bırakmak bilgisayarda tüm kullanıcılar için ve yönetilen tüm kodlar için güvenlik kontrollerini sonlandırır. Yan yana .NET Framework sürümleri yüklüyse, bu komut bilgisayarda yüklü her sürüm için güvenliği kapatır. **-List** seçeneği güvenliğin kapalı olduğunu gösterir, ancak başka hiçbir şey güvenliğin kapatılmış olduğu diğer kullanıcılara açık bir şekilde değildir.  
  
 Yönetici haklarına sahip olmayan bir Kullanıcı Caspol. exe ' yi çalıştırdığında, **– Machine** seçeneği belirtilmediği takdirde tüm seçenekler Kullanıcı düzeyi ilkesine başvurur. Bir yönetici Caspol. exe ' yi çalıştırdığında, **– User** seçeneği belirtilmediği takdirde tüm seçenekler makine ilkesine başvurur.  
  
 Caspol. exe ' ye **her şey** izin kümesi işlevinin eşdeğeri verilmelidir. Araçta, Caspol.exe'in çalışması için gereken izinlerin verilmesini önleyecek biçimlerde ilke üzerinde değişiklik yapılmasını önleyen koruyucu bir mekanizma vardır. Bu tür değişiklikler yapmaya çalışırsanız, Caspol.exe istenen ilke değişikliğinin aracı kesintiye uğratacağını ve ilke değişikliğinin reddedildiğini size bildirir. Bu koruyucu mekanizmayı, **– zorlama** seçeneğini kullanarak belirli bir komut için kapatabilirsiniz.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Güvenlik Yapılandırma Dosyalarını El İle Düzenleme  
 Üç güvenlik yapılandırması dosyası, Caspol.exe tarafından desteklenen üç ilke düzeyine karşılık gelir: Makine ilkesi için bir dosya, belirli bir kullanıcı ilkesi için bir dosya ve kuruluş ilkesi için bir dosya. Yalnızca makine, kullanıcı veya kuruluş ilkesi Caspol.exe kullanılarak değiştirildiğinde, bu dosyalar disk üzerinde oluşturulur. Gerekirse, varsayılan güvenlik ilkesini diske kaydetmek için Caspol. exe ' deki **– Reset** seçeneğini kullanabilirsiniz.  
  
 Çoğu durumda, güvenlik yapılandırma dosyalarını el ile düzenlemek önerilmez. Ancak bu dosyalarda değişiklik yapılmasının gerekeceği bazı senaryolar da olabilir (örneğin, bir yönetici belirli bir kullanıcı için güvenlik yapılandırmasını düzenlemek isteyebilir).  
  
## <a name="examples"></a>Örnekler  
 **-addfulltrust**  
  
 Özel izin içeren bir izin kümesinin makine ilkesine eklendiğini varsayalım. Bu özel izin `MyPerm.exe`uygulanır ve `MyOther.exe``MyPerm.exe` sınıflarına başvurur. İki derleme de tam güven derleme listesine eklenmelidir. Aşağıdaki komut, `MyPerm.exe` derlemesini makine ilkesi için tam güven listesine ekler.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Aşağıdaki komut, `MyOther.exe` derlemesini makine ilkesi için tam güven listesine ekler.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Aşağıdaki komut, makine ilkesi kod grubu hiyerarşisinin kök dizinine bir alt kod grubu ekler. Yeni kod grubu, **Internet** bölgesinin bir üyesidir ve **yürütme** izin kümesi ile ilişkilendirilir.  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Aşağıdaki komut, \netserver\netshare yerel intranet izinleri \\paylaşıma veren bir alt kod grubu ekler.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Aşağıdaki komut, `Mypset` izin kümesini Kullanıcı ilkesine ekler.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Aşağıdaki komut, 1,2 olarak etiketlenmiş kod grubunun kullanıcı ilkesindeki izin kümesini değiştirir. **yürütme** izin kümesine.  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Aşağıdaki komut, 1.2.1 etiketli kod grubunun varsayılan ilkesindeki üyelik koşulunu değiştirir. ve **dışlamalı** bayrak ayarını değiştirir. Üyelik koşulu, **Internet** bölgesinden kaynaklanan ve **dışlamalı** bayrak açık olan kod olacak şekilde tanımlanır.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Aşağıdaki komut, ad `Mypset` olan izin kümesini `newpset.xml`bulunan izin kümesi olarak değiştirir. Geçerli sürümün, kod grubu hiyerarşisi tarafından kullanılan izin kümelerini değiştirmeyi desteklemediğini unutmayın.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-zorla**  
  
 Aşağıdaki komut, Kullanıcı ilkesinin kök kod grubunun (1 etiketli), **hiçbir şey** adlı izin kümesiyle ilişkilendirilmesine neden olur. Bu Caspol.exe'nın çalışmasını engeller.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-kurtar**  
  
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
  
 Aşağıdaki komut, Kullanıcı ilkesinden **yürütme** izin kümesini kaldırır.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Aşağıdaki komut, `Mypset` Kullanıcı ilkesi düzeyinden kaldırır.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Aşağıdaki komut, `myassembly` ait olduğu makine ilkesinin tüm kod gruplarını gösterir.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Aşağıdaki komut, `myassembly` ait olduğu makinenin, kuruluşun ve belirtilen özel kullanıcı ilkesinin tüm kod gruplarını gösterir.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveizin**  
  
 Aşağıdaki komut, makine ve Kullanıcı ilke düzeylerine göre `testassembly` izinlerini hesaplar.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
