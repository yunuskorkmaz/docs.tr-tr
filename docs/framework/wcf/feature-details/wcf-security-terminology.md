---
title: "WCF Güvenlik Terimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 386e58c5b04ed82f9ee42c7f04eacd4610c2a598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-security-terminology"></a>WCF Güvenlik Terimleri
Bazı güvenlik ele alırken kullanılan terminolojiyi bilinmiyor olabilir. Bu konu, bazı güvenlik koşulları kısa açıklamaları sağlar, ancak her öğe için kapsamlı belgeler sağlamak üzere tasarlanmamıştır.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]içinde kullanılan terimleri [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] belgelerine bakın [temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 erişim denetimi listesi (ACL)  
 Bir nesne için geçerli bir güvenlik korumaları listesi. (Bir nesne bir dosya, işlem, olay veya başka bir güvenlik açıklayıcısı sahip herhangi bir şey olabilir.) ACL içindeki bir erişim denetim girdisi (ACE) giriştir. ACL'ler iki tür vardır: isteğe bağlı ve sistem.  
  
 kimlik doğrulama  
 Kullanıcı, bilgisayar, hizmet veya işlem ne iddia ettiği doğrulama işlemi.  
  
 yetkilendirme  
 Erişim ve kaynak haklarını denetleme eylemi. Örneğin, bir grubun üyesi bir dosyayı okumaya izin vererek, ancak yalnızca dosyayı değiştirmek için başka bir grup üyeleri izin verme.  
  
 Sertifika yetkilisinin (CA)  
 Sunucuları ve bu sertifikaları isteyen istemcilerin sunucu ve istemci kimlik doğrulama sertifikaları veren CA'yı tanımlar. Dijital imzalar kullanılan ortak bir anahtar içerdiğinden, bu da olarak adlandırılır bir *imza sertifikası*. CA bir kök yetkilisi ise, CA sertifikasını için olarak adlandırılabilir bir *kök sertifika*. Bazen olarak bilinen bir *site sertifikası*.  
  
 CA hiyerarşisi  
 CA hiyerarşisi birden çok CA içerir. Böylece her CA hiyerarşisi daha yüksek düzeyde başka bir CA tarafından hiyerarşinin en üst kadar olarak da bilinen sertifikalı düzenlenmiş *kök yetkilisi*, ulaşıldı.  
  
 sertifika  
 Bir varlık ve bu nedenle bu iki parça bilgi birbirine bağlayan varlığın ortak anahtarı hakkında bilgi içeren bir dijital olarak imzalanmış ifade. Bir sertifika yetkilisi varlık kimin olduğu yazacaktır olduğu doğrulandıktan sonra tarafından güvenilen bir kuruluş (veya varlık) adı verilen bir sertifika yetkilisi, verilir.  
  
 Sertifikaları farklı veri türlerini içerebilir. Örneğin, bir X.509 sertifikası sertifika, sertifika, sertifika, ad ve ortak anahtar sertifikası isteme varlığın sertifikayı veren CA'ın adını imzalamak için kullanılan algoritma seri numarası biçimi içerir ve CA'ın imza.  
  
 Sertifika deposu  
 Genellikle, kalıcı bir depolama burada sertifikalar, sertifika iptal listeleri (CRL'ler) ve sertifika güven listelerini (CTL) depolanır. Ancak, oluşturmak ve kalıcı depolama alanına konması gerekmez sertifikalar ile çalışırken, bir sertifika deposu yalnızca bellekte açmak için mümkündür.  
  
 Talepleri  
 Bilgi gönderenin kimliğini oluşturmak için kullanılan başka bir varlıktan geçirildi. Örneğin, bir kullanıcı adı ve parola belirteci veya bir X.509 sertifikası.  
  
 İstemci sertifikası  
 Bir Web tarayıcısı bir Web sunucusunda kimlik doğrulaması gibi istemci kimlik doğrulaması için kullanılan bir sertifikaya başvurur. Bir Web tarayıcı istemci güvenli bir Web sunucusuna erişmeye çalıştığında, istemci sertifikasını istemcinin kimliğini doğrulamak izin vermek için sunucusuna gönderir.  
  
 kimlik bilgileri  
 Daha önce kimlik doğrulaması, bir parola veya bir Kerberos protokolü anahtarı gibi kendi kimliğini oluşturmak için bir güvenlik sorumlusu kullanan oturum açma verileri. Kimlik bilgileri, kaynaklara erişimi denetlemek için kullanılır.  
  
 Sindirilmiş veri  
 Bir veri içerik türü ortak anahtar şifreleme standardı tarafından (PKCS) verileri ve içeriği ileti karmasını (Özet) herhangi bir türde oluşur #7 tanımlı.  
  
 dijital imza  
 Gönderenin kimliğini gönderilen bilgilerin bağlar verileri. Dijital imza herhangi bir iletisi, dosya veya diğer dijital olarak kodlanmış bilgi ile birlikte veya ayrı olarak iletilebilir. Dijital imzalar genel anahtar ortamlarında kullanılır ve kimlik doğrulaması ve bütünlük hizmetleri sağlar.  
  
 encoding  
 Veri bitleri akışa kapatma işlemi. Kodlama verileri olanları sıfırlar ve bir akışa dönüştürür seri hale getirme işlemi parçasıdır.  
  
 Exchange anahtar çifti  
 Böylece bunlar güvenle depolanabilir ve diğer kullanıcılarla değiştirilen oturum anahtarları şifrelemek için kullanılan ortak/özel anahtar çifti.  
  
 hash  
 Bir sabit boyutlu sayısal rasgele bir veri miktarı matematiksel bir işlev (bkz. karma algoritması) uygulanarak alınan değer. Verileri genellikle olarak bilinen rastgele verileri içeren bir *nonce*. Hem hizmet hem de istemci sonuç karmaşıklığını artırmak için exchange nonce öğelerinin katkıda. Sonuç olarak da bilinen olan bir *ileti özeti*. Parola şifreli olsa bile bir karma değer gönderme bir parola gibi hassas verileri göndermekten daha güvenlidir. Alındığında, bir karma doğrulanabilir böylece karma göndereni ve alıcısı karma algoritması ve nonce öğelerinin kabul etmelisiniz.  
  
 karma algoritması  
 Bir ileti veya oturum anahtarı gibi veriler parçasının karma değeri üretmek için kullanılan bir algoritma. Tipik karma algoritmalarını MD2, MD4, MD5 ve SHA-1 içerir.  
  
 Kerberos protokolü  
 İstemcilerin ağ kimlik doğrulama hizmeti ile nasıl etkileşim kuracağını tanımlar protokolü. İstemcileri biletleri Kerberos Anahtar Dağıtım Merkezi (KDC) alanından elde ve bağlantıları oluşturulduğunda bunların sunucuları bu raporları sunar. Kerberos biletleri istemcinin ağ kimlik bilgileri temsil eder.  
  
 Yerel güvenlik yetkilisi (LSA)  
 Kimliğini doğrular ve yerel sistem açın kullanıcılar oturum korumalı bir alt. LSA ayrıca yönleri hakkında bilgi tüm yerel güvenlik topluca sistem yerel güvenlik ilkesi olarak bilinen bir sistemde korur.  
  
 Anlaşma  
 Bir uygulama katmanı Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) ve diğer SSP arasında görevi gören bir güvenlik desteği sağlayıcısı (SSP). Bir uygulama bir ağda oturum açmak için SSPI içine çağırdığında isteğini işlemek için bir SSP belirtebilirsiniz. Uygulama belirtiyorsa `Negotiate`, `Negotiate` isteği çözümler ve müşteri yapılandırılmış güvenlik ilkesini temel alarak isteği işlemek için en iyi SSP'yi seçer.  
  
 nonce  
 "" Yeniden yürütme saldırılarını üstesinden gelmek için kullanılan rastgele oluşturulmuş bir değeri.  
  
 inkar edilemez  
 Bu nedenle sorumluluk reddedecek şekilde girişiminde herhangi bir kullanıcı tarafından irrefutably countering belirli eylemleri gerçekleştiren kullanıcıları tanımlamak için yeteneği. Örneğin, bir dosya silindiğinde bir sistem bir kullanıcı kimliği oturum açabilir.  
  
 Ortak anahtar şifreleme standardı (PKCS)  
 Ortak anahtar şifrelemesini dağıtımını hızlandırmak için güvenli sistemleri dünya çapında geliştiriciler ile işbirliği içinde RSA Data Security, Inc. tarafından üretilen belirtimleri.  
  
 PKCS #7  
 Şifreleme iletisi söz dizimi standardı. Veri hangi şifreleme uygulanabilir, dijital imzalar ve şifreleme gibi genel söz dizimi. Ayrıca, sertifika veya sertifika iptal listeleri ve iletiye zaman damgaları gibi diğer ileti öznitelikleri yayınlamak için sözdizimi da sağlar.  
  
 düz metin  
 Şifreli bir ileti. Düz metin iletileri bazen denir *doğrulamaya* iletileri.  
  
 ayrıcalık  
 Sisteminin kapatılmasını, aygıt sürücülerini yükleme veya sistem saatinin değiştirilmesi gibi çeşitli sistem güvenlikle ilgili işlemler gerçekleştirme hakkı bir kullanıcının. Bir kullanıcının erişim belirtecini tutun kullanıcı veya kullanıcı grupları ayrıcalıkları listesini içerir.  
  
 Özel anahtar  
 Bir ortak anahtar algoritması kullanılan bir anahtar çifti gizli yarısı. Özel anahtarları, genellikle bir simetrik oturum anahtarı şifreleme, dijital olarak imzalamak bir ileti veya karşılık gelen ortak anahtar ile şifrelenmiş bir iletinin şifresini çözmek için kullanılır. Ayrıca bkz. "ortak anahtarı."  
  
 process  
 Uygulamanın altında çalıştığı güvenlik bağlamı. Genellikle, izinleri ve ayrıcalıklarına sahip olan kullanıcının verilen bir işlem altında çalışan tüm uygulamaları almak için güvenlik bağlamı bir kullanıcı ile ilişkilidir.  
  
 Ortak/özel anahtar çifti  
 Ortak anahtar şifrelemesi için kullanılan şifreleme anahtarları kümesi. Her bir kullanıcı için bir şifreleme hizmeti sağlayıcısı (CSP) genellikle iki ortak/özel anahtar çiftlerini korur: exchange anahtar çifti ve dijital imza anahtar çifti. Her iki anahtar çiftleri oturumdan oturuma saklanır.  
  
 Ortak anahtar  
 Bir oturum anahtarı ya da bir dijital imza çözme genellikle kullanılan bir şifreleme anahtarı. Ortak anahtar, yalnızca ilgili özel anahtara sahip kişi iletinin şifresini çözebilir güvence altına almak, bir iletiyi şifrelemek için de kullanılabilir.  
  
 Ortak anahtar şifrelemesi  
 Anahtarlar, verileri şifrelemek için bir anahtar ve başka bir anahtar çifti verilerin şifresini çözmek için kullandığı şifreleme. Buna karşılık, aynı simetrik şifreleme algoritmaları, şifreleme ve şifre çözme için anahtar. Uygulamada, ortak anahtar şifrelemesini genellikle bir simetrik şifreleme algoritması kullanır oturum anahtarını korumak için kullanılır. Bu durumda, ortak anahtar oturum anahtarı şifrelemek için kullanılan hangi sırayla bazı verileri şifrelemek için kullanılan ve özel anahtar, şifre çözme için kullanılır. Oturum anahtarları korumaya ek olarak, ortak anahtar şifrelemesini ayrıca dijital olarak iletiye (özel anahtarı kullanarak) oturum açın ve (genel anahtarını kullanarak) imzayı doğrulamak için kullanılabilir.  
  
 Ortak anahtar altyapısı (PKI)  
 Oluşturma, dağıtma ve ortak anahtar uygulamaları yönetmek için tümleşik bir dizi hizmet ve Yönetimsel Araçlar sağlayan bir altyapı.  
  
 geri çevirme  
 Bir kullanıcı yanlışlıkla gerçekleştirilen diğer taraflar sırasında bir eylem reddetme olanağı aksi kanıtlamak olamaz. Örneğin, kimin bir dosyayı siler ve kimlerin bunu bitti başarıyla reddedebilirsiniz kullanıcı.  
  
 kök yetkilisi  
 CA hiyerarşisi üstündeki CA. Kök yetkilisi hiyerarşisi ileri düzeyde CA'larda onaylar.  
  
 Güvenli Karma algoritması (SHA)  
 Bir ileti özeti üretir bir karma algoritması. SHA, diğer yerler yanı sıra dijital imza standart (DSS) dijital imza algoritması (DSA) ile kullanılır. SHA dört çeşitleri vardır: SHA-1, SHA-256, SHA-384 ve SHA-512. SHA-1 160 bitlik ileti özeti üretir. 512 bit ileti özetleyen, sırasıyla ve SHA-256, SHA-384 ve SHA-512 256 bit, 384 bit oluşturur. SHA Ulusal Standartlar ve Enstitüsü Technology (NIST) tarafından ve Ulusal Güvenlik Teşkilatı (NSA) tarafından geliştirilmiştir.  
  
 Güvenli Yuva Katmanı (SSL)  
 Genel ve gizli anahtar teknolojisini kullanan güvenli ağ iletişimi için protokol.  
  
 güvenlik bağlamı  
 Şu anda etkin olan kuralları ve güvenlik öznitelikleri. Örneğin, bilgisayarda oturum açmış geçerli kullanıcı veya akıllı kart kullanıcı tarafından girilen kişisel kimlik numarası. SSPI için bir güvenlik bağlamı bir oturum anahtarı veya oturum süresi boyunca belirtisi gibi bir bağlantı için ilgili güvenlik verileri içeren bir donuk veri yapısıdır.  
  
 güvenlik sorumlusu  
 Güvenlik sistemi tarafından tanınan bir varlık. Asıl adlar otonom işlemlerin yanı sıra İnsan kullanıcılar içerebilir.  
  
 Güvenlik Desteği Sağlayıcısı (SSP)  
 Bir veya daha fazla güvenlik paketleri uygulamaları için kullanılabilir hale getirerek SSPI uygulayan bir dinamik bağlantı kitaplığı (DLL). Her güvenlik paketi, bir uygulamanın SSPI işlev çağrılarını ve gerçek güvenlik modelinin işlevleri arasındaki eşlemeleri sağlar. Güvenlik paketleri Kerberos kimlik doğrulaması ve Microsoft LAN Yöneticisi'ni (LanMan) gibi güvenlik protokollerini destekler.  
  
 Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI)  
 Microsoft Uzaktan yordam çağrısı (RPC) ve Windows gibi güvenlik sağlayıcıları gibi aktarım düzeyinde uygulamalar arasında ortak bir arabirim güvenlik dağıtılmış. SSPI bir aktarım uygulamanın kimliği doğrulanmış bir bağlantı elde etmek için çeşitli güvenlik sağlayıcılardan biri çağırmasına izin verir. Bu çağrı güvenlik protokolün ayrıntıları kapsamlı bilgi gerektirmez.  
  
 Güvenlik belirteci hizmeti  
 Hizmetleri vermek ve özel güvenlik belirteçlerinde (verilen belirteçler) multiservice senaryo yönetmek için tasarlanmıştır. Özel belirteçler genellikle özel bir kimlik bilgileri dahil güvenlik onaylar biçimlendirme dili (SAML) belirteçleri olan.  
  
 sunucu sertifikası  
 Bir Web tarayıcısı Web sunucusuna kimlik doğrulaması gibi sunucu kimlik doğrulaması için kullanılan bir sertifikaya başvurur. Bir Web tarayıcı istemci güvenli bir Web sunucusuna erişmeye çalıştığında sunucu sertifikasını sunucunun kimliğini doğrulamak izin vermek için tarayıcıya gönderir.  
  
 Oturumu  
 Bir exchange iletilerin tek bir anahtar malzemesini koruma altında. Örneğin, SSL oturumları ve geriye bu anahtarın altında birden çok ileti göndermek için tek bir anahtar kullanın.  
  
 oturum anahtarı  
 Bir kez kullanılır ve atılır rastgele oluşturulan bir anahtar. Oturum anahtarları simetrik (şifreleme ve şifre çözme için kullanılan). Hedeflenen alıcı ortak anahtarıyla şifrelemesi ile korunan iletiyle gönderilirler. Bir oturum anahtarı yaklaşık 40 ila 2.000 arasında bit rastgele bir sayı oluşur.  
  
 ek kimlik bilgileri  
 Bir güvenlik sorumlusu yabancı güvenlik etki alanları için kimlik doğrulaması için kimlik bilgilerini kullanın.  
  
 simetrik şifreleme  
 Tek bir anahtar şifreleme ve şifre çözme için kullandığı şifreleme. Simetrik şifreleme, büyük miktarlarda verinin şifrelerken tercih edilir. Daha fazla ortak simetrik şifreleme algoritmaları bazıları şunlardır: RC2, RC4'ü ve veri şifreleme standardı (DES).  
  
 Ayrıca bkz: "genel anahtar şifreleme."  
  
 Simetrik anahtar  
 Hem şifreleme hem de şifre çözme için kullanılan tek bir anahtar. Oturum anahtarları genellikle simetrik.  
  
 belirteç (SID)  
 Bir erişim belirteci bir oturum için güvenlik bilgilerini içerir. Sistem, kullanıcı oturum açtığında ve kullanıcı adına yürütülen her işlem belirteci bir kopyası bulunduğunda bir erişim belirteci oluşturur. Belirteç, kullanıcı, kullanıcı grupları ve kullanıcı ayrıcalıkları tanımlar. Sistem güvenliği sağlanabilir nesnelere erişimini denetlemek ve kullanıcının yerel bilgisayarda çeşitli sistem güvenlikle ilgili işlemler gerçekleştirme olanağı denetlemek için bu belirteci kullanır. İki tür erişim belirteçleri, birincil ve kimliğe bürünme vardır.  
  
 Aktarım Katmanı  
 Her iki hizmet kalitesi ve bilgileri doğru teslimini sorumludur ağ katmanı. Bu katmana gerçekleştirilen görevleri hata algılama ve düzeltme arasındadır.  
  
 güven listesi (sertifika güven listesi veya CTL)  
 Bir güvenilir varlık tarafından imzalanmış öğeleri önceden tanımlanmış bir listesi. Bir CTL sertifikaların karmaları veya dosya adlarının bir listesini listesi gibi her şey olabilir. Listedeki tüm öğeleri (imzalama varlık tarafından onaylanan) kimlik doğrulaması yapılır.  
  
 güven sağlayıcısı  
 Belirli bir dosya güvenilir olup olmadığına karar verir yazılım. Bu karara dosyasıyla ilişkili sertifika temel alır.  
  
 Kullanıcı asıl adı (UPN)  
 Bir kullanıcı hesabı adı (bazen denir *kullanıcı oturum açma adı*) ve kullanıcı hesabının bulunduğu etki alanını tanıtan bir etki alanı adı. Bu bir Windows etki alanında oturum açmak için standart kullanımdır. Biçim: someone@example.com (olduğu gibi bir e-posta adresi).  
  
> [!NOTE]
>  Standart UPN form yanı sıra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] UPN'ler alt düzey biçiminde, örneğin, cohowinery.com\someone kabul eder.  
  
 X.509  
 Kendi gerekli bölümleri tanımlayan bir Uluslararası tanınan standart sertifikalar için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
