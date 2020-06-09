---
title: Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
ms.openlocfilehash: f9138102435aab07e5c1771ce5dba85bacbcac99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586357"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme
Yetkilendirme, bir bilgisayar kaynağını değiştirme, görüntüleme veya başka bir şekilde erişme iznine sahip olan varlıkları belirleme işlemidir. Örneğin, bir işletmede, çalışanlarının dosyalarına yalnızca yöneticilerin erişmesine izin verilebilir. Windows Communication Foundation (WCF), yetkilendirme işlemi gerçekleştirmek için iki mekanizmayı destekler. İlk mekanizma, mevcut ortak dil çalışma zamanı (CLR) yapılarını kullanarak yetkilendirmeyi denetlemenize olanak sağlar. İkincisi, *kimlik modeli*olarak bilinen talep tabanlı bir modeldir. WCF, gelen iletilerden talepler oluşturmak için kimlik modelini kullanır; Kimlik modeli sınıfları, özel yetkilendirme şemaları için yeni talep türlerini destekleyecek şekilde genişletilebilir. Bu konu, kimlik modeli özelliğinin ana programlama kavramlarının yanı sıra özelliğin kullandığı en önemli sınıfların bir listesini sunmaktadır.  
  
## <a name="identity-model-scenarios"></a>Kimlik modeli senaryoları  
 Aşağıdaki senaryolar kimlik modelinin kullanımını temsil eder.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Senaryo 1: kimlik, rol ve grup taleplerini destekleme  
 Kullanıcılar bir Web hizmetine iletiler gönderir. Web hizmetinin erişim denetimi gereksinimleri kimlik, rol veya grupları kullanır. İleti gönderici bir rol veya grup kümesiyle eşlenir. Rol veya grup bilgileri, erişim denetimleri gerçekleştirmek için kullanılır.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Senaryo 2: zengin talepler destekleme  
 Kullanıcılar bir Web hizmetine iletiler gönderir. Web hizmetinin erişim denetimi gereksinimleri, kimlik, roller veya gruplardan daha zengin bir model gerektirir. Web hizmeti, belirli bir kullanıcının zengin talep tabanlı modeli kullanarak belirli bir korumalı kaynağa erişip erişemeyeceğini belirler. Örneğin, bir Kullanıcı, diğer kullanıcıların erişimi olmayan ücret bilgileri gibi belirli bilgileri okuyabilir.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Senaryo 3: farklı talepler eşleme  
 Bir Kullanıcı bir Web hizmetine ileti gönderir. Kullanıcı kimlik bilgilerini çeşitli şekillerde belirtebilir: X. 509.440 sertifikası, Kullanıcı adı belirteci veya Kerberos belirteci. Web hizmeti, Kullanıcı kimlik bilgisi türünden bağımsız olarak, erişim denetimi denetimlerini aynı şekilde gerçekleştirmek için gereklidir. Zaman içinde ek kimlik bilgisi türleri destekleniyorsa, sistem buna uygun şekilde gelişmelidir.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Senaryo 4: birden fazla kaynağa erişimi belirleme  
 Bir Web hizmeti birden fazla kaynağa erişmeye çalışır. Hizmet, Kullanıcı ile ilişkili talepleri, kaynağa erişmek için gereken taleplerle karşılaştırarak, belirli bir kullanıcının hangi korumalı kaynaklara erişimi olduğunu belirler.  
  
## <a name="identity-model-terms"></a>Kimlik modeli terimleri  
 Aşağıdaki liste, kimlik modeli kavramlarını anlatmak için kullanılan anahtar terimleri tanımlar.  
  
 Yetkilendirme ilkesi  
 Bir giriş talepleri kümesini bir çıkış talepleri kümesiyle eşlemek için bir kurallar kümesi. Talep kümelerinin bir değerlendirme bağlamına ve daha sonra bir yetkilendirme bağlamına eklendiği yetkilendirme ilkesi sonuçları değerlendiriliyor.  
  
 Yetkilendirme bağlamı  
 Bir talep kümesi ve sıfır veya daha fazla özellik kümesi. Bir veya daha fazla yetkilendirme ilkesini değerlendirme sonucu.  
  
 İste  
 Bir talep türü, sağ ve bir değer birleşimi.  
  
 Talep kümesi  
 Belirli bir veren tarafından verilen talepler kümesi.  
  
 Talep türü  
 Bir talep türü. Kimlik modeli API 'SI tarafından tanımlanan talepler, <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> sınıfının özellikleridir. Sistem tarafından sunulan talep türleri örnekleri,,,,, <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.System%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A> , ve <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A> .  
  
 Değerlendirme bağlamı  
 Yetkilendirme ilkesinin değerlendirildiği bir bağlam. Özellikler ve talep kümelerini içerir. Değerlendirme tamamlandıktan sonra yetkilendirme bağlamının temeli olur.  
  
 Kimlik talebi  
 Hakkı kimlik olan bir talep.  
  
 Veren  
 En az bir kimlik talebi içeren ve başka bir talep kümesi veren bir talep kümesi.  
  
 Özellikler  
 Bir değerlendirme bağlamı veya yetkilendirme içeriğiyle ilişkili bir bilgi kümesi.  
  
 Korumalı kaynak  
 Sisteme yalnızca belirli gereksinimlerin karşılanması durumunda yalnızca kullanılabilecek, erişilebilen veya başka şekilde işlenebilen bir şey.  
  
 Sağ  
 Kaynak üzerinde bir özellik. Kimlik modeli API 'SI tarafından tanımlanan haklar, <xref:System.IdentityModel.Claims.Rights> sınıfının özellikleridir. Sistem tarafından belirtilen hakların örnekleri <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> .  
  
 Değer  
 Bir hakkı talep eden bir şey.  
  
## <a name="claims"></a>Talepler  
 Kimlik modeli, talep tabanlı bir sistemdir. Talepler, sistem içindeki bazı varlıkla ilişkili özellikleri (genellikle bu sistemin bir kullanıcısı) anlatmaktadır. Belirli bir varlıkla ilişkili talepler kümesi, anahtar olarak düşünülebilir. Belirli talepler, bir kapıda kilit açmak için kullanılan bir fiziksel anahtarla benzer şekilde bu anahtarın şeklini tanımlar. Talepler, kaynaklara erişim kazanmak için kullanılır. Verilen korumalı bir kaynağa erişim, erişim girişiminde bulunan varlıkla ilişkili taleplerle ilgili kaynağa erişmek için gereken talepler karşılaştırılmasıyla belirlenir.  
  
 Talep, belirli bir değere göre doğru bir ifadedir. Bir hak, "okuma", "yazma" veya "yürütme" gibi bir şey olabilir. Bir değer bir veritabanı, dosya, posta kutusu veya özellik olabilir. Taleplerde de bir talep türü vardır. Talep türü ve sağ birleşimi, değere göre özellikleri belirtme mekanizmasını sağlar. Örneğin, "biyograf. doc" değeri üzerinde "Read" doğru "dosya" türünde bir talep, bu tür bir talebin ilişkilendirildiği varlığın biografi. doc dosyasına okuma erişimi olduğunu gösterir. "Marsessproperty" değerine sahip "ad" türünde bir talep, "Marsessproperty" değeri üzerinde "Marsessproperty" olan bir talep, bu tür bir talebin ilişkili olduğu varlığın "MARI" değerine sahip bir ad özelliği olduğunu gösterir.  
  
 Çeşitli talep türleri ve hakları kimlik modelinin bir parçası olarak tanımlandığından, sistem Genişletilebilir, bu da kimlik modeli altyapısının üzerine binen üst, ek talep türleri ve haklar tanımlamak için çeşitli sistemlere izin verir.  
  
### <a name="identity-claims"></a>Kimlik talepleri  
 Belirli bir hak, kimliğin bir sağdır. Bu hakka sahip talepler, varlığın kimliği hakkında bir bildirim yapar. Örneğin, "" değerine sahip "Kullanıcı asıl adı" (UPN) türünde bir talep someone@example.com ve kimlik hakkı, belirli bir etki alanındaki belirli bir kimliği gösterir.  
  
#### <a name="system-identity-claim"></a>Sistem kimliği talebi  
 Kimlik modeli bir kimlik talebi tanımlar: sistem. Sistem kimlik talebi, bir varlığın geçerli uygulama veya sistem olduğunu gösterir.  
  
### <a name="sets-of-claims"></a>Talep kümeleri  
 Talepler, bu varlık son olarak "Self" kavramsa bile, her zaman sistemdeki bazı varlıklar tarafından her zaman verildiği için, kimliği temsil eden talepler modeli önemlidir. Talepler bir küme olarak birlikte gruplandırılır ve her bir küme bir veren içerir. Veren yalnızca bir talepler kümesidir. Bu tür bir özyinelemeli ilişki sonunda sona bitmeli ve herhangi bir talep kümesi kendi verenler olabilir.  
  
 Aşağıdaki şekilde, tek bir talepler kümesinin, veren olarak başka bir talep kümesi olduğu ve bu da sertifika veren tarafından sistem talebi ayarlanmış olan farklı bir talep kümesi olduğu üç talep kümesi örneği gösterilmektedir. Bu nedenle, talep kümesi, yoğun bir şekilde derinlemesine olabilecek bir hiyerarşi oluşturur.  
  
 ![Hiyerarşi içindeki talepler kümesi.](./media/managing-claims-and-authorization-with-the-identity-model/claims-sets-hierarchy.gif)  
  
 Birden çok talep kümesi, aşağıdaki şekilde gösterildiği gibi aynı verme talep kümesine sahip olabilir:
  
 ![Aynı veren talep kümesine sahip birden çok talep kümesi.](./media/managing-claims-and-authorization-with-the-identity-model/multiple-claim-sets-same-issuing-claim-set.gif)  
  
 Kendi veren bir talep kümesi dışında, kimlik modeli bir döngü oluşturmak için talep kümeleri için herhangi bir destek sağlamaz. Bu nedenle, talep kümesi B tarafından, talep kümesi tarafından verilen ve kendisi tarafından verilen talep kümesi tarafından verilen bir durum, hiçbir şekilde gerçekleşmeyebilir. Ayrıca, kimlik modeli birden çok veren talep kümesi için herhangi bir destek sağlamaz. İki veya daha fazla veren 'in belirli bir talep kümesini vermesi gerekiyorsa, her biri aynı talepleri içeren, ancak farklı verenler olan birden çok talep kümesi kullanmanız gerekir.  
  
### <a name="the-origin-of-claims"></a>Taleplerin kaynağı  
 Talepler, çeşitli kaynaklardan gelebilir. Bir genel talep kaynağı, bir kullanıcı tarafından sunulan ve örneğin bir Web hizmetine gönderilen iletinin bir parçası gibi kimlik bilgileridir. Sistem bu talepleri doğrular ve Kullanıcı ile ilişkili bir talepler kümesinin bir parçası haline gelir. Diğer sistem bileşenleri Ayrıca, işletim sistemi, ağ yığını, çalışma zamanı ortamı veya uygulama dahil, ancak bunlarla sınırlı olmamak üzere talepler kaynakları da olabilir. Ayrıca, uzak hizmetler bir talepler kaynağı da olabilir.  
  
### <a name="authorization-policies"></a>Yetkilendirme İlkeleri  
 Kimlik modelinde talepler, yetkilendirme ilkesini değerlendirme sürecinin bir parçası olarak oluşturulur. Yetkilendirme ilkesi, mevcut talepler kümesini (muhtemelen boş) inceler ve zaten mevcut olan talebe ve aktiften çıkarılma ek bilgilere göre ek talepler eklemeyi seçebilir. Bu, talepler arasındaki eşlemenin temelini sağlar. Sistemdeki taleplerin varlığı veya yokluğu, bir yetkilendirme ilkesinin, ek talepler eklemesine göre davranışını etkiler.  
  
 Örneğin, yetkilendirme ilkesi, sistemi kullanan çeşitli varlıkların Doğum tarihleri içeren bir veritabanına erişebilir. Yetkilendirme ilkesi, içeriğe bir "Over18" talebi eklemek için bu bilgileri kullanır. Bu Over18 talebinin, yaklaşık 18 yaşından fazla olan varlıkla ilgili hiçbir bilgiyi açıklamadığını unutmayın. ' Over18 ' talebinin yorumlamasının, bu talebin semantiğinin anlaşıldığına bağlı olduğunu unutmayın. Talebi ekleyen yetkilendirme ilkesi, bu semantikleri bir düzeyde anlamıştır. Daha sonra ilke değerlendirmesinden kaynaklanan talepleri inceleyerek bu semantiklerden de haberdar olur.  
  
 Belirli bir yetkilendirme ilkesi, diğer yetkilendirme ilkeleri talep içerdiğinden, bu yetkilendirme ilkesi henüz daha fazla talep ekleyebileceğinden, birden çok kez değerlendirilmesini gerektirebilir. Kimlik modeli, zordaki herhangi bir yetkilendirme ilkesi tarafından daha fazla talep eklenene kadar değerlendirmeye devam etmek için tasarlanmıştır. Yetkilendirme ilkelerinin sürekli değerlendirilmesi, yetkilendirme ilkelerine göre belirli bir değerlendirme sırasını zorunlu kılmak için gereksinimi önler; Bunlar herhangi bir sırada değerlendirilebilirler. Örneğin, Policy X yalnızca talep ekle B talebini eklerse, bu, ilk olarak X olarak değerlendiriliyorsa, başlangıçta Z talebini eklemez. Daha sonra, bir değerlendirilir ve B. X talebi eklendiğinde ikinci bir kez değerlendirilir ve bu süre bu kez Claim Z değerini ekler.  
  
 Belirli bir sistem, zorlamalı olarak birçok yetkilendirme ilkesine sahip olabilir.  
  
### <a name="a-key-making-machine"></a>Anahtar oluşturma makinesi  
 Bir grup ilişkili yetkilendirme ilkesini değerlendirmek, anahtar yapan bir makine kullanma gibidir. Yetkilendirme ilkeleri her biri değerlendirilir ve talepler kümesi oluşturulur ve anahtarın şeklini oluşturur. Anahtarın şekli tamamlandığında, bazı kilitleri açmayı denemek için kullanılabilir. Anahtarın şekli, bir Yetkilendirme Yöneticisi tarafından oluşturulan bir "yetkilendirme bağlamında" saklanır.  
  
### <a name="authorization-context"></a>Yetkilendirme bağlamı  
 Yetkilendirme Yöneticisi, farklı yetkilendirme ilkelerini açıklandığı şekilde değerlendirir ve sonuç bir yetkilendirme bağlamıdır (bir talep kümesi ve bazı ilişkili özellikler kümesi). Yetkilendirme bağlamı, bu bağlamda hangi taleplerin bulunduğunu belirlemek için incelenebilir, bu çeşitli talepler arasındaki ilişkiler (örneğin, veren talep kümesi) ve sonuç olarak bunları bir kaynağa erişmek için uyması gereken bazı gereksinimlere göre karşılaştırın.  
  
### <a name="locks"></a>Kilitler  
 Bir yetkilendirme bağlamı (bir talepler kümesi) bir anahtarlık ise, belirli bir korumalı kaynağa erişim verilmesi için karşılanması gereken gereksinimler, anahtarın sığması gereken kilidi oluşturur. Kimlik modeli, bu tür gereksinimlerin nasıl ifade edireceğini değil, ancak sistemin talep tabanlı doğası verildiğinde, yetkilendirme bağlamındaki talepleri bazı gerekli talepler kümesiyle karşılaştırmayı içerir.  
  
### <a name="a-recap"></a>Bir recap  
 Kimlik modeli, talepler kavramını temel alarak. Talepler kümeler halinde gruplandırılır ve bir yetkilendirme bağlamında toplanır. Yetkilendirme bağlamı bir talepler kümesi içerir ve bir Yetkilendirme Yöneticisi ile ilişkili bir veya daha fazla yetkilendirme ilkesini değerlendirme sonucudur. Bu talep kümeleri, erişim gereksinimlerinin karşılanıp karşılanmadığını belirlemede incelenebilir. Aşağıdaki şekilde, bu çeşitli kimlik modeli kavramları arasındaki ilişkiler gösterilmektedir.  
  
 ![Talepleri ve Yetkilendirmeyi Yönetme](media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF ve kimlik modeli  
 WCF kimlik modeli altyapısını yetkilendirme gerçekleştirme temeli olarak kullanır. WCF 'de, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıf, bir hizmetin parçası olarak *Yetkilendirme* ilkelerini belirtmenizi sağlar. Bu tür yetkilendirme ilkeleri, *dış yetkilendirme ilkeleri*olarak bilinir ve yerel ilke temelinde veya uzak bir hizmetle etkileşime girerek talep işleme gerçekleştirebilir. Sınıfı tarafından temsil edilen Yetkilendirme Yöneticisi, <xref:System.ServiceModel.ServiceAuthorizationManager> dış yetkilendirme ilkelerini çeşitli kimlik bilgisi türlerini (belirteçleri) tanıyan yetkilendirme ilkeleriyle birlikte değerlendirir ve gelen iletiye uygun taleplerle *Yetkilendirme bağlamı* olarak adlandırılan öğeleri doldurur. Yetkilendirme bağlamı sınıf tarafından temsil edilir <xref:System.IdentityModel.Policy.AuthorizationContext> .  
  
## <a name="identity-model-programming"></a>Kimlik modeli programlama  
 Aşağıdaki tabloda, Identity model uzantıları 'nı programlamak için kullanılan nesne modeli açıklanmaktadır. Bu sınıfların hepsi <xref:System.IdentityModel.Policy> ya da <xref:System.IdentityModel.Claims> ad alanlarında bulunur.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|Yetkilendirme bileşeni|Arabirimi uygulayan bir kimlik modeli sınıfı <xref:System.IdentityModel.Policy.IAuthorizationComponent> .|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Tek bir salt okunurdur dize özelliği sağlayan bir arabirim: ID. Bu özelliğin değeri, bu arabirimi uygulayan sistemdeki her bir örnek için benzersizdir.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|Sıfır veya daha fazla özelliği olan bir örnek kümesi içeren bir *Yetkilendirme bileşeni* `ClaimSet` ; bir veya daha fazla yetkilendirme ilkesini değerlendirme sonucu.|  
|<xref:System.IdentityModel.Claims.Claim>|Talep türü, sağ ve değer birleşimi. Sağ ve değer parçaları talep türü tarafından kısıtlanıyor.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Soyut temel sınıf. `Claim`Örnek koleksiyonu.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Sealed bir sınıf. `ClaimSet`Sınıfının uygulanması.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Soyut temel sınıf. İlke değerlendirmesi sırasında bir yetkilendirme ilkesine geçirilir.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|`IAuthorizationComponent`Yetkilendirme İlkesi sınıfları tarafından türetilmiş ve uygulanan arabirim.|  
|<xref:System.IdentityModel.Claims.Rights>|Önceden tanımlanmış sağ değerleri içeren bir statik sınıf.|  
  
 Aşağıdaki sınıflar, kimlik modeli programlama için de kullanılır, ancak <xref:System.IdentityModel.Policy> veya <xref:System.IdentityModel.Claims> ad alanlarında bulunamaz.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Bir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> hizmet içindeki her işlem için talep tabanlı yetkilendirme denetimleri gerçekleştirmek üzere — yöntemi sağlayan bir sınıf. Sınıfından türetmeniz ve metodunu geçersiz kılmanız gerekir.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Yetkilendirmeyle ilgili bir hizmetin davranışına ilişkin çeşitli özellikler sağlayan Sealed bir sınıf.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Şu anda çalışan (veya çalıştırmak üzere) işlemi için, yetkilendirme bağlamı da dahil olmak üzere güvenlik bağlamı sağlayan bir sınıf. Bu sınıfın bir örneği, öğesinin bir parçasıdır <xref:System.ServiceModel.OperationContext> .|  
  
### <a name="significant-members"></a>Önemli Üyeler  
 Aşağıdaki Üyeler genellikle yeni talep türleri oluşturmak için kullanılır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Türetilmiş sınıflar, bir hizmette işlemleri çalıştırmadan önce talep tabanlı erişim denetimleri gerçekleştirmek için bu yöntemi uygular. <xref:System.ServiceModel.OperationContext>Erişim denetimi kararı verirken, sağlanan veya başka bir yerde bulunan tüm bilgiler incelenebilir. <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>Dönerse `true` , erişim verilir ve işlemin çalışmasına izin verilir. `CheckAccessCore`Dönerse `false` , erişim reddedilir ve işlem çalıştırılmaz. Bir örnek için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|<xref:System.ServiceModel.ServiceAuthorizationManager>Hizmeti için döndürür. , <xref:System.ServiceModel.ServiceAuthorizationManager> Yetkilendirme kararları getirmekten sorumludur.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Hizmet için belirtilen özel yetkilendirme ilkelerinin koleksiyonu. Bu ilkeler, gelen iletilerdeki kimlik bilgileriyle ilişkili ilkelere ek olarak değerlendirilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Policy.EvaluationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationComponent>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims>
- <xref:System.IdentityModel.Policy>
- <xref:System.IdentityModel.Tokens>
- <xref:System.IdentityModel.Selectors>
- [Talepler ve Belirteçler](claims-and-tokens.md)
- [Beyanlar ve Kaynaklara Erişimi Reddetme](claims-and-denying-access-to-resources.md)
- [Beyan Oluşturma ve Kaynak Değerleri](claim-creation-and-resource-values.md)
- [Nasıl yapılır: Özel Beyan Oluşturma](../extending/how-to-create-a-custom-claim.md)
- [Nasıl yapılır: Talepleri Karşılaştırma](../extending/how-to-compare-claims.md)
- [Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma](../extending/how-to-create-a-custom-authorization-policy.md)
- [Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Güvenliğe genel bakış](security-overview.md)
- [Yetkilendirme](authorization-in-wcf.md)
