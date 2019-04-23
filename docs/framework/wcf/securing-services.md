---
title: Hizmetleri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: 65d4f2858c2be4c2a6872f96ef3739bb16253d74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157683"
---
# <a name="securing-services"></a>Hizmetleri Güvenli Hale Getirme
Bir Windows Communication Foundation (WCF) hizmetinin güvenlik iki birincil gereksinimlerini oluşur: güvenlik ve yetkilendirme aktarın. (Üçüncü bir gereksinim, güvenlik olaylarının denetlenmesini açıklanan [denetim](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Kısaca, aktarım güvenliği (hem hizmet hem de istemci kimlik doğrulama) kimlik gizliliği (ileti şifreleme) ve bütünlüğü (dijital oynama algılamak imzalama) içerir. Yetkilendirme, kaynaklarına, örneğin, bir dosyayı okumak yalnızca ayrıcalıklı kullanıcıların erişim denetimidir. WCF özelliklerini kullanarak, iki birincil gereksinimlerini kolayca uygulanır.  
  
 Dışında <xref:System.ServiceModel.BasicHttpBinding> sınıfı (veya [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırma öğesinde), aktarım güvenliği tüm önceden tanımlanmış bağlamaları için varsayılan olarak etkindir. Bu bölümdeki konular, iki temel senaryo içerir: Internet Information Services (IIS) üzerinde barındırılan bir intranet hizmeti üzerinde uygulama aktarım güvenliği ve yetkilendirme ve IIS'de barındırılan bir hizmete uygulama aktarım güvenliği ve yetkilendirme.  
  
> [!NOTE]
>  Windows XP Home Windows kimlik doğrulamasını desteklemez. Bu nedenle, bir hizmet söz konusu sistemdeki çalıştırmamalısınız.  
  
## <a name="security-basics"></a>Güvenlik temel kavramları  
 Güvenlik dayanır *kimlik bilgilerini*. Bir kimlik bilgisi, varlığın kim olduğunu beyan olduğunu kanıtlar. (Bir *varlık* bir kişi, bir yazılım işlemi, bir şirket veya yetkilendirilebilir herhangi bir şey olabilir.) Örneğin, bir istemci bir hizmet sağlar bir *talep* , *kimlik*, ve kimlik bilgisi bir yolla bu talebi kanıtlar. Tipik bir senaryoda, kimlik bilgileri değişimi gerçekleşir. İlk olarak, bir hizmeti bir talep kimliğini sağlar ve bir kimlik bilgisi istemciye kanıtlar. Buna karşılık, istemci bir talep kimliğini sağlar ve bir kimlik hizmeti sunar. Her iki taraf diğer tarafın kimlik bilgilerini güveniyorsanız bir *güvenli bağlam* gizliliği hangi tüm iletileri değiş tokuş edileceğini oluşturulabilir ve kendi bütünlüğünü korumak için imzalı tüm iletiler. Hizmete istemcinin kimliğini iletişim kurduktan sonra ardından kimlik için talep eşleşebilir bir *rol* veya *üyelik* grubundaki. Rol veya istemcinin ait olduğu Grup kullanarak her iki durumda da, hizmet *yetkilendirir* sınırlı sayıda işlemleri gerçekleştirmek için istemci temel rol veya grup ayrıcalıklarına.  
  
## <a name="windows-security-mechanisms"></a>Windows güvenlik mekanizmaları  
 İstemci ve hizmet bilgisayar ağda oturum açmak için her ikisini de gerektiren bir Windows etki alanındaki her ikisi de varsa, kimlik bilgilerinin Windows altyapısı tarafından sağlanır. Bu durumda, ağa bir bilgisayar kullanıcı oturum açtığında kimlik bilgileri oluşturulur. Kullanıcıları ve bilgisayarları güvenilen kümesine ait olarak, her kullanıcı ve her bilgisayar ağ üzerinde doğrulanmış olması gerekir. Bir Windows sisteminde, her bir kullanıcı ve bilgisayar olarak da bilinen bir *güvenlik sorumlusu*.  
  
 Tarafından desteklenen bir Windows etki alanındaki bir *Kerberos* denetleyicisi Kerberos denetleyicisi her güvenlik sorumlusu için bilet verme hakkında temel bir düzeni kullanır. Biletleri denetleyicisi verir sistemdeki diğer bilet granters tarafından güvenilmiyor. Her varlığın çalışır bazı işlem ya da erişim gerçekleştirmek bir *kaynak* (bir dosya veya dizin bir makinede gibi), anahtar geçişi için geçerliliğini incelenir ve asıl geçerse, işlem için başka bir bilet verilir. Bilet verme Bu yöntem her işlem için asıl doğrulanırken alternatif daha verimlidir.  
  
 Windows etki alanlarında kullanılan bir, daha az güvenli eski NT LAN Manager (NTLM) mekanizmasıdır. Kerberos (genellikle dışında bir Windows etki alanı, bir çalışma grubu gibi) burada kullanılamaz durumda, NTLM, alternatif olarak kullanılabilir. NTLM, IIS için bir güvenlik seçeneği olarak da kullanılabilir.  
  
 Bir Windows sisteminde her bilgisayar ve kullanıcı kümesine rollerin ve grupların atayarak yetkilendirme çalışır. Örneğin, her Windows bilgisayarı gerekir ayarlanması ve bir kişi (veya kişi grubunu) rolünü denetlenen *yönetici*. Başka bir rol budur *kullanıcı*, daha kısıtlı bir izin kümesi vardır. Rol ek olarak, kullanıcı gruplarına atanır. Bir grup içindeki aynı rolü gerçekleştirmek birden fazla kullanıcı sağlar. Uygulamada, bu nedenle, Windows makine kullanıcı gruplarına atama tarafından yönetilir. Örneğin, birkaç kullanıcı bir bilgisayarın kullanıcıları grubuna atanabilir ve çok daha kısıtlı bir kullanıcı kümesini Yöneticiler grubuna atanabilir. Yerel bir makinede bir yönetici ayrıca yeni gruplar oluşturabilir ve diğer kullanıcılar (veya hatta diğer grupları) grubuna atayın.  
  
 Windows çalıştıran bir bilgisayarda, bir dizindeki her klasör korunabilir. Diğer bir deyişle, bir klasör ve dosyaları erişebilen bir denetim seçin ve bunlar dosyasını kopyalayın veya değiştirme (en yüksek ayrıcalıklı durumda) olup olmadığını bir dosya bir dosyayı silin veya klasöre dosya ekleyin. Bu erişim denetimi olarak bilinir ve bu mekanizma erişim denetimi listesi (ACL) olarak bilinir. ACL'yi oluştururken herhangi grup veya grupları, aynı zamanda için tek bir etki alanı üyeleri erişim ayrıcalıkları atayabilirsiniz.  
  
 WCF altyapısı, bu Windows güvenlik mekanizmaları kullanması için tasarlanmıştır. Bu nedenle, güvenlik, intranet üzerinde dağıtılır ve istemcileri Windows etki alanının bir üyesi için sınırlı bir hizmeti oluşturuyorsanız, kolayca uygulanır. Yalnızca geçerli kullanıcılar etki alanında oturum açabilir. Kullanıcılar oturum açtıktan sonra Kerberos denetleyicisi herhangi bir bilgisayar veya uygulama ile güvenli bağlamları kurmak her bir kullanıcı etkinleştirir. Yerel bir makinede grupları bir kolayca oluşturulabilir ve bilgisayarda erişim ayrıcalıkları atamak için belirli klasörlere korurken, bu gruplar kullanılabilir.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Windows Güvenlik Intranet hizmetler üzerinde uygulama  
 Özel bir Windows etki alanında çalışan bir uygulamayı güvenli hale getirmek için ya da varsayılan güvenlik ayarlarını kullanabilirsiniz <xref:System.ServiceModel.WSHttpBinding> veya <xref:System.ServiceModel.NetTcpBinding> bağlama. Varsayılan olarak, WCF hizmetleri aynı Windows etki alanı'teki herkes erişebilir. Bu kullanıcılar ağa oturum olduğundan, bunlar güvenilirdir. Bir hizmet ve istemci arasında iletileri için gizlilik şifrelenir ve bütünlük için imzalanır. Windows Güvenlik kullanan bir hizmet oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows kimlik bilgileri ile bir hizmeti güvenli hale getirme](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>PrincipalPermissionAttribute sınıfı kullanarak Yetkilendirme  
 Bir bilgisayardaki kaynaklara erişimini kısıtlamak gerekiyorsa, en kolay yolu kullanmaktır <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfı. Bu öznitelik, kullanıcı bir belirtilen bir Windows grubu veya rolü yoğun hizmet işlemlerini çağırmayı kısıtlamak için ya da belirli bir kullanıcı olmasını sağlar. Daha fazla bilgi için [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Kimliğe bürünme  
 Kimliğe bürünme, kaynaklara erişimi denetlemek için kullanabileceğiniz başka bir mekanizmadır. Varsayılan olarak, IIS tarafından barındırılan bir hizmet hesabından kimliği altında çalışır. ASP.NET hesabından yalnızca iznine sahip kaynaklara erişebilirsiniz. Ancak, bir klasör için ACL ASPNET hizmet hesabı hariç, ancak bazı diğer kimlikleri klasöre erişmek izin ayarlamak mümkündür. Sorunun sonra bunu yapmak için ASP.NET hesabından izin verilmiyorsa klasöre erişmek bu kullanıcılara izin verecek şekilde nasıl olur. Yanıt, kimliğe bürünme, hizmet belirli bir kaynağa erişmek için istemci kimlik bilgilerini kullanmak için izin verebileceğiniz kullanmaktır. Yalnızca belirli kullanıcılara izni olan bir SQL Server veritabanına erişirken bunun başka bir örnektir. Kimliğe bürünme kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir hizmette istemci kimliğine bürünme](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) ve [temsilcilik ve kimliğe bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Internet güvenliği  
 Internet üzerindeki güvenlik intranet güvenlik gereksinimleri aynıdır oluşur. Hizmet gerçekliği kanıtlamak için kimlik bilgilerini sunmak gereken ve istemcileri için hizmet kimliklerini kanıtlamak gerekir. Bir istemcinin kimliği kanıtlanmış sonra hizmet istemci ne kadar kaynaklarına erişimi denetleyebilirsiniz. Ancak, Internet heterojen yapısı nedeniyle, sunulan kimlik bilgilerinin bir Windows etki alanında kullanılanlardan farklı. Bilet kimlik bilgileri, İnternet'e sahip bir etki alanı kullanıcı kimlik doğrulaması bir Kerberos denetleyicisi işleme ise hizmet ve istemcileri kimlik sunmak için çeşitli yollar birini kullanır. Bu konunun amacı, ancak Internet üzerinden erişilebilir bir WCF hizmeti oluşturma olanak tanıyan ortak bir yaklaşım sunmak için olabilir.  
  
### <a name="using-iis-and-aspnet"></a>IIS ve ASP.NET kullanarak  
 Bu sorunları çözmek için gereksinimleri Internet güvenliği ve mekanizmaları yeni değildir. IIS, Microsoft'un Web sunucusu için Internet ve bu sorunları gidermeye birçok güvenlik özelliği vardır; Ayrıca, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] WCF hizmetleri kullanarak güvenlik özellikleri içerir. Bu güvenlik özelliklerinden yararlanmak için IIS üzerinde bir WCF Hizmeti barındırma.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>ASP.NET üyelik ve rol sağlayıcıları kullanma  
 ASP.NET üyelik ve rol sağlayıcısı içerir. Sağlayıcı, ayrıca, her çağıranın erişim ayrıcalıkları belirtmenizi sağlar çağıranlar kimlik doğrulaması için kullanıcı adı/parola çiftlerinin bir veritabanı hizmetidir. WCF ile önceden varolan bir üyelik ve rol sağlayıcısını yapılandırma yoluyla kolayca kullanabilirsiniz. Bu gösteren örnek bir uygulama için bkz. [üyelik ve rol sağlayıcısı](../../../docs/framework/wcf/samples/membership-and-role-provider.md) örnek.  
  
### <a name="credentials-used-by-iis"></a>IIS tarafından kullanılan kimlik bilgileri  
 Kerberos denetleyicisi tarafından desteklenen bir Windows etki alanı farklı olarak, Internet dilediğiniz zaman oturum açan kullanıcıların milyonlarca yönetmek için tek bir denetleyici olmadan bir ortamdır. Bunun yerine, kimlik bilgilerini Internet'teki en sık X.509 sertifikaları (Güvenli Yuva Katmanı ya da SSL sertifikaları olarak da bilinir) biçimindedir. Bu sertifikalar genellikle tarafından verilen bir *sertifika yetkilisi*, sertifika ve kişinin güvenilirliğini, onaylayan bir üçüncü taraf şirket olabilen için verildi. Internet hizmet kullanıma sunmak için hizmet kimlik doğrulaması için bu tür bir güvenilen sertifika sağlamanız gerekir.  
  
 Soru, bu noktada, bu tür bir sertifika nasıl ulaşabileceğinizi ortaya? Authenticode veya VeriSign gibi bir üçüncü taraf sertifika yetkilisi hizmetinizi dağıtmadan ve hizmetiniz için bir sertifika satın almak hazır olduğunuzda Git bir yaklaşımdır. Ancak, WCF ile geliştirme aşamasında olan ve henüz hazır değil bir sertifika satın alma işleminde kaydetmek, Araçlar ve teknikler X.509 sertifikaları oluşturmak için mevcut bir üretim dağıtımının benzetimini yapmak için kullanabilirsiniz. Daha fazla bilgi için [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Güvenlik modu  
 WCF güvenliğini programlama birkaç kritik karar noktaları kapsar. En temel biri olan seçimi *güvenlik modu*. İki önemli güvenlik modu *aktarım modu* ve *mesaj moduna*.  
  
 Her iki ana mod semantiği birleştiren, üçüncü bir moddur *aktarım ileti kimlik bilgilerini modunda*.  
  
 İleti güvenliği nasıl güvenlik modunu belirler ve her seçeneği avantajları ve dezavantajları, aşağıda açıklandığı gibi vardır. Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Aktarım modu  
 Ağ ve uygulama arasında birden fazla katman vardır. Bunlardan biri *aktarım* katman *,* uç noktalar arasında ileti aktarımını yönetir. Mevcut bir amaç için ise yalnızca WCF her biri güvenli aktarım ileti çeşitli aktarım protokolünü kullanan anlamanız gerekir. (Aktarımları hakkında daha fazla bilgi için bkz: [taşımalar](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Yaygın olarak kullanılan protokol HTTP'dir; TCP da başka bir özelliktir. Her biri bu protokolleri, ileti aktarım mekanizması (veya mekanizmaları) göre belirli Protokolü güvenliğini sağlayabilirsiniz. Örneğin, HTTP protokolü yaygın olarak "HTTPS" kısaltılır HTTP üzerinden SSL kullanarak güvenli Güvenlik için aktarım modu seçtiğinizde, bu nedenle, ister protokolü tarafından belirlenen mekanizmasının kullanılması seçim. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfı ve aktarım için kendi güvenlik modunu ayarlama SSL üzerinden HTTP (HTTPS) güvenlik mekanizması olarak seçiyorsunuz. Aktarım modu avantajlarından daha düşük bir düzeyde güvenlik tümleşik olduğundan, ileti modu daha verimli olmasıdır. Taşıma için belirtimine göre aktarım modunu kullanırken, güvenlik mekanizması uygulanmalıdır ve bu nedenle iletileri güvenli bir şekilde yalnızca noktadan noktaya aktarma üzerinden akabilir.  
  
#### <a name="message-mode"></a>İleti modu  
 Buna karşılık, ileti modu, her ileti bir parçası olarak güvenlik verileri dahil olmak üzere güvenlik sağlar. XML ve SOAP güvenlik üst bilgileri, kimlik bilgilerini ve ileti gizliliği ve bütünlük her iletinin dahil olduğundan emin olmak için gereken diğer veriler kullanma. Her ileti tek tek her ileti işleme için performans üzerindeki bir Ücretli sonuçlanır için güvenlik verilerini içerir. (Aktarım katmanı güvenli hale getirildikten sonra aktarım modunda tüm iletileri ücretsiz flow.) Bununla birlikte, ileti güvenliği aktarım güvenliği bir avantajı vardır: daha esnektir. Diğer bir deyişle, güvenlik gereksinimlerini taşıma tarafından belirlenen değil. İleti güvenliğini sağlamak için herhangi bir türde istemci kimlik bilgilerini kullanabilirsiniz. (Aktarım modunda Aktarım Protokolü, kullanabileceğiniz istemci kimlik bilgisi türünü belirler.)  
  
#### <a name="transport-with-message-credentials"></a>İleti kimlik bilgileri ile aktarma  
 Üçüncü modu, hem aktarım hem de ileti güvenlik en iyi şekilde birleştirir. Bu modda, aktarım güvenliği, gizliliği ve bütünlüğü her iletinin verimli bir şekilde sağlamak için kullanılır. Aynı zamanda, her ileti iletinin doğrulanmasını sağlar, kimlik bilgisi verileri içerir. Kimlik doğrulama ile yetkilendirme da uygulanabilir. Bir gönderici kimlik doğrulaması yaparak kaynaklara erişim izni (reddedildi göre Gönderen Kimliği veya).  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Kimlik bilgisi değeri ve istemci kimlik bilgileri türünü belirtme  
 Güvenlik modu seçtikten sonra istemci kimlik bilgileri türünü belirtme isteyebilirsiniz. Ne tür bir istemci sunucuya kendi kimliğini doğrulamak için kullanmanız gerekir istemci kimlik bilgileri türünü belirtir.  
  
 Tüm senaryolarda, ancak bir istemci kimlik bilgisi türü gerektirir. HTTP (HTTPS) üzerinden SSL kullanarak bir hizmet kendisini istemcinin kimliğini doğrular. Bu kimlik doğrulama işleminin bir parçası olarak, hizmetin sertifika adlı bir işlem istemciye gönderilen *anlaşma*. SSL korumalı aktarım tüm iletileri gizli olmasını sağlar.  
  
 İstemcinin kimliğinin doğrulanmasını gerektiren bir hizmeti oluşturuyorsanız, tercih ettiğiniz bir istemci kimlik bilgisi türü taşıma ve seçili modu bağlıdır. Örneğin, HTTP aktarımı kullanarak ve aktarım modunu seçme temel, Özet ve diğerleri gibi çeşitli seçenekler sunar. (Bunlar hakkında daha fazla bilgi için kimlik bilgisi türleri, bkz: [anlama HTTP kimlik doğrulaması](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Bir hizmet ağın diğer kullanıcıların kullanıma sunulacak bir Windows etki alanı oluşturuyorsanız, kullanılacak Windows istemcisi kimlik bilgisi türü kolayıdır. Ancak, ayrıca bir sertifika ile hizmet sağlamanız gerekebilir. Bu gösterilen [nasıl yapılır: İstemci kimlik bilgileri değerlerini belirtme](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Kimlik bilgileri değerlerini  
 A *kimlik bilgisi değeri* olan gerçek kimlik bilgisi hizmeti kullanır. Bir kimlik bilgisi türünü belirttikten sonra gerçek kimlik bilgileri ile hizmetinizi yapılandırma gerekebilir. Ardından Windows seçtiğiniz (ve hizmet, bir Windows etki alanı üzerinde çalışır varsa), gerçek kimlik değeri belirtmeyin.  
  
## <a name="identity"></a>Kimlik  
 Wcf'de, terim *kimlik* sunucu ve istemci için farklı bir anlama sahiptir. Kısaca, hizmet çalışırken, bir kimlik için güvenlik bağlamı kimlik doğrulamasından sonra atanır. Gerçek kimlik görüntülemek için <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> özelliklerini <xref:System.ServiceModel.ServiceSecurityContext> sınıfı. Daha fazla bilgi için [nasıl yapılır: Güvenlik bağlamını İnceleme](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Buna karşılık, istemcide kimlik hizmeti doğrulamak için kullanılır. Tasarım zamanında, bir istemci geliştiricisinin ayarlayabilirsiniz [ \<kimlik >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğesine hizmetten alınan bir değer. Çalışma zamanında istemci gerçek hizmetin kimliğini karşı öğenin değerini denetler. İstemci denetimi başarısız olursa iletişimi sona erer. Hizmet bir makine hesabı altında çalışıyorsa, hizmeti belirli bir kullanıcının kimliğine veya hizmet asıl adı (SPN) altında çalışıyorsa, değer kullanıcı asıl adı (UPN) olabilir. Daha fazla bilgi için [kimlik doğrulama ile hizmet kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Kimlik bilgileri, ayrıca bir sertifika veya sertifika tanımlayan bir sertifika bulundu. bir alan olabilir.  
  
## <a name="protection-levels"></a>Koruma düzeyleri  
 `ProtectionLevel` Özellik üzerinde birkaç öznitelik sınıfları gerçekleşir (aşağıdaki gibi <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları). Koruma düzeyi iletileri (ileti bölümlerini) bir hizmet oturumunuz destekleyen imzalanmış ve şifrelenmiş veya imza veya şifreleme gönderilen olup olmadığını belirten bir değerdir. Özelliği hakkında daha fazla bilgi için bkz. [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md)ve programlama örnekleri için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Bir servis sözleşmesi ile tasarlama hakkında daha fazla bilgi için `ProtectionLevel` bağlam içinde görebilir [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Koruma Düzeylerini Anlama](../../../docs/framework/wcf/understanding-protection-level.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Hizmet Sözleşmeleri Tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)
- [Güvenlik](../../../docs/framework/wcf/feature-details/security.md)
- [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Nasıl yapılır: ProtectionLevel özelliğini ayarlama](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Nasıl yapılır: Windows kimlik bilgileri ile bir hizmeti güvenli hale getirme](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Nasıl yapılır: Güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [Nasıl yapılır: İstemci kimlik bilgileri türünü belirtme](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
- [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Nasıl yapılır: Bir hizmette istemci kimliğine bürünme](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Nasıl yapılır: Güvenlik bağlamını İnceleme](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
