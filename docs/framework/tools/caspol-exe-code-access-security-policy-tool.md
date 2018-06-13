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
ms.openlocfilehash: f2306d51d88ab2d3b74ed6381a6de0acebf1e62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410104"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)
Kod Erişim Güvenliği (CAS) İlkesi aracı (Caspol.exe) kullanıcıların ve yöneticilerin güvenlik ilkesini makine ilkesi düzeyinde, kullanıcı ilkesi düzeyinde ve kuruluş ilkesi düzeyinde değiştirmelerini sağlar.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Caspol.exe sürece CAS ilkesini etkilemez [ \<legacyCasPolicy > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ayarlanır `true`. CasPol.exe tarafından gösterilen veya değiştirilen ayarlar yalnızca CAS ilkesini kullanmayı seçen uygulamaları etkiler. Daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  64 bit bilgisayarlarda güvenlik ilkesi 64-bit ve 32-bit sürümleri içerir. İlkenizdeki değişikliklerin 32-bit ve 64-bit sürümlerine uygulandığından emin olmak için Caspol.exe'nin 32-bit ve 64-bit sürümlerinin ikisini de çalıştırın.  
  
 Kod Erişimi Güvenlik İlkesi aracı, .NET Framework ve Visual Studio ile otomatik olarak yüklenir. Caspol.exe %windir%\Microsoft.NET\Framework içinde bulabilirsiniz\\*sürüm* 32 bit sistemler veya %windir%\Microsoft.NET\Framework64\\*sürüm* 64 bitlik sistemlerde. (Örneğin, %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe konumu, 64-bit sistemde .NET Framework 4 içindir.) Bilgisayarınızda .NET Framework'un birden çok sürümü yan yana çalışıyorsa, aracın birden çok sürümü yüklenebilir. Aracı yükleme dizininden çalıştırabilirsiniz. Ancak, kullanmanızı öneririz [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md), gerekli olmadığı, yükleme klasörüne gidin.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
caspol [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> veya<br /><br /> **-af** *assembly_file*|Özel güvenlik nesnesi (örneğin, özel bir izin veya özel üyelik koşulu) uygulayan bir derlemeyi belirli bir ilke düzeyi için tam güven derleme listesine ekler. *Assembly_file* bağımsız değişkeni eklemek için derlemeyi belirtir. Bu dosya imzalanmalıdır bir [güçlü ad](../../../docs/framework/app-domains/strong-named-assemblies.md). Kullanarak bir güçlü ad ile bir derlemeyi imzalayabilirsiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> İlkeye, özel izin içeren bir izin kümesi her eklendiğinde, özel izni uygulayan derleme o ilke düzeyi için tam güven listesine eklenmelidir. Bir güvenlik ilkesinde (makine ilkesi gibi) kullanılan özel güvenlik nesneleri (özel kod grupları veya üyelik koşulları gibi) uygulayan derlemeler her zaman tam güven derleme listesine eklenmelidir. **Dikkat:** diğer derlemelerden özel güvenlik nesnesi uygulama bütünleştirilmiş koduna başvuruyor, tam güven derleme listesine başvurulan derlemeleri eklemeniz gerekir. Visual Basic, C++ ve JScript kullanılarak oluşturulan özel güvenlik nesneleri sırasıyla Microsoft.VisualBasic.dll, Microsoft.VisualC.dll veya Microsoft.JScript.dll'ye başvuru yapar. Bu derlemeler varsayılan olarak tam güven derleme listesinde bulunmaz. Özel bir güvenlik nesnesi eklemeden önce uygun derlemeyi tam güven listesine eklemeniz gerekir. Bunun yapılmaması durumunda güvenlik sistemi çalışmaz ve tüm derlemelerin yüklenmesi başarısız olur. Bu durumda, Caspol.exe **-tüm - sıfırlama** seçeneği değil güvenlik onarın. Güvenliği onarmak için, özel güvenlik nesnesini kaldırmak üzere güvenlik dosyalarını el ile düzenlemeniz gerekir.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*bayrakları*]<br /><br /> veya<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*bayrakları*]|Kod grubu hiyerarşisine yeni bir kod grubu ekler. Ya da belirtebilirsiniz *parent_label* veya *parent_name*. *Parent_label* bağımsız değişkeni (örneğin, 1 etiket belirtir. veya 1.1.) eklenen kod grubunun üst kod grubudur. *Parent_name* bağımsız değişkeni eklenen kod grubunun üst kod grubun adını belirtir. Çünkü *parent_label* ve *parent_name* olabilir birbirinin yerine kullanılan Caspol.exe bunları ayırt etmenize kurabilmesi gerekir. Bu nedenle, *parent_name* bir rakamla başlayamaz. Ayrıca, *parent_name* yalnızca A-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Mship* bağımsız değişkeni için yeni kod grubunda üyelik koşulu belirtir. Daha fazla bilgi için tablosuna bakın *mship* bu bölümün sonraki kısımlarında bağımsız değişkenler.<br /><br /> *Pset_name* bağımsız değişkeni yeni kod grubuyla ilişkilendirilecek izin kümesi adıdır. Bir veya daha fazla de ayarlayabilirsiniz *bayrakları* yeni grup için. Tablonun daha fazla bilgi için bkz: *bayrakları* bu bölümün sonraki kısımlarında bağımsız değişkenler.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> veya<br /><br /> **-ap** {*adlı*_*psfile* &#124; *psfile* *pset_name*}|İlkeye yeni bir adlandırılmış izin kümesi ekler. İzin kümesi XML'de yazılmış ve bir .xml dosyasında depolanmış olmalıdır. XML dosyası iznin adını içeriyorsa ayarlamak, yalnızca bu dosyanın (*psfile*) belirtilir. XML dosyasını izin kümesi adı içermiyorsa, hem XML dosya adı belirtmeniz gerekir (*psfile*) ve izin kümesi adı (*pset_name*).<br /><br /> Bir izin kümesinde kullanılan tüm izinlerin genel derleme önbelleğinde bulunan derlemelerde tanımlanması gerektiğini unutmayın.|  
|**-a**[**üm**]|Bunu izleyen tüm seçeneklerin makineye, kullanıcıya ve kuruluş ilkelerine uygulanacağını belirtir. **-Tüm** seçenek her zaman şu anda oturum açmış kullanıcı ilkesi için başvuruyor. Bkz: **- customall** seçeneği geçerli kullanıcı dışındaki bir kullanıcının kullanıcı ilkesine bakın.|  
|**-chggroup** {*etiket &#124;adı*} {*mship* &#124; *pset_name*&#124;<br /><br /> *Bayrakları* `}`<br /><br /> veya<br /><br /> **-cg** {*etiket &#124;adı*} {*mship* &#124; *pset_name*&#124;<br /><br /> *Bayrakları* `}`|Bir kod grubun üyelik koşulu, izin kümesi veya ayarlarını değiştirir **özel**, **levelfinal**, **adı**, veya **açıklama**bayrakları. Ya da belirtebilirsiniz *etiket* veya *adı*. *Etiket* bağımsız değişkeni (örneğin, 1 etiket belirtir. veya 1.1.) kod grubudur. *Adı* bağımsız değişkeni değiştirmek için kod grubunun adını belirtir. Çünkü *etiket* ve *adı* olabilir birbirinin yerine kullanılan Caspol.exe bunları ayırt etmenize kurabilmesi gerekir. Bu nedenle, *adı* bir rakamla başlayamaz. Ayrıca, *adı* yalnızca A-Z, 0-9 ve alt çizgi karakterini içerebilir.<br /><br /> *Pset_name* bağımsız değişkeni kod grubuyla ilişkilendirilecek izni adını belirtir. Daha sonra bu bölümdeki tablolarda, bilgi bakın *mship* ve *bayrakları* bağımsız değişkenler.|  
|**-chgpset***psfile pset_name*<br /><br /> veya<br /><br /> **-TP** *psfile pset_name*|Adlandırılmış bir izin kümesini değiştirir. *Psfile* bağımsız değişkeni sağlayan yeni tanımı izin kümesi için; serileştirilmiş izin kümesi dosyası XML biçiminde değil. *Pset_name* bağımsız değişkeni değiştirmek istediğiniz izin kümesi adını belirtir.|  
|**-customall***yolu*<br /><br /> veya<br /><br /> **-ca***yolu* |Bunu izleyen tüm seçeneklerin makineye, kuruluşa ve belirtilen özel kullanıcı ilkelerine uygulanacağını belirtir. Özel kullanıcının güvenlik yapılandırma dosyası konumunu belirtmelisiniz *yolu* bağımsız değişkeni.|  
|**-cu**[**stomuser**] *yolu*|Adına Caspol.exe çalışmakta olan bir kullanıcıya ait olmayan özel bir kullanıcı ilkesinin yönetilmesine olanak verir. Özel kullanıcının güvenlik yapılandırma dosyası konumunu belirtmelisiniz *yolu* bağımsız değişkeni.|  
|**-enterprise**<br /><br /> veya<br /><br /> **-tr**|Bunu izleyen tüm seçeneklerin kuruluş düzeyinde ilkeye uygulanacağını belirtir. Kurumsal yönetici olmayan kullanıcılar kuruluş ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Kuruluş dışı senaryolarda bu ilke varsayılan olarak makine ve kullanıcı ilkesini engellemez.|  
|**-e**[**xecution**] {**üzerinde** &#124; **kapalı**}|Kod yürütülmeye başlamadan önce çalıştırmak için izni denetleyen mekanizmayı etkinleştirir veya devre dışı bırakır. **Not:** de bu anahtarı kaldırılmıştır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Aracın kendini kaldırma testini engeller ve ilkeyi kullanıcı tarafından belirtilen şekilde değiştirir. Normal olarak Caspol.exe, ilke değişikliklerinin Caspol.exe'nin düzgün çalışmasını önleyip önlemeyeceğini denetler; önleyecekse Caspol.exe ilke değişikliğini kaydetmez ve bir hata iletisi yazdırır. Caspol.exe bu Caspol.exe kendisini çalışmasını önler olsa bile ilke değişikliğini zorunlu kılmak için kullanın **– force** seçeneği.|  
|**-h**[**ardım**]|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
|**-l**[**ist**]|Belirtilen makine, kullanıcı, kuruluş veya tüm ilke düzeyleri için kod grubu hiyerarşisini ve izin kümelerini listeler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listdescription**<br /><br /> veya<br /><br /> **-ld**|Belirtilen ilke düzeyi için tüm kod grubu açıklamalarını listeler.|  
|**-listfulltrust**<br /><br /> veya<br /><br /> **-lf**|Belirtilen ilke düzeyi için tam güven derleme listesinin tüm içeriğini listeler.|  
|**-listgroups**<br /><br /> veya<br /><br /> **-lg**|Belirtilen ilke düzeyi veya tüm ilke düzeylerinin kod gruplarını görüntüler. Caspol.exe önce kod grubunun ilk etiket düzeyini, ardından adı (null değilse) görüntüler.|  
|**-listpset** veya **-lp**|Belirtilen ilke düzeyi veya tüm ilke düzeyleri için izin kümelerini görüntüler.|  
|**-m**[**akinesi**]|Bunu izleyen tüm seçeneklerin makine düzeyinde ilkeye uygulanacağını belirtir. Yönetici olmayan kullanıcılar makine ilkesini görüntüleyebilirler ancak onu değiştirmek için yeterli hakları yoktur. Yöneticiler, **-makine** varsayılandır.|  
|**-polchgprompt** {**üzerinde** &#124; **kapalı**}<br /><br /> veya<br /><br /> **-Gö** {**üzerinde** &#124; **kapalı**}|Caspol.exe ilke değişikliklerine neden olan bir seçenek kullanılarak her çalıştırıldığında komut istemini etkinleştirir veya devre dışı bırakır.|  
|**-quiet**<br /><br /> veya<br /><br /> **-q**|İlke değişikliklerine neden olan bir seçenek için normal olarak görüntülenen istemi geçici olarak devre dışı bırakır. Genel değişiklik istemi ayarı değişmez. Tüm Caspol.exe komutları için istemin devre dışı bırakılmasından kaçınmak üzere seçeneği yalnızca tek komut temelinde kullanın.|  
|**-r**[**ecover**]|Bir yedek dosyadan ilkeyi kurtarır. Bir ilke değişikliği her yapıldığında, Caspol.exe eski ilkeyi bir yedekleme dosyasına depolar.|  
|**-remfulltrust** *assembly_file*<br /><br /> veya<br /><br /> **-rf***assembly_file*|Bir derlemeyi ilke düzeyi tam güven listesinden kaldırır. Bu işlem, özel izin içeren bir izin kümesi ilke tarafından artık kullanılmıyorsa gerçekleştirilmelidir. Ancak, yalnızca derleme halen kullanılmakta olan herhangi bir özel izni uygulamıyorsa tam güven listesinden özel izin uygulayan bir derlemeyi kaldırmanız gerekir. Bir derlemeyi listeden kaldırdığınızda, bağımlı olduğu derlemeleri de kaldırmanız gerekir.|  
|**-remgroup** {*etiket &#124;adı*}<br /><br /> veya<br /><br /> **-rg** {l*abel &#124; adı*}|Etiketinin veya adının belirttiği kod grubunu kaldırır. Belirtilen kod grubunda alt kod grupları varsa, Caspol.exe tüm alt kod gruplarını da kaldırır.|  
|**-rempset** *pset_name*<br /><br /> veya<br /><br /> **-rp** *pset_name*|Belirtilen izin kümesini ilkeden kaldırır. *Pset_name* bağımsız değişkeni gösterir kaldırmak için hangi izni ayarlayın. Caspol.exe izin kümesini yalnızca herhangi bir kod grubu ile ilişkili değilse kaldırır. Varsayılan (yerleşik) izin kümeleri kaldırılamaz.|  
|**-Sıfırla**<br /><br /> veya<br /><br /> **-rs**|İlkeyi varsayılan durumuna geri döndürür ve diskte kalıcı kılar. Değiştirilen bir ilke onarılamayacak şekilde görünüyorsa ve siz de yükleme varsayılanları ile baştan başlamak istiyorsanız, bu yararlıdır. Varsayılan ilkeyi özel güvenlik yapılandırma dosyalarında yapılan değişiklikler için bir başlangıç noktası olarak kullanmak istediğinizde sıfırlama da kullanışlı olabilir. Daha fazla bilgi için bkz: [güvenlik yapılandırma dosyalarını el ile düzenleme](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> veya<br /><br /> **-rsld**|İlke varsayılan durumu daha kısıtlayıcı bir sürümünü döndürür ve diske devam ediyorsa; önceki bir makine İlkesi yedeğini oluşturur ve adlı bir dosyaya devam ediyorsa `security.config.bac`.  İlke koddan için hiçbir izin verir. Kilitli ilkesi varsayılan ilkesi benzerdir `Local Intranet`, `Trusted Sites`, ve `Internet` bölgeleri ve karşılık gelen kod gruplarına sahip alt kod grup yok.|  
|**-resolvegroup** *assembly_file*<br /><br /> veya<br /><br /> **-rsg***assembly_file*|Kod grupları gösteren belirli bir derleme (*assembly_file*) ait. Varsayılan olarak bu seçenek, derlemenin ait olduğu makine, kullanıcı ve kuruluş ilkesi düzeylerini gösterir. Yalnızca bir ilke düzeyini görüntülemek için bu seçeneği ile birlikte kullanmak **-makine**, **-kullanıcı**, veya **-enterprise** seçeneği.|  
|**-resolveperm** *assembly_file*<br /><br /> veya<br /><br /> **-rsp** *assembly_file*|Derlemenin çalışmasına izin verilmişse, güvenlik ilkesinin belirtilen (veya varsayılan) düzeyinin derlemeye verdiği tüm izinleri görüntüler. *Assembly_file* bağımsız değişkeni derleme belirtir. Belirtirseniz **-tüm** seçeneği Caspol.exe hesaplar kullanıcı, makine ve kurumsal ilkesini temel alarak derleme izinlerini; Aksi takdirde, varsayılan davranış kuralları geçerlidir.|  
|**-s**[**ik**] {**üzerinde** &#124; **kapalı**}|Kod erişim güvenliğini açar veya kapatır. Belirtme **-s kapalı** seçeneği devre dışı bırakmayın rol tabanlı güvenlik. **Not:** de bu anahtarı kaldırılmıştır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve sonraki sürümler. Daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md). **Dikkat:** kod erişim güvenliği devre dışı bırakıldığında, tüm kod erişim taleplerin başarılı. Kod erişimi güvenliğini devre dışı bırakmak sistemi virüsler ve solucanlar gibi zararlı kodların saldırılarına açık hale getirir. Güvenliğin devre dışı bırakılması belli oranda performans artışı sağlayabilir ancak bu işlem yalnızca genel sistem güvenliğinin ihlal edilmemesine yardımcı olacak diğer güvenlik önlemleri alındığı zaman yapılmalıdır. Diğer güvenlik önlemlerine ilişkin örnekler arasında ortak ağ bağlantılarını kesme, bilgisayarları fiziksel olarak güvenlik altına alma vb. sayılabilir.|  
|**-u**[**ser**]|Bunu izleyen tüm seçeneklerin, adına Caspol.exe çalıştıran kullanıcı için kullanıcı düzeyi ilkesine uygulanacağını belirtir. Yönetici olmayan kullanıcılar için **-kullanıcı** varsayılandır.|  
|**-?**|Caspol.exe için komut sözdizimini ve seçenekleri görüntüler.|  
  
 *Mship* kodu grup üyeliği koşulunu belirtir, bağımsız değişkeni ile kullanılabilir **- addgroup** ve **- chggroup** seçenekleri. Her *mship* bağımsız bir .NET Framework sınıf olarak uygulanır. Belirtmek için *mship,* aşağıdakilerden birini kullanın.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-allcode**|Tüm kodu belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.AllMembershipCondition>.|  
|**-appdir**|Uygulama dizini belirtir. Belirtirseniz **– appdir** üyelik koşulu kod URL kanıtı uygulama dizin kanıtı bu kodu ile karşılaştırılır. Her iki kanıt değeri de aynıysa, bu üyelik koşulu gerçekleşmiş demektir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition>.|  
|**-özel***xmldosyası* |Özel üyelik koşulu ekler. Zorunlu *xmldosyası* bağımsız değişken özel üyelik koşulu XML serileştirilmesi içeren .xml dosyasını belirtir.|  
|**-karma** *KarmaAlgoritma* {**-onaltılık** *hashValue* &#124; **-dosya** *assembly_file* }|Belirtilen derleme karmasına sahip kodu belirtir. Bir karmayı kod grubu üyelik koşulu olarak kullanmak için, karma değerini ya da derleme dosyasını belirtmelisiniz. Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.HashMembershipCondition>.|  
|**-pub** { **-cert** *cert_file_name*&#124;<br /><br /> **-Dosya** *signed_file_name* &#124; **-onaltılık***hex_string* }|Belirtilen yazılım yayıncısına sahip kodu (bir sertifika dosyasıyla, bir dosyadaki imzayla veya bir X 509 sertifikasının onaltılı gösterimiyle sunulduğu şekilde) belirtir. Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.PublisherMembershipCondition>.|  
|**-site** *Web sitesi*|Belirtilen kaynak siteyi içeren kodu belirtir. Örneğin:<br /><br /> **-site** www.proseware.com<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.SiteMembershipCondition>.|  
|**-strong - dosya** *dosya_adı* {*adı* &#124; **- noname**} {*sürüm* &#124; **- noversion**}|Dosya adı, derleme adı olarak bir dize ve derleme sürümü tarafından belirlenen olarak belirli bir tanımlayıcı adı biçiminde olan kod belirtir *ana*. *küçük*. *Yapı*. *Düzeltme*. Örneğin:<br /><br /> **-strong - dosya** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.StrongNameMembershipCondition>.|  
|**-url** *URL'si*|Belirtilen URL'den kaynaklanan kodu belirtir. URL'de http:// veya ftp:// gibi bir protokol bulunmalıdır. Ayrıca, bir joker karakter (\*) belirli bir URL birden çok derlemelerden belirtmek için kullanılır. **Not:** bir URL birden çok ad kullanılarak tanımlanabilir olduğundan, üyelik koşulu kod kimliğini onaylaması için güvenli bir şekilde olmadığı bir URL kullanarak. Mümkün olan yerlerde, bir tanımlayıcı ad üyelik koşulu, bir yayımcı üyelik koşulu veya karma üyelik koşulu kullanın. <br /><br /> Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.UrlMembershipCondition>.|  
|**-Bölge** *BölgeAdı*|Belirtilen kaynak bölgeyi içeren kodu belirtir. *BölgeAdı* bağımsız değişkeni aşağıdaki değerlerden biri olabilir: **Bilgisayarım**, **Intranet**, **güvenilen**, **Internet** , veya **güvenilmeyen**. Bu üyelik koşulu hakkında daha fazla bilgi için bkz: <xref:System.Security.Policy.ZoneMembershipCondition> sınıfı.|  
  
 *Bayrakları* ile kullanılan bağımsız değişkeni **– addgroup** ve **– chggroup** seçenekleri, aşağıdakilerden birini kullanarak belirtilir.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|**-Açıklama "** *açıklama* **"**|İle kullandıysanız **– addgroup** seçeneği, eklemek için bir kod grup için açıklamayı belirtir. İle kullandıysanız **– chggroup** seçeneği, düzenlemek bir kod grubu için açıklamayı belirtir. *Açıklama* bağımsız değişkeni çift tırnak içine alınmalıdır.|  
|**-özel** {**üzerinde**&#124;**kapalı**}|Ayarlandığında **üzerinde**, yalnızca kod grupla ilişkili izin kümesi eklemekte olduğunuz veya değiştirme olarak kabul biraz kod kodu grup üyeliği koşulunu ne zaman uygun olduğunu gösterir. Bu seçenek ayarlandığında **kapalı**, Caspol.exe, ilke düzeyindeki tüm eşleşen kod gruplarının izin kümeleri göz önünde bulundurur.|  
|**-levelfinal** {**üzerinde**&#124;**kapalı**}|Ayarlandığında **üzerinde**, hiçbir ilke düzey eklenen veya değiştirilen kod grubunun oluştuğu altındaki değerlendirilir gösterir. Bu seçenek genellikle makine ilkesi düzeyinde kullanılır. Örneğin, makine düzeyinde bir kod grubu için bu bayrağı ayarlarsanız ve bazı kodlar bu kod grubunun üyelik koşulu ile eşleşirse, Caspol.exe bu kod için kullanıcı düzeyi ilkesini hesaplamaz veya uygulamaz.|  
|**-adı "** *adı* **"**|İle kullandıysanız **– addgroup** seçeneği, komut dosyası eklemek için bir kod grup adını belirtir. İle kullandıysanız **- chggroup** seçeneği, bir kod grubu düzenlemek komut dosyası adını belirtir. *Adı* bağımsız değişkeni çift tırnak içine alınmalıdır. *Adı* bağımsız değişkeni bir rakamla başlayamaz ve yalnızca A-Z, içerebilir 0-9 ve alt çizgi karakteri. Kod grupları başvurulabilir için bunu *adı* yerine kendi sayısal etiketine göre. *Adı* ayrıca komut dosyası oluşturma amacıyla çok yararlı olur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik ilkesi üç ilke düzeyi kullanılarak ifade edilir: Makine ilkesi, kullanıcı ilkesi ve kuruluş ilkesi. Bir derlemenin aldığı izin kümesi, bu üç ilke düzeyi tarafından izin verilen izin kümelerinin kesişimi ile belirlenir. Her ilke düzey kod gruplarının hiyerarşik bir yapısı ile temsil edilir. Her kod grubunun bir üyelik koşulu vardır ve bu koşul hangi kodun o grubun üyesi olduğunu belirler. Adlandırılmış bir izin kümesi aynı zamanda her kod grubu ile ilişkilidir. Bu izin kümesi, çalışma zamanı tarafından, üyelik koşulunu karşılayan kodun sahip olmasına izin verilen izinleri belirtir. Bir kod grubu hiyerarşisi, ilişkili adlandırılmış izin kümeleriyle birlikte, güvenlik ilkesinin her düzeyini tanımlar ve korur. Kullanabileceğiniz **– kullanıcı**, **- customuser**, **– makine** ve **-enterprise** güvenlik ilkesi düzeyini ayarlamak için Seçenekler.  
  
 Güvenlik İlkesi ve çalışma zamanı kodu hangi izinleri nasıl belirlediğini hakkında daha fazla bilgi için bkz: [Güvenlik İlkesi Yönetimi](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Kod Grupları ve İzin Kümelerine Başvurma  
 Kod grupları bir hiyerarşide başvurular kolaylaştırmak için **-liste** seçeneği kod grupları sayısal etiketlerine birlikte girintili listesini görüntüler (1, 1.1, 1.1.1 ve benzeri). Kod gruplarını hedefleyen diğer komut satırı işlemleri belirli kod gruplarına başvuru yapmak için de sayısal etiketleri kullanır.  
  
 Adlandırılmış izin kümelerine, adlarına göre başvuru yapılır. **– Listesi** seçeneği adlandırılmış izin listesi tarafından izlenen kod gruplarının listesini bu ilkedeki kullanılabilir ayarlar görüntüler.  
  
## <a name="caspolexe-behavior"></a>Caspol.exe Davranışı  
 Dışındaki tüm seçenekleri **-s**[**ik**] {**üzerinde** &#124; **kapalı**} Caspol.exe yüklendiğini .NET Framework sürümü kullanın ile. Sürümü ile yüklü Caspol.exe çalıştırırsanız *X* çalışma zamanı, değişiklikler yalnızca bu sürümü için uygulanır. Çalışma zamanının, diğer yan yana yüklemeleri varsa etkilenmez. Komut satırından, belirli çalışma zamanı sürümü dizininde olmaksızın Caspol.exe çalıştırırsanız, araç o yoldaki ilk çalışma zamanı sürümü dizininden (genellikle yüklü en son çalışma zamanı sürümü) yürütülür.  
  
 **-S**[**ik**] {**üzerinde** &#124; **kapalı**} bilgisayar genelinde işlemi bir seçenektir. Kod erişim güvenliği devre dışı bırakmak bilgisayarda tüm kullanıcılar için ve yönetilen tüm kodlar için güvenlik kontrollerini sonlandırır. Yan yana .NET Framework sürümleri yüklüyse, bu komut bilgisayarda yüklü her sürüm için güvenliği kapatır. Ancak **-liste** seçenek gösterir güvenlik kapalıdır, hiçbir şey açıkça güvenlik devre dışı diğer kullanıcılar için gösterir.  
  
 Yönetici hakları olmayan bir kullanıcı Caspol.exe çalıştığında, tüm seçenekleri kullanıcı düzeyi ilkesi sürece başvuran **– makine** seçeneği belirtildi. Bir yönetici Caspol.exe çalıştığında, tüm seçenekleri için makine ilkesini sürece başvurmak **– kullanıcı** seçeneği belirtildi.  
  
 Caspol.exe denk verilmelidir **her şeyi** işlevine izin kümesi. Araçta, Caspol.exe'in çalışması için gereken izinlerin verilmesini önleyecek biçimlerde ilke üzerinde değişiklik yapılmasını önleyen koruyucu bir mekanizma vardır. Bu tür değişiklikler yapmaya çalışırsanız, Caspol.exe istenen ilke değişikliğinin aracı kesintiye uğratacağını ve ilke değişikliğinin reddedildiğini size bildirir. Bu koruyucu mekanizması için belirli bir komut kullanarak kapatabilirsiniz **– force** seçeneği.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Güvenlik Yapılandırma Dosyalarını El İle Düzenleme  
 Üç güvenlik yapılandırması dosyası, Caspol.exe tarafından desteklenen üç ilke düzeyine karşılık gelir: Makine ilkesi için bir dosya, belirli bir kullanıcı ilkesi için bir dosya ve kuruluş ilkesi için bir dosya. Yalnızca makine, kullanıcı veya kuruluş ilkesi Caspol.exe kullanılarak değiştirildiğinde, bu dosyalar disk üzerinde oluşturulur. Kullanabileceğiniz **– sıfırlama** gerekirse varsayılan güvenlik ilkesi diske kaydetmek için Caspol.exe seçeneği.  
  
 Çoğu durumda, güvenlik yapılandırma dosyalarını el ile düzenlemek önerilmez. Ancak bu dosyalarda değişiklik yapılmasının gerekeceği bazı senaryolar da olabilir (örneğin, bir yönetici belirli bir kullanıcı için güvenlik yapılandırmasını düzenlemek isteyebilir).  
  
## <a name="examples"></a>Örnekler  
 **-addfulltrust**  
  
 Özel izin içeren bir izin kümesinin makine ilkesine eklendiğini varsayalım. Bu özel izin uygulanan `MyPerm.exe`, ve `MyPerm.exe` başvuruyor sınıflarda `MyOther.exe`. İki derleme de tam güven derleme listesine eklenmelidir. Aşağıdaki komut ekler `MyPerm.exe` Makine ilkesi için tam güven listesine derleme.  
  
```  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Aşağıdaki komut ekler `MyOther.exe` Makine ilkesi için tam güven listesine derleme.  
  
```  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Aşağıdaki komut, makine ilkesi kod grubu hiyerarşisinin kök dizinine bir alt kod grubu ekler. Yeni kod grubunun üyesi olan **Internet** bölge ve ilişkili olduğu **yürütme** izin kümesi.  
  
```  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Aşağıdaki komut paylaşımı sunan bir alt kod grubu ekler \\\netserver\netshare yerel intranet izinleri.  
  
```  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Aşağıdaki komut ekler `Mypset` izni kullanıcı ilkesi ayarlandı.  
  
```  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Aşağıdaki komut değişiklikleri kod grubunun kullanıcı ilkesine izni 1.2 etiketli. için **yürütme** izin kümesi.  
  
```  
caspol -user -chggroup 1.2. Execution  
```  
  
 Aşağıdaki komut değişiklikleri varsayılan ilke kodu grubunun üyeliği koşul 1.2.1 Etiketli. ve değişiklikleri ayarını **özel** bayrağı. Üyelik koşulu kaynaklandığı kod olarak tanımlanan **Internet** bölge ve **özel** bayrağı geçti.  
  
```  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Aşağıdaki komut adıyla ayarlanmış izni değiştirir `Mypset` içinde kapsanan ayarlama izni `newpset.xml`. Geçerli sürümün, kod grubu hiyerarşisi tarafından kullanılan izin kümelerini değiştirmeyi desteklemediğini unutmayın.  
  
```  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Aşağıdaki komut kullanıcı ilkesinin kök kod grubu'ilişkilendirilecek (etiketli 1) neden olan **hiçbir şey** izin kümesi adı. Bu Caspol.exe'nın çalışmasını engeller.  
  
```  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-Kurtarma**  
  
 Aşağıdaki komut, en son kaydedilen makine ilkesini kurtarır.  
  
```  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Aşağıdaki komut 1.1 etiketli kod grubunu kaldırır. Bu kod grubunda herhangi bir alt kod grubu varsa, bu gruplar da silinir.  
  
```  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Aşağıdaki komut kaldırır **yürütme** izni kullanıcı ilkesinden ayarlandı.  
  
```  
caspol -user -rempset Execution  
```  
  
 Aşağıdaki komut kaldırır `Mypset` kullanıcı ilkesi düzeyinden.  
  
```  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Makine ilkesi tüm kod grupları aşağıdaki komut gösterir `myassembly` ait.  
  
```  
caspol -machine -resolvegroup myassembly  
```  
  
 Makine, kurumsal ve belirtilen özel kullanıcı ilkesi tüm kod grupları aşağıdaki komut gösterir `myassembly` ait.  
  
```  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Aşağıdaki komutu izinlerini hesaplar `testassembly` makine ve kullanıcı ilkesi düzeylerine göre.  
  
```  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
