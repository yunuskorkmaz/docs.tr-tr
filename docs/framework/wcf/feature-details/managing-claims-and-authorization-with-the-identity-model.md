---
title: "Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b69c17b9fcb14bbd70b60c32965fb1163c22e765
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme
Yetkilendirme hangi varlıkların değiştirmek, görüntüleme veya aksi halde bir bilgisayar kaynağına erişmek için izne sahip belirleme işlemidir. Örneğin, bir iş ortamında, yalnızca Yöneticiler, çalışanlarına dosyalara erişmesine izin. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Yetkilendirme işlemi gerçekleştirmek için iki mekanizma destekler. İlk mekanizma, varolan ortak dil çalışma zamanı (CLR) yapıları kullanarak yetkilendirmeyi denetlemenizi sağlar. İkinci olarak bilinen bir talep tabanlı modeldir *kimlik modeli*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]gelen iletilere talep oluşturmak üzere kimlik modelini kullanır; Kimlik modeli sınıfları için özel yetkilendirme düzenleri yeni talep türlerini desteklemek için genişletilebilir. Bu konuda özelliğini kullanıyor en önemli sınıfları listesini yanı sıra kimliği Model özelliğinin ana programlama kavramları hakkında genel bir bakış sunulmaktadır.  
  
## <a name="identity-model-scenarios"></a>Kimlik modeli senaryoları  
 Aşağıdaki senaryolarda kimlik modelini kullanmak temsil eder.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Senaryo 1: Kimlik, rol ve grup talepleri destekleme  
 Kullanıcılar bir Web hizmetine iletileri gönderir. Erişim denetimi gereksinimlerine Web hizmeti kimliği, roller veya gruplar kullanın. İletiyi gönderen bir dizi roller veya gruplar için eşlenir. Rol veya grup bilgileri erişim denetimleri gerçekleştirmek için kullanılır.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Senaryo 2: Zengin talep destekleme  
 Kullanıcılar bir Web hizmetine iletileri gönderir. Erişim denetimi gereksinimlerine Web hizmeti kimliği, roller veya gruplar daha zengin bir modeli gerektirir. Web hizmeti belirli bir kullanıcının zengin talep tabanlı modelini kullanarak belirli bir korumalı kaynağa erişim izni olup olmadığını belirler. Örneğin, bir kullanıcı diğer kullanıcıların erişimi olmayan maaş bilgileri gibi belirli bilgileri okuyabilir.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Senaryo 3: Farklı talep eşleme  
 Bir kullanıcı bir Web hizmeti için bir ileti gönderir. Kullanıcı kimlik bilgilerini çeşitli farklı şekillerde belirtebilir: X.509 sertifikası, kullanıcı adı belirteci veya Kerberos belirteci. Web hizmeti aynı şekilde, kullanıcı kimlik bilgisi türü ne olursa olsun erişim denetimi kontrolleri gerçekleştirmek için gerekli değildir. Zaman içinde ek kimlik bilgisi türlerinin destekleniyorsa, sistem uygun şekilde gelişmesi.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Senaryo 4: Birden çok kaynaklarına erişimi belirleme  
 Bir Web hizmeti birden çok kaynağa erişmeyi dener. Hizmet kaynağa erişmek için talepleri kullanıcıyla ilişkili talep karşılaştırarak belirli bir kullanıcının erişimi olan korumalı hangi kaynakların gerekli belirler.  
  
## <a name="identity-model-terms"></a>Kimlik modeli koşulları  
 Aşağıdaki listede kimlik modeli kavramları açıklamak için kullanılan anahtar terimleri tanımlar.  
  
 Yetkilendirme İlkesi  
 Çıkış talep kümesine giriş talep kümesine eşleme kuralları kümesi. Talep kümesinde bir değerlendirme bağlamı ve daha sonra bir kimlik doğrulama bağlamını eklenmekte olan değerlendirilirken yetkilendirme ilkesi sonuçlanır.  
  
 Yetkilendirme bağlamı  
 Talep kümeleri kümesini ve sıfır veya daha fazla özellikleri. Bir veya daha fazla yetkilendirme ilkeleri değerlendirme sonucu.  
  
 Talep  
 Sağa, bir talep türü ve değer birleşimi.  
  
 Talep kümesi  
 Belirli bir veren tarafından verilen talepler kümesi.  
  
 Talep türü  
 Talep türü. Kimlik modeli API'si tarafından tanımlanan özelliklerini taleplerdir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> sınıfı. Sistem tarafından sağlanan talep türlerine örnek olarak verilebilir <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, ve <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 Değerlendirme bağlamı  
 Bir yetkilendirme ilkesi değerlendirileceğini bağlamı. Özellikler ve talep kümeleri içerir. Değerlendirme tamamlandıktan sonra bir kimlik doğrulama bağlamını temelini haline gelir.  
  
 Kimlik talebi  
 Bir talep, sağ kimliğidir.  
  
 Veren  
 En az bir kimlik talebi içerir ve başka yayımlandı olarak kabul edilen bir talep kümesine talep kümesi.  
  
 Özellikler  
 Değerlendirme bağlamı veya yetkilendirme bağlamı ile ilgili bilgileri kümesi.  
  
 Korumalı kaynak  
 Yalnızca kullanılan sistem erişilen, veya bir şeyin belirli gereksinimler karşılanırsa aksi yönetilebilir.  
  
 Sağ  
 Bir kaynak üzerinde bir özelliği. Kimlik modeli API'si tarafından tanımlanan özelliklerini haklarıdır <xref:System.IdentityModel.Claims.Rights> sınıfı. Sistem tarafından sağlanan hakları örnekleri <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Değer  
 Bir şey üzerinde bir hakkı talep.  
  
## <a name="claims"></a>Talepleri  
 Talep tabanlı bir sistemin kimlik modelidir. Talep sistem, genellikle bir kullanıcı sistem bazı varlıkla ilişkilendirilmiş yetenekleri açıklanmaktadır. Belirli bir varlıkla ilişkilendirilen talep kümesi, bir anahtar olarak düşünülebilir. Belirli talepleri benzer bir kapısının kilidi açmak için kullanılan fiziksel bir anahtar için bu anahtarı şeklini tanımlayın. Talepler, kaynaklara erişmek için kullanılır. Belirli bir korumalı kaynağa erişim izni varlık çalışırken erişim ile ilişkili talep ile bu kaynağa erişmek için gerekli talep karşılaştırarak belirlenir.  
  
 Bir talep belirli bir değeri göre sağa ifadesidir. Bir hak "Okuma", "Yazma" veya "Yürütme." gibi olabilir Bir değer, bir veritabanı, bir dosya, bir posta kutusu veya bir özellik olabilir. Talepler bir talep türü de bulunur. Talep türü ve sağa birleşimi değeri göre özelliklerini belirtmek için mekanizma sağlar. Örneğin, bir talep türü "Dosyası" değeri "Biography.doc" üzerinde doğru "Okuma" ile böyle bir talep ilişkili olduğu varlık Biography.doc dosyaya okuma erişimi olduğunu gösterir. Bir talep türü "Name" değeri "Martin" üzerinden sağ "PossessProperty" ile böyle bir talep ilişkili olduğu varlık "Martin" değerine sahip bir Name özelliğine sahip olduğunu gösterir.  
  
 Çeşitli talep türlerini ve hakları kimlik modelin parçası olarak tanımlanmasına rağmen ek talep türlerini ve hakları gerekli olarak tanımlamak için kimlik modeli altyapısının en üstünde derleme çeşitli sistemleri sağlayan genişletilebilir bir sistemdir.  
  
### <a name="identity-claims"></a>Kimlik talepleri  
 Belirli bir hak kimliğinin olmasıdır. Bu hakka sahip talep kimliği deyimi varlık olun. Örneğin, bir talep türü "kullanıcı asıl adı" (UPN) değerini "someone@example.com" ve belirli bir etki alanındaki belirli bir kimlik kimlik sağındaki gösterir.  
  
#### <a name="system-identity-claim"></a>Sistem kimlik talebi  
 Bir kimlik talep kimlik modelini tanımlar: Sistem. Sistem kimlik talebi bir varlık geçerli uygulama veya sistem olduğunu gösterir.  
  
### <a name="sets-of-claims"></a>Talep kümesi  
 Talepleri her zaman sistemde bazı varlık tarafından verilen varlık sonuçta bazı kavramı olsa bile kimliğini temsil etmek talep modelinin önemlidir, çünkü "self". Talepler bir küme olarak birlikte gruplandırılmış ve bir veren her ayarlanmış. Bir veren yalnızca talep kümesidir. Böyle bir özyinelemeli ilişki sonunda bitmelidir ve herhangi bir kendi veren olarak ayarlandığında isteyin.  
  
 Aşağıdaki şekilde üç adet talep örneği bir talep kümesi, verenini talep kümesine verenini olarak sistem sırayla olan başka bir talep kümesini, sahip olduğu gösterir. Bu nedenle, talep kümesi rasgele derin bir hiyerarşi oluşturur.  
  
 ![Beyanlar ve yetkilendirmeyi yönetme](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Birden çok talep kümesi, aynı talep kümesine, aşağıdaki çizimde gösterildiği gibi veren olabilir.  
  
 ![Beyanlar ve yetkilendirmeyi yönetme](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 Kendi veren bir talep kümesi dışında kimlik modelinde bir döngü oluşturuyor talep kümeleri için herhangi bir destek sağlamaz. Bu nedenle talep kümesi A kendisini bir talep kümesi tarafından verilmiş olan talep kümesi tarafından B, burada verilen bir durumda hiçbir zaman ortaya çıkabilir. Ayrıca, kimlik modelinde, birden çok verenler sağlamak talep kümeleri için herhangi bir destek sağlamaz. İki veya daha fazla veren verilen bir talep kümesini dağıtmalı, ardından, birden çok talep kümelerinin, her aynı talepleri içeren, ancak farklı verenler sahip kullanmanız gerekir.  
  
### <a name="the-origin-of-claims"></a>Talep kaynağı  
 Talepler bir çeşitli kaynaklardan gelebilir. Bir ortak talep örneğin bir Web hizmetine gönderilen bir iletinin bir parçası olarak bir kullanıcı tarafından sunulan kimlik bilgilerini kaynağıdır. Bu tür talepler sistem doğrular ve kullanıcıyla ilişkili talep kümesinin bir parçası olur. Diğer sistem bileşenlerini de dahil ancak bunlarla sınırlı olmamak üzere, işletim sistemi, ağ yığını, çalışma zamanı ortamı veya uygulama talep kaynakları olabilir. Ayrıca, uzak hizmetleri de talep kaynağı olabilir.  
  
### <a name="authorization-policies"></a>Yetkilendirme İlkeleri  
 Kimlik modelinde, talepler değerlendirme yetkilendirme ilkesi işleminin bir parçası üretilir. Bir yetkilendirme ilkesi (büyük olasılıkla boş) mevcut talepler kümesini inceleyen ve talep zaten mevcut ve onun elden ek bilgileri temel alarak ek talepleri eklemek isteyebilirsiniz. Bu talep arasında eşleme temelini sağlar. Varlığının veya yokluğunun sisteminde talepler olup ek talep ekler göre bir yetkilendirme ilkesi davranışını etkiler.  
  
 Örneğin, yetkilendirme ilkesi sistemini kullanarak çeşitli varlıkları birthdates içeren bir veritabanına erişimi vardır. Yetkilendirme İlkesi, bir "Over18" talep bağlama eklemek için bu bilgileri kullanır. Bu Over18 talep 18 yaşın üzerinde olduğu gerçeği farklı varlık hakkında hiçbir bilgi açıklamaz unutmayın. Bu talep semantiği anlama 'Over18' talep yorumu bağlı olduğunu unutmayın. Talep eklenen yetkilendirme ilkesi bu semantiği bazı düzeyinde bilir. Daha sonra ilke değerlendirme sürümünden neden talep inceler kodu aynı zamanda bu semantiği bilinçli.  
  
 Belirtilen yetkilendirme ilkesi, diğer yetkilendirme ilkeleri talepleri eklemek gibi daha fazla talep henüz bu yetkilendirme ilkesi ekleme olasılığınız olduğundan, birden çok kez değerlendirilmesi gerektirebilir. Kimlik modeli için hiçbir daha fazla talep zorla Yetkilendirme İlkeleri hiçbiri tarafından bağlamı için eklenene kadar değerlendirme devam etmek için tasarlanmıştır. Bu yetkilendirme ilkeleri sürekli değerlendirmesi herhangi belirli değerlendirme sırası göre yetkilendirme ilkelerini zorlamak için gereksinim engeller; herhangi bir sırada değerlendirilebilir. İlke X İlkesi A talep B eklediyseniz, yalnızca talep Z ekler, X ilk olarak değerlendirilirse, örneğin, daha sonra başlangıçta talep Z eklemez. Sonuç olarak, A değerlendirilir ve talep B. X sonra ikinci bir kez değerlendirilir ve bu süre talep Z ekler ekler.  
  
 Belirli bir sistem birçok Yetkilendirme İlkeleri yürürlükte olabilir.  
  
### <a name="a-key-making-machine"></a>Bir anahtar yapma makine  
 Bir grup ilişkili Yetkilendirme İlkeleri değerlendiren anahtarları sağlayan bir makine gibi kullanmaktır. Yetkilendirme her değerlendirilir ve anahtarın şekli oluşturma talep kümesi oluşturulan ilkelerdir. Anahtar şeklini tamamlandıktan sonra bazı kilitleri açmak için kullanılabilir. Anahtar şeklini "bir Yetkilendirme Yöneticisi tarafından oluşturulan bir yetkilendirme bağlamı" depolanır.  
  
### <a name="authorization-context"></a>Yetkilendirme bağlamı  
 Bir Yetkilendirme Yöneticisi'ni açıklandığı gibi çeşitli yetkilendirme ilkelerini değerlendirir ve bir kimlik doğrulama bağlamını (talep kümelerinin ve ilişkili bazı özellikler kümesi) sonucudur. Hangi talepleri bu çeşitli talep (örneğin, sertifika veren talep kümesi) arasındaki ilişkileri bu bağlamda mevcut olduğunu belirlemek ve sonuçta bunlar erişimi karşılamalıdır bazı gereksinimler karşı karşılaştırmak için kimlik doğrulama bağlamını incelenebilir bir Kaynak.  
  
### <a name="locks"></a>Kilitler  
 Bir kimlik doğrulama bağlamını (talep kümesi) bir anahtar ise, belirli bir korumalı kaynağa erişim izni vermek için karşılanması gereken gereksinimleri anahtar sığmalıdır kilidi oluşturur. Kimlik modeli bu gereksinimleri nasıl ifade resmileştirin değil, ancak bunlar sistem talep tabanlı yapısını verilen bazı gerekli talep dizi yetkilendirme bağlamında talep karşılaştırma içeren.  
  
### <a name="a-recap"></a>Bir özeti  
 Kimlik modelinde, talepler kavramı temel alır. Talep kümeleri halinde gruplandırılır ve bir yetkilendirme bağlamında bir araya getirilir. Bir kimlik doğrulama bağlamını talepler kümesi içeren ve Yetkilendirme Yöneticisi ile ilişkili bir veya daha fazla yetkilendirme ilkeleri değerlendirme sonucu. Bu ayarlar erişim gereksinimlerin karşılandığından, belirlemek için incelenebilir talep. Aşağıdaki şekilde bu çeşitli kimlik modeli kavramları arasındaki ilişkiler gösterilmektedir.  
  
 ![Beyanlar ve yetkilendirmeyi yönetme](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF ve kimlik modeli  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Kimlik modeli altyapısı yetkilendirme gerçekleştirmek için temel olarak kullanır. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> sınıfı belirtmenize olanak verir *yetkilendirme* ilkeleri bir hizmetin parçası olarak. Bu tür Yetkilendirme İlkeleri olarak da bilinir *dış Yetkilendirme İlkeleri*, ve yerel ilke veya bir uzak hizmetiyle etkileşim tarafından temel talep işleme gerçekleştirebilirsiniz. Tarafından temsil edilen Yetkilendirme Yöneticisi <xref:System.ServiceModel.ServiceAuthorizationManager> sınıf türleri (belirteçleri) çeşitli kimlik bilgisi tanıması Yetkilendirme İlkeleri ile birlikte dış yetkilendirme ilkelerini değerlendirir ve ne adlı doldurur bir  *kimlik doğrulama bağlamını* talepleri bir gelen iletiyi uygun. Kimlik doğrulama bağlamını tarafından temsil edilen <xref:System.IdentityModel.Policy.AuthorizationContext> sınıfı.  
  
## <a name="identity-model-programming"></a>Kimlik programlama modeli  
 Aşağıdaki tabloda, program kimliği Model uzantılarını için kullanılan nesne modeli açıklanmaktadır. Tüm bu sınıflar ya da mevcut <xref:System.IdentityModel.Policy> veya <xref:System.IdentityModel.Claims> ad alanları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|Yetkilendirme bileşeni|Arabirimini uygulayan bir kimlik modeli sınıfı <xref:System.IdentityModel.Policy.IAuthorizationComponent> arabirimi.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Tek bir salt okunur dize özelliği sağlayan bir arabirimi: kimliği. Bu özelliğin değeri bu arabirimi gerçekleştiren sistemdeki her örneği için benzersizdir.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|Bir *yetkilendirme bileşen* kümesi içeren `ClaimSet` sıfır veya daha fazla özellik örnekleriyle; bir veya daha fazla yetkilendirme ilkeleri değerlendirme sonucu.|  
|<xref:System.IdentityModel.Claims.Claim>|Bir talep türü, sağa ve değer birleşimi. Sağ ve değer bölümlerini talep türü ile sınırlıdır.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Özet temel sınıf. Bir koleksiyonu `Claim` örnekleri.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Korumalı bir sınıf. Uygulaması `ClaimSet` sınıfı.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Özet temel sınıf. Bir yetkilendirme ilkesi için ilke değerlendirmesi sırasında geçirildi.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Arabirim türetilen `IAuthorizationComponent` ve yetkilendirme ilkesi sınıfları tarafından uygulanır.|  
|<xref:System.IdentityModel.Claims.Rights>|Önceden tanımlanmış sağ değerleri içeren bir statik sınıf.|  
  
 Aşağıdaki sınıflar kimlik programlama modeli için de kullanılır, ancak içinde bulunamadı <xref:System.IdentityModel.Policy> veya <xref:System.IdentityModel.Claims> ad alanları.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Bir yöntem sağlayan bir sınıf — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>— talep tabanlı yetkilendirme gerçekleştirmek için her bir işlemde bir hizmet denetler. Sınıfından türetilen ve yöntemini geçersiz kılın.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Bir hizmet olarak davranışını ilgili çeşitli özellikler sağlayan bir korumalı sınıfı yetkilendirme için geçerlidir.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Kimlik doğrulama bağlamını, şu anda çalışan (veya yaklaşık çalıştırılacak) dahil olmak üzere güvenlik bağlamı sağlayan bir sınıf işlemi. Bu sınıf örneği parçası olan <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Önemli üyeleri  
 Aşağıdaki üyeleri, yaygın olarak yeni talep türleri oluşturmak için kullanılır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Türetilen sınıflar hizmet işlemleri çalıştırılmadan önce talep esaslı erişim denetimleri gerçekleştirmek için bu yöntemi uygulaması. Sağlanan tüm bilgileri <xref:System.ServiceModel.OperationContext>, veya başka bir yerde karar denetleyin erişim yaparken incelenebilir. Varsa <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndürür `true`, sonra erişim verilir ve çalıştırmak için işleme izin. Varsa `CheckAccessCore` döndürür `false`, sonra erişim reddedildi ve işlemi çalışmaz. Bir örnek için bkz: [nasıl yapılır: Özel Yetkilendirme Yöneticisi için bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Döndürür <xref:System.ServiceModel.ServiceAuthorizationManager> hizmeti. <xref:System.ServiceModel.ServiceAuthorizationManager> Yetkilendirme kararları sorumludur.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Hizmeti için belirtilen özel Yetkilendirme İlkeleri koleksiyonu. Bu ilkeler, gelen iletileri kimlik bilgileri ile ilişkili bu ilkelere ek olarak değerlendirilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Policy.EvaluationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationComponent>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims>  
 <xref:System.IdentityModel.Policy>  
 <xref:System.IdentityModel.Tokens>  
 <xref:System.IdentityModel.Selectors>  
 [Beyanlar ve belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Beyanlar ve kaynaklara erişimi reddetme](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)  
 [Talep oluşturma ve kaynak değerleri](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Nasıl yapılır: özel beyan oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)  
 [Nasıl yapılır: Beyanları](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Nasıl yapılır: özel yetkilendirme ilkesi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)  
 [Nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
