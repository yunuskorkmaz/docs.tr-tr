---
title: Hizmetleri Güvenli Hale Getirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
caps.latest.revision: 28
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: ffc985d528bfdcdd9b62772a8a8ba61823c95e76
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="securing-services"></a>Hizmetleri Güvenli Hale Getirme
Güvenlik bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] servis oluşur iki birincil gereksinimlerini: güvenlik ve yetkilendirme aktarın. (Üçüncü bir gereksinim güvenlik olaylarının denetlenmesini açıklanan [denetim](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Kısaca, Aktarım güvenlik (hem hizmet hem de istemci kimliğini doğrulama) kimlik doğrulama, gizliliği (ileti şifreleme) ve bütünlüğü (oynama algılamak imzalama sayısal) içerir. Yetkilendirme kaynaklarına, örneğin, bir dosyayı okumak yalnızca ayrıcalıklı kullanıcıların erişim denetimdir. Özelliklerini kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], iki birincil gereksinimlerini kolayca uygulanır.  
  
 Dışında <xref:System.ServiceModel.BasicHttpBinding> sınıfı (veya [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırma öğesinde), Aktarım güvenlik tüm önceden tanımlanmış bağlamaları için varsayılan olarak etkinleştirilir. Bu bölümdeki konular, iki temel senaryo kapsar: Internet Information Services (IIS) üzerinde barındırılan bir intranet hizmeti üzerinde aktarımı güvenlik ve yetkilendirme uygulayarak ve IIS üzerinde barındırılan bir hizmete aktarımı güvenlik ve yetkilendirme uygulama.  
  
> [!NOTE]
>  Windows XP Home Windows kimlik doğrulamasını desteklemez. Bu nedenle, bir hizmeti bu sistemde çalışmamalıdır.  
  
## <a name="security-basics"></a>Güvenlik temel kavramları  
 Güvenlik kullanır *kimlik bilgileri*. Bir kimlik bilgisi bir varlık kimin iddia ettiği olduğunu kanıtlar. (Bir *varlık* bir kişi, bir yazılım işlemi, bir şirket veya yetki verilmesi herhangi bir şey olabilir.) Örneğin, bir hizmetin istemci yaptığında bir *talep* , *kimlik*, ve bazı şekilde bu talep kimlik bilgisi kanıtlar. Tipik bir senaryo, kimlik bilgileri değişimi oluşur. İlk olarak, bir hizmeti bir talep kimliğini sağlar ve bir kimlik bilgisi istemciye kanıtlar. Buna karşılık, istemci bir talep kimliğini sağlar ve hizmet için kimlik bilgileri gösterir. Her iki taraf diğer kişinin kimlik bilgilerini güveniyorsanız sonra bir *güvenli içeriği* hangi tüm iletileri içinde gizliliği alınıp verilen kurulabilir ve bunların bütünlüğü korunacak imzalı tüm iletiler. Hizmetin kimliğini iletişim kurduktan sonra ardından için kimlik bilgilerini Taleplerde eşleştirebilirsiniz bir *rol* veya *üyelik* grubundaki. Rol veya istemcinin ait olduğu grubu kullanarak her iki durumda da, hizmet *yetkilendirir* sınırlı sayıda işlemleri gerçekleştirmek için istemci tabanlı rol veya grup ayrıcalıklarını.  
  
## <a name="windows-security-mechanisms"></a>Windows güvenlik mekanizmaları  
 İstemci ve hizmet bilgisayarı ağda oturum açmak için her ikisini de gerektiren bir Windows etki alanındaki her ikisi de varsa, kimlik bilgileri Windows altyapısı tarafından sağlanır. Bu durumda, ağa bilgisayar kullanıcı oturum açtığında kimlik bilgileri oluşturulur. Her kullanıcı ve ağ üzerindeki her bilgisayar kullanıcıları ve bilgisayarları güvenilen kümesine ait olarak doğrulanması gerekir. Bir Windows sisteminde, her bir kullanıcı ve bilgisayar olarak da bilinen bir *güvenlik sorumlusu*.  
  
 Tarafından desteklenen bir Windows etki alanındaki bir *Kerberos* denetleyicisi, Kerberos denetleyicisi biletleri her güvenlik sorumlusu verme dayalı bir şemasını kullanır. Bilet denetleyicisi verir sistemdeki diğer bilet granters tarafından güvenilmiyor. Her bir varlık çalışır bazı işlem ya da erişim gerçekleştirmek bir *kaynak* (bir dosya veya dizin bir makinede gibi), anahtar için kendi geçerlilik incelenir ve geçerse, asıl işlemi için başka bir bilet verilir. Bilet verme Bu yöntem, her işlem için asıl doğrulamak çalışan alternatif daha verimli olur.  
  
 Windows etki alanlarında kullanılan bir daha eski, daha az güvenli NT LAN Yöneticisi (NTLM) mekanizmasıdır. (Genellikle dışında bir Windows etki alanı, bir çalışma grubu gibi) Kerberos burada kullanılamaz durumda NTLM alternatif olarak kullanılabilir. NTLM, IIS için bir güvenlik seçeneği olarak da kullanılabilir.  
  
 Bir Windows sisteminde her bilgisayar ve kullanıcı rolleri ve grupları kümesine atayarak yetkilendirme çalışır. Örneğin, her Windows bilgisayarı ayarlamak ve gerekir rolde bir kişi (veya grup kişi) tarafından denetlenen *yönetici*. Başka bir rolü budur *kullanıcı*, çok daha kısıtlı bir izin kümesi vardır. Rol ek olarak, kullanıcı gruplarına atanır. Bir grup birden çok kullanıcıların aynı role gerçekleştirmesine izin verir. Uygulamada, bu nedenle, kullanıcı gruplarına atayarak bir Windows makinesine yönetilir. Örneğin, birkaç kullanıcı bir bilgisayarın kullanıcıları grubuna atanabilir ve çok daha kısıtlı bir kullanıcı kümesini Yöneticiler grubuna atanabilir. Bir yerel makinede yönetici ayrıca yeni gruplar oluşturabilir ve diğer kullanıcıları (veya hatta diğer grupları) grubuna atayın.  
  
 Windows çalıştıran bir bilgisayarda bir dizin her klasöründe korunabilir. Diğer bir deyişle, bir klasör ve dosyaları erişebilen denetimi seçin ve bunlar dosya kopyaladığınızda veya (en yüksek ayrıcalıklı durumda) değiştirme olup olmadığına bakılmaksızın bir dosyayı bir dosyayı silin veya klasöre dosya eklemek. Bu erişim denetimi olarak bilinir ve mekanizma erişim denetim listesi (ACL) olarak bilinir. ACL oluştururken, tüm grup veya grupları yanı için tek bir etki alanı üyeleri erişim ayrıcalıkları atayabilirsiniz.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Altyapısı bu Windows güvenlik mekanizmaları kullanmak için tasarlanmıştır. Bu nedenle, intranet üzerinde dağıtılan ve istemcileri Windows etki alanının bir üyesi için sınırlı bir hizmeti oluşturuyorsanız, güvenlik kolayca uygulanır. Yalnızca geçerli kullanıcılar etki alanında oturum açabilir. Kullanıcı oturum açtıktan sonra herhangi bir bilgisayar veya uygulama güvenli bağlamlarla oluşturmak her bir kullanıcı Kerberos denetleyicisi sağlar. Yerel makinede grupları kolayca oluşturulabilir ve bilgisayarda erişim ayrıcalıkları atamak için belirli klasörleri korurken, bu grupları kullanılabilir.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Windows güvenliği Intranet Services'de uygulama  
 Özel olarak bir Windows etki alanı üzerinde çalışan bir uygulama güvenliğini sağlamak için ya da varsayılan güvenlik ayarlarını kullanabilirsiniz <xref:System.ServiceModel.WSHttpBinding> veya <xref:System.ServiceModel.NetTcpBinding> bağlama. Varsayılan olarak, aynı Windows etki alanı üzerinde herkes erişebilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri. Kullanıcılar ağda oturum olduğundan, bunlar güvenilir. Bir hizmet ve istemci arasındaki iletileri gizliliği için şifrelenir ve bütünlük için imzalanır. Windows güvenliği kullanan bir hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows kimlik bilgileri olan bir hizmeti güvenli](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>PrincipalPermissionAttribute sınıfı kullanarak Yetkilendirme  
 Bir bilgisayardaki kaynaklara erişimini kısıtlamak gerekiyorsa, en kolay yolu kullanmaktır <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfı. Bu öznitelik, kullanıcının belirtilen Windows grubu veya rolü olması yoğun hizmet işlemlerini çağrılmasını kısıtlamak için veya belirli bir kullanıcı olmasını sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtla](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Kimliğe bürünme  
 Kimliğe bürünme kaynaklara erişimi denetlemek için kullanabileceğiniz başka bir mekanizmadır. Varsayılan olarak, IIS tarafından barındırılan bir hizmete ASPNET hesabı kimliği altında çalışır. ASP.NET hesabından yalnızca iznine sahip kaynaklara erişebilir. Ancak, ASPNET hizmet hesabını dışlamak ancak klasörüne erişmek diğer belirli kimlikleri izin vermek için bir klasör ACL ayarlamak mümkündür. Soru sonra bu kullanıcıların bunu yapmak için ASP.NET hesabından verilmiyorsa klasörü erişmesine izin vermek nasıl olur. Yanıt, kimliğe bürünme, belirli bir kaynağa erişmek için istemci kimlik bilgilerini kullanmak için hizmet yapabildiği izin kullanmaktır. Yalnızca belirli kullanıcılara izni olan bir SQL Server veritabanına erişirken bunun başka bir örnektir. Kimliğe bürünme kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir hizmete bir istemcinin kimliğine bürünmek](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) ve [temsilcilik ve kimliğe bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Internet güvenliği  
 Internet üzerindeki güvenlik intranet güvenlik aynı gereksinimlerini oluşur. Bir hizmetin gerçekliği kanıtlamak için kimlik bilgilerini sunmak için ihtiyaç ve hizmete kimliğini kanıtlamak istemcileri gerekir. Bir istemcinin kimliğini kanıtlanmış sonra hizmet istemci kaynaklara sahip ne kadar erişimi denetleyebilirsiniz. Ancak, Internet heterojen yapısı nedeniyle, sunulan kimlik bilgilerini bir Windows etki alanında kullanılanlardan farklı. Kimlik doğrulaması kimlik bilgilerini, Internet üzerindeki biletlerini sahip bir etki alanı kullanıcıları için bir Kerberos denetleyicisi işleme ise hizmetler ve istemcileri kimlik sunmak için birçok farklı yöntemle herhangi birini kullanır. Amacı, bu konu, ancak oluşturmanızı sağlayan ortak bir yaklaşım sunmak için olan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Internet üzerinden erişilebilen hizmet.  
  
### <a name="using-iis-and-aspnet"></a>IIS ve ASP.NET kullanma  
 Bu sorunları çözmek için gereksinimler Internet security and mekanizmaları yeni değildir. IIS Microsoft'un Web sunucusu için Internet ve bu sorunları gidermek birçok güvenlik özelliği vardır; Ayrıca, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] içeren güvenlik özellikleri [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetleri kullanabilir. Bu güvenlik özelliklerden yararlanmak için konağı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] IIS'de hizmet.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>ASP.NET üyelik ve rol sağlayıcıları kullanma  
 ASP.NET üyelik ve rol sağlayıcısı içerir. Sağlayıcı bir kullanıcı adı/parola çifti her çağıranın erişim ayrıcalıkları belirtmenizi sağlar arayanlar kimlik doğrulaması için veritabanıdır. İle [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], önceden varolan bir üyelik ve rol sağlayıcısı yapılandırması aracılığıyla kolayca kullanabilirsiniz. Bu gösteren örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../docs/framework/wcf/samples/membership-and-role-provider.md) örnek.  
  
### <a name="credentials-used-by-iis"></a>IIS tarafından kullanılan kimlik bilgileri  
 Kerberos denetleyicisi tarafından desteklenen bir Windows etki alanı farklı olarak, Internet dilediğiniz zaman oturum açan kullanıcıların milyonlarca yönetmek için tek bir denetleyici olmadan bir ortamdır. Bunun yerine, kimlik bilgileri Internet üzerindeki en sık X.509 sertifikaları (Güvenli Yuva Katmanı ya da SSL, sertifikaları olarak da bilinir) şeklindedir. Bu sertifikalar genellikle tarafından verilen bir *sertifika yetkilisi*, bu sertifikanın ve kişi Orijinallik onaylayan bir üçüncü taraf şirket olabilen için yayımlanmıştır. Internet hizmet kullanıma sunmak için da hizmetiniz kimliğini doğrulamak için bu tür bir güvenilen sertifika sağlamanız gerekir.  
  
 Sorunun bu noktada, bu tür bir sertifika nasıl aldığınız ortaya? Authenticode veya VeriSign gibi bir üçüncü taraf sertifika yetkilisi hizmetinizi dağıtmak ve hizmetiniz için bir sertifika satın almak hazır olduğunuzda Git bir yaklaşımdır. Ancak, ile geliştirme aşamasındadır varsa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve henüz bir sertifika satın alma işleminde yürütmek için hazır, araçları ve teknikleri Üretim dağıtımı benzetimini yapmak için kullanabileceğiniz X.509 sertifikalarını oluşturmak için mevcut. Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Güvenlik modu  
 Programlama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] güvenlik birkaç önemli karar noktaları kapsar. En temel biri seçimi *güvenlik modunu*. İki ana güvenlik modu *aktarım modu* ve *ileti modu*.  
  
 Her iki ana mod semantiği birleştirir, üçüncü bir mod *ileti kimlik bilgileri modu ile aktarma*.  
  
 İleti güvenliği nasıl güvenlik modunu belirler ve her seçenek avantajları ve dezavantajları, aşağıda açıklandığı gibi vardır. Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Aktarım modu  
 Ağ ve uygulama arasında birkaç katmandan vardır. Bunlardan biri *aktarım* katman *,* uç noktalar arasında ileti aktarımını yönetir. Mevcut bir amaçla ise yalnızca, anlamanız gereken [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] her biri ileti aktarımını güvenliğini sağlayabilirsiniz, birçok aktarım protokollerini kullanır. (Aktarımları hakkında daha fazla bilgi için bkz: [taşımaları](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Yaygın olarak kullanılan bir protokol HTTP'dir; başka bir TCP olur. Bu protokollerin her ileti bir mekanizma (veya mekanizmaları) tarafından aktarımı belirli protokolüne güvenliğini sağlayabilirsiniz. Örneğin, HTTP protokolünü yaygın olarak "HTTPS" kısaltılır HTTP üzerinden güvenliğinin SSL ile Bu nedenle, güvenlik aktarım modu seçtiğinizde, protokolü tarafından gerektiği şekilde mekanizması kullanmayı seçmeden. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfı ve aktarım için kendi güvenlik modunu ayarlama SSL üzerinden HTTP (HTTPS) güvenlik mekanizması olarak seçme. Aktarım modu avantajlarından daha düşük bir düzeyde güvenlik tümleşik olduğundan, ileti modu'den daha verimli olmasıdır. Aktarım modu kullanırken, güvenlik mekanizması taşıma için belirtimine göre uygulanması gerekir ve böylece iletileri güvenli bir şekilde yalnızca noktadan noktaya aktarma üzerinden akabilir.  
  
#### <a name="message-mode"></a>İleti modu  
 Buna karşılık, ileti modu, her ileti bir parçası olarak güvenlik verileri dahil olmak üzere güvenlik sağlar. XML ve SOAP Güvenliği üstbilgileri, kimlik bilgilerini ve bütünlüğü ve gizliliği iletinin her iletinin dahil olduğundan emin olmak için gereken diğer verileri kullanma. Her ileti tek tek işlenmesi gerektiği için ücretli performansı sonuçlanır için güvenlik verileri, her ileti içerir. (Aktarım katmanı güvenli hale getirildikten sonra aktarım modunda tüm iletileri serbestçe akışı.) Bununla birlikte, ileti güvenliği taşıma güvenliği üzerinde bir avantaj vardır: daha esnektir. Diğer bir deyişle, güvenlik gereksinimlerini taşıma tarafından belirlenmiş olmak zorunda değildir. İleti güvenliğini sağlamak için herhangi bir türde istemci kimlik bilgileri kullanabilirsiniz. (Aktarım modunda aktarım protokolünü kullanabilirsiniz istemci kimlik bilgileri türünü belirler.)  
  
#### <a name="transport-with-message-credentials"></a>İleti kimlik bilgileriyle taşıma  
 Üçüncü modu en iyi aktarım ve ileti güvenliği birleştirir. Bu modda, taşıma güvenliği her ileti bütünlüğü ve gizliliği verimli bir şekilde sağlamak için kullanılır. Aynı anda her ileti iletinin kimliğinin doğrulanmasını sağlar, kimlik bilgisi verileri içerir. İle kimlik doğrulaması, yetkilendirme da uygulanabilir. Bir gönderici kimlik doğrulaması yaparak kaynaklarına erişimi izni (reddedildi göre gönderenin kimliğini veya).  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Kimlik bilgisi değeri ve istemci kimlik bilgileri türünü belirtme  
 Güvenlik modu seçtikten sonra bir istemci kimlik bilgisi türü belirtmek isteyebilirsiniz. İstemci kimlik bilgisi türü bir istemci sunucuya kendi kimliğini doğrulamak için kullanmanız gerekir hangi türünü belirtir.  
  
 Tüm senaryolarda, ancak bir istemci kimlik bilgisi türü gerektirir. HTTP (HTTPS) üzerinden SSL kullanarak bir hizmet kendi istemcinin kimliğini doğrular. Bu kimlik doğrulama bir parçası olarak, hizmetin sertifika adlı bir işlem istemcisinde gönderilir *anlaşma*. SSL korumalı aktarım tüm iletileri gizli olmasını sağlar.  
  
 İstemcinin kimliğinin doğrulanmasını gerektiren bir hizmeti oluşturuyorsanız, tercih ettiğiniz bir istemci kimlik bilgisi türü taşıma ve modu seçili bağlıdır. Örneğin, aktarım modu seçme ve HTTP aktarımı kullanarak temel, Özet ve diğerleri gibi çeşitli seçenekler sunar. (Bunlar hakkında daha fazla bilgi için kimlik bilgisi türlerini, bkz: [anlama HTTP kimlik doğrulaması](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Yalnızca ağ diğer kullanıcılar için kullanılabilir olacak bir Windows etki alanında bir hizmet oluşturuyorsanız, kullanılacak Windows istemcisi kimlik bilgisi türü kolayıdır. Ancak, bir sertifika ile bir hizmet sağlamak de gerekebilir. Bu gösterilen [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Kimlik bilgisi değerleri  
 A *kimlik bilgisi değeri* olan gerçek kimlik bilgisi hizmeti kullanır. Bir kimlik bilgisi türü belirledikten sonra hizmetiniz gerçek kimlik bilgileriyle yapılandırmanız gerekebilir. Ardından, Windows seçtiğiniz (ve hizmet, bir Windows etki alanı üzerinde çalışır varsa), gerçek kimlik bilgisi değeri belirtmeyin.  
  
## <a name="identity"></a>Kimlik  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], terimi *kimlik* sunucu ve istemci için farklı anlamları vardır. Kısaca, bir hizmeti çalıştıran, bir kimlik güvenlik bağlamına kimlik doğrulamasından sonra atanır. Gerçek kimliğini görüntülemek için kontrol <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> özelliklerini <xref:System.ServiceModel.ServiceSecurityContext> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: güvenlik bağlamını İnceleme](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Buna karşılık, istemcide, kimlik hizmetini doğrulamak için kullanılır. Tasarım zamanında bir istemci Geliştirici ayarlayabilirsiniz [ \<kimliği >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesine hizmetinden alınan bir değer. Çalışma zamanında istemci hizmeti gerçek kimliğini karşı öğenin değerini denetler. İstemci denetimi başarısız olursa iletişimi sona erer. Hizmet bir makine hesabı altında çalışıyorsa, belirli bir kullanıcının kimlik veya bir hizmet asıl adı (SPN) altında hizmet çalışıyorsa, değer bir kullanıcı asıl adı (UPN) olabilir. Daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Kimlik bilgisi ayrıca bir sertifika veya sertifika tanımlayan bir sertifikanın bulunan bir alan olabilir.  
  
## <a name="protection-levels"></a>Koruma düzeyleri  
 `ProtectionLevel` Özelliği üzerinde birkaç öznitelik sınıfları oluşur (gibi <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları). Koruma düzeyi iletileri (ileti bölümleri) bir hizmet oturumunuz destekleyen imzalanmış ve şifrelenmiş veya imza veya şifreleme gönderilen olup olmadığını belirten bir değerdir. Özelliği hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md)ve programlama örnekler için bkz: [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Bir hizmet sözleşmesini ile tasarlama hakkında daha fazla bilgi için `ProtectionLevel` bağlamda bkz [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Temsilcilik ve Kimliğe Bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Hizmet Sözleşmeleri Tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Güvenlik](../../../docs/framework/wcf/feature-details/security.md)  
 [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Nasıl yapılır: Güvenlik Modunu Ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Nasıl Yapılır: Güvenlik Bağlamını İnceleme](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
