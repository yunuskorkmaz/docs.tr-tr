---
title: Bulutta yerel uygulamalar için Azure güvenliği
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native uygulamalar için Azure güvenliği
ms.date: 05/13/2020
ms.openlocfilehash: 223d9e77aca611697958981bf2ee3a630fb9fffb
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374500"
---
# <a name="azure-security-for-cloud-native-apps"></a>Bulutta yerel uygulamalar için Azure güvenliği

Bulutta yerel uygulamalar, geleneksel uygulamalardan güvenli şekilde daha kolay ve daha zor olabilir. Alt tarafta, daha küçük uygulamalar için güvenli hale getirmeniz ve güvenlik altyapısını oluşturmak için daha fazla enerji ayırmanız gerekir. Çoğu hizmet dağıtımında programlama dillerinin ve stillerinin heterojen doğası da birçok farklı sağlayıcıdan güvenlik bültenlerine daha fazla dikkat etmeniz gereken anlamına gelir.

Ters çevir tarafında, her biri kendi veri deposuna sahip olan daha küçük hizmetler, bir saldırının kapsamını sınırlar. Bir saldırgan tek bir sistemi zorlayıyorsa, saldırganın tek parçalı bir uygulamada olduğundan başka bir sisteme atlamasını daha zor olabilir. İşlem sınırları güçlü sınırlardır. Ayrıca, bir veritabanı yedeklemesi sızıntıbulunursa, veritabanının yalnızca bir veri alt kümesini içermesi ve kişisel verilerin içermesi olası olması nedeniyle hasar daha sınırlı olur.

## <a name="threat-modeling"></a>Tehdit modelleme

Avantaj, bulutta yerel uygulamaların dezavantajlarının olumsuz yönlerini anlamazsa, aynı bütünsel Security anlayış 'in izlenmesi gerekir. Güvenlik ve güvenli düşünce, geliştirme ve işlemler hikayesinin her adımının bir parçası olmalıdır. Bir uygulamayı planlarken şu gibi sorular sorun:

- Bu verilerin kaybedilmesi ne olur?
- Bu hizmete eklenen hatalı verilerin hasar sayısını nasıl sınırlayabiliriz?
- Bu verilere kimler erişebilsin?
- Geliştirme ve yayınlama sürecinin çevresinde denetim ilkeleri var mı?

Tüm bu sorular [tehdit modelleme](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool)adlı bir işlemin parçasıdır. Bu işlem, sisteme ne kadar tehdit olduğunu, tehditlerin ne olasılığından ve potansiyel olarak ne kadar hasar olduğunu yanıtlamaya çalışır.

Tehditler listesi kurulduktan sonra, bunların azaltıcı olup olmadığına karar vermeniz gerekir. Bazen tehdit, bunun üzerinde enerji harcamamasının planlanmaması açısından çok düşüktür ve pahalıdır. Örneğin, bazı durum düzeyi aktör, milyonlarca cihaz tarafından kullanılan bir işlemin tasarımına değişiklikler ekleyebilir. Artık, [halka 3](https://en.wikipedia.org/wiki/Protection_ring)' te belirli bir kod parçasını çalıştırmak yerine, bu kod halka 0 ' da çalıştırılır. Bu, hiper yöneticiyi atlayabilmesine ve saldırı kodunu çıplak makinelerde çalıştırabilmesine olanak tanıyarak, bu donanımda çalışan tüm sanal makinelerde saldırılara izin verir.

Değiştirilen işlemcilerin, mikro bir kapsam olmadan algılanmaları ve bu işlemcinin açık bir tasarımı hakkında bilgi sahibi olmanız zordur. Bu senaryonun gerçekleşmesi ve hafifletmemesi, büyük olasılıkla hiçbir tehdit modelinin bunun için yararlanma koruması oluşturulmasını önermez.

`Id`Saldırıları arttırmaya (URL 'de ile değiştirme) veya SQL ekleme saldırılarına izin veren bozuk erişim denetimleri gibi daha olası tehditler, `Id=2` `Id=3` korumaları geliştirmek için daha çekici bir olasılıktır. Bu tehditlere yönelik azaltmaları, şirketin saygınlığını sunan embarırmet güvenlik boşluklarını derlemek ve engellemek için oldukça mantıklı.

## <a name="principle-of-least-privilege"></a>En az ayrıcalık ilkesi

Bilgisayar güvenliği 'ndeki temel fikirlerden biri, en az ayrıcalık (POLP) prensibi. Bu aslında büyük bir güvenlik biçiminin dijital veya fiziksel olduğu bir temel fikir olabilir. Kısacası, herhangi bir kullanıcının veya işlemin, görevini yürütmek için gereken en az sayıda haklara sahip olması gerekir.

Örnek olarak, bir bankadaki teller göz önünde bulundurun: güvenli erişim, yaygın olmayan bir etkinliktir. Bu nedenle, ortalama teller güvenli bir şekilde kendini açamaz. Erişim kazanmak için, isteklerini ek güvenlik denetimleri gerçekleştiren bir banka Yöneticisi aracılığıyla ilerlemeleri gerekir.

Bir bilgisayar sisteminde, harika bir örnek, bir veritabanına bağlanan Kullanıcı haklarından oluşur. Çoğu durumda, veritabanı yapısını derlemek ve uygulamayı çalıştırmak için kullanılan tek bir kullanıcı hesabı vardır. Olağanüstü durumlar dışında, uygulamayı çalıştıran hesabın şema bilgilerini güncelleştirme yeteneğinin olması gerekmez. Farklı ayrıcalık düzeyleri sağlayan birkaç hesap olmalıdır. Uygulama yalnızca tablolardaki verilere okuma ve yazma erişimi veren izin düzeyini kullanmalıdır. Bu tür bir koruma, veritabanı tablolarını bırakmayı veya kötü amaçlı Tetikleyicileri ortaya çıkaracak saldırıları ortadan kaldırır.

Bulutta yerel bir uygulama oluşturmanın neredeyse her bölümü, en az ayrıcalık ilkesini hatırlayıp yararlı olabilir. Rol tabanlı erişim denetimi (RBAC) içinde güvenlik duvarları, ağ güvenlik grupları, roller ve kapsamlar ayarlarken bu dosyayı yürütmeye ulaşabilirsiniz.

## <a name="penetration-testing"></a>Sızma testi

Uygulamalar daha karmaşık hale geldiğinde, bir alarma hızında saldırı vektörü sayısı artar. Tehdit modellemesi, sistemi oluşturan kişilerle aynı şekilde yürütüldüğünü eğilimi gösterir. Birçok geliştiricinin Kullanıcı etkileşimleriyle ilgili sorunları planlama ve ardından kullanım dışı Kullanıcı arabirimleri oluştururken, çoğu geliştirici her saldırı vektörünü görmekte güçlük çekiyor. Ayrıca, sistemi oluşturan geliştiricilerin saldırı yöntemleri açısından önemli değildir ve önemli bir şeyi kaçırmamak da mümkündür.

Sızma testi veya "kalem testi", sisteme saldırmayı denemek için dış aktörlerin oluşturulmasını içerir. Bu saldırganlar, bir dış danışmanlık şirketi veya iş diğer bir bölümünden daha iyi güvenlik bilgisine sahip diğer geliştiriciler olabilir. Bu kişiler, sistemi dikey olarak ayırmak için planın sağladığı Blanche 'e verilirler. Sık sık düzeltme olması gereken kapsamlı güvenlik delikleri bulacaksınız. Bazen saldırı vektörü, CEO ile karşı bir sızdırma saldırısından yararlanmak gibi tamamen beklenmedik bir şekilde görünür.

Azure 'un kendisi, [Microsoft içindeki bir bilgisayar korsanlarından](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)sürekli saldırılardır. Yıllarca, bunlar dışarıdan yararlanmadan önce çok zararlı olabilecek saldırı vektörlerini ilk kez bulmaktan önce yaptık. Bir hedefin daha fazla olması halinde, dış aktörlerin bundan büyük olasılıkla faydalanma olasılığı yüksektir ve dünyanın dört bir yanındaki Azure 'dan daha fazla sayıda hedef vardır.

## <a name="monitoring"></a>İzleme

Bir saldırgan bir uygulamaya sızma denemesi yapmanız gerekir, bunun bir uyarı olması gerekir. Sık sık saldırılar, hizmetlerden günlükleri inceleyerek daha fazla bulunabilir. Saldırılar, başarılı bir şekilde başarısız olabilecek telltişaretlerini bırakabilir. Örneğin, bir parolayı tahmin etmeye çalışan bir saldırgan, oturum açma sistemine çok sayıda istek yapar. Oturum açma sistemi etrafında izlemek, tipik erişim düzeniyle satır dışı olan tuhaf desenlerini algılayabilir. Bu izleme, bir işlem kişisini, bir dizi onay ölçümünü etkinleştirmek üzere uyarabilecek bir uyarıya dönüştürülebilir. Yüksek derecede çok büyük bir izleme sistemi, istekleri engellemek veya yanıtları kısıtlamak için kuralları eklemek için bu sapmaları temel alan işlem gerçekleştirebilir.

## <a name="securing-the-build"></a>Derlemeyi güvenli hale getirme

Güvenliğin genellikle yapı sürecinin etrafında olduğu bir yerdir. Yalnızca, derleme, güvenli olmayan kod veya iade kimlik bilgileri için tarama gibi güvenlik denetimleri çalıştırmamalıdır, ancak yapılandırmanın kendisi güvende olmalıdır. Yapı sunucusu tehlikeye girerse, ürüne rastgele kod tanıtımı için harika bir vektör sağlar.

Bir saldırganın bir Web uygulamasında oturum açan kişilerin parolalarını çalmak için bakmasını düşünün. Başka bir sunucuya herhangi bir oturum açma isteğini yansıtmak için, kullanıma alınan kodu değiştiren bir yapı adımı ortaya çıkarabilir. Bir sonraki kod derlemeden geçtiğinde sessizce güncelleştirilir. Kaynak kodu güvenlik açığı taraması, derlemeden önce çalıştığı için bunu yakalamaz. Aynı şekilde, derleme adımları yapı sunucusunda canlı olduğundan, hiçbir kimse onu bir kod incelemesinin içinde yakalayamaz. Yararlanılabilen kod, parolaların nereden bir şekilde bir yere gidebileceği üretime gider. Büyük olasılıkla, derleme işlemi değişikliklerinden bir denetim günlüğü yok veya en az bir zaman denetimini izlemiyor.

Bu, sisteme bölmek için kullanılabilecek, en düşük bir değer hedefine yönelik kusursuz bir örnektir. Bir saldırgan sistemin çevre ağına ulaştığında, izinlerini, istedikleri yere gerçek zarar verebilecek bir noktaya yükseltmek için yollar bulmaya başlayabilir.

## <a name="building-secure-code"></a>Güvenli kod oluşturma

.NET Framework zaten güvenli bir çerçeve. Bu, dizilerin uçlarını yürüyerek yönetilmeyen kodların bazı bazı türlerini önler. Çalışma, keşfedildiği şekilde güvenlik boşluklarını gidermek için etkin bir şekilde yapılır. Hatta, aracıdaki sorunları bulmak ve bunları yararlanmak yerine onları raporlamak için araştırmacıları ödeyen bir [hata sıçratı programı](https://www.microsoft.com/msrc/bounty) vardır.

.NET kodunu daha güvenli hale getirmek için birçok yol vardır. [.Net Için güvenli kodlama yönergeleri](../../standard/security/secure-coding-guidelines.md) gibi yönergeler, kodun baştan sona güvendiğinden emin olmak için makul bir adımdır. [OWASP en iyi 10](https://owasp.org/www-project-top-ten/) , güvenli kod oluşturmaya yönelik başka bir değerli kılavuzdur.

Yapı işlemi, kaynak kodundaki sorunları üretime yapmadan önce saptamak için tarama araçlarını koymak için iyi bir yerdir. Çoğu projenin diğer bazı paketlere bağımlılıkları vardır. Güncel olmayan paketleri tarayabileceğiniz bir araç, gecelik bir derlemede sorunları yakalar. Docker görüntülerini oluştururken bile, temel görüntüde bilinen güvenlik açıklarına sahip olmadığından emin olmak ve denetlemek yararlı olur. Denetlenecek başka bir şey, hiçbir kimsenin kimlik bilgilerini yanlışlıkla denetledi.

## <a name="built-in-security"></a>Yerleşik güvenlik

Azure, kullanıcıların çoğunluğu için kullanılabilirliği ve güvenliği dengelemek üzere tasarlanmıştır. Farklı kullanıcılar farklı güvenlik gereksinimlerine sahip olacak ve bu nedenle bulut güvenliğine yaklaşımına ince ayar yapması gerekir. Microsoft [Güven Merkezi](https://azure.microsoft.com/support/trust-center/)'nde harika bir güvenlik bilgisi yayınlar. Bu kaynak, yerleşik saldırı risk azaltma teknolojilerinin nasıl çalıştığını anlamak isteyen bu profesyonellerin ilk durağı olmalıdır.

[Azure danışmanı](https://azure.microsoft.com/services/advisor/) Azure Portal içinde, sürekli olarak bir ortamı tarayan ve öneriler getiren bir sistemdir. Bu önerilerin bazıları kullanıcıları paradan tasarruf etmek için tasarlanmıştır, ancak diğerleri, bir depolama kapsayıcısının dünya çapında açık olması ve bir sanal ağ tarafından korunmamasından dolayı, güvensiz olabilecek yapılandırmaların tanımlanması için tasarlanmıştır.

## <a name="azure-network-infrastructure"></a>Azure ağ altyapısı

Şirket içi dağıtım ortamında, ağ kurulması için harika bir enerji kullanımı idealdir. Yönlendiricileri, anahtarları ve bu tür karmaşık işleri ayarlama. Ağlar belirli kaynakların diğer kaynaklarla iletişim kurmasına ve bazı durumlarda erişimi engellemesine olanak tanır. Sık kullanılan bir ağ kuralı, geliştirme ortamından üretim ortamına erişimi, yarı geliştirilmiş bir kod parçasının awry çalıştırması ve çok fazla veri silmesi ihtimaline karşı kısıtlamasıdır.

Çoğu PaaS Azure kaynaklarının çoğu, en temel ve izin veren ağ kurulumuna sahiptir. Örneğin, Internet üzerindeki herkes bir App Service 'e erişebilir. Yeni SQL Server örnekleri genellikle sınırlı gelir, böylece dış taraflar bunlara erişemez, ancak Azure tarafından kullanılan IP adresi aralıklarına aracılığıyla izin verilir. Bu nedenle, SQL Server dış tehditlerden korunurken, bir saldırganın yalnızca Azure 'daki tüm SQL örneklerine karşı saldırıları başlatabilecekleri Azure köprü kurucu ayarlaması gerekir.

Neyse ki, çoğu Azure kaynağı daha ayrıntılı erişim denetimi sağlayan bir Azure sanal ağına yerleştirilebilir. Şirket içi ağların, daha geniş dünyadan korunan özel ağları oluşturma yöntemine benzer şekilde, sanal ağlar Azure ağı içinde bulunan özel IP adresi Adaları 'lardır.

![Şekil 9-1 Azure 'da bir sanal ağ](./media/virtual-network.png)

**Şekil 9-1**. Azure 'da bir sanal ağ.

Şirket içi ağların ağa erişimi yöneten bir güvenlik duvarı olduğu şekilde, sanal ağın sınırında benzer bir güvenlik duvarı kurabilirsiniz. Varsayılan olarak, bir sanal ağdaki tüm kaynaklar yine de Internet ile konuşabilir. Yalnızca bazı açık güvenlik duvarı özel durumu gerektiren gelen bağlantılarıdır.

Ağ oluşturulduğunda, depolama hesapları gibi iç kaynaklar yalnızca sanal ağ üzerindeki kaynaklara göre erişime izin verecek şekilde ayarlanabilir. Bu güvenlik duvarı, daha fazla güvenlik düzeyi sağlar ve bu depolama hesabı için anahtarlar sızmış olması gerekir. saldırganlar, sızan anahtarlarla yararlanmaya yönelik bağlantı kurabiliyor. Bu, en az ayrıcalık prensibi bir örnektir.

Azure Kubernetes kümesindeki düğümler, Azure 'da daha doğal olan diğer kaynaklar gibi sanal bir ağa katılabilir. Bu işlevselliğe [Azure Container Networking arabirimi](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md)adı verilir. Aslında, sanal makinelerin ve kapsayıcı görüntülerinin ayrıldığı sanal ağ içinde bir alt ağ ayırır.

Bir sanal ağ içindeki her kaynağın diğer her kaynakla iletişim kurmasını sağlamak için, en az ayrıcalık ilkesini gösteren yolun sonuna kadar devam edin. Örneğin, bir depolama hesabı ve SQL veritabanı üzerinde Web API 'SI sağlayan bir uygulamada, veritabanının ve depolama hesabının birbirleriyle iletişim kurmasına gerek yoktur. Aralarında herhangi bir veri paylaşımı web uygulamasına gider. Bu nedenle, iki hizmet arasındaki trafiği reddetmek için bir [ağ güvenlik grubu (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) kullanılabilir.

Kaynaklar arasındaki iletişimi reddetme ilkesi, özellikle de trafik kısıtlamaları olmadan Azure kullanmanın bir arka planıyla gelen uygulama için sinir bozucu olabilir. Diğer bulutlarda, ağ güvenlik grupları kavramı çok daha yaygındır. Örneğin, AWS üzerindeki varsayılan ilke, bir NSG 'de kurallar tarafından etkinleştirilinceye kadar kaynaklar kendileri arasında iletişim kuramaz. Bunu geliştirmekten daha yavaş olsa da, daha kısıtlayıcı bir ortam daha güvenli bir varsayılan değer sağlar. Uygun DevOps uygulamalarından yararlanarak, özellikle izinleri yönetmek için [Azure Resource Manager ya da Terlarform](infrastructure-as-code.md) kullanmak kuralların denetlenmesine daha kolay hale getirir.

Sanal ağlar, şirket içi ve bulut kaynakları arasında iletişim kurarken da yararlı olabilir. Bir sanal özel ağ, iki ağı sorunsuzca birlikte eklemek için kullanılabilir. Bu, tüm kullanıcıların yerinde olduğu senaryolar için herhangi bir ağ geçidi sıralaması olmadan bir sanal ağın çalıştırılmasını sağlar. Bu ağı kurmak için kullanılabilecek çeşitli teknolojiler vardır. En basit, birçok yönlendirici ve Azure arasında kurulabilirler, [siteden sıteye VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) kullanmaktır. Trafik, Internet üzerinden, diğer tüm trafik olarak bayt başına aynı maliyetten şifrelenir ve tünel oluşturulur. Daha fazla bant genişliği veya daha fazla güvenlik istenmekte olan senaryolarda Azure, şirket içi ağ ile Azure arasında özel bir bağlantı hattı kullanan [Express Route](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) adlı bir hizmet sunar. Daha pahalı ve daha da güvenli hale gelir.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Azure kaynaklarına erişimi kısıtlamak için rol tabanlı erişim denetimi

RBAC, Azure 'da çalışan uygulamalara kimlik sağlayan bir sistemdir. Uygulamalar, anahtarları veya parolaları kullanmanın yanı sıra bu kimliği kullanarak kaynaklara erişebilir.

## <a name="security-principals"></a>Güvenlik sorumluları

RBAC 'deki ilk bileşen bir güvenlik sorumlusidir. Bir güvenlik sorumlusu, bir Kullanıcı, Grup, hizmet sorumlusu veya yönetilen kimlik olabilir.

![Şekil 9-2 farklı türlerde güvenlik sorumluları](./media/rbac-security-principal.png)

**Şekil 9-2**. Farklı türlerde güvenlik sorumluları.

- Kullanıcı-Azure Active Directory bir hesabı olan herhangi bir Kullanıcı, bir kullanıcı.
- Grup-Azure Active Directory bir kullanıcı koleksiyonu. Bir grubun üyesi olarak, bir Kullanıcı, kendilerine ek olarak o grubun rollerini de alır.
- Hizmet sorumlusu-hizmetlerin veya uygulamaların çalıştırıldığı bir güvenlik kimliği.
- Yönetilen kimlik-Azure tarafından yönetilen bir Azure Active Directory kimliği. Yönetilen kimlikler genellikle Azure hizmetlerinde kimlik doğrulaması için kimlik bilgilerini yöneten bulut uygulamaları geliştirilirken kullanılır.

Güvenlik sorumlusu her bir kaynağa uygulanabilir. Bu, Azure Kubernetes içinde çalışan bir kapsayıcıya bir güvenlik sorumlusu atamak ve bunun Key Vault depolanan gizli dizilerle erişmesine izin vermek mümkün olduğu anlamına gelir. Azure Işlevi, çağıran bir kullanıcı için bir JWT doğrulamak üzere bir Active Directory örneğiyle iletişim kurmasına izin veren bir izni alabilir. Hizmet sorumlusu ile hizmetler etkinleştirildikten sonra, izinleri roller ve kapsamlar kullanılarak yönetilebilir.

## <a name="roles"></a>Roller

Bir güvenlik sorumlusu birçok rolü veya daha fazla bir benzerleme vurguladı, aşı birçok HATS 'yi kullanarak alabilir. Her rol, "Azure Service Bus uç noktasından iletileri oku" gibi bir dizi izin tanımlar. Güvenlik sorumlusu etkin izin kümesi, güvenlik sorumlusu 'nın sahip olduğu tüm rollere atanan tüm izinlerin birleşimidir. Azure 'da çok sayıda yerleşik rol bulunur ve kullanıcılar kendi rollerini tanımlayabilirler.

![Şekil 9-3 RBAC rol tanımları](./media/rbac-role-definition.png)

**Şekil 9-3**. RBAC rol tanımları.

Azure 'da yerleşik olarak, sahip, katkıda bulunan, okuyucu ve Kullanıcı hesabı Yöneticisi gibi birçok üst düzey rol de vardır. Sahip rolüyle, bir güvenlik sorumlusu tüm kaynaklara erişebilir ve diğerlerine izin atayabilir. Katkıda bulunan, tüm kaynaklara aynı düzeyde erişime sahiptir ancak izin atayamazlar. Okuyucu yalnızca mevcut Azure kaynaklarını görüntüleyebilir ve bir kullanıcı hesabı Yöneticisi, Azure kaynaklarına erişimi yönetebilir.

[DNS bölgesi katılımcısı](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) gibi daha ayrıntılı yerleşik roller, tek bir hizmetle sınırlı haklara sahiptir. Güvenlik sorumluları, herhangi bir sayıda rol alabilir.

## <a name="scopes"></a>Kapsamlar

Roller, Azure 'daki kısıtlanmış bir kaynak kümesine uygulanabilir. Örneğin, bir Service Bus sırasından daha önceki bir örneğe kapsam uygulayarak, tek bir sıraya yönelik izni daraltabilirsiniz: "iletileri Azure Service Bus uç noktadan oku `blah.servicebus.windows.net/queue1` "

Kapsam tek bir kaynak kadar dar olabilir veya bir kaynak grubuna, aboneliğe veya hatta yönetim grubuna uygulanabilir.

Bir güvenlik sorumlusunun belirli bir izni varsa test edilirken rol ve kapsamın birleşimi hesaba alınır. Bu bileşim, güçlü bir yetkilendirme mekanizması sağlar.

## <a name="deny"></a>Reddet

Daha önce RBAC için yalnızca "izin ver" kurallara izin verilir. Bu davranış, derleme için karmaşık bazı kapsamlar yaptı. Örneğin, bir güvenlik sorumlusu, bir depolama hesaplarının potansiyel olarak sonsuz bir listesine açık izin verilmesi dışında tüm depolama hesaplarına erişimine izin verir. Her yeni depolama hesabı oluşturulduğunda, bu hesap listesine eklenmelidir. Bu, kesinlikle istenen yönetim yükünü ekledi.

Reddetme kuralları izin verme kurallarına göre önceliklidir. Artık aynı "tümüne izin ver" dışında bir kapsamın temsil edilebilmesi, "tümüne izin ver" ve "Bu tek tek Reddet" şeklinde iki kural olarak temsil edilebilir. Reddetme kuralları, her bir gövdeye erişimi reddeterek yönetimi yalnızca yönetim kolaylığı sağlar ancak ekstra güvenli kaynaklar için izin verir.

## <a name="checking-access"></a>Erişim denetleniyor

Imagine de, çok sayıda rol ve kapsamın olması, hizmet sorumlusunun etkin iznini belirlemek oldukça zordur. Üzerinde engelleyen reddetme kuralları, yalnızca karmaşıklığın arttırmasını sağlar. Neyse ki, herhangi bir hizmet sorumlusu için etkili izinleri gösterebilmiş bir izin Hesaplayıcısı vardır. Normalde, Şekil 10-3 ' de gösterildiği gibi, portaldaki ıAM sekmesinde bulunur.

![Şekil 9-4 bir App Service için Izin Hesaplayıcı](./media/check-rbac.png)

**Şekil 9-4**. Bir App Service için izin Hesaplayıcı.

## <a name="securing-secrets"></a>Gizli dizileri güvenli hale getirme

Parolalar ve sertifikalar, saldırganlar için ortak bir saldırı vektördür. Parola çözme donanımı, bir deneme yanılma saldırısı yapabilir ve saniye başına milyarlarca parola tahmin etmeye çalışabilir. Bu nedenle, kaynaklara erişmek için kullanılan parolaların çok çeşitli karakterlerle güçlü olması önemlidir. Bu parolalar tam olarak anımsanması olanaksız olan parolaların türüdür. Neyse ki, Azure 'daki parolaların gerçekten herhangi bir insan tarafından bilinmesi gerekmez.

Birçok güvenlik [uzmanı](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) , kendi parolalarınızı korumak için parola Yöneticisi kullanmanın en iyi yaklaşım olduğunu önerir. Parolalarınızı tek bir konumda merkezileştirirken, son derece karmaşık parolaların kullanılmasına ve her hesap için benzersiz olduklarından emin olmayı sağlar. Azure 'da aynı sistem vardır: gizlilikler için merkezi bir mağaza.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault veritabanları, API anahtarları ve sertifikalar gibi şeyler için parolaları depolamak üzere merkezi bir konum sağlar. Kasaya bir gizli dizi girildiğinde bu, hiçbir zaman bir daha gösterilmemiştir ve bunu çıkarmak ve görüntülemek için komutlar tam olarak karmaşıktır. Güvende bilgiler yazılım şifrelemesi veya FIPS 140-2 düzey 2 tarafından doğrulanan donanım güvenliği modülleri kullanılarak korunur.

Anahtar kasasına erişim RBACs üzerinden sağlanır. Bu, kasadaki bilgilere yalnızca herhangi bir kullanıcının erişemeyeceği anlamına gelir. Bir Web uygulamasının Azure Key Vault ' de depolanan veritabanı bağlantı dizesine erişmesini söylediklerini varsayalım. Erişim kazanmak için uygulamaların bir hizmet sorumlusu kullanarak çalıştırılması gerekir. Bu kabul edilen rolün altında gizli dizileri güvenli bir şekilde okuyabilirler. Bir uygulamanın kasaya sahip olduğu erişimi daha fazla sınırlayabilmesi için bir dizi farklı güvenlik ayarı vardır. bu sayede gizli dizileri güncelleştiremez, ancak yalnızca bunları okuyabilir.

Yalnızca beklenen uygulamaların kasaya eriştiğinden emin olmak için anahtar kasasına erişim izlenebilir. Günlükler, Azure Izleyici ile tümleştirilebilir ve beklenmeyen koşullara göre uyarı ayarlama yeteneğinin kilidini açabilir.

## <a name="kubernetes"></a>Kubernetes

Kubernetes içinde, küçük gizli bilgi parçalarını korumak için benzer bir hizmet vardır. Kubernetes gizli dizileri, tipik `kubectl` yürütülebilir dosya aracılığıyla ayarlanabilir.

Gizli dizi oluşturmak, depolanacak değerlerin Base64 sürümünü bulmak kadar basittir:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Ardından `secret.yml` , aşağıdaki örneğe benzer bir örnek olarak adlı bir gizli dizi dosyasına ekleyin:

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

Son olarak, bu dosya aşağıdaki komut çalıştırılarak Kubernetes içine yüklenebilir:

```console
kubectl apply -f ./secret.yaml
```

Bu gizlilikler daha sonra birimlere bağlanabilir veya ortam değişkenleri aracılığıyla kapsayıcı işlemlerine sunulabilir. Uygulamalar oluşturmaya yönelik [on iki öğeli uygulama](https://12factor.net/) yaklaşımı, ayarları bir uygulamaya aktarmak için en düşük ortak paydayı kullanmayı önerir. İşletim sistemi veya uygulamadan bağımsız olarak desteklendiklerinden, ortam değişkenleri en düşük ortak paydatır.

Yerleşik Kubernetes gizliliklerini kullanmanın bir alternatifi, Kubernetes içindeki Azure Key Vault gizli dizilerle erişimdir. Bunu yapmanın en kolay yolu, yük gizli dizilerini bulmak için kapsayıcıya bir RBAC rolü atamak. Uygulama daha sonra gizli dizileri erişmek için Azure Key Vault API 'Lerini kullanabilir. Ancak, bu yaklaşım kodda değişiklik yapılmasını gerektirir ve ortam değişkenlerini kullanma örüntüsünün izmez. Bunun yerine, [Azure Key Vault Injector](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354)kullanımı aracılığıyla bir kapsayıcıya değer eklemek mümkündür. Bu yaklaşım aslında doğrudan Kubernetes gizli dizileri kullanmaktan daha güvenlidir, çünkü bunlar kümedeki kullanıcılar tarafından erişilebilirler.

## <a name="encryption-in-transit-and-at-rest"></a>Aktarım ve bekleme sırasında şifreleme

Verilerin güvende tutulması, disk üzerinde veya farklı hizmetler arasında geçiş yapılıp yapılmayacağını önemli hale gelir. Verileri sızma göre tutmanın en etkili yolu, başkalarının tarafından kolayca okuyameyen bir biçimde şifrelemedir. Azure, çok çeşitli şifreleme seçeneklerini destekler.

### <a name="in-transit"></a>Yoldaki

Azure 'da ağ üzerindeki trafiği şifrelemek için birkaç yol vardır. Azure hizmetlerine erişim, genellikle Aktarım Katmanı Güvenliği (TLS) kullanan bağlantılar üzerinden yapılır. Örneğin, Azure API 'Lerine yönelik tüm bağlantılar TLS bağlantısı gerektirir. Aynı şekilde, Azure Storage 'daki uç noktalara yapılan bağlantılar yalnızca TLS şifreli bağlantı üzerinden çalışacak şekilde kısıtlanabilir.

TLS karmaşık bir protokoldür ve güvenlik sağlamak için bağlantının TLS kullandığını bilmek yeterlidir. Örneğin, TLS 1,0, zaman içinde güvensiz ve TLS 1,1 çok daha iyi değildir. TLS sürümleri içinde bile, bağlantıların şifresinin çözülmesi daha kolay hale getirmek için çeşitli ayarlar vardır. En iyi eylem, sunucu bağlantısının güncel ve iyi yapılandırılmış protokoller kullanıp kullanmamakta olup olmadığını kontrol etmek ve göz atın.

Bu denetim, SSL Labs SSL sunucu testi gibi bir dış hizmet tarafından yapılabilir. Tipik bir Azure uç noktasına karşı bir test çalıştırması, bu durumda Service Bus uç noktası, bir için neredeyse mükemmel bir puan verir.

Azure SQL veritabanları gibi hizmetler de verilerin gizli kalmasını sağlamak için TLS şifrelemesi kullanır. TLS kullanarak aktarım sırasında verilerin şifrelenmesi hakkında ilgi çekici bir bölüm, Microsoft 'un TLS çalıştıran bilgisayarlar arasındaki bağlantıyı dinlemek mümkün değildir. Bu, şirketlerin Microsoft 'un doğru ve hatta standart saldırgandan daha fazla kaynağa sahip bir durum aktörinin risk altında olabileceğini karşılayan şirketler için rahatlığını sağlamalıdır.

![Şekil 9-5 Service Bus uç noktası için bir puanı gösteren SSL Labs raporu.](./media/ssl-report.png)

**Şekil 9-5**. Service Bus uç noktası için bir puanı gösteren SSL Labs raporu.

Bu şifreleme düzeyi her zaman yeterli olmayacaksa da, Azure TLS bağlantılarının oldukça güvenli hale getirilmesine güvenmelidir. Azure, şifreleme artdığı için güvenlik standartlarını gelişmeye devam edecektir. Güvenlik standartlarını izlerken ve Azure 'ı geliştirdiklerinde güncelleştiren bir kişi olduğunu bilmek iyi bir deneyimdir.

### <a name="at-rest"></a>Bekleyen

Herhangi bir uygulamada, verilerin diskte oturduğu birçok yer vardır. Uygulama kodunun kendisi bir depolama mekanizmasından yüklenir. Çoğu uygulama SQL Server, Cosmos DB, hatta başaramayabiliriz Price-verimli tablo depolaması gibi bazı veritabanı türlerini de kullanır. Bu veritabanlarının hepsi, uygun izinlere sahip uygulamalardan hiç kimsenin verilerinizi okuyabileceğinden emin olmak için yoğun olarak şifrelenmiş depolama kullanır. Sistem işleçleri de şifrelenmiş verileri okuyamıyorum. Böylece müşteriler gizli kalacağından emin olmaya devam edebilir.

### <a name="storage"></a>Depolama

Azure 'un büyük bir bölümü Azure depolama altyapısıdır. Sanal makine diskleri, Azure depolama 'nın üzerine bağlanır. Azure Kubernetes Hizmetleri, kendilerini Azure Storage üzerinde barındırılan sanal makinelerde çalışır. Azure Işlevleri uygulamaları ve Azure Container Instances gibi sunucusuz teknolojilerin yanı sıra Azure Storage 'ın parçası olan disk kalmadı.

Azure Storage iyi şifrelenirse, başka her şeyin de şifrelenmesi için bir temel sağlar. Azure depolama [,](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) [fıps 140-2](https://en.wikipedia.org/wiki/FIPS_140) uyumlu [256 bit AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)ile şifrelenir. Bu, son 20 veya bu yıla göre çok sayıda akademik bir şifreleme teknolojisi olan iyi kabul edilir. Mevcut olduğunda, anahtarla ilgili bilgi sahibi olmayan birisinin AES tarafından şifrelenen verileri okumasına izin veren bilinen pratik bir saldırı yoktur.

Varsayılan olarak, Azure depolama 'yı şifrelemek için kullanılan anahtarlar Microsoft tarafından yönetilir. Bu anahtarlara kötü amaçlı erişimi önlemeyi önlemeye olanak sağlamak için kapsamlı korumalar vardır. Ancak, belirli şifreleme gereksinimlerine sahip kullanıcılar Azure Key Vault yönetilen [kendi depolama anahtarlarını da sağlayabilir](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) . Bu anahtarlar herhangi bir zamanda iptal edilebilir, bu da depolama hesabının içeriğini erişilemez kullanarak etkin bir şekilde işleyebilir.

Sanal makineler şifreli depolama kullanır, ancak Windows üzerinde BitLocker veya Linux üzerinde DM-Crypt gibi teknolojileri kullanarak başka bir şifreleme katmanı sağlamak mümkündür. Bu teknolojiler, disk görüntüsünün depolama alanı dışına sızmış olsa bile, okunması olanaksız kalacağından, bu teknolojiler anlamına gelir.

### <a name="azure-sql"></a>Azure SQL

Azure SQL 'de barındırılan veritabanları, verilerin şifreli kalmasını sağlamak için [Saydam veri şifrelemesi (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) adlı bir teknoloji kullanır. Varsayılan olarak, yeni oluşturulan tüm SQL veritabanlarında etkindir, ancak eski veritabanları için el ile etkinleştirilmelidir. TDE gerçek zamanlı şifrelemeyi ve şifre çözmeyi yalnızca veritabanının değil, ayrıca yedeklemeleri ve işlem günlüklerini yürütür.

Şifreleme parametreleri `master` veritabanında depolanır ve başlangıçta kalan işlemler için bellekte okur. Bu, `master` veritabanının şifrelenmemiş kalması gerektiği anlamına gelir. Gerçek anahtar Microsoft tarafından yönetilir. Ancak, exacting güvenlik gereksinimleri olan kullanıcılar, Azure depolama için yapılan Key Vault aynı şekilde kendi anahtarını sağlayabilir. Key Vault, anahtar döndürme ve iptal etme gibi hizmetleri sağlar.

TDS 'in "saydam" bölümü, şifreli bir veritabanını kullanmak için gerekli olan istemci değişikliklerinin olmadığını bulmanızdan geliyor. Bu yaklaşım iyi güvenlik sağlarken, veritabanı parolasının sızması, kullanıcıların verilerin şifresini çözebilmesi için yeterli değildir. Bir veritabanındaki tek tek sütunları veya tabloları şifreleyen başka bir yaklaşım vardır. [Always Encrypted](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) , şifreli verilerin veritabanının içinde düz metin olarak görünmesini sağlar.

Bu şifreleme katmanını ayarlamanın, şifreleme sıralamasını seçmek ve ilişkili anahtarların depolanacağı Key Vault nerede olması için SQL Server Management Studio bir sihirbaz aracılığıyla çalıştırılması gerekir.

![Şekil 9-6 Always Encrypted kullanarak şifrelenecek tablodaki sütunları seçme](./media/always-encrypted.png)

**Şekil 9-6**. Always Encrypted kullanılarak şifrelenecek tablodaki sütunları seçme.

Bu şifrelenmiş sütunlardan bilgileri okuyan istemci uygulamalarının, şifrelenmiş verileri okumak için özel uygulamalar yapması gerekir. Bağlantı dizelerinin ile güncelleştirilmeleri gerekir `Column Encryption Setting=Enabled` ve Key Vault istemci kimlik bilgileri alınmalıdır. SQL Server istemci daha sonra sütun şifreleme anahtarlarıyla öncelikli olmalıdır. Bu işlem yapıldıktan sonra, kalan eylemler SQL Istemcisi için standart arabirimleri kullanır. Diğer bir deyişle, SQL Client üzerinde oluşturulan kaber ve Entity Framework gibi araçlar, değişiklik yapılmadan çalışmaya devam edecektir. Always Encrypted, her dilde SQL Server her bir sürücü için kullanılamayabilir.

Her ikisi de istemciye özgü anahtarlarla kullanılabilecek TDE ve Always Encrypted birleşimi, en exacting şifreleme gereksinimlerinin de desteklenmesini sağlar.

### <a name="cosmos-db"></a>Cosmos DB

Cosmos DB, Microsoft tarafından Azure 'da sunulan en yeni veritabanıdır. Güvenlik ve şifreleme konusunda baştan sona oluşturulmuştur. AES-256bit şifreleme tüm Cosmos DB veritabanları için standarttır ve devre dışı bırakılamaz. İletişim için TLS 1,2 gereksinimiyle birlikte kullanıldığında, tüm depolama çözümü şifrelenir.

![Şekil 9-7 Cosmos DB içindeki veri şifreleme akışı](./media/cosmos-encryption.png)

**Şekil 9-7**. Cosmos DB içindeki veri şifreleme akışı.

Cosmos DB müşteri şifreleme anahtarları sağlamak için sağlamasa da, takım tarafından, bunun dışında PCI DSS uyumlu olduğundan emin olmak için önemli bir iş yapılır. Cosmos DB Ayrıca Azure SQL Always Encrypted benzer bir şekilde tek sütunlu şifrelemeyi desteklemez.

## <a name="keeping-secure"></a>Güvenli tutma

Azure, yüksek güvenlikli bir ürünü serbest bırakmak için gereken tüm araçlara sahiptir. Ancak, bir zincir en zayıf bağlantı kadar güçlü olur. Azure üzerinde dağıtılan uygulamalar uygun bir güvenlik anlayış ve iyi güvenlik denetimi ile geliştirilmemişse, zincirde zayıf bağlantı haline gelir. Azure 'da yüklü yazılımların Azure 'un kendisi kadar güvenli olduğundan emin olmak için kullanılabilen çok sayıda harika Statik Analiz Aracı, şifreleme kitaplığı ve güvenlik uygulaması vardır. [Statik analiz araçları](https://www.whitesourcesoftware.com/), [şifreleme kitaplıkları](https://www.libressl.org/)ve [güvenlik uygulamaları](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)örnekleri içerir.

>[!div class="step-by-step"]
>[Önceki](security.md) 
> [Sonraki](devops.md)
