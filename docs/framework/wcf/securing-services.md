---
title: Hizmetleri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: fa486c31a7c7310f28cbeaac208dddb05d7cf1e7
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320234"
---
# <a name="securing-services"></a>Hizmetleri Güvenli Hale Getirme
Windows Communication Foundation (WCF) hizmetinin güvenliği iki birincil gereksinimden oluşur: aktarım güvenliği ve yetkilendirme. (Üçüncü bir gereksinim, güvenlik olaylarının denetlenmesi, [denetimde](./feature-details/auditing-security-events.md)açıklanmaktadır.) Kısaca aktarım güvenliği, kimlik doğrulaması (hizmetin ve istemcinin kimliğini doğrulamak), gizliliği (ileti şifreleme) ve bütünlüğü (izinsiz değişiklik algılamak için dijital imzalama) içerir. Yetkilendirme, kaynaklara erişim denetimi, örneğin yalnızca ayrıcalıklı kullanıcıların bir dosyayı okumasına izin verir. WCF özelliklerini kullanarak, iki birincil gereksinim kolayca uygulanır.  
  
 @No__t-0 sınıfı (veya yapılandırmada [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesi) dışında, tüm önceden tanımlanmış bağlamalar için aktarım güvenliği varsayılan olarak etkindir. Bu bölümdeki konular iki temel senaryoyu kapsar: Internet Information Services (IIS) üzerinde barındırılan bir intranet hizmetinde güvenlik ve yetkilendirme aktarma ve IIS üzerinde barındırılan bir hizmette aktarım güvenliği ve yetkilendirme uygulama.  
  
> [!NOTE]
> Windows XP Home, Windows kimlik doğrulamasını desteklemez. Bu nedenle, bu sistemde bir hizmet çalıştırmamalıdır.  
  
## <a name="security-basics"></a>Güvenlik temelleri  
 Güvenlik, *kimlik bilgilerini*kullanır. Bir kimlik bilgisi, bir varlığın nerede olduğunu kanıtlar. (Bir *varlık* bir kişi, bir yazılım işlemi, bir şirket veya yetkilendirilmiş olabilecek herhangi bir şey olabilir.) Örneğin, bir hizmetin bir istemcisi bir *kimlik* *talebi* yapar ve kimlik bilgisi talep bir şekilde talep eder. Tipik bir senaryoda kimlik bilgileri alışverişi oluşur. İlk olarak, bir hizmet kimliğinin bir talebini yapar ve bunu istemciye kimlik bilgileri ile kanıtlar. Buna karşılık, istemci bir kimlik talebi yapar ve hizmete bir kimlik bilgisi sunar. Her iki taraf da diğer kimlik bilgilerine güvense, tüm iletilerin gizli olarak alınıp alındığı ve tüm iletilerin bütünlüğünü korumak için imzalandığı bir *güvenli bağlam* oluşturulabilir. Hizmet istemcinin kimliğini belirledikten sonra, kimlik bilgisinin taleplerini bir gruptaki bir *rol* ya da *üyelikle* eşleştirebilir. Her iki durumda da istemcinin ait olduğu rolü veya grubu kullanarak, hizmet, rolü rol veya grup ayrıcalıklarına göre sınırlı bir işlem kümesi gerçekleştirmesini *yetkilendirir* .  
  
## <a name="windows-security-mechanisms"></a>Windows güvenlik mekanizmaları  
 İstemci ve hizmet bilgisayarının her ikisi de ağda oturum açmasını gerektiren bir Windows etki alanında ise, kimlik bilgileri Windows altyapısı tarafından sağlanır. Bu durumda, kimlik bilgileri bir bilgisayar kullanıcısı ağda oturum açtığında oluşturulur. Her Kullanıcı ve ağdaki her bilgisayar, Güvenilen Kullanıcı ve bilgisayar kümesine ait olarak doğrulanıp doğrulanması gerekir. Bir Windows sisteminde, her bir Kullanıcı ve bilgisayar *güvenlik sorumlusu*olarak da bilinir.  
  
 *Kerberos denetleyicisi* tarafından desteklenen bir Windows etki alanında, Kerberos denetleyicisi her güvenlik sorumlusu için bilet vermeyi temel alan bir düzen kullanır. Denetleyicinin verdiği biletler, sistemdeki diğer bilet vericileri tarafından güvenilirdir. Bir varlık bir işlem gerçekleştirmeye veya bir *kaynağa* (örneğin, bir makinedeki dosya veya dizin) erişmeyi denediğinde, bilet geçerliliği için incelenir ve geçerse, bir işlem için sorumlu tarafından başka bir bilet verilir. Bilet verme yöntemi, her işlem için sorumluyu doğrulamaya çalışılması gerekenden daha etkilidir.  
  
 Windows etki alanlarında kullanılan daha eski, daha az güvenli bir mekanizma NT LAN Manager (NTLM) ' dir. Kerberos 'un kullanılabileceği durumlarda (genellikle bir çalışma grubu gibi bir Windows etki alanının dışında), NTLM alternatif olarak kullanılabilir. NTLM Ayrıca IIS için bir güvenlik seçeneği olarak da kullanılabilir.  
  
 Bir Windows sisteminde, yetkilendirme, her bilgisayar ve kullanıcıyı bir rol ve grup kümesine atayarak işe yarar. Örneğin, her Windows bilgisayarının *yönetici*rolünde bir kişi (veya kişi grubu) tarafından ayarlanması ve denetlenmesi gerekir. Diğer bir rol, *kullanıcının*çok daha kısıtlanmış bir izin kümesine sahip olan izinleridir. Rolüne ek olarak, kullanıcılar gruplara atanır. Bir grup, birden fazla kullanıcının aynı rolde gerçekleştirmesine izin verir. Uygulamada, bu nedenle, kullanıcılar gruplara atanarak bir Windows makinesi yönetilir. Örneğin, birkaç Kullanıcı bir bilgisayarın kullanıcı grubuna atanabilir ve Yöneticiler grubuna çok daha kısıtlanmış bir kullanıcı kümesi atanabilir. Bir yerel makinede yönetici de yeni gruplar oluşturabilir ve başka kullanıcılar (hatta diğer grupları) gruba atayabilir.  
  
 Windows çalıştıran bir bilgisayarda, bir dizindeki her klasör korunabilir. Diğer bir deyişle, bir klasörü seçebilir ve dosyalara kimlerin erişebileceğini ve dosyayı kopyalayıp kopyalayamayacağını ya da (en ayrıcalıklı durumda) bir dosyayı değiştirebilir, bir dosyayı silebilir veya klasöre dosya ekleyebilirler. Bu, erişim denetimi olarak bilinir ve bunun mekanizması erişim denetim listesi (ACL) olarak bilinir. ACL oluştururken, her grup veya gruba ve bir etki alanının bireysel üyelerine erişim ayrıcalıkları atayabilirsiniz.  
  
 WCF altyapısı, bu Windows Güvenlik mekanizmalarını kullanmak için tasarlanmıştır. Bu nedenle, bir intranette dağıtılan ve istemcileri Windows etki alanının üyeleriyle sınırlı olan bir hizmet oluşturuyorsanız, güvenlik kolayca uygulanabilir. Yalnızca geçerli kullanıcılar etki alanında oturum açabilir. Kullanıcılar oturum açtıktan sonra, Kerberos denetleyicisi her kullanıcının başka bir bilgisayar veya uygulamayla güvenli bağlamlar kurmasını sağlar. Yerel bir makinede gruplar kolayca oluşturulabilir ve belirli klasörler korunurken, bu gruplar bilgisayardaki erişim ayrıcalıklarını atamak için kullanılabilir.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Intranet hizmetlerinde Windows güvenliği uygulama  
 Yalnızca bir Windows etki alanında çalışan bir uygulamanın güvenliğini sağlamak için, <xref:System.ServiceModel.WSHttpBinding> veya <xref:System.ServiceModel.NetTcpBinding> bağlamasının varsayılan güvenlik ayarlarını kullanabilirsiniz. Varsayılan olarak, aynı Windows etki alanındaki herkes WCF hizmetlerine erişebilir. Bu kullanıcılar ağda oturum açtığından güvenilir. Bir hizmet ve istemci arasındaki iletiler gizlilik için şifrelenir ve bütünlüğü için imzalanır. Windows güvenliği kullanan bir hizmetin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows kimlik bilgileriyle bir hizmetin güvenliğini sağlama](how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>PrincipalPermissionAttribute sınıfı kullanılarak yetkilendirme  
 Bir bilgisayardaki kaynakların erişimini kısıtlamanız gerekirse, en kolay yol <xref:System.Security.Permissions.PrincipalPermissionAttribute> sınıfını kullanmaktır. Bu öznitelik, kullanıcının belirtilen bir Windows grubu veya rolünde olmasını veya belirli bir Kullanıcı olmasını sağlayarak hizmet işlemlerinin çağrılmasını kısıtlamanıza olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: erişimi PrincipalPermissionAttribute sınıfıyla kısıtlama](how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Kimliğe bürünme  
 Kimliğe bürünme, kaynaklara erişimi denetlemek için kullanabileceğiniz başka bir mekanizmadır. Varsayılan olarak, IIS tarafından barındırılan bir hizmet, ASPNET hesabının kimliği altında çalışacaktır. ASPNET hesabı yalnızca iznine sahip olduğu kaynaklara erişebilir. Ancak, bir klasörü için ACL 'yi, ASPNET hizmet hesabını hariç tutacak şekilde ayarlamak mümkündür, ancak belirli diğer kimliklerin klasöre erişmesine izin verir. Bu durumda, ASPNET hesabının yapmasına izin verilmiyorsa bu kullanıcıların klasöre erişmesine izin verme işlemi yapılır. Yanıt, hizmetin belirli bir kaynağa erişmek için istemcinin kimlik bilgilerini kullanmasına izin verilen kimliğe bürünme özelliğini kullanmaktır. Diğer bir örnek, yalnızca belirli kullanıcıların izne sahip olduğu bir SQL Server veritabanına erişirken olur. Kimliğe bürünme kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet üzerinde bir Istemcinin kimliğine bürünme](how-to-impersonate-a-client-on-a-service.md) ve [temsili ve kimliğe bürünme](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Internet üzerinde güvenlik  
 Internet üzerindeki güvenlik, bir intranette güvenlikle aynı gereksinimlerden oluşur. Bir hizmetin, kimlik bilgilerini sağlaması gerekir ve bu hizmetin kimliğini kanıtlamaları için sağlaması gerekir. İstemcinin kimliği kanıtlanmış olduktan sonra hizmet, istemcinin kaynaklara ne kadar erişimin olduğunu denetleyebilir. Ancak, Internet 'in heterojen doğası nedeniyle, sunulan kimlik bilgileri bir Windows etki alanında kullanılanlardan farklı. Bir Kerberos denetleyicisi kimlik bilgileri için bilet içeren bir etki alanındaki kullanıcıların kimlik doğrulamasını işlediğinde, Internet üzerinde, hizmetler ve istemciler kimlik bilgilerini sunmak için çeşitli farklı yollarla yararlanır. Bununla birlikte, bu konunun amacı, Internet üzerinden erişilebilen bir WCF hizmeti oluşturmanızı sağlayan ortak bir yaklaşım sunmalıdır.  
  
### <a name="using-iis-and-aspnet"></a>IIS ve ASP.NET kullanma  
 Internet güvenliğinin gereksinimleri ve bu sorunları çözecek mekanizmalar yeni değildir. IIS, Microsoft 'un Internet için Web sunucusudur ve bu sorunları gideren birçok güvenlik özelliğine sahiptir; Ayrıca, ASP.NET, WCF hizmetlerinin kullanabileceği güvenlik özelliklerini içerir. Bu güvenlik özelliklerinden yararlanmak için IIS 'de bir WCF hizmeti barındırın.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>ASP.NET üyeliğini ve rol sağlayıcılarını kullanma  
 ASP.NET bir üyelik ve rol sağlayıcısı içerir. Sağlayıcı, arayanların kimlik doğrulaması için Kullanıcı adı/parola çiftlerinin bir veritabanıdır ve bu da her çağıranın erişim ayrıcalıklarını belirtmenize olanak tanır. WCF ile, önceden var olan bir üyeliği ve rol sağlayıcısını yapılandırma aracılığıyla kolayca kullanabilirsiniz. Bunu gösteren örnek bir uygulama için, [Üyelik ve rol sağlayıcısı](./samples/membership-and-role-provider.md) örneğine bakın.  
  
### <a name="credentials-used-by-iis"></a>IIS tarafından kullanılan kimlik bilgileri  
 Kerberos denetleyicisi tarafından desteklenen bir Windows etki alanının aksine Internet, her zaman milyonlarca kullanıcının oturum açmasını yönetmek için tek bir denetleyici olmayan bir ortamdır. Bunun yerine, en çok Internet 'teki kimlik bilgileri X. 509.440 sertifikalardır (Güvenli Yuva Katmanı veya SSL, sertifikalar olarak da bilinir). Bu sertifikalar genellikle sertifika *yetkilisi*tarafından verilir ve bu, sertifikanın orijinalliğini ve verildiği kişiyi gösteren bir üçüncü taraf şirketi olabilir. Hizmetinizi Internet 'te kullanıma sunmak için, hizmetinizin kimliğini doğrulamak üzere bu tür bir güvenilen sertifika da sağlamanız gerekir.  
  
 Bu noktada soru, bu tür bir sertifikayı nasıl edinebilirim? Bir yaklaşım Authenticode veya VeriSign gibi bir üçüncü taraf sertifika yetkilisine gitmeye, hizmetinizi dağıtmaya ve hizmetiniz için bir sertifika satın almanıza olanak sağlar. Ancak, WCF ile geliştirme aşamasındaysanız ve henüz bir sertifika satın almaya hazırsanız, bir üretim dağıtımının benzetimini yapmak için kullanabileceğiniz X. 509.952 sertifikaları oluşturmak için araçlar ve teknikler mevcuttur. Daha fazla bilgi için bkz. [sertifikalarla çalışma](./feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Güvenlik modları  
 WCF güvenliği programlama birkaç kritik karar noktası gerektirir. En temel bir *güvenlik modu*tercih edilir. İki ana güvenlik modu *Aktarım modu* ve *ileti modudur*.  
  
 Her iki ana modun semantiğini birleştiren üçüncü bir mod, *ileti kimlik bilgileri moduyla aktarımdır*.  
  
 Güvenlik modu, iletilerin nasıl güvenli olduğunu ve her bir seçeneğin aşağıda açıklandığı gibi olumlu ve olumsuz yönleri olduğunu belirler. Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Aktarım modu  
 Ağ ve uygulama arasında birkaç katman vardır. Bunlardan*biri, uç* noktalar arasında ileti aktarımını yöneten *Aktarım* katmanıdır. Mevcut amaç için, yalnızca WCF 'nin her biri ileti aktarımını güvenli hale getirmek için çeşitli aktarım protokollerini kullandığını anladığınızı bilmeniz gerekir. (Aktarımlar hakkında daha fazla bilgi için bkz. [taşımalar](./feature-details/transports.md).)  
  
 Yaygın olarak kullanılan bir protokol HTTP 'dir. diğeri ise TCP 'dir. Bu protokollerin her biri, protokole özgü bir mekanizma (veya mekanizmalar) tarafından ileti aktarımını güvenli hale getirebilirsiniz. Örneğin, HTTP protokolünün HTTP üzerinden SSL kullanılarak güvenliği sağlanır, genellikle "HTTPS" olarak kısaltılır. Bu nedenle, güvenlik için aktarım modunu seçtiğinizde, mekanizmayı protokol tarafından dikte edildiği şekilde kullanmayı tercih edersiniz. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfını seçer ve güvenlik modunu taşıma olarak ayarlarsanız, güvenlik mekanizması olarak HTTP (HTTPS) üzerinden SSL 'yi seçersiniz. Aktarım modunun avantajı, güvenlik, karşılaştırmalı bir şekilde düşük düzeyde tümleştirileceği için ileti modundan daha verimlidir. Aktarım modunu kullanırken, güvenlik mekanizması taşımanın belirtimine göre uygulanmalıdır ve bu nedenle iletiler yalnızca aktarım üzerinden noktadan noktaya güvenli bir şekilde akabilir.  
  
#### <a name="message-mode"></a>İleti modu  
 Buna karşılık, ileti modu her iletinin parçası olarak güvenlik verilerini dahil ederek güvenlik sağlar. XML ve SOAP güvenlik üst bilgilerini kullanarak, iletinin bütünlüğünü ve gizliliğini sağlamak için gereken kimlik bilgileri ve diğer veriler her iletiye dahil edilir. Her ileti güvenlik verilerini içerir, bu nedenle her iletinin tek tek işlenmesi gerektiğinden performansla ilgili olarak sonuçlanır. (Aktarım modunda, aktarım katmanı güvenli hale getirildikten sonra tüm iletiler serbestçe akar.) Ancak, ileti güvenliğinin aktarım güvenliği üzerinde bir avantajı vardır: daha esnektir. Diğer bir deyişle, güvenlik gereksinimleri taşıma tarafından belirlenmemiştir. İletinin güvenliğini sağlamak için herhangi bir tür istemci kimlik bilgisini kullanabilirsiniz. (Aktarım modunda, Aktarım Protokolü, kullanabileceğiniz istemci kimlik bilgisinin türünü belirler.)  
  
#### <a name="transport-with-message-credentials"></a>Ileti kimlik bilgileriyle taşıma  
 Üçüncü mod hem aktarım hem de ileti güvenliğinin en iyi şekilde birleşir. Bu modda, aktarım güvenliği her iletinin gizliliğini ve bütünlüğünü verimli bir şekilde sağlamak için kullanılır. Aynı zamanda, her ileti kimlik doğrulamasının doğrulanmasını sağlayan kimlik bilgisi verilerini içerir. Kimlik doğrulama ile, yetkilendirme da uygulanabilir. Bir göndereni kimlik doğrulaması yaparak, kaynak erişimi gönderenin kimliğine göre verilebilir (veya reddedilebilir).  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Istemci kimlik bilgisi türünü ve kimlik bilgisi değerini belirtme  
 Bir güvenlik modu seçtikten sonra, bir istemci kimlik bilgisi türü de belirtmek isteyebilirsiniz. İstemci kimlik bilgileri türü, istemcinin sunucuda kimliğini doğrulamak için kullanması gereken türü belirtir.  
  
 Ancak, tüm senaryolar istemci kimlik bilgisi türü gerektirmez. HTTP (HTTPS) üzerinden SSL kullanarak, bir hizmet istemcinin kimliğini doğrular. Bu kimlik doğrulamanın bir parçası olarak hizmetin sertifikası, *anlaşma*adlı bir işlemde istemciye gönderilir. SSL ile güvenli aktarım, tüm iletilerin gizli olmasını sağlar.  
  
 İstemcinin kimliğinin doğrulanmasını gerektiren bir hizmet oluşturuyorsanız, bir istemci kimlik bilgisi türü tercih ettiğiniz aktarım ve mod seçili olmasına bağlıdır. Örneğin, HTTP taşıma ve taşıma modunu seçme, temel, Özet ve diğerleri gibi çeşitli seçenekler sunar. (Bu kimlik bilgisi türleri hakkında daha fazla bilgi için bkz. [http kimlik doğrulamasını anlama](./feature-details/understanding-http-authentication.md).)  
  
 Windows etki alanı üzerinde yalnızca ağın diğer kullanıcıları tarafından kullanılabilecek bir hizmet oluşturuyorsanız, en kolay kullanımı Windows istemci kimlik bilgisi türüdür. Ancak, sertifikaya sahip bir hizmet sağlamanız da gerekebilir. Bu, [nasıl yapılır: Istemci kimlik bilgileri değerlerini belirtme](how-to-specify-client-credential-values.md)bölümünde gösterilmiştir.  
  
#### <a name="credential-values"></a>Kimlik bilgisi değerleri  
 *Kimlik bilgisi değeri* , hizmetin kullandığı gerçek kimlik bilgileridir. Bir kimlik bilgisi türü belirledikten sonra, hizmetinizi gerçek kimlik bilgileriyle yapılandırmanız da gerekebilir. Windows 'u seçtiyseniz (ve hizmet bir Windows etki alanında çalışır), gerçek bir kimlik bilgisi değeri belirtmeyin.  
  
## <a name="identity"></a>Kimlik  
 WCF 'de, *kimliğin kimliği* sunucu ve istemciye farklı anlamlara sahiptir. Kısaca, bir hizmeti çalıştırırken kimlik doğrulamasından sonra güvenlik bağlamına bir kimlik atanır. Gerçek kimliği görüntülemek için <xref:System.ServiceModel.ServiceSecurityContext> sınıfının <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> ve <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> özelliklerini kontrol edin. Daha fazla bilgi için bkz. [nasıl yapılır: güvenlik bağlamını İnceleme](how-to-examine-the-security-context.md).  
  
 Buna karşılık, istemci üzerindeki kimlik, hizmeti doğrulamak için kullanılır. Tasarım zamanında, bir istemci geliştiricisi [\<ıdentity >](../configure-apps/file-schema/wcf/identity.md) öğesini hizmetten elde edilen bir değere ayarlayabilir. Çalışma zamanında istemci, öğenin değerini hizmetin gerçek kimliğiyle karşılaştırır. Denetim başarısız olursa, istemci iletişimi sonlandırır. Hizmet bir makine hesabı altında çalışıyorsa, hizmet belirli bir kullanıcının kimliği veya hizmet asıl adı (SPN) altında çalışıyorsa, bu değer bir Kullanıcı asıl adı (UPN) olabilir. Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](./feature-details/service-identity-and-authentication.md). Kimlik bilgisi bir sertifika veya sertifikayı tanımlayan bir sertifikada bulunan bir alan olabilir.  
  
## <a name="protection-levels"></a>Koruma düzeyleri  
 @No__t-0 özelliği çeşitli öznitelik sınıflarında (<xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> sınıfları gibi) oluşur. Koruma düzeyi, bir hizmeti destekleyen mesajların (veya ileti bölümlerinin) imzalı, imzalanmış ve şifrelenmiş olduğunu veya imza ya da şifreleme olmadan gönderilip gönderilmeyeceğini belirten bir değerdir. Özelliği hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](understanding-protection-level.md)ve programlama örnekleri için bkz. [nasıl yapılır: ProtectionLevel özelliğini ayarlama](how-to-set-the-protectionlevel-property.md). Bağlamında `ProtectionLevel` ile bir hizmet sözleşmesi tasarlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini tasarlama](designing-service-contracts.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Kimlik Doğrulama ile Hizmet Kimliği](./feature-details/service-identity-and-authentication.md)
- [Koruma Düzeylerini Anlama](understanding-protection-level.md)
- [Temsilcilik ve Kimliğe Bürünme](./feature-details/delegation-and-impersonation-with-wcf.md)
- [Hizmet Sözleşmeleri Tasarlama](designing-service-contracts.md)
- [Security](./feature-details/security.md)
- [Güvenliğe Genel Bakış](./feature-details/security-overview.md)
- [Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama](how-to-set-the-protectionlevel-property.md)
- [Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme](how-to-secure-a-service-with-windows-credentials.md)
- [Nasıl yapılır: Güvenlik Modunu Ayarlama](how-to-set-the-security-mode.md)
- [Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme](how-to-specify-the-client-credential-type.md)
- [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Nasıl yapılır: Bir Hizmette İstemci Kimliğine Bürünme](how-to-impersonate-a-client-on-a-service.md)
- [Nasıl Yapılır: Güvenlik Bağlamını İnceleme](how-to-examine-the-security-context.md)
