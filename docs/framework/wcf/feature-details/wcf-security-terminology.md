---
title: WCF Güvenlik Terimleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
ms.openlocfilehash: 6751513b72f732bd7392de11a203467a9ead1bce
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743349"
---
# <a name="wcf-security-terminology"></a>WCF Güvenlik Terimleri
Güvenliği tartışmak için kullanılan bazı terminoloji tanıdık gelebilir. Bu konu, bazı güvenlik koşullarının kısa açıklamalarını sağlar, ancak her öğe için kapsamlı belgeler sağlamaya yönelik değildir.  
  
 Windows Communication Foundation (WCF) belgelerinde kullanılan terimler hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramlar](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 erişim denetim listesi (ACL)  
 Bir nesne için geçerli olan güvenlik korumalarının listesi. (Bir nesne bir dosya, işlem, olay veya bir güvenlik tanımlayıcısına sahip başka bir şey olabilir.) ACL 'deki bir giriş bir erişim denetimi girişi (ACE). İki tür ACL vardır: isteğe bağlı ve sistem.  
  
 kimlik doğrulama  
 Bir kullanıcının, bilgisayarın, hizmetin veya işlemin ne olduğunu doğrulama süreci.  
  
 yetkilendirme  
 Bir kaynağa erişimi ve hakları denetleme eylemi. Örneğin, bir grubun üyelerinin bir dosyayı okumasına izin verme, ancak yalnızca başka bir grubun üyelerinin dosyayı değiştirmesine izin verme.  
  
 sertifika yetkilisi (CA) sertifikası  
 Bu sertifikaları isteyen sunuculara ve istemcilere sunucu ve istemci kimlik doğrulama sertifikaları veren CA 'yı tanımlar. Dijital imzalarda kullanılan bir ortak anahtar içerdiğinden *imza sertifikası*olarak da adlandırılır. CA bir kök yetkilisise, CA sertifikasına *kök sertifika*denir. Bazen *Site sertifikası*olarak da bilinir.  
  
 CA hiyerarşisi  
 CA hiyerarşisi birden çok CA içerir. Her CA 'nın, hiyerarşinin en üstüne, *kök yetkili*olarak da bilinene kadar daha yüksek düzeyde başka bir CA tarafından sertifikalanabilmesi için düzenlenir.  
  
 sertifika  
 Bir varlık ve varlığın ortak anahtarı hakkında bilgi içeren, bu iki bilgi parçasını birbirine bağlayan dijital imzalı bir ifade. Sertifika, yetkili varlığın kim olduğunu doğruladıktan sonra, sertifika yetkilisi olarak adlandırılan güvenilir bir kuruluş (veya varlık) tarafından verilir.  
  
 Sertifikalar, farklı veri türleri içerebilir. Örneğin, bir X. 509.440 sertifikası, sertifika biçimini, sertifikanın seri numarasını, sertifikayı imzalamak için kullanılan algoritmayı, sertifikayı veren CA 'nın adını, sertifikayı isteyen varlığın adını ve ortak anahtarını içerir ve CA imzası.  
  
 sertifika deposu  
 Genellikle, sertifikaların, sertifika iptal listelerinin (CRL 'Ler) ve sertifika güven listelerinin (CTL) depolandığı kalıcı bir depolama alanı. Ancak, kalıcı depolamaya koymak zorunda olmayan sertifikalarla çalışırken yalnızca bellekte bir sertifika deposu oluşturmak ve açmak mümkündür.  
  
 claims  
 Bir varlıktan gönderenin kimliğini oluşturmak için kullanılan başka bir varlığa geçirilen bilgiler. Örneğin, bir Kullanıcı adı ve parola belirteci ya da bir X. 509.440 sertifikası.  
  
 istemci sertifikası  
 Web sunucusunda bir Web tarayıcısının kimlik doğrulaması gibi, istemci kimlik doğrulaması için kullanılan bir sertifikaya başvurur. Bir Web tarayıcısı istemcisi güvenli bir Web sunucusuna erişmeyi denediğinde, istemci, istemcinin kimliğini doğrulamasına izin vermek için sertifikasını sunucuya gönderir.  
  
 Credentials  
 Bir güvenlik sorumlusunun parola veya Kerberos protokol bileti gibi kendi kimliğini oluşturmak için kullandığı önceden kimliği doğrulanmış oturum açma verileri. Kimlik bilgileri, kaynaklara erişimi denetlemek için kullanılır.  
  
 oluşan veriler  
 Herhangi bir türden verilerin yanı sıra içeriğin ileti karması (Özet) içeren ortak anahtar şifreleme standardı (PKCS) #7 tarafından tanımlanan veri içeriği türü.  
  
 Dijital imza  
 Gönderenin kimliğini gönderilmekte olan bilgilere bağlayan veriler. Dijital imza herhangi bir ileti, dosya veya dijital olarak kodlanan diğer bilgilerle birlikte paketlenmiştir veya ayrı olarak iletilebilir. Dijital imzalar ortak anahtar ortamlarında kullanılır ve kimlik doğrulama ve bütünlük hizmetleri sağlar.  
  
 {1&gt;encoding&lt;1}  
 Verileri bir bit akışına çevirme işlemi. Kodlama, verileri bir ve sıfırlardan oluşan bir akışa dönüştüren serileştirme işleminin bir parçasıdır.  
  
 Exchange anahtar çifti  
 Oturum anahtarlarını şifrelemek için kullanılan ortak/özel anahtar çifti, güvenli bir şekilde saklanabilmesi ve diğer kullanıcılarla değiş tokuş olmaları sağlanır.  
  
 hash  
 Rastgele bir veri miktarına matematiksel bir işlev (bkz. karma algoritma) uygulanarak elde edilen sabit boyutlu bir sayısal değer. Veriler genellikle, *nonce*olarak bilinen rastgele verileri içerir. Hem hizmet hem de istemci, sonuçta elde edilen karmaşıklığın artması için Exchange 'e katkıda bulunur. Sonuç *ileti özeti*olarak da bilinir. Bir karma değer gönderilmesi, parola şifrelense bile parola gibi hassas verileri gönderdikten daha güvenlidir. Karma gönderici ve alıcı karma algoritmasını ve nonce 'yi kabul etmelidir, bu nedenle, alındıktan sonra bir karma doğrulanabilir.  
  
 karma algoritması  
 İleti veya oturum anahtarı gibi bazı veri parçalarından oluşan bir karma değer oluşturmak için kullanılan algoritma. Tipik karma algoritmalar arasında MD2, MD4, MD5 ve SHA-1 bulunur.  
  
 Kerberos protokolü  
 İstemcilerin bir ağ kimlik doğrulama hizmeti ile nasıl etkileşime gireceğini tanımlayan bir protokol. İstemciler, Kerberos Anahtar Dağıtım Merkezi (KDC) tarafından bilet elde eder ve bağlantılar oluşturulduğunda bu biletleri sunuculara sunar. Kerberos biletleri, istemcinin ağ kimlik bilgilerini temsil eder.  
  
 Yerel güvenlik yetkilisi (LSA)  
 Kullanıcıları kimlik doğrulaması yapan ve yerel sistemde oturum açan korumalı bir alt sistem. LSA ayrıca, sistemin yerel güvenlik ilkesi olarak bilinen bir sistemdeki tüm yerel güvenlik özellikleri hakkında bilgi de sağlar.  
  
 'Nin  
 Güvenlik desteği sağlayıcısı arabirimi (SSPI) ve diğer SSPs 'ler arasında bir uygulama katmanı görevi gören bir güvenlik desteği sağlayıcısı (SSP). Bir uygulama bir ağda oturum açmak için SSPI 'e çağırdığında, isteği işlemek için bir SSP belirtebilir. Uygulama `Negotiate`belirtiyorsa, isteği analiz `Negotiate` ve müşterinin yapılandırdığı güvenlik ilkesine göre isteği işlemek için en iyi SSP 'yi seçer.  
  
 nonce  
 "Yeniden yürütme" saldırılarını erteetmek için kullanılan rastgele oluşturulmuş bir değer.  
  
 kabullenme  
 Belirli eylemleri gerçekleştiren kullanıcıları belirleyebilme, bu nedenle bir kullanıcı tarafından sorumluluğu reddetme girişimlerini düzensiz şekilde geri alma. Örneğin, bir sistem, bir dosya silindiğinde kullanıcının KIMLIĞINI günlüğe alabilir.  
  
 Ortak anahtar şifreleme standardı (PKCS)  
 Ortak anahtar şifrelemenin dağıtımını hızlandırmak için dünya çapındaki güvenli sistem geliştiricileri ile birlikte RSA Data Security, Inc. tarafından oluşturulan belirtimler.  
  
 PKCS #7  
 Şifreleme Iletisi sözdizimi standardı. Dijital imzalar ve şifreleme gibi şifrelemenin uygulanabileceğini belirten genel bir sözdizimi. Ayrıca, sertifikaların veya sertifika iptal listelerinin ve zaman damgaları gibi diğer ileti özniteliklerinin iletiye dağıtımını yapmak için sözdizimi de sağlar.  
  
 düz metin  
 Şifrelenmeyen bir ileti. Düz metin iletiler bazen düz *metin* iletileri olarak adlandırılır.  
  
 ayrıcalıklar  
 Bir kullanıcının, sistemi kapatma, aygıt sürücülerini yükleme veya sistem saatini değiştirme gibi sistemle ilgili çeşitli işlemleri gerçekleştirme hakkı. Kullanıcının erişim belirteci, kullanıcının veya Kullanıcı gruplarının tutamayacağı ayrıcalıkların bir listesini içerir.  
  
 özel anahtar  
 Ortak anahtar algoritmasında kullanılan anahtar çiftinin gizli yarısı. Özel anahtarlar genellikle bir simetrik oturum anahtarını şifrelemek, bir iletiyi dijital olarak imzalamak veya karşılık gelen ortak anahtarla şifrelenen bir iletinin şifresini çözmek için kullanılır. Ayrıca bkz. "ortak anahtar".  
  
 process  
 Uygulamanın çalıştığı güvenlik bağlamı. Genellikle, güvenlik bağlamı bir kullanıcıyla ilişkilendirilir, bu nedenle belirli bir işlem altında çalışan tüm uygulamalar sahip olan kullanıcının izinlerini ve ayrıcalıklarını alır.  
  
 ortak/özel anahtar çifti  
 Ortak anahtar şifrelemesi için kullanılan bir şifreleme anahtarları kümesi. Her Kullanıcı için bir şifreleme hizmeti sağlayıcısı (CSP) genellikle iki ortak/özel anahtar çifti tutar: bir Exchange anahtar çifti ve dijital imza anahtar çifti. Her iki anahtar çifti de oturumdan oturuma tutulur.  
  
 ortak anahtar  
 Genellikle bir oturum anahtarının veya dijital imzanın şifresini çözerken kullanılan bir şifreleme anahtarı. Ortak anahtar Ayrıca bir iletiyi şifrelemek için de kullanılabilir ve yalnızca ilgili özel anahtara sahip olan kişinin ileti şifresini çözemeyeceğini garanti edebilir.  
  
 ortak anahtar şifrelemesi  
 Bir çift anahtar kullanan şifreleme, verileri şifrelemek için bir anahtar ve verilerin şifresini çözmek için kullanılan diğer anahtar. Buna karşılık, hem şifreleme hem de şifre çözme için aynı anahtarı kullanan simetrik şifreleme algoritmaları. Uygulamada, ortak anahtar şifrelemesi genellikle bir simetrik şifreleme algoritmasının kullandığı oturum anahtarını korumak için kullanılır. Bu durumda, ortak anahtar, daha sonra bazı verileri şifrelemek için kullanılan ve özel anahtar şifre çözme için kullanılan oturum anahtarını şifrelemek için kullanılır. Ortak anahtar şifrelemesi, oturum anahtarlarını korumanın yanı sıra bir iletiyi dijital olarak imzalamak için de kullanılabilir (özel anahtar kullanılarak) ve imzayı doğrulayabilir (ortak anahtar kullanılarak).  
  
 ortak anahtar altyapısı (PKI)  
 Ortak anahtar uygulamaları oluşturmaya, dağıtmaya ve yönetmeye yönelik tümleşik bir hizmet kümesi ve yönetim araçları sağlayan bir altyapı.  
  
 kar  
 Bir kullanıcının diğer taraflar aksini kanıtlayamazken, bir eylemi gerçekleştirmeyi çok seyrek reddetme özelliği. Örneğin, bir dosyayı silen ve bu işlemi başarılı bir şekilde reddedebilen bir kullanıcı.  
  
 kök yetkili  
 CA hiyerarşisinin en üstündeki CA. Kök yetkili, CA 'Ların, hiyerarşinin bir sonraki düzeyinde sertifika yetkilileri.  
  
 Güvenli karma algoritması (SHA)  
 İleti Özeti üreten bir karma algoritması. SHA, dijital Imza standardı (DSS) içindeki dijital Imza algoritması (DSA) ile diğer yerleri arasında kullanılır. SHA 'nın dört türlü derecesi vardır: SHA-1, SHA-256, SHA-384 ve SHA-512. SHA-1 160 bitlik bir ileti özeti üretir. SHA-256, SHA-384 ve SHA-512 sırasıyla 256-bit, 384-bit ve 512-bit ileti digests oluşturma. SHA, ulusal standartlar ve Teknoloji Enstitüsü (NıST) ve Ulusal Güvenlik Kurumu (NSA) tarafından geliştirilmiştir.  
  
 Güvenli Yuva Katmanı (SSL)  
 Ortak ve gizli anahtar teknolojisinin birleşimini kullanarak güvenli ağ iletişimleri için bir protokol.  
  
 güvenlik bağlamı  
 Şu anda etkin olan güvenlik öznitelikleri veya kuralları. Örneğin, geçerli kullanıcı bilgisayarda oturum açtı veya akıllı kart kullanıcısı tarafından girilen kişisel kimlik numarası. SSPI için, bir güvenlik bağlamı, bir bağlantıyla ilgili güvenlik verilerini (oturum anahtarı veya oturum süresinin bir göstergesi gibi) içeren donuk bir veri yapısıdır.  
  
 güvenlik sorumlusu  
 Güvenlik sistemi tarafından tanınan bir varlık. Sorumlular, insan kullanıcıları ve otonom süreçler içerebilir.  
  
 güvenlik desteği sağlayıcısı (SSP)  
 Bir veya daha fazla güvenlik paketini uygulamalar için kullanılabilir hale getirerek SSPI 'yi uygulayan bir dinamik bağlantı kitaplığı (DLL). Her güvenlik paketi, bir uygulamanın SSPI işlev çağrıları ile gerçek bir güvenlik modelinin işlevleri arasında eşlemeler sağlar. Güvenlik paketleri Kerberos kimlik doğrulaması ve Microsoft LAN Manager (LanMan) gibi güvenlik protokollerini destekler.  
  
 Güvenlik desteği sağlayıcısı arabirimi (SSPI)  
 Microsoft Uzak yordam çağrısı (RPC) gibi aktarım düzeyi uygulamalar ve Windows dağıtılmış güvenlik gibi güvenlik sağlayıcıları arasındaki ortak bir arabirim. SSPI, bir aktarım uygulamasının kimliği doğrulanmış bir bağlantı almak için çeşitli güvenlik sağlayıcılarından birini çağırmasını sağlar. Bu çağrılar güvenlik protokolünün ayrıntıları hakkında kapsamlı bilgi gerektirmez.  
  
 Güvenlik belirteci hizmeti  
 Çoklu hizmet senaryosunda özel güvenlik belirteçleri (verilen belirteçler) vermek ve yönetmek için tasarlanan hizmetler. Özel belirteçler genellikle özel bir kimlik bilgisi içeren güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteçleridir.  
  
 sunucu sertifikası  
 Sunucu kimlik doğrulaması için kullanılan bir sertifikaya başvurur, örneğin bir Web sunucusunun Web tarayıcısında doğrulanması. Bir Web tarayıcısı istemcisi güvenli bir Web sunucusuna erişmeyi denediğinde, sunucu, sunucunun kimliğini doğrulamasına izin vermek için sertifikasını tarayıcıya gönderir.  
  
 oturumuna  
 Tek bir anahtarlama malzemesinin korunmasından daha fazla ileti alışverişi. Örneğin, SSL oturumları, bu anahtar altında birden fazla iletiyi ileri ve geri göndermek için tek bir anahtar kullanır.  
  
 oturum anahtarı  
 Bir kez kullanılan ve sonra atılan rastgele oluşturulmuş bir anahtar. Oturum anahtarları simetrik (hem şifreleme hem de şifre çözme için kullanılır). Bu iletiler, hedeflenen alıcıdan ortak anahtarla şifreleme ile korunan iletiyle birlikte gönderilir. Oturum anahtarı, yaklaşık 40 ile 2.000 bit arasında rastgele bir sayı içerir.  
  
 ek kimlik bilgileri  
 Yabancı güvenlik etki alanlarına güvenlik sorumlusu kimlik doğrulaması sırasında kullanılacak kimlik bilgileri.  
  
 simetrik şifreleme  
 Şifreleme ve şifre çözme için tek bir anahtar kullanan şifreleme. Büyük miktarlarda veriyi şifrelerken simetrik şifreleme tercih edilir. Daha yaygın simetrik şifreleme algoritmalarından bazıları RC2, RC4 ve veri şifreleme standardı (DES) ' dir.  
  
 Ayrıca bkz. "ortak anahtar şifrelemesi."  
  
 simetrik anahtar  
 Hem şifreleme hem de şifre çözme için kullanılan tek bir anahtar. Oturum anahtarları genellikle simetrik olur.  
  
 Belirteç (erişim belirteci)  
 Erişim belirteci bir oturum açma oturumunun güvenlik bilgilerini içerir. Sistem, bir Kullanıcı oturum açtığında bir erişim belirteci oluşturur ve Kullanıcı adına çalıştırılan her işlemin belirtecin bir kopyası vardır. Belirteç kullanıcıyı, kullanıcının gruplarını ve kullanıcının ayrıcalıklarını tanımlar. Sistem, güvenli kılınabilir nesnelere erişimi denetlemek ve kullanıcının yerel bilgisayarda sistemle ilgili çeşitli işlemleri gerçekleştirme becerisini denetlemek için belirtecini kullanır. İki tür erişim belirteci vardır, birincil ve kimliğe bürünme.  
  
 Aktarım katmanı  
 Hem hizmet kaliteden hem de bilgilerin doğru teslimatmasından sorumlu olan ağ katmanı. Bu katmanda gerçekleştirilen görevler arasında hata algılama ve düzeltme vardır.  
  
 güven listesi (sertifika güven listesi veya CTL)  
 Güvenilen bir varlık tarafından imzalanmış olan öğelerin önceden tanımlanmış listesi. CTL, sertifika karmalarının bir listesi veya dosya adları listesi gibi herhangi bir şey olabilir. Listedeki tüm öğelerin imza varlığı tarafından kimliği doğrulanır (onaylandı).  
  
 güven sağlayıcısı  
 Belirli bir dosyanın güvenilir olup olmadığına karar veren yazılım. Bu karar, dosyayla ilişkili sertifikayı temel alır.  
  
 Kullanıcı asıl adı (UPN)  
 Kullanıcı hesabı adı (bazen *Kullanıcı oturum açma adı*olarak adlandırılır) ve Kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı. Bu, bir Windows etki alanında oturum açmak için standart kullanımdır. Biçim: someone@example.com (bir e-posta adresi için).  
  
> [!NOTE]
> WCF, standart UPN biçimine ek olarak alt düzey biçimde UPN 'leri kabul eder, örneğin, cohowınara. com\someone.  
  
 X. 509.440  
 Gerekli parçalarını tanımlayan sertifikalar için uluslararası olarak tanınan bir standart.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Windows Communication Foundation Kavramları](../../../../docs/framework/wcf/fundamental-concepts.md)
- [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
