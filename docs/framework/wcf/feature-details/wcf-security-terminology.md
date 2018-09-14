---
title: WCF Güvenlik Terimleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 72a2ea1393daa7435ae233d1e420cf88b6f5b6af
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529428"
---
# <a name="wcf-security-terminology"></a>WCF Güvenlik Terimleri
Bazı güvenlik ele alınırken kullanılan terminolojiyi bilinmiyor olabilir. Bu konu başlığı altında güvenlik terimlerden bazılarının açıklamaları kısa sağlar, ancak her öğe için kapsamlı bilgi sağlamak için tasarlanmamıştır.  
  
 Windows Communication Foundation (WCF) belgelerde kullanılan terimler hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 erişim denetimi listesi (ACL)  
 Bir nesne için geçerli bir güvenlik koruması listesi. (Nesnenin bir dosya, işlem, olay veya başka bir güvenlik tanımlayıcısının sahip herhangi bir şey olabilir.) Bir ACL erişim denetimi girişi (ACE) girdidir. İki ACL türü vardır: isteğe bağlı ve sistem.  
  
 kimlik doğrulama  
 Bir kullanıcı, bilgisayar, hizmet veya işlemin ne olduğunu beyan doğrulama işlemi.  
  
 yetkilendirme  
 Erişim ve bir kaynak haklarını denetleme işlemi. Örneğin, bir dosyayı okumak bir grubun üyesi izin vererek, ancak yalnızca grubun üyeleri, dosyayı değiştirmek için başka bir izin verme.  
  
 Sertifika yetkilisi (CA) sertifikası  
 Sunucuları ve bu sertifikaları isteyen istemcilerin sunucu ve istemci kimlik doğrulama sertifikaları veren CA'yı tanımlar. Dijital imzalar kullanılan ortak anahtar içerdiği için bu da verilir bir *imza sertifikası*. CA kök yetkilisi ise, CA sertifikası için olarak başvurulabilir bir *kök sertifika*. Ayrıca bazen olarak bilinen bir *site sertifikası*.  
  
 CA hiyerarşisi  
 CA hiyerarşisi birden fazla CA içerir. Böylece her CA hiyerarşisi daha yüksek bir düzeyde başka bir CA tarafından hiyerarşinin en üstüne kadar olarak da bilinen sertifikalıdır düzenlenmiş *kök yetkilisi*, ulaşıldı.  
  
 sertifika  
 Bir varlığı ve varlığın ortak anahtar, bu nedenle bu iki bilgi parçasını birbirine bağlama hakkında bilgi içeren dijital olarak imzalanmış bir ifade. Yetkilisi varlığı kullanan, söylüyor olduğu doğrulandıktan sonra bir sertifika tarafından güvenilen bir kuruluş (veya varlık) adı verilen bir sertifika yetkilisi, verilir.  
  
 Sertifikalar, farklı veri türleri içerebilir. Örneğin, bir X.509 sertifikasının sertifika, sertifikayı, sertifika, ortak anahtar sertifikası isteme varlık ve adını sertifikayı veren CA'ın adını imzalamak için kullanılan algoritma seri numarası biçimini içerir ve CA'ın imzası.  
  
 Sertifika deposu  
 Genellikle, kalıcı depolama ortamı burada sertifikalar, sertifika iptal listelerini (CRL'ler) ve sertifika güven listelerini (CTL) depolanır. Ancak, oluşturmak ve bir sertifika deposu yalnızca bellekte kalıcı depolama alanına konmuş gerekmez sertifikalarıyla çalışırken açmak için mümkündür.  
  
 Talep  
 Bilgiler bir varlıktan diğerine gönderenin kimliğini oluşturmak için kullanılan geçirildi. Örneğin, bir kullanıcı adı ve parola belirteci veya bir X.509 sertifikası.  
  
 İstemci sertifikası  
 Bir Web sunucusunda bir Web tarayıcısı kimlik doğrulaması gibi istemci kimlik doğrulaması için kullanılan bir sertifikaya başvurur. Bir Web tarayıcısı istemcisini güvenli bir Web sunucusuna erişmeye çalıştığında, istemci istemcinin kimliğini doğrulamak izin vermek için sunucu sertifikasını gönderir.  
  
 Kimlik bilgileri  
 Daha önce bir parola veya bir Kerberos protokolü anahtarı gibi kendi kimliğini oluşturmak için kullandığı bir güvenlik sorumlusu oturum açma verilerini kimlik doğrulaması. Kimlik bilgileri, kaynaklara erişimi denetlemek için kullanılır.  
  
 Veri Sindirilmiş  
 Bir veri içerik türü ortak anahtar şifreleme standardı tarafından (PKCS) # 7'de her türlü veri artı içeriğin bir ileti karmasını (Özet) oluşur tanımlı.  
  
 dijital imza  
 Gönderenin kimliğini gönderilen bilgilerin bağlar verileri. Bir dijital imza herhangi bir ileti, dosya ya da dijital olarak kodlanmış diğer bilgileri ile birlikte veya ayrı olarak iletilebilir. Dijital imzalar, ortak anahtar ortamlarında kullanılan ve kimlik doğrulaması ve bütünlük hizmetleri sağlar.  
  
 encoding  
 BITS bir akışa veri kapatma işlemi. Kodlama verileri olanları sıfırlar ve bir akışa dönüştürür seri hale getirme işleminin parçasıdır.  
  
 Exchange anahtar çifti  
 Böylece bunlar güvenli bir şekilde depolanabilir ve diğer kullanıcılarla değiştirilen oturum anahtarlarını şifrelemek için kullanılan bir ortak/özel anahtar çifti.  
  
 hash  
 Sabit boyutlu sayısal bir rastgele bir veri miktarı için bir matematiksel işlev (bkz. karma algoritması) uygulayarak alınan değer. Verileri genellikle olarak bilinen rastgele verileri içeren bir *nonce*. Hem hizmet hem de istemci sonucu karmaşıklığını artırmak için exchange nonce öğelerinin katkıda bulunur. Sonuç olarak da bilinen, bir *ileti özeti*. Parola şifreli olsa bile bir karma değer gönderme parola gibi hassas verilerin göndermekten daha güvenlidir. Alındığında, bir karma değer doğrulanabilir böylece karma gönderen ve alıcı karma algoritması ve nonce öğelerinin kabul etmelisiniz.  
  
 Karma algoritması  
 İleti veya oturum anahtarı gibi veriler parçasının bir karma değer oluşturmak için kullanılan algoritma. Tipik bir karma algoritmaları, MD2, MD4, MD5 ve SHA-1 içerir.  
  
 Kerberos protokolü  
 İstemcilerin ağ kimlik doğrulama hizmetiyle nasıl etkileşim kuracağını tanımlayan bir protokol. İstemcileri biletleri Kerberos Anahtar Dağıtım Merkezi (KDC) öğesinden edinmek ve bu anahtarları sunucularına bağlantı kurulduğunda sundukları. Kerberos biletleri, istemcinin ağ kimlik bilgileri temsil eder.  
  
 Yerel güvenlik yetkilisi (LSA)  
 Kimlik doğrulaması ve oturum açın, yerel sistem kullanıcı korumalı bir alt. LSA, ayrıca tüm yönleri hakkında bir sistemde, sistemin yerel güvenlik ilkesi topluca bilinen bilgileri yerel güvenlik korur.  
  
 Anlaşma  
 Bir uygulama katmanı arasında güvenlik desteği Sağlayıcısı Arabirimi (SSPI) ve diğer SSP'ler görevi gören bir güvenlik desteği sağlayıcısı (SSP). Bir uygulama bir ağda oturum açmak için SSPI içinde çağırdığında, bu isteği işlemek için bir SSP belirtebilirsiniz. Uygulama belirtiyorsa `Negotiate`, `Negotiate` isteği analiz eder ve müşteri yapılandırılmış güvenlik ilkesini temel alarak bir isteği işlemek için en iyi SSP seçer.  
  
 nonce  
 "" Yeniden yürütme saldırıları aşmak için kullanılan rastgele oluşturulmuş bir değeri.  
  
 inkar edilemez  
 Bu nedenle sorumluluk engellemek için bir kullanıcı tarafından girişimlerini irrefutably countering belirli eylemler gerçekleştiren kullanıcıları tanımlamak için yeteneği. Örneğin, bir dosya silindiğinde bir sistem bir kullanıcının kimliği oturum açabilir.  
  
 Ortak anahtar şifreleme standardı (PKCS)  
 Ortak anahtar şifrelemesi dağıtımı hızlandırmak için dünya çapındaki güvenlik sistemleri geliştiriciler ile işbirliği içinde RSA veri güvenliği, Inc. tarafından üretilen belirtimleri.  
  
 PKCS #7  
 Şifreli ileti söz dizimi standart. Veri hangi şifreleme uygulanabilir, dijital imzalar ve şifreleme gibi genel söz dizimi. Ayrıca, sertifika veya sertifika iptal listeleri ve iletiye zaman damgaları gibi diğer ileti öznitelikleri yayınlamak için söz dizimi da sağlar.  
  
 düz metin  
 Şifreli ileti. Düz metin iletileri bazen denir *düz metin olarak* iletileri.  
  
 ayrıcalık  
 Sistemi kapatmadan, cihaz sürücüleri yükleniyor veya sistem saatinin değiştirilmesi gibi çeşitli sistem güvenlikle ilgili işlemler gerçekleştirme hakkı kullanıcı. Bir kullanıcının erişim belirtecini ayrıcalıkları tutun kullanıcı veya kullanıcı grupları listesini içerir.  
  
 özel anahtar  
 Gizli yarısı anahtar çiftinin bir ortak anahtar algoritması kullanılamaz. Özel anahtarları, genellikle bir simetrik oturum anahtarı şifreleme, dijital olarak bir ileti oturum veya karşılık gelen ortak anahtar ile şifrelenmiş bir iletinin şifresinin çözülmesi için kullanılır. Ayrıca bkz. "genel anahtar."  
  
 process  
 Bir uygulamanın çalıştığı güvenlik bağlamı. Genellikle belirli bir işlem altında çalışan tüm uygulamaların izinleri ve ayrıcalıklarına sahip olan kullanıcı, bu nedenle güvenlik bağlamı bir kullanıcıyla ilişkili olur.  
  
 Ortak/özel anahtar çifti  
 Ortak anahtar şifrelemesi için kullanılan şifreleme anahtarlarını bir dizi. Her bir kullanıcı için bir şifreleme hizmeti sağlayıcısı (CSP) genellikle iki ortak/özel anahtar çifti tutar: bir exchange anahtar çifti ve dijital imza anahtar çifti. Her iki anahtar çiftleri oturumdan oturuma korunur.  
  
 Ortak anahtar  
 Bir oturum anahtarı veya bir dijital imza şifresini çözerken genelde kullanılan bir şifreleme anahtarı. Ortak anahtarı, yalnızca ilgili özel anahtarın kişiyle iletinin şifresini çözebilir güvence altına alır, bir iletinin şifrelenmesi için de kullanılabilir.  
  
 Ortak anahtar şifrelemesi  
 Şifreleme anahtarları, verileri şifrelemek için bir anahtar ve diğer bir anahtar çifti verilerin şifresini çözmek için kullanır. Buna karşılık, aynı simetrik şifreleme algoritmaları, şifreleme ve şifre çözme için anahtar. Uygulamada, ortak anahtar şifrelemesi genellikle bir simetrik şifreleme algoritması kullanır. oturum anahtarını korumak için kullanılır. Bu durumda, ortak anahtarı oturum anahtarı şifrelemek için kullanılan hangi sırayla bazı verileri şifrelemek için kullanılan ve şifre çözme için kullanılan özel anahtarı. Oturum anahtarları korunmasına ek olarak, ortak anahtar şifrelemesi da dijital olarak (özel anahtarı kullanarak) bir iletiyi imzalamak ve (ortak anahtar kullanarak) imzayı doğrulamak için kullanılabilir.  
  
 Ortak anahtar altyapısı (PKI)  
 Bir altyapı oluşturma, dağıtma ve ortak anahtar uygulamaları yönetmek için tümleşik bir dizi hizmet ve Yönetimsel Araçlar sağlar.  
  
 Red  
 Bir kullanıcı yanlışlıkla gerçekleştirilen bir eylem çalışırken diğer taraflara reddetme olanağı, aksi takdirde kanıtlamak olamaz. Örneğin, kimin bir dosyayı siler ve kimin işlemi başarıyla reddedebilirsiniz kullanıcı.  
  
 kök yetkilisi  
 CA üstünde bir CA hiyerarşisi. Kök yetkilisi hiyerarşisinin sonraki düzeyi CA'larda onaylar.  
  
 Güvenli Karma algoritması (SHA)  
 Bir karma algoritma ileti özeti üretir. SHA, diğer yerler yanı sıra dijital imza standart (DSS) dijital imza algoritması (DSA) ile kullanılır. Dört çeşitleri SHA vardır: SHA-1, SHA-256, SHA-384 ve SHA-512. SHA-1, 160 bitlik ileti özeti üretir. 256 bit, 384 bit SHA-256, SHA-384 ve SHA-512 oluşturun ve 512 bit ileti özetleyen, sırasıyla. SHA Ulusal Standartlar ve teknoloji kurumu (NIST) tarafından ve Ulusal Güvenlik Agency (NSA) tarafından geliştirilmiştir.  
  
 Güvenli Yuva Katmanı (SSL)  
 Genel ve gizli anahtar teknoloji bir birleşimi kullanılarak güvenli ağ iletişim için bir protokol.  
  
 güvenlik bağlamı  
 Şu anda etkin olan kuralları ve güvenlik öznitelikleri. Örneğin, bilgisayarda oturum açmış geçerli kullanıcı veya akıllı kart kullanıcı tarafından girilen kişisel kimlik numarası. SSPI için bir güvenlik bağlamı bir oturum anahtarı veya göstergesidir oturumun süresi gibi bir bağlantı ile ilgili güvenlik verilerini içeren bir donuk bir veri yapısıdır.  
  
 güvenlik sorumlusu  
 Güvenlik sistemi tarafından tanınan bir varlığın. İlkeleri otonom işlemlerin yanı sıra, İnsan kullanıcılar ekleyebilirsiniz.  
  
 Güvenlik Desteği Sağlayıcısı (SSP)  
 Bir veya daha fazla güvenlik paketleri uygulamaları için kullanılabilir hale getirerek SSPI uygulayan bir dinamik bağlantı kitaplığı (DLL). Her güvenlik paketi, bir uygulamanın SSPI işlev çağrıları ve bir gerçek güvenlik modelinin işlevleri arasında eşleme sağlar. Güvenlik paketleri Kerberos kimlik doğrulaması ve Microsoft LAN Yöneticisi (LanMan) gibi güvenlik protokollerini destekler.  
  
 Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI)  
 Microsoft Uzak yordam çağrısı (RPC) ve Windows gibi güvenlik sağlayıcıları gibi aktarım düzeyinde uygulamalar arasında ortak bir arabirim güvenlik dağıtılmış. SSPI, kimliği doğrulanmış bir bağlantı almak için birçok güvenlik sağlayıcılardan birini çağırmak bir aktarım uygulamasını sağlar. Bu çağrılar güvenlik protokolünün ayrıntılarını kapsamlı bilgi gerektirmez.  
  
 Güvenlik belirteci hizmeti  
 Hizmetleri vermek ve multiservice senaryosunda özel güvenlik belirteçleri (verilen belirteçler) yönetmek için tasarlanmıştır. Özel belirteçler genellikle özel bir kimlik bilgisi içeren güvenlik onaylama işaretleme dili (SAML) belirteçleri biçimindedir.  
  
 sunucu sertifikası  
 Bir Web tarayıcısı Web sunucusuna kimlik doğrulaması gibi sunucu kimlik doğrulaması için kullanılan bir sertifikaya başvurur. Bir Web tarayıcısı istemcisini güvenli bir Web sunucusuna erişmeye çalıştığında sunucu sertifikasını sunucunun kimliğini doğrulamak izin vermek için tarayıcının gönderir.  
  
 Oturumu  
 Bir exchange ileti tek bir parçanın malzemesi koruma altında. Örneğin, SSL oturumları ve geriye bu anahtarı altında birden çok ileti göndermek için tek bir anahtarı kullanın.  
  
 oturum anahtarı  
 Bir kez kullanıldığını ve atılır rastgele oluşturulmuş bir anahtar. Oturum anahtarları simetrik (şifreleme ve şifre çözme için kullanılan). Amaçladığınız alıcının bir ortak anahtar ile şifrelemesi ile korunan bir ileti ile gönderilir. Bir oturum anahtarı bir rasgele sayı yaklaşık 40 ila 2.000 arasında bit oluşur.  
  
 ek kimlik bilgileri  
 Yabancı güvenlik etki alanları için bir güvenlik sorumlusunun kimlik doğrulaması kimlik bilgilerini kullanın.  
  
 simetrik şifreleme  
 Tek bir anahtar şifreleme ve şifre çözme için kullandığı şifreleme. Simetrik şifreleme, büyük miktarlarda verileri şifrelerken tercih edilir. Daha yaygın simetrik şifreleme algoritmaları RC2, RC4 ve veri şifreleme standardı (DES) bazılarıdır.  
  
 Ayrıca bkz: "ortak anahtar şifreleme."  
  
 Simetrik anahtar  
 Şifreleme ve şifre çözme için kullanılan tek bir anahtarı. Oturum anahtarları, genellikle simetrik.  
  
 belirteci (erişim belirteci)  
 Bir erişim belirteci bir oturum için güvenlik bilgilerini içerir. Sistem, kullanıcı oturum açtığında ve kullanıcı adına çalıştırılan her işlem belirteci kopyasına sahip bir erişim belirteci oluşturur. Belirteç, kullanıcının, kullanıcı grupları ve kullanıcının ayrıcalıkları tanımlar. Sistem güvenliği sağlanabilir nesnelere erişimi denetleyen ve kullanıcının yerel bilgisayarda çeşitli sistem güvenlikle ilgili işlemler gerçekleştirme olanağı denetlemek için bu belirteci kullanır. İki tür erişim belirteçleri, birincil ve kimliğe bürünme vardır.  
  
 Aktarım Katmanı  
 Her iki hizmet kalitesi ve bilgilerin doğru teslim sorumlu ağ katmanı. Bu katmana gerçekleştirilen görevleri hata algılama ve düzeltme arasındadır.  
  
 güven listesi (sertifika güven listesi veya CTL)  
 Önceden tanımlanmış bir güvenilir varlık tarafından imzalanmış öğeleri listesi. Bir CTL sertifikaların karmaları veya dosya adlarının bir listesini listesi gibi her şey olabilir. Listedeki tüm öğeleri (imzalayan varlık tarafından onaylanan) doğrulanır.  
  
 güven sağlayıcısı  
 Belirli bir dosya güvenilir olup olmadığına karar verir yazılım. Bu karar dosyasıyla ilişkili sertifika temel alır.  
  
 Kullanıcı asıl adı (UPN)  
 Bir kullanıcı hesabı adı (bazen denir *kullanıcı oturum açma adı*) ve kullanıcı hesabının bulunduğu etki alanını tanıtan bir etki alanı adı. Bu, bir Windows etki alanında oturum açma için standart kullanımdır. Biçim: someone@example.com (olduğu gibi bir e-posta adresi).  
  
> [!NOTE]
>  Ek olarak standart UPN form, WCF, alt düzey form, örneğin, cohowinery.com\someone UPN kabul eder.  
  
 X.509  
 Kendi gerekli bölümlerini tanımlayan bir uluslararası olarak tanınan standart sertifikaları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Windows Communication Foundation Kavramları](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
