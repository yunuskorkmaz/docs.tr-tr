---
title: Buluta özgü uygulamalar için azure güvenliği
description: Azure için Cloud Native .NET Uygulamalarını Temel Alma | Bulut Yerel Uygulamalar için Azure Güvenliği
ms.date: 06/30/2019
ms.openlocfilehash: 13b5ad7a883a83014913fa0a6a020610c28c524f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989148"
---
# <a name="azure-security-for-cloud-native-apps"></a>Buluta özgü uygulamalar için azure güvenliği

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulut ait uygulamalar geleneksel uygulamalara göre hem daha kolay hem de güvenli hale getirmek daha zor olabilir. Dezavantajı, daha küçük uygulamalar güvenli ve güvenlik altyapısı oluşturmak için daha fazla enerji ayırmak gerekir. Çoğu hizmet dağıtımında programlama dillerinin ve stillerinin heterojen yapısı, birçok farklı sağlayıcının güvenlik bültenlerine daha fazla dikkat etmeniz gerektiği anlamına da gelir.

Diğer taraftan, her biri kendi veri deposuna sahip olan daha küçük hizmetler, bir saldırının kapsamını sınırlar. Bir saldırgan bir sistemden ödün verirse, saldırganın tek bir uygulamada olduğundan başka bir sisteme sıçrama yapması büyük olasılıkla daha zordur. Süreç sınırları güçlü sınırlardır. Ayrıca, bir veritabanı yedekleme sazlarsa, bu veritabanı yalnızca bir veri alt kümesi içerdiğinden ve kişisel veri içerme olasılığı düşük olduğundan, hasar daha sınırlıdır.

## <a name="threat-modeling"></a>Tehdit modelleme

Avantajları bulut-yerli uygulamaların dezavantajları ağır basar olursa olsun, aynı bütünsel güvenlik zihniyet takip edilmelidir. Güvenlik ve güvenli düşünme, geliştirme ve operasyon hikayesinin her adımının bir parçası olmalıdır. Bir uygulama planlarken gibi sorular sormak:

- Bu verilerin kaybolmasının etkisi ne olur?
- Bu hizmete enjekte edilen kötü verilerden kaynaklanan hasarı nasıl sınırlandırabiliriz?
- Bu verilere kimler erişmeli?
- Geliştirme ve serbest bırakma süreci etrafında denetim politikaları var mı?

Tüm bu sorular [tehdit modelleme](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool)denilen bir sürecin parçasıdır. Bu süreç, sisteme yönelik tehditlerin ne kadar olduğu, tehditlerin ne kadar olası olduğu ve bunların potansiyel zararı sorusunu yanıtlamaya çalışır.

Tehdit listesi oluşturulduktan sonra, bunların hafifletmeye değer olup olmadığına karar vermeniz gerekir. Bazen bir tehdit çok olası ve bunun için planlamak için pahalı bunun üzerine enerji harcamaya değmez. Örneğin, bazı durum düzeyindeaktör milyonlarca aygıt tarafından kullanılan bir işlemin tasarımına değişiklikler enjekte edebilir. Şimdi, [Halka 3'te](https://en.wikipedia.org/wiki/Protection_ring)belirli bir kod parçasını çalıştırmak yerine, bu kod Halka 0'da çalıştırılır. Bu, hipervizörü atlayabilen ve çıplak metal makinelerdeki saldırı kodunu çalıştırabilen bir yararlanmaya izin vererek, bu donanımda çalışan tüm sanal makinelere saldırılar yapılmasına izin verir.

Değiştirilen işlemciler bir mikroskop ve bu işlemcinin silikon tasarımı hakkında gelişmiş bilgi olmadan tespit etmek zordur. Bu senaryonun gerçekleşmesi olası değildir ve azaltmak için pahalı, bu nedenle muhtemelen hiçbir tehdit modeli bunun için yararlanmak koruma bina tavsiye ederim.

Artan saldırılara `Id` `Id=2` `Id=3` (URL'de değiştirme) veya SQL enjeksiyonuna izin veren kırık erişim denetimleri gibi daha olası tehditler, koruma oluşturmak için daha caziptir. Bu tehditleriçin hafifletmeler oldukça oluşturmak ve şirketin itibarını lekeleyen utanç verici güvenlik delikleri önlemek için makul.

## <a name="principle-of-least-privilege"></a>En az ayrıcalık ilkesi

Bilgisayar güvenliğinin kurucu fikirlerinden biri de En Az Ayrıcalık Ilkesi (POLP) 'dir. Aslında güvenlik her türlü en temel bir fikir dijital ya da fiziksel olsun. Kısacası, ilke, herhangi bir kullanıcı veya işlem görevini yürütmek için mümkün olan en az sayıda hakka sahip olması gerektiğidir.

Örnek olarak, bir bankada veznedarlar düşünün: kasaya erişmek nadir bir etkinliktir. Yani, ortalama bir veznedar kasayı kendileri açamaz. Erişim sağlamak için, ek güvenlik denetimleri gerçekleştiren bir banka müdürü aracılığıyla isteklerini yükseltmeleri gerekir.

Bir bilgisayar sisteminde, fantastik bir örnek bir veritabanına bağlanan bir kullanıcının haklarıdır. Çoğu durumda, hem veritabanı yapısını oluşturmak hem de uygulamayı çalıştırmak için kullanılan tek bir kullanıcı hesabı vardır. Ekstrem durumlar dışında, uygulamayı çalıştıran hesabın şema bilgilerini güncelleştirme yeteneğine ihtiyacı yoktur. Farklı ayrıcalık düzeyleri sağlayan çeşitli hesaplar olmalıdır. Uygulama yalnızca tablolardaki verilere okuma ve yazma erişimi veren izin düzeyini kullanmalıdır. Bu tür bir koruma, veritabanı tablolarını düşürmeyi veya kötü amaçlı tetikleyiciler getirmeyi amaçlayan saldırıları ortadan kaldırır.

Bulut ait bir uygulama oluşturmanın hemen hemen her bölümü, en az ayrıcalık ilkesini hatırlamaktan yararlanabilir. Rol tabanlı erişim denetiminde (RBAC) güvenlik duvarları, ağ güvenlik grupları, roller ve kapsamlar kurarken bunu oyunda bulabilirsiniz.

## <a name="penetration-testing"></a>Sızma testi

Uygulamalar daha karmaşık hale geldikçe saldırı vektörlerinin sayısı endişe verici bir oranda artar. Tehdit modelleme sistemi oluşturan aynı kişiler tarafından yürütülme eğilimindedir bu kusurlu. Birçok geliştiricinin kullanıcı etkileşimlerini öngörmekte ve sonra kullanılamaz kullanıcı arabirimleri oluşturmakta zorlandığı gibi, çoğu geliştirici de her saldırı vektörü görmekte zorlanır. Sistemi oluşturan geliştiricilerin saldırı metodolojileri hakkında bilgili olmaması ve çok önemli bir şeyi kaçırması da mümkündür.

Penetrasyon testi veya "kalem testi" sisteme saldırmak için harici aktörler getirerek içerir. Bu saldırganlar harici bir danışmanlık şirketi veya işin başka bir bölümünden iyi güvenlik bilgisine sahip diğer geliştiriciler olabilir. Sistemi çökertmek için onlara tam yetki verildi. Sık sık, onlar yamalı olması gereken geniş güvenlik delikleri bulacaksınız. Bazen saldırı vektörü CEO'ya karşı bir kimlik avı saldırısından yararlanmak gibi tamamen beklenmedik bir şey olabilir.

Azure kendisi sürekli [Microsoft içinde hacker](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)bir ekip saldırılar geçiyor. Yıllar geçtikçe, düzinelerce potansiyel felaket saldırı vektörü bulan ilk kişi oldular. Bir hedef ne kadar cazip olursa, ebedi aktörlerin bu hedeften yararlanmaya çalışması o kadar olasıdır ve dünyada Azure'dan daha cazip birkaç hedef vardır.

## <a name="monitoring"></a>İzleme

Bir saldırgan bir uygulamaya girmeye çalışırsa, bunun bazı uyarı olmalıdır. Sık sık, saldırılar hizmetlerden günlükleri inceleyerek tespit edilebilir. Saldırılar, başarılı olmadan önce fark edilebilen işaretler bırakır. Örneğin, parolayı tahmin etmeye çalışan bir saldırgan, oturum açma sistemine birçok istekte bulunacaktır. Giriş sistemi etrafında izleme tipik erişim deseni ile çizgi dışında garip desenler algılayabilir. Bu izleme, bir tür karşı önlemi etkinleştirmek için bir operasyon kişisini uyarabilecek bir uyarıya dönüştürülebilir. Son derece olgun bir izleme sistemi, bu sapmalara dayanarak, istekleri engellemek veya yanıtları daraltmak için proaktif kurallar ekleyerek harekete geçebilir.

## <a name="securing-the-build"></a>Yapının güvenliğini sağlama

Güvenliğin genellikle göz ardı edildiği bir yer, yapı işleminin etrafındadır. Yapı, güvenli olmayan kod veya iade edilmiş kimlik bilgilerini tarama gibi güvenlik denetimlerini çalıştırmakla birlikte, yapının kendisi de güvenli olmalıdır. Yapı sunucusu tehlikeye girerse, ürüne rasgele kod tanıtmak için harika bir vektör sağlar.

Bir saldırganın bir web uygulamasına giriş yapan kişilerin parolalarını çalmak için aradığını düşünün. Herhangi bir giriş isteğini başka bir sunucuya yansıtmak için kullanıma alındı kodunu değiştiren bir yapı adımı başlatabilirler. Kod yapıdan bir daha geçince sessizce güncellenir. Kaynak kodu güvenlik açığı taraması, yapıdan önce çalıştığı için bunu yakalamaz. Aynı şekilde, yapı adımları yapı sunucusunda canlı olduğundan, kimse bunu bir kod incelemesinde yakalayamaz. Yararlanılan kod, parolaları toplayabileceği üretime gider. Büyük olasılıkla yapı işlemi değişikliklerinin denetim günlüğü yoktur veya en azından denetimi izleyen kimse yoktur.

Bu, sisteme girmek için kullanılabilecek düşük değerli bir hedefin mükemmel bir örneğidir. Bir saldırgan sistemin çevresini ihlal ettikten sonra, izinlerini istedikleri her yerde gerçek zarar verecek şekilde yükseltmenin yollarını bulmaya başlayabilirler.

## <a name="building-secure-code"></a>Güvenli kod oluşturma

.NET Framework zaten oldukça güvenli bir çerçevedir. Dizilerin uçlarından yürümek gibi yönetilmeyen kodların bazı tuzaklarından kaçınır. Güvenlik açıklarını tespit edildiklerinde gidermek için aktif olarak çalışmalar yapılır. Hatta araştırmacılara, çerçevedeki sorunları bulmaları ve bunları sömürmek yerine bildirmeleri için para ödeyen bir [böcek ödül programı](https://www.microsoft.com/msrc/bounty) bile var.

.NET kodunu daha güvenli hale getirmenin birçok yolu vardır. .NET makalesi [için Güvenli kodlama yönergeleri](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) gibi yönergeleri izleyerek, kodun sıfırdan güvenli olduğundan emin olmak için atması gereken makul bir adımdır. [OWASP top 10](https://owasp.org/www-project-top-ten/) güvenli kod oluşturmak için başka bir paha biçilmez bir kılavuzdur.

Yapı işlemi, üretime geçmeden önce kaynak kodundaki sorunları algılamak için tarama araçlarını yerleştirmek için iyi bir yerdir. Çoğu projenin diğer bazı paketlere bağımlılığı vardır. Eski paketleri tarayan bir araç, bir gecelik yapıda sorunları yakalar. Docker görüntüleri oluştururken bile, temel görüntünün bilinen güvenlik açıkları olmadığından emin olmak ve kontrol etmek yararlıdır. Kontrol edilmesi gereken başka bir şey de, kimsenin yanlışlıkla kimlik bilgilerini iade etmediğidir.

## <a name="built-in-security"></a>Yerleşik güvenlik

Azure, kullanıcıların çoğu için kullanılabilirlik ve güvenliği dengelemek için tasarlanmıştır. Farklı kullanıcıların farklı güvenlik gereksinimleri olacak, bu nedenle bulut güvenliğine yaklaşımlarında ince ayar yapmak zorundalar. Microsoft, [Güven Merkezi'nde](https://azure.microsoft.com/support/trust-center/)büyük miktarda güvenlik bilgisi yayımlar. Bu kaynak, yerleşik saldırı azaltma teknolojilerinin nasıl çalıştığını anlamak isteyen profesyoneller için ilk durak olmalıdır.

Azure Portalı'nda, [Azure Danışmanı](https://azure.microsoft.com/services/advisor/) sürekli olarak bir ortamı tarayan ve önerilerde bulunan bir sistemdir. Bu önerilerden bazıları kullanıcılardan para kazanmak için tasarlanmıştır, ancak diğerleri, bir depolama kapsayıcısının dünyaya açık olması ve Sanal Ağ tarafından korunmaması gibi potansiyel olarak güvensiz yapılandırmaları belirlemek üzere tasarlanmıştır.

## <a name="azure-network-infrastructure"></a>Azure ağ altyapısı

Şirket içi dağıtım ortamında, büyük miktarda enerji ağ kurmaya adanır. Yönlendiriciler, anahtarlar ve bu tür kurma karmaşık bir iştir. Ağlar, belirli kaynakların diğer kaynaklarla konuşmasına ve bazı durumlarda erişimi engellemesine olanak sağlar. Sık kullanılan ağ kuralı, yarı gelişmiş bir kod parçasının ters çalışır ve bir veri alanını siler olasılığı nedeniyle geliştirme ortamından üretim ortamına erişimi kısıtlamaktır.

Kutunun dışında, çoğu PaaS Azure kaynağı yalnızca en temel ve izin veren ağ kurulumuna sahiptir. Örneğin, Internet'teki herkes bir uygulama hizmetine erişebilir. Yeni SQL Server örnekleri genellikle kısıtlanır, böylece dış taraflar bunlara erişemez, ancak Azure tarafından kullanılan IP adresi aralıklarına izin verilir. Bu nedenle, SQL sunucusu dış tehditlere karşı korunurken, saldırganın yalnızca Azure'daki tüm SQL örneklerine karşı saldırılar başlatabilecekleri bir Azure köprü başı kurması gerekir.

Neyse ki, azure kaynaklarının çoğu daha ince taneli erişim denetimine olanak tanıyan bir Azure Sanal Ağına yerleştirilebilir. Şirket içi ağların daha geniş dünyadan korunan özel ağlar oluşturmasına benzer şekilde, sanal ağlar Azure ağı içinde bulunan özel IP adreslerine sahiptir.

![Şekil 10-1 Azure](./media/virtual-network.png)
Şekil**10-1'de**bir sanal ağ. Azure'da sanal ağ.

Şirket içi ağların ağa erişimi düzenleyen bir güvenlik duvarı olması gibi, sanal ağın sınırında da benzer bir güvenlik duvarı oluşturabilirsiniz. Varsayılan olarak, sanal ağdaki tüm kaynaklar Internet ile konuşmaya devam edebilir. Yalnızca bir tür açık güvenlik duvarı özel durumu gerektiren gelen bağlantılardır.

Ağ kurulduğunda, depolama hesapları gibi iç kaynaklar yalnızca Sanal Ağ'daki kaynaklartarafından erişime izin verecek şekilde ayarlanabilir. Bu güvenlik duvarı, depolama hesabının anahtarlarının sızdırılması halinde, saldırganların sızdırılan anahtarlardan yararlanmak için bu güvenlik düzeyine bağlanmalarını sağlar. Bu en az ayrıcalık ilkesinin başka bir örneğidir.

Azure Kubernetes kümesindeki düğümler, Azure'a daha özgü diğer kaynaklar gibi sanal bir ağa katılabilir. Bu işlevsellik [Azure Kapsayıcı Ağ Arabirimi](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md)olarak adlandırılır. Sonuç olarak, sanal ağ içinde sanal makinelerin ve konteyner görüntülerinin tahsis edildiği bir alt ağ ayırır.

En az ayrıcalık ilkesini gösteren yolda devam, sanal ağ içinde her kaynak diğer tüm kaynaklarla konuşmak gerekmez. Örneğin, bir depolama hesabı ve SQL veritabanı üzerinden web API sağlayan bir uygulamada, veritabanı ve depolama hesabının birbiriyle konuşması gerekmez. Aralarındaki herhangi bir veri paylaşımı web uygulaması üzerinden gider. Bu nedenle, bir [ağ güvenlik grubu (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) iki hizmet arasındaki trafiği reddetmek için kullanılabilir.

Kaynaklar arasındaki iletişimi reddetme ilkesi, özellikle trafik kısıtlaması olmadan Azure'u kullanma geçmişinden gelen, uygulanması rahatsız edici olabilir. Diğer bazı bulutlarda, ağ güvenlik grupları kavramı çok daha yaygındır. Örneğin, AWS'deki varsayılan ilke, kaynakların NSG'deki kurallartarafından etkinleştirilene kadar kendi aralarında iletişim kuramamalarıdır. Bunu geliştirmek daha yavaş olsa da, daha kısıtlayıcı ortam daha güvenli bir varsayılan sağlar. Özellikle izinleri yönetmek için Azure [Kaynak Yöneticisi veya Terraform'u](infrastructure-as-code.md) kullanmak, uygun DevOps uygulamalarından yararlanmak kuralları denetlemeyi kolaylaştırabilir.

Sanal Ağlar, şirket içi ve bulut kaynakları arasında iletişim kurarken de yararlı olabilir. Sanal özel ağ, iki ağı sorunsuz bir şekilde birbirine bağlamak için kullanılabilir. Bu, tüm kullanıcıların yerinde olduğu senaryolar için herhangi bir ağ geçidi olmadan sanal bir ağ çalıştırmaya olanak tanır. Bu ağı kurmak için kullanılabilecek bir dizi teknoloji vardır. En basiti, birçok yönlendirici ve Azure arasında kurulabilen [siteden siteye VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) kullanmaktır. Trafik şifrelenir ve diğer trafik gibi bayt başına aynı maliyetle Internet üzerinden tünel. Daha fazla bant genişliği veya daha fazla güvenliğin arzu edildiği senaryolarda Azure, şirket içi ağ ile Azure arasında özel bir devre kullanan [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) adlı bir hizmet sunar. Kurmak daha pahalı ve zor ama aynı zamanda daha güvenli.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Azure kaynaklarına erişimi kısıtlamak için rol tabanlı erişim denetimi

RBAC, Azure'da çalışan uygulamalariçin kimlik sağlayan bir sistemdir. Uygulamalar, anahtarları veya parolaları kullanmanın yanı sıra bu kimliği kullanarak kaynaklara erişebilir.

## <a name="security-principals"></a>Güvenlik İlkeleri

RBAC'ın ilk bileşeni bir güvenlik ilkesidir. Güvenlik sorumlusu kullanıcı, grup, hizmet sorumlusu veya yönetilen kimlik olabilir.

![Şekil 10-2 Farklı güvenlik](./media/rbac-security-principal.png)
ilkeleri şekilleri**Şekil 10-2**. Farklı güvenlik ilkeleri türleri.

- Kullanıcı - Azure Active Directory'de hesabı olan tüm kullanıcı bir kullanıcıdır.
- Grup - Azure Active Directory'den kullanıcı koleksiyonu. Bir grubun üyesi olarak, bir kullanıcı kendi ek olarak bu grubun rollerini üstleniyor.
- Hizmet sorumlusu - Hizmetlerin veya uygulamaların çalıştırıldığı bir güvenlik kimliği.
- Yönetilen kimlik - Azure tarafından yönetilen bir Azure Etkin Dizin kimliği. Yönetilen kimlikler genellikle Azure hizmetlerine kimlik bilgilerini yöneten bulut uygulamaları geliştirirken kullanılır.

Güvenlik ilkesi çoğu kaynağa uygulanabilir. Bu, Azure Kubernetes içinde çalışan bir kapsayıcıya bir güvenlik ilkesi atamanın mümkün olduğu ve Key Vault'ta depolanan sırlara erişebilmesi anlamına gelir. Azure İşlevi, bir çağrı kullanıcısı için JWT'yi doğrulamak için Etkin Dizin örneğiyle konuşmasına izin veren bir izin alabilir. Hizmetler bir hizmet ilkesiyle etkinleştirildikten sonra, izinleri roller ve kapsamlar kullanılarak parçalı olarak yönetilebilir.

## <a name="roles"></a>Roller

Bir güvenlik müdürü birçok rol alabilir veya daha sartorial bir benzetme kullanarak, birçok şapka giymek. Her rol, "Azure Hizmet Veri Hizmeti Veri Tos ucunoktasından gelen iletileri oku" gibi bir dizi izin tanımlar. Bir güvenlik ilkesinin etkili izin kümesi, güvenlik ilkesinin sahip olduğu tüm rollere atanan tüm izinlerin birleşimidir. Azure'da çok sayıda yerleşik rol vardır ve kullanıcılar kendi rollerini tanımlayabilir.

![Şekil 10-3 RBAC](./media/rbac-role-definition.png)
rol tanımları**Şekil 10-3**. RBAC rol tanımları.

Azure'da yerleşik olarak, Sahibi, Katılımcısı, Okuyucu suçlu ve Kullanıcı Hesap Yöneticisi gibi üslüs rolü de yer alıyor. Sahip rolüyle, bir güvenlik ilkesi tüm kaynaklara erişebilir ve başkalarına izin atayabilir. Katkıda bulunan kişi tüm kaynaklara aynı erişim düzeyine sahiptir, ancak izin atayamaz. Okuyucu yalnızca varolan Azure kaynaklarını görüntüleyebilir ve Bir Kullanıcı Hesabı Yöneticisi Azure kaynaklarına erişimi yönetebilir.

[DNS Zone Katılımcısı](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) gibi daha ayrıntılı yerleşik rollerin hakları tek bir hizmetle sınırlıdır. Güvenlik ilkeleri herhangi bir sayıda rol alabilir.

## <a name="scopes"></a>Kapsamlar

Roller, Azure'daki kısıtlı bir kaynak kümesine uygulanabilir. Örneğin, bir Hizmet Veri Hizmeti Veri Servisi kuyruğundan önceki okuma örneğine kapsam uygulayarak, izni tek bir kuyruğa daraltabilirsiniz: "Azure Hizmet Veri Servisi bitiş noktasından `blah.servicebus.windows.net/queue1`gelen iletileri okuyun "

Kapsam tek bir kaynak kadar dar olabilir veya tüm kaynak grubuna, aboneye ve hatta yönetim grubuna uygulanabilir.

Bir güvenlik sorumlusunun belirli bir izni olup olmadığını sınarken, rol ve kapsam birleşimi dikkate alınır. Bu kombinasyon güçlü bir yetkilendirme mekanizması sağlar.

## <a name="deny"></a>Reddet

Daha önce, RBAC için yalnızca "izin ver" kurallarına izin verilirdi. Bu davranış, bazı kapsamları oluşturmak için karmaşık yaptı. Örneğin, bir güvenlik ilkesinin, sonsuz depolama hesapları listesine açık izin verilmesi gerekmesi dışında tüm depolama hesaplarına erişmesine izin vermek. Her yeni depolama hesabı oluşturulduğunda, bu hesap listesine eklenmesi gerekir. Bu kesinlikle arzu değildi yönetim yükü ekledi.

İnkar kuralları izin kurallarından önce gelir. Şimdi aynı "bir hariç tüm" kapsamı temsil eden iki kural olarak temsil edilebilir "tüm izin" ve "bu belirli bir inkar". Kuralları reddetmek yalnızca yönetimi kolaylaştırmakla kalmıyor, aynı zamanda herkese erişimi reddederek ekstra güvenli kaynaklara da izin verir.

## <a name="checking-access"></a>Erişimi denetleme

Tahmin edebileceğiniz gibi, çok sayıda rol ve kapsama sahip olmak, bir hizmet müdürünün etkili iznini bulmak oldukça zor olabilir. Bunun üzerine kuralları kazıklama, sadece karmaşıklığı artırmak için hizmet vermektedir. Neyse ki, herhangi bir hizmet sorumlusu için etkili izinleri gösterebilen bir izin hesap makinesi vardır. Genellikle, Şekil 10-3'te gösterildiği gibi portaldaki IAM sekmesinin altında bulunur.

![Şekil 10-4 Bir uygulama](./media/check-rbac.png)
hizmeti için izin hesapmakinesi**Şekil 10-4**. Bir uygulama hizmeti için izin hesap makinesi.

## <a name="securing-secrets"></a>Sırları ngüvenliğini sağlamak

Parolalar ve sertifikalar saldırganlar için yaygın bir saldırı vektörüdür. Parola çözme donanımı kaba kuvvet saldırısı yapabilir ve saniyede milyarlarca parola tahmin etmeye çalışabilir. Bu nedenle, kaynaklara erişmek için kullanılan parolaların çok çeşitli karakterlerle güçlü olması önemlidir. Bu parolalar tam olarak hatırlanması imkansız parolalar türüdür. Neyse ki, Azure'daki parolaların aslında herhangi bir insan tarafından bilinmesi gerekmez.

Birçok güvenlik uzmanı, kendi parolalarınızı saklamak için parola yöneticisi kullanmanın en iyi yaklaşım olduğunu [öne sürer.](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) Parolalarınızı tek bir konumda merkezileştirirken, son derece karmaşık parolalar kullanmanızı ve her hesap için benzersiz olmalarını sağlar. Aynı sistem Azure'da da bulunur: sırlar için merkezi bir mağaza.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault, veritabanları, API anahtarları ve sertifikalar gibi şeyler için paroladepolamak için merkezi bir konum sağlar. Bir kez bir sır Vault girilir, bir daha asla gösterilmez ve ayıklamak ve görüntülemek için komutları kasıtlı olarak karmaşıktır. Kasadaki bilgiler yazılım şifrelemesi veya FIPS 140-2 Düzey 2 doğrulanmış Donanım Güvenlik Modülleri kullanılarak korunur.

Anahtar kasasına erişim RBAC'lar aracılığıyla sağlanır, yani sadece herhangi bir kullanıcı kasadaki bilgilere erişemez. Bir web uygulamasının Azure Key Vault'ta depolanan veritabanı bağlantı dizesine erişmek istediğini söyleyin. Erişim sağlamak için uygulamaların bir hizmet ilkesi kullanılarak çalıştırılması gerekir. Bu üstlenilen rolün altında, kasadaki sırları okuyabilirler. Bir uygulamanın kasaya erişimini daha da sınırlandırabilen, böylece sırları güncelleştiremesin, yalnızca bunları okuyabilmek için farklı güvenlik ayarları vardır.

Yalnızca beklenen uygulamaların kasaya erişebilmesini sağlamak için anahtar kasasına erişim izlenebilir. Günlükler Azure Monitor'a geri entegre edilebilmekte ve beklenmeyen koşullarla karşılaşıldığında uyarı ayarlama olanağı nın kilidi açılabilir.

## <a name="kubernetes"></a>Kubernetes

Kubernetes'te, küçük gizli bilgileri saklamak için de benzer bir hizmet var. Kubernetes Secrets tipik `kubectl` yürütülebilir üzerinden ayarlanabilir.

Bir sır oluşturmak, depolanacak değerlerin base64 sürümünü bulmak kadar basittir:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Ardından, örneğin aşağıdaki örneğe benzeyen bir `secret.yml` sırlar dosyasına ekleme:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

Son olarak, bu dosya aşağıdaki komutu çalıştırarak Kubernetes'e yüklenebilir:

```console
kubectl apply -f ./secret.yaml
```

Bu sırlar daha sonra hacimlere monte edilebilir veya ortam değişkenleri aracılığıyla kapsayıcı işlemlerine maruz kalınabilir. Uygulama oluşturmada [on iki faktörlü uygulama](https://12factor.net/) yaklaşımı, ayarları bir uygulamaya iletmek için en düşük ortak paydayı kullanmayı önerir. Ortam değişkenleri en düşük ortak paydadır, çünkü işletim sistemi veya uygulama ne olursa olsun desteklenirler.

Yerleşik Kubernetes sırlarını kullanmanın alternatifi, Azure Key Vault'taki sırlara Kubernetes'in içinden erişmektir. Bunu yapmanın en basit yolu, sırları yüklemek isteyen kapsayıcıya bir RBAC rolü atamaktır. Uygulama daha sonra sırlara erişmek için Azure Key Vault API'lerini kullanabilir. Ancak, bu yaklaşım kodda değişiklik gerektirir ve çevre değişkenlerini kullanma deseni izlemez. Bunun yerine, [Azure Anahtar Kasası Enjektörü'nün](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354)kullanımı yla değerleri bir konteynere enjekte etmek mümkündür. Bu yaklaşım aslında kümedeki kullanıcılar tarafından erişilebildiği için Kubernetes sırlarını doğrudan kullanmaktan daha güvenlidir.

## <a name="encryption-in-transit-and-at-rest"></a>Aktarım ve istirahatte şifreleme

Verileri güvende tutmak, ister diskte olsun ister çeşitli farklı hizmetler arasında geçiş yapmak önemlidir. Verilerin sızmasını engellemenin en etkili yolu, verileri başkaları tarafından kolayca okunabilen bir biçimde şifrelemektir. Azure çok çeşitli şifreleme seçeneklerini destekler.

### <a name="in-transit"></a>Transit halinde

Azure'da ağdaki trafiği şifrelemenin birkaç yolu vardır. Azure hizmetlerine erişim genellikle Aktarım Katmanı Güvenliği (TLS) kullanan bağlantılar üzerinden yapılır. Örneğin, Azure API'lerine yapılan tüm bağlantılar TLS bağlantıları gerektirir. Aynı şekilde, Azure depolama sındaki uç noktalara bağlantılar yalnızca TLS şifreli bağlantılar üzerinden çalışmak üzere sınırlandırılabilir.

TLS karmaşık bir protokoldür ve sadece bağlantının TLS kullandığını bilmek güvenliği sağlamak için yeterli değildir. Örneğin, TLS 1.0 kronik olarak güvensiz, TLS 1.1 ise çok daha iyi değildir. TLS sürümlerinde bile, bağlantıların şifresini çözmeyi kolaylaştıracak çeşitli ayarlar vardır. Yapılacak en iyi hareket, sunucu bağlantısının güncel ve iyi yapılandırılmış protokoller kullanıp kullanmamasını kontrol etmek ve görmektir.

Bu denetim, SSL laboratuvarlarının SSL Server Testi gibi harici bir hizmet tarafından yapılabilir. Tipik bir Azure bitiş noktasına karşı yapılan bir test çalışması, bu durumda bir servis veri günü bitiş noktası, neredeyse mükemmel bir A puanı verir.

Azure SQL veritabanları gibi hizmetler bile verileri gizli tutmak için TLS şifrelemekullanır. TLS kullanarak aktarım daki verileri şifrelemenin ilginç yanı, Microsoft'un bile TLS çalıştıran bilgisayarlar arasındaki bağlantıyı dinlemesinin mümkün olmamasıdır. Bu, verilerinin Microsoft uygun veya hatta standart saldırgandan daha fazla kaynağa sahip bir devlet aktörü tarafından risk altında olabileceğinden endişe duyan şirketler için konfor sağlamalıdır.

![Şekil 10-5 SSL laboratuvarları, Servis Veri Yolunun bitiş noktası için A puanını gösterir. ](./media/ssl-report.png)
 **Şekil 10-5**. SSL laboratuvarları, Hizmet Veri Meskeni bitiş noktası için A puanını gösterir.

Bu şifreleme düzeyi her zaman için yeterli olmasa da, Azure TLS bağlantılarının oldukça güvenli olduğu konusunda güven uyandırmalıdır. Azure, şifreleme geliştikçe güvenlik standartlarını geliştirmeye devam edecektir. Güvenlik standartlarını izleyen ve Azure'u iyileştirirken güncelleyen biri lerinin olduğunu bilmek güzel.

### <a name="at-rest"></a>Istirahatte

Herhangi bir uygulamada, verilerin diskte olduğu birkaç yer vardır. Uygulama kodunun kendisi bazı depolama mekanizmasından yüklenir. Çoğu uygulama aynı zamanda SQL Server, Cosmos DB, hatta inanılmaz fiyat-verimli Tablo Depolama gibi veritabanı çeşit kullanın. Bu veritabanlarının tümü, uygun izinlere sahip uygulamalar dışında kimsenin verilerinizi okuyamadığından emin olmak için ağır şifrelenmiş depolama alanı kullanır. Sistem operatörleri bile şifrelenmiş verileri okuyamaz. Böylece müşteriler gizli bilgilerinin gizli kalacağından emin olabilir.

### <a name="storage"></a>Depolama

Azure'un büyük bir kısmının temeli Azure Depolama motorudur. Sanal makine diskleri Azure Depolama'nın üstüne monte edilir. Azure Kubernetes Hizmetleri, Azure Depolama'da barındırılan sanal makinelerde çalışır. Azure İşlevleri Uygulamaları ve Azure Kapsayıcı Örnekleri gibi sunucusuz teknolojilerbile Azure Depolama'nın bir parçası olan diski biter.

Azure Depolama iyi şifrelenmişse, diğer her şeyin de şifrelenilmesi için bir temel sağlar. Azure Depolama [FIPS 140-2](https://en.wikipedia.org/wiki/FIPS_140) uyumlu [256 bit AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)ile [şifrelenir.](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) Bu, son 20 yıldır kapsamlı bir akademik incelemeye konu olan saygın bir şifreleme teknolojisidir. Şu anda, anahtarı bilmeyen birinin AES tarafından şifrelenmiş verileri okumasına izin verecek bilinen bir pratik saldırı yok.

Varsayılan olarak, Azure Depolama'yı şifrelemek için kullanılan anahtarlar Microsoft tarafından yönetilir. Bu anahtarlara kötü amaçlı erişimi önlemek için kapsamlı korumalar vardır. Ancak, belirli şifreleme gereksinimleri olan kullanıcılar Azure Key Vault'ta yönetilen [kendi depolama anahtarlarını](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) da sağlayabilirler. Bu anahtarlar herhangi bir zamanda iptal edilebilir ve bu da Depolama hesabının içeriğini erişilemez hale getirir.

Sanal makineler şifreli depolama kullanır, ancak Windows'daki BitLocker veya Linux'ta DM-Crypt gibi teknolojileri kullanarak başka bir şifreleme katmanı sağlamak mümkündür. Bu teknolojiler, disk görüntüsü depodan sızdırılmış olsa bile, onu okumak neredeyse imkansız kalır anlamına gelir.

### <a name="azure-sql"></a>Azure SQL

Azure SQL'de barındırılan veritabanları, verilerin şifrelenmeyi sürdürmesini sağlamak için [Saydam Veri Şifreleme (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) adlı bir teknoloji kullanır. Yeni oluşturulan tüm SQL veritabanlarında varsayılan olarak etkinleştirilir, ancak eski veritabanları için el ile etkinleştirilmelidir. TDE, sadece veritabanının değil, yedeklemelerin ve işlem günlüklerinin de gerçek zamanlı şifrelemeve şifre çözme işlemlerini yürütür.

Şifreleme parametreleri `master` veritabanında depolanır ve başlangıçta, kalan işlemler için belleğe okunur. Bu, veritabanının `master` şifrelenmemiş kalması gerektiği anlamına gelir. Gerçek anahtar Microsoft tarafından yönetilir. Ancak, titiz güvenlik gereksinimleri olan kullanıcılar, Azure Depolama'da olduğu gibi Key Vault'ta da kendi anahtarlarını sağlayabilirler. Anahtar Kasası, anahtar döndürme ve iptal gibi hizmetler sağlar.

TDS'nin "Saydam" bölümü, şifreli bir veritabanını kullanmak için gereken istemci değişiklikleri nin olmamasından kaynaklanır. Bu yaklaşım iyi bir güvenlik sağlarken, veritabanı parolasını sızdırmak kullanıcıların verilerin şifresini çözebilmesi için yeterlidir. Veritabanındaki tek tek sütunları veya tabloları şifreleyen başka bir yaklaşım daha vardır. [Her zaman Şifrelenmiş,](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) şifrelenmiş verilerin hiçbir noktada veritabanı içinde düz metin de görünmesini sağlar.

Bu şifreleme katmanının ayarlanması, şifreleme nin türünü ve ilişkili anahtarları depolamak için Key Vault'ta nerede olduğunu seçmek için SQL Server Management Studio'da bir sihirbaz aracılığıyla çalışma gerektirir.

![Şekil 10-6 Her Zaman Şifrelenmiş](./media/always-encrypted.png)
Şekil**10-6**kullanılarak şifrelenecek bir tablodaki sütunları seçmek. Her Zaman Şifrelenmiş kullanarak şifrelenecek bir tablodaki sütunları seçmek.

Bu şifrelenmiş sütunlardan bilgileri okuyan istemci uygulamalarının, şifrelenmiş verileri okumak için özel izinler ödemesi gerekir. Bağlantı dizeleri ile `Column Encryption Setting=Enabled` güncelleştirilmeli ve istemci kimlik bilgileri Anahtar Kasa'dan alınmalıdır. SQL Server istemcisi daha sonra sütun şifreleme anahtarları ile astarlanmış olmalıdır. Bu yapıldıktan sonra, kalan eylemler SQL Client için standart arabirimleri kullanır. Diğer bir diğer olarak, SQL Client'ın üzerine inşa edilen Dapper ve Entity Framework gibi araçlar değişiklik yapmadan çalışmaya devam edecektir. Her Zaman Şifrelenmiş henüz her dildeki her SQL Server sürücüsü için kullanılamayabilir.

Her ikisi de istemciye özgü anahtarlarla kullanılabilen TDE ve Her Zaman Şifrelenmiş kombinasyonu, en titiz şifreleme gereksinimlerinin bile desteklenmesini sağlar.

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB, Microsoft tarafından Azure'da sağlanan en yeni veritabanıdır. Güvenlik ve kriptografi göz önünde bulundurularak sıfırdan inşa edilmiştir. AES-256bit şifreleme tüm Cosmos DB veritabanları için standarttır ve devre dışı tutulamaz. TLS 1.2 iletişim gereksinimi ile birleştiğinde, tüm depolama çözümü şifrelenir.

![Şekil 10-7 Cosmos DB](./media/cosmos-encryption.png)
Şekil**10-7**içindeki veri şifreleme akışı. Cosmos DB içindeki veri şifreleme akışı.

Cosmos DB müşteri şifreleme anahtarları sağlamak için sağlamaz iken, bu olmadan PCI-DSS uyumlu kalmasını sağlamak için ekip tarafından yapılan önemli çalışmalar olmuştur. Cosmos DB, Azure SQL'deki Always Encrypted'e benzer herhangi bir sütun şifrelemesini de desteklemez.

## <a name="keeping-secure"></a>Güvenli tutma

Azure, son derece güvenli bir ürün piyasaya çıkarmak için gereken tüm araçlara sahiptir. Ancak, bir zincir sadece en zayıf halkası kadar güçlüdür. Azure'un üstüne dağıtılan uygulamalar uygun bir güvenlik zihniyeti ve iyi güvenlik denetimleri ile geliştirilmemişse, zincirdeki zayıf halka haline gelir. Azure'da yüklü olan yazılımın Azure'un kendisi kadar güvenli olmasını sağlamak için kullanılabilecek birçok büyük statik analiz aracı, şifreleme kitaplıkları ve güvenlik uygulamaları vardır. Örnekler [statik analiz araçları,](https://www.whitesourcesoftware.com/) [şifreleme kitaplıkları](https://www.libressl.org/)ve [güvenlik uygulamaları](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)içerir.

>[!div class="step-by-step"]
>[Önceki](security.md)
>[Sonraki](devops.md)
