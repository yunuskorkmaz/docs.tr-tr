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
ms.openlocfilehash: 9341ff8bfb2aec4eb7274d444fca4497fa66f210
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875576"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme
Yetkilendirme hangi varlıkları değiştirmek, görüntülemek veya aksi halde bir bilgisayar kaynağına erişmek için izne sahip belirleme işlemidir. Örneğin, bir iş ortamında, yalnızca Yöneticiler çalışanlarına dosyalara erişmek için izin. Windows Communication Foundation (WCF), Yetkilendirme işlemi gerçekleştirmek için iki mekanizmayı destekler. İlk mekanizması, var olan ortak dil çalışma zamanı (CLR) yapıları kullanarak Yetkilendirme denetlemenize olanak tanıyor. İkinci olarak bilinen bir beyana dayalı modelidir *kimlik modeli*. WCF gelen istenmeyen iletilere talep oluşturmak için kimlik modeli kullanır; Kimlik modeli sınıfları için özel yetkilendirme düzenleri yeni talep türlerini destekleyecek şekilde genişletilebilir. Bu konuda özelliğini kullanan en önemli sınıflar listesini yanı sıra, başlıca programlama kavramları kimlik modeli özelliğinin genel bir bakış sunulmaktadır.  
  
## <a name="identity-model-scenarios"></a>Kimlik modeli senaryoları  
 Aşağıdaki senaryolarda temsil eden kimlik modeli kullanın.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Senaryo 1: Kimlik, rol ve grup talepleri destekleme  
 Kullanıcılar, bir Web hizmetine iletileri gönderir. Web hizmeti erişim denetimi gereksinimleri, kimlik, roller veya gruplar kullanın. İletiyi gönderenin bir rol veya grup kümesine eşlenir. Rol veya grup bilgilerini erişim denetimleri gerçekleştirmek için kullanılır.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Senaryo 2: Zengin talep destekleme  
 Kullanıcılar, bir Web hizmetine iletileri gönderir. Web hizmeti erişim denetimi gereksinimleri, kimlik, roller veya gruplar daha zengin bir modeli gerektirir. Web hizmeti, belirli bir kullanıcının zengin beyana dayalı modeli kullanarak belirli bir korumalı kaynağa erişimi olup olmadığını belirler. Örneğin, bir kullanıcı, diğer kullanıcılara erişim olmaması maaş bilgilerini gibi belirli bilgileri okuyabilir olabilir.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Senaryo 3: Birbirinden farklı talep eşleme  
 Bir kullanıcı, bir Web hizmetine bir ileti gönderir. Kullanıcı kimlik bilgilerini bir dizi farklı yolla belirtebilirsiniz: X.509 Sertifika, kullanıcı adı belirteci veya Kerberos belirteci. Web hizmeti erişim denetimi kontrolleri aynı şekilde, kullanıcı kimlik bilgisi türü ne olursa olsun gerçekleştirmek için gereklidir. Zaman içinde ek bir kimlik bilgisi türlerinin destekleniyorsa, sistem buna uygun olarak değişime uğramaktadır.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Senaryo 4: Birden çok kaynaklarına erişimi belirleme  
 Bir Web hizmeti, birden çok kaynağa erişmeyi dener. Hizmet kaynağa erişmek için talepleri kullanıcıyla ilişkili talep karşılaştırarak, belirli bir kullanıcının erişimi olan hangi korunan kaynaklara gerekli belirler.  
  
## <a name="identity-model-terms"></a>Kimlik modeli koşulları  
 Aşağıdaki listede, kimlik modeli kavramları açıklamak için kullanılan anahtar terimlerini tanımlar.  
  
 Yetkilendirme İlkesi  
 Çıkış talep kümesine giriş talep kümesi eşleme kuralları kümesi. Değerlendirme bağlamı ve daha sonra bir yetkilendirme bağlamı eklenen kümeleri değerlendirilirken yetkilendirme ilkesi sonuçlarında talep.  
  
 Yetkilendirme bağlamı  
 Talep kümeleri kümesini ve sıfır veya daha fazla özellik. Bir veya daha fazla yetkilendirme ilkelerini değerlendirme sonucu.  
  
 Talep  
 Sağa bir talep türü ve değeri birleşimi.  
  
 Talep kümesi  
 Belirli bir veren tarafından verilen bir talepler kümesi.  
  
 Talep türü  
 Talep türü. Talep kimlik modeli API tarafından tanımlanan özellikleridir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> sınıfı. Sistem tarafından sağlanan talep türlerinin örnekleridir <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, ve <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 Değerlendirme bağlamı  
 Bir yetkilendirme ilkesi değerlendirilme bir bağlamı. Özellikler ve talep kümeleri içerir. Değerlendirme tamamlandıktan sonra kimlik doğrulama bağlamını temel haline gelir.  
  
 Kimliği talebi  
 Bir talep, sağ kimliğidir.  
  
 Veren  
 Talep kümesini talep kümesi en az bir kimlik talebi içeren ve başka yayımlandı olarak değerlendirilir.  
  
 Özellikler  
 Bir değerlendirme bağlamı veya bağlam yetkilendirme ile ilişkili bilgileri kümesi.  
  
 Korumalı kaynak  
 Yalnızca kullanılan sistemdeki bir sorun erişilen veya belirli gereksinimleri karşılanırsa, aksi takdirde yönetilebilir.  
  
 Sağ  
 Bir kaynak üzerinde bir özelliği. Kimlik modeli API tarafından tanımlanan özelliklerini haklarıdır <xref:System.IdentityModel.Claims.Rights> sınıfı. Sistem tarafından sağlanan haklarına örnekler <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Değer  
 Bir şey üzerine bir hak iddia.  
  
## <a name="claims"></a>Talep  
 Kimlik modeli beyana dayalı bir sistemdir. Talepler, genellikle bir kullanıcı, sistemin bir sistemde bazı varlıkla ilişkili özellikleri açıklanmaktadır. Belirli bir varlıkla ilişkilendirilen talep kümesi, bir anahtar olarak düşünülebilir. Belirli bir talep benzer şekilde bir kapısının kilidi açmak için kullanılan bir fiziksel anahtar, anahtar şeklini tanımlar. Talep kaynaklarına erişmek için kullanılır. Belirli bir korumalı kaynağa erişim izni varlık çalışırken erişim ile ilişkili talep ile bu kaynağa erişmek için gereken talepleri karşılaştırma tarafından belirlenir.  
  
 Bir talep belirli bir değere göre bir sağ ifadesidir. "Okuma", "Yazma" veya "Yürütme" gibi bir hak bir şey olabilir Bir değer, bir veritabanı, bir dosya, posta kutusu veya bir özelliği olabilir. Talepler bir talep türü de var. Talep türü ve sağ birleşimi, değere göre özelliklerini belirtmek için bir mekanizma sağlar. Örneğin, bir talep türü "Dosya" değer "Biography.doc" üzerinde doğru "Okuma" ile böyle bir talep ilişkili olduğu varlık Biography.doc dosya için okuma erişimi olduğunu gösterir. Bir talep türü "Name" değeri "Martin" üzerinde doğru "PossessProperty" ile böyle bir talep ilişkili olduğu varlık "Martin" değerine sahip bir Name özelliğine sahip olduğunu gösterir.  
  
 Çeşitli talep türlerini ve hakları kimlik modelinin bir parçası tanımlansa da, ek talep türlerini ve hakları gerekli olarak tanımlamak için kimlik modeli altyapısının en üstünde oluşturmaya çeşitli sistemler sağlayan genişletilebilir bir sistemdir.  
  
### <a name="identity-claims"></a>Kimlik talepleri  
 Belirli bir hak kimlik olmasıdır. Bu hakka sahip talep kimliği bir deyimi varlık olun. Örneğin, bir talep türü "kullanıcı asıl adı" (UPN) değerini "someone@example.com" ve kimlik sağındaki belirli bir etki alanındaki belirli bir kimlik belirtir.  
  
#### <a name="system-identity-claim"></a>Sistem Kimliği talebi  
 Bir kimlik talebi kimlik modeli tanımlar: Sistemi. Sistem kimlik talebi, varlığın geçerli uygulama veya sistem olduğunu gösterir.  
  
### <a name="sets-of-claims"></a>Talep kümesi  
 Talepleri her zaman sistemdeki bazı varlık tarafından verilen bu varlığın bazı kavramı, sonuçta olsa bile kimlik temsil eden talep modelinin önemlidir, çünkü "kendisi". Talepler bir küme olarak birlikte gruplanır ve bir veren her ayarlanmış. Bir veren yalnızca bir talepler kümesidir. Böyle bir özyinelemeli ilişki sonunda bitmelidir ve kendi veren olarak ayarlandığında herhangi talep.  
  
 Aşağıdaki şekilde, bir talepler kümesi, sertifikayı veren talepler, talep kümesine verenini olarak sistem sırayla sahip başka bir dizi sahip olduğu üç talep kümesi örneği gösterilmektedir. Bu nedenle, talep kümesi derinliklerde bir hiyerarşi oluşturur.  
  
 ![Hiyerarşi içinde talep kümesi.](./media/managing-claims-and-authorization-with-the-identity-model/claims-sets-hierarchy.gif)  
  
 Aynı talep kümesine, aşağıdaki resimde gösterildiği gibi veren birden çok talep kümesi içerebilir:
 
  
 ![Birden fazla aynı verme ile talep kümesini talep.](./media/managing-claims-and-authorization-with-the-identity-model/multiple-claim-sets-same-issuing-claim-set.gif)  
  
 Kendi veren bir talep kümesi dışında kimlik modeli bir döngü oluşturmak talep kümeleri için herhangi bir destek sağlamaz. Bu nedenle talep kümesi A kendisi bir talep kümesi tarafından verilmiş olan talep kümesi tarafından B, burada verilen bir durumla hiçbir zaman ortaya çıkabilir. Ayrıca, kimlik modeli birden çok verenler talep kümeleri için herhangi bir destek sağlamaz. Ardından belirli bir talep kümesi iki veya daha fazla veren dağıtmalı, her aynı talepleri içeren, ancak farklı verenler sahip birden çok talep kümesi kullanmanız gerekir.  
  
### <a name="the-origin-of-claims"></a>Taleplerin kaynağı  
 Talepler, çeşitli kaynaklardan gelebilir. Bir ortak talep bir kullanıcı tarafından örneğin bir Web hizmetine gönderilen bir iletinin bir parçası olarak sunulan kimlik bilgilerini kaynağıdır. Bu tür talepler sistem doğrular ve kullanıcıyla ilişkili talep kümesinin bir parçası haline gelmeden. Diğer sistem bileşenlerini dahil ancak bunlarla sınırlı olmamak, işletim sistemi, ağ yığını, çalışma zamanı ortamı veya uygulama iddialara kaynakları da olabilir. Ayrıca, uzak hizmetleri talep kaynağı da olabilir.  
  
### <a name="authorization-policies"></a>Yetkilendirme İlkeleri  
 Kimlik modelinde, talep yetkilendirme ilkesini değerlendirme işleminin bir parçası olarak oluşturulur. Bir yetkilendirme ilkesi (büyük olasılıkla boş) mevcut talepler kümesini inceleyen ve talep zaten mevcut ve tüm olanaklarına ek bilgileri temel alarak ek talep eklemek tercih edebilirsiniz. Bu talep arasındaki eşlemeyi temelini sağlar. Varlığı veya yokluğu talep sistemdeki ek talep ekler olup olmadığı ile ilgili bir yetkilendirme ilkesi davranışını etkiler.  
  
 Örneğin, yetkilendirme ilkesi birthdates sistemini kullanarak çeşitli varlıklar içeren bir veritabanına erişimi vardır. Yetkilendirme İlkesi, bir "Over18" talep içeriği eklemek için bu bilgileri kullanır. Bu Over18 talep 18 yıl üzerinden olduğu gerçeği dışında varlık hakkında herhangi bir bilgi açıklamaz unutmayın. Yorumu 'Over18' talep, talep semantiği anlamaya bağlı olduğunu unutmayın. Bu semantiği düzeyde talep eklenen yetkilendirme ilkesi farkındadır. Sonradan neden ilke değerlendirmesinden gelen talepleri inceler kod Ayrıca bu semantiği bilginizi artırın.  
  
 Belirtilen yetkilendirme ilkesi, diğer yetkilendirme ilkeleri talep ekledikçe daha fazla talep henüz bu yetkilendirme ilkesi ekleyebilirsiniz olduğundan, birden çok kez hesaplanacak gerektirebilir. Kimlik modeli, daha fazla talep herhangi biriyle zorla Yetkilendirme İlkeleri bağlamına eklenene kadar değerlendirmeye devam etmek için tasarlanmıştır. Bu sürekli değerlendirme, Yetkilendirme İlkeleri Yetkilendirme İlkeleri ile ilgili herhangi bir belirli değerlendirme sırada zorlamak için gereksinim engeller; herhangi bir sırada değerlendirilebilir. İlke bir talep B eklediyseniz ilke X yalnızca talep Z eklerse, X ilk olarak değerlendirildiği taktirde, ardından, başlangıçta talep Z eklemez. Sonuç olarak, bir değerlendirilir ve talep b X ardından ikinci bir kez değerlendirilir ve isteğe bağlı olarak bu süre talep Z ekler ekler.  
  
 Belirli bir sistem çok sayıda yetkilendirme ilkelerini yürürlüğe olabilir.  
  
### <a name="a-key-making-machine"></a>Bir anahtar yapımı makine  
 Bir grup ilişkili yetkilendirme ilkeleri değerlendirme anahtarları sağlayan bir makine gibi kullanmaktır. Yetkilendirme İlkeleri şunlardır: her değerlendirilir ve anahtarın şekli oluşturan oluşturmaya talep kümesi oluşturulur. Anahtar şeklini tamamlandıktan sonra bazı kilit açmak için kullanılabilir. Anahtar şeklini "bir Yetkilendirme Yöneticisi tarafından oluşturulan bir yetkilendirme bağlamı" depolanır.  
  
### <a name="authorization-context"></a>Yetkilendirme bağlamı  
 Açıklandığı gibi çeşitli kimlik doğrulama ilkelerini bir Yetkilendirme Yöneticisi'ni değerlendirir ve sonucu olan bir kimlik doğrulama bağlamını (talep kümeleri ve ilişkili bazı özellikler kümesi). Yetkilendirme bağlamında hangi talepleri çeşitli dayandırabilmektedir (örneğin, sertifika veren talep kümesi) arasındaki ilişkileri bu bağlamda mevcut olduğunu belirlemek ve sonuçta bunların erişim karşılamalıdır bazı gereksinimler karşı karşılaştırma incelenebilir bir Kaynak.  
  
### <a name="locks"></a>Kilitler  
 Bir yetkilendirme bağlam (talepler kümesi) bir anahtar ise, belirli bir korumalı kaynağa erişim izni vermek için karşılanması gereken gereksinimleri anahtar uymalı kilit oluşturur. Kimlik modeli bu gereksinimleri nasıl ifade resmileştirin değil, ancak bunlar, sistemin talebe dayalı gereği bazı gerekli talepler kümesi karşı yetkilendirme bağlamında talepleri karşılaştırma içeren.  
  
### <a name="a-recap"></a>Bir özeti  
 Kimlik modeli geçici olarak talep kavramını temel alır. Talep kümeleri halinde gruplandırılır ve bir yetkilendirme bağlamında toplanır. Bir kimlik doğrulama bağlamını talepler kümesi içeriyor ve bir Yetkilendirme Yöneticisi ile ilişkili bir veya daha fazla yetkilendirme ilkelerini değerlendirme sonucu. Bu talep, ayarlar, erişim gereksinimleri karşıladığınızdan olmadığını belirlemek için incelenebilir. Aşağıdaki şekilde bu çeşitli kimlik modeli kavramlar arasındaki ilişkiler gösterilmektedir.  
  
 ![Talep ve yetkilendirmeyi yönetme](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF ve kimlik modeli  
 WCF, yetkilendirme gerçekleştirmek için temel olarak kimlik modeli altyapısı kullanır. Wcf'de, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıfı belirtmenize olanak verir *yetkilendirme* ilkeleri bir hizmetin parçası olarak. Bu tür Yetkilendirme İlkeleri olarak da bilinir *Dış kimlik doğrulama ilkelerini*, ve temel alarak yerel ilke veya uzak bir hizmetle etkileşim tarafından talep işleme gerçekleştirirler. Tarafından temsil edilen Yetkilendirme Yöneticisi <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı dış Yetkilendirme İlkeleri (belirteçler) türlerini çeşitli kimlik bilgisi tanımak Yetkilendirme İlkeleri ile birlikte değerlendirir ve ne çağrılır dolduran bir  *Yetkilendirme bağlamında* talepleri bir gelen iletiyi uygun ile. Yetkilendirme bağlamında tarafından temsil edilen <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
## <a name="identity-model-programming"></a>Kimlik programlama modeli  
 Aşağıdaki tabloda, program kimlik modeli uzantıları için kullanılan nesne modelini açıklar. Bu sınıfların tümü ya da mevcut <xref:System.IdentityModel.Policy> veya <xref:System.IdentityModel.Claims> ad alanları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|Yetkilendirme bileşeni|Uygulayan bir kimlik modeli sınıf <xref:System.IdentityModel.Policy.IAuthorizationComponent> arabirimi.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Tek bir salt okunur dize özelliği sağlayan bir arabirimi: Kimliği. Bu özelliğin değeri bu arabirimi uygulayan bir sistemde her örneği için benzersizdir.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|Bir *yetkilendirme bileşen* bir dizi içeren `ClaimSet` sıfır veya daha fazla özellik örnekleriyle; bir veya daha fazla yetkilendirme ilkelerini değerlendirme sonucu.|  
|<xref:System.IdentityModel.Claims.Claim>|Bir talep türü, sağa ve değer birleşimi. Sağa ve değer bölümleri talep türüne göre kısıtlanır.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Soyut bir temel sınıf. Bir koleksiyonu `Claim` örnekleri.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Korumalı bir sınıf. Uygulanışı `ClaimSet` sınıfı.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Soyut bir temel sınıf. Bir yetkilendirme ilkesi için ilke değerlendirmesi sırasında geçirildi.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Türetilmiş bir arabirim `IAuthorizationComponent` ve yetkilendirme ilkesi sınıfları tarafından uygulanır.|  
|<xref:System.IdentityModel.Claims.Rights>|Önceden tanımlanmış doğru değerleri içeren bir statik sınıf.|  
  
 Aşağıdaki sınıflar kimlik programlama modeli için de kullanılır, ancak içinde bulunamadı <xref:System.IdentityModel.Policy> veya <xref:System.IdentityModel.Claims> ad alanları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Bir yöntem sağlayan bir sınıf — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>— talep tabanlı yetkilendirme gerçekleştirmek için her bir işlemde bir hizmet denetler. Sınıfından türetilir ve yöntemini geçersiz kılmanız gerekir.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Bir hizmet olarak davranışını ilgili çeşitli özellikler sağlayan korumalı sınıf için yetkilendirme ile ilgilidir.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Güvenlik bağlamı, kimlik doğrulama bağlamını, şu anda çalıştırmak için (veya yaklaşık çalıştırmak için) dahil olmak üzere sağlayan bir sınıf işlemi. Bu sınıfın bir örneğinin parçası olduğu <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Önemli üyeleri  
 Aşağıdaki üyeleri yeni talep türleri oluşturmak için yaygın olarak kullanılır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Türetilen sınıflar, hizmet işlemleri çalıştırılmadan önce talep tabanlı erişim denetimleri gerçekleştirmek için bu yöntemi uygular. Sağlanan tüm bilgileri <xref:System.ServiceModel.OperationContext>, veya başka bir yerde karar denetleyin erişim yaparken incelenebilir. Varsa <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndürür `true`, ardından erişim verilir ve çalıştırmak için işleme izin verilir. Varsa `CheckAccessCore` döndürür `false`, sonra erişim reddedildi ve işlemi çalışmaz. Bir örnek için bkz [nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Döndürür <xref:System.ServiceModel.ServiceAuthorizationManager> hizmeti. <xref:System.ServiceModel.ServiceAuthorizationManager> Yetkilendirme kararları sorumludur.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Hizmet için belirtilen özel Yetkilendirme İlkeleri koleksiyonu. Bu ilkeler, gelen iletileri kimlik bilgileri ile ilgili bu ilkelere ek olarak değerlendirilir.|  
  
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
- [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Talepler ve Kaynaklara Erişimi Reddetme](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)
- [Talep Oluşturma ve Kaynak Değerleri](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Nasıl yapılır: Özel talep oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
- [Nasıl yapılır: Talepleri karşılaştırma](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Nasıl yapılır: Özel yetkilendirme ilkesi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)
- [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
