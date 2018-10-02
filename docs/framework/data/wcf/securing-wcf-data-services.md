---
title: WCF veri hizmetlerinin güvenliğini sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 56ece9c2c81f05047e85ab681e7cfe0da65f35b9
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032445"
---
# <a name="securing-wcf-data-services"></a>WCF veri hizmetlerinin güvenliğini sağlama
Bu konuda, geliştirme, dağıtma ve çalıştırma için belirli güvenlik konuları açıklanmaktadır. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ve desteği olan hizmetlere erişen uygulamalar [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Güvenli oluşturmaya yönelik önerileri de izlemelidir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar.  
  
 Güvenli hale getirmeyi planlarken bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]-tabanlı [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmet, hem kimlik doğrulama, bulma ve bir sorumlunun kimliğini doğrulama işlemi hem de yetkilendirme, bir kimliği doğrulanmış olup olmadığını belirleme işlemi almalıdır Asıl istenen kaynaklara erişmesine izin verilir. İletiyi SSL kullanarak şifrelenip şifrelenmeyeceğinizi de göz önünde bulundurmalısınız.  
  
## <a name="authenticating-client-requests"></a>İstemci İsteklerinde Kimlik Doğrulama  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] herhangi bir türden kendi kimlik doğrulaması uygulamaz, ancak bunun yerine sağladığı kimlik doğrulamadan veri hizmeti ana bilgisayarı üzerinde kullanır. Bunun anlamı, hizmet aldığı herhangi bir istek ağ ana bilgisayar tarafından önceden doğrulanmış olduğunu varsayar ve ana bilgisayarın ilkesine uygun şekilde tarafından sağlanan arabirimleri aracılığıyla istek için tanımlanan [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Bu kimlik doğrulama seçenekleri ve yaklaşımları ayrıntıları [OData ve kimlik doğrulama serisinde](https://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Veri Hizmeti için Kimlik Doğrulama Seçenekleri  
 Aşağıdaki tabloda, WCF Veri Hizmeti için isteklerin kimliğini doğrulamanıza yardımcı olacak kimlik doğrulama mekanizmalarından bazıları listelenmektedir.  
  
|Kimlik doğrulama seçenekleri|Açıklama|  
|----------------------------|-----------------|  
|Anonim kimlik doğrulama|HTTP anonim kimlik doğrulama etkinleştirildiğinde, herhangi bir ilke veri hizmetine bağlanabilir. Anonim erişim için kimlik bilgileri gerekmez. Bu seçeneği, yalnızca herkesin veri hizmetine erişmesini istediğinizde kullanın.|  
|Temel ve özet kimlik doğrulama|Kimlik doğrulama için bir kullanıcı adı ve paroladan oluşan kimlik bilgileri gereklidir. Windows olmayan istemcilerin kimlik doğrulamasını destekler. **Güvenlik Notu:** temel doğrulama kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir. Özet kimlik doğrulama, sağlanan kimlik bilgilerini temel alan bir karma değer gönderir; bu nedenle temel kimlik doğrulamaya göre daha güvenlidir. Her ikisi de ortadaki adam saldırılarına maruz kalabilir. Bu kimlik doğrulama yöntemlerini kullanırken, Güvenli Yuva Katmanı (SSL) kullanarak istemci ile veri hizmeti arasındaki iletişimi şifrelemeyi göz önünde bulundurmanız gerekir. <br /><br /> Microsoft Internet Information Services (IIS), her iki temel uygulanmasını sağlar ve Özet kimlik doğrulaması için HTTP istekleri bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Bu Windows Kimlik Doğrulama Sağlayıcısı uygulaması, Windows kullanıcısının kimlik doğrulaması üzerinde sorunsuz bir şekilde anlaşmaya varmak için veri hizmetine isteğin HTTP üstbilgisindeki kimlik bilgilerini sağlayan bir .NET Framework istemci uygulaması sağlar. Daha fazla bilgi için [Özet kimlik doğrulaması Teknik Başvurusu](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Bazı özel kimlik doğrulama hizmeti ve değil Windows kimlik bilgilerini temel alan, veri hizmeti temel kimlik doğrulama kullanmasını istediğinizde, özel bir uygulamalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP modülü kimlik doğrulama için.<br /><br /> Bir özel temel kimlik doğrulama düzeni kullanma örneği için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gönderiye bakın [özel temel kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkID=200388) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisindeki.|  
|Windows kimlik doğrulaması|Windows tabanlı kimlik bilgileri, NTLM veya Kerberos kullanılarak değiştirilir. Bu mekanizma, basit veya özet kimlik doğrulamaya göre daha güvenlidir, ancak istemcinin Windows tabanlı bir uygulama olmasını gerektirir. IIS HTTP istekleri için Windows kimlik doğrulamasının uygulanmasını da sağlar bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Daha fazla bilgi için [ASP.NET formları kimlik doğrulamasına genel bakış](https://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Windows kimlik doğrulaması ile kullanılacak bir örnek [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gönderiye bakın [Windows kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkID=200384) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisindeki.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Form kimlik doğrulaması|Forms kimlik doğrulaması, kullanıcıların kimliğini kendi kodunuzu kullanarak ve ardından bir tanımla bilgisinde veya sayfa URL'sinde bir kimlik doğrulama belirteci tutarak doğrulamanızı sağlar. Oluşturduğunuz bir oturum açma formunu kullanarak kullanıcılarınızın kullanıcı adını ve parolasını doğrularsanız. Kimliği doğrulanmamış istekler, kullanıcının kimlik bilgileri sağladığı ve formu gönderdiği bir oturum açma sayfasına yönlendirilir. Uygulama isteğin kimliğini doğrularsa, sistem sonraki istekler için kimliği yeniden oluşturabilecek bir anahtar içeren bir anahtar verir. Daha fazla bilgi için [form kimlik doğrulama sağlayıcısı](https://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Güvenlik Notu:** form kimlik doğrulaması kullandığınızda varsayılan olarak, forms kimlik doğrulaması bileti içeren tanımlama bilgisinin güvenli değil bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması. Hem kimlik doğrulama anahtarını hem de ilk oturum açma kimlik bilgilerini korumak için SSL kullanılmasını gerekli tutmayı dikkate almanız gerekir. <br /><br /> Kimlik doğrulaması ile nasıl kullanılacağı hakkında bir örnek form için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gönderiye bakın [form kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkID=200389) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisindeki.|  
|Beyana dayalı kimlik doğrulama|Talep tabanlı kimlik doğrulaması, veri hizmeti kullanıcının kimliğini doğrulamak için bir güvenilen "üçüncü taraf" kimlik sağlayıcı hizmetinden yararlanır. Kimlik sağlayıcısı, veri hizmeti kaynaklarına erişmek isteyen kullanıcının kimliğini olumlu bir şekilde doğrular ve istenen kaynaklara erişim izni sağlayan bir belirteç verir. Bu belirteç, daha sonra veri hizmetine sunulur. Veri hizmeti, erişim belirtecini veren kimlik hizmetiyle kurulan güven ilişkisine göre kullanıcıya erişim sağlar.<br /><br /> Beyana dayalı kimlik doğrulama sağlayıcısı kullanmanın avantajı, güven etki alanları arasında çeşitli türden istemcilerin kimliğini doğrulamak için kullanılabilmeleridir. Veri hizmeti, böyle bir üçüncü taraf sağlayıcı kullanarak kullanıcıları koruma ve kimliklerini doğrulama gereksinimlerinden kurtulabilir. OAuth 2.0, hizmet olarak şirket dışı kimlik doğrulama için Microsoft Azure AppFabric Erişim Denetimi tarafından desteklenen beyana dayalı bir kimlik doğrulama protokolüdür. Bu protokol REST tabanlı hizmetleri destekler. OAuth 2.0 ile kullanma örneği için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gönderiye bakın [OData ve OAuth](https://go.microsoft.com/fwlink/?LinkId=200514) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisindeki.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>İstemci Kitaplığında kimlik doğrulama  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı bir istek yaparken kimlik bilgileri sağlamazsa bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti. Bir kullanıcının kimliğini doğrulamak için veri hizmeti tarafından oturum açma kimlik bilgileri gereklidir, bu kimlik bilgileri sağlanabilir bir <xref:System.Net.NetworkCredential> erişilen <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>, aşağıdaki örnekte olduğu gibi:  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Daha fazla bilgi için [nasıl yapılır: istemci kimlik bilgileri belirtmek için bir veri hizmeti isteği](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Veri hizmeti oturum açma kimlik bilgilerini gerektirdiğinde belirtilemez kullanarak bir <xref:System.Net.NetworkCredential> nesne, beyana dayalı belirteç veya kimlik bilgisi gibi el ile üst bilgileri HTTP isteğinde genellikle ayarlamalısınız `Authorization` ve `Cookie` üstbilgileri. Bu tür bir kimlik doğrulama senaryosu hakkında daha fazla bilgi için gönderiye bakın [OData ve kimlik doğrulama: istemci tarafı kancaları](https://go.microsoft.com/fwlink/?LinkID=200385). İstek iletisinde HTTP üstbilgilerini ayarlama örneği için bkz: [nasıl yapılır: istemci isteğinde üst bilgilerini ayarla](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Kimliğe bürünme  
 Genellikle veri hizmeti, veri hizmetini barındıran çalışan işleminin kimlik bilgilerini kullanarak sunucudaki veya veritabanındaki dosyalar gibi gerekli kaynaklara erişir. Kimliğe bürünme kullanılırken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları isteği yapan kullanıcının Windows kimliğiyle (kullanıcı hesabı) yürütebilir. Kimliğe bürünme, genel olarak kullanıcının kimliğini doğrulamak için IIS'den yararlanan uygulamalarda kullanılır ve gerekli kaynaklara erişmek için bu ilkenin kimlik bilgileri kullanılır. Daha fazla bilgi için [ASP.NET kimliğe bürünme](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Veri Hizmeti Yetkilendirmesini Yapılandırma  
 Yetkilendirme, uygulama kaynaklarının daha önce başarılı olan bir kimlik doğrulama temel alınarak belirlenen bir ilkeye veya işleme erişimini sağlamaktır. Genel bir uygulama olarak, yeterli hakları yalnızca istemci uygulamaları tarafından gerekli kılınan işlemleri gerçekleştirmek için veri hizmetinin kullanıcılarına vermeniz gerekir.  
  
### <a name="restrict-access-to-data-service-resources"></a>Veri Hizmeti Kaynaklarına Erişimi Kısıtlama  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ortak okuma ve yazma erişimi veri hizmeti kaynaklarına karşı vermenizi sağlar (varlık kümesi ve hizmet işlemleri) için veri hizmetine erişebilen herhangi bir kullanıcı. Okuma ve yazma erişimini tanımlayan kurallar, veri hizmeti tarafından kullanılan ve hizmet işlemlerine sunulan her varlık kümesi için ayrı ayrı tanımlanabilir. Hem okuma hem de yazma erişimini yalnızca istemci uygulaması tarafından gerekli kılınan kaynaklarla sınırlamanızı öneririz. Daha fazla bilgi için [en az kaynak erişim gereksinimlerini](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Rol Tabanlı Kesiciler Uygulama  
 Kesiciler, istekleri veri hizmeti tarafından kullanılmadan önce veri hizmeti kaynaklarına karşı kesmenizi sağlar. Daha fazla bilgi için [dinleyicileri](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Kesiciler, isteği yapan kimliği doğrulanmış kullanıcıya göre yetkilendirme kararları vermenizi sağlar. Bir kimliği doğrulanmış kullanıcı kimliğine göre veri hizmeti kaynaklarına erişimi kısıtlamak nasıl bir örnek için bkz [nasıl yapılır: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Kalıcı Veri Deposu ve Yerel Kaynaklara Erişimi Kısıtlama  
 Kalıcı depoya erişmek için kullanılan hesaplara, yalnızca veritabanı veya dosya sisteminde veri hizmetinin gereksinimlerini desteklemek için yeterli haklar verilmelidir. Bu, anonim kimlik doğrulama kullanıldığında barındırma uygulamasını çalıştırmak için kullanılan hesaptır. Daha fazla bilgi için [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Kimliğe bürünme kullanıldığında, kimliği doğrulanmış kullanıcıların genellikle Windows grubunun parçası olarak bu kaynaklara erişmesi sağlanmalıdır.  
  
## <a name="other-security-considerations"></a>Güvenlik Hakkında Diğer Önemli Noktalar  
  
### <a name="secure-the-data-in-the-payload"></a>Yükte Verileri Güvenli Hale Getirme  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] HTTP protokolünü temel alır. HTTP iletisinde, üstbilgi veri hizmeti tarafından uygulanan kimlik doğrulamaya bağlı olarak değerli kullanıcı kimlik bilgileri içerebilir. İleti gövdesi, korunması gereken değerli müşteri verileri de içerebilir. Her iki durumda da, bu bilgileri çevrimiçi olarak korumak için SSL'yi kullanmanızı öneririz.  
  
### <a name="ignored-message-headers-and-cookies"></a>Yoksayılan İleti Üstbilgileri ve Tanımlama Bilgileri  
 İçerik türleri ve kaynak konumları bildirenlerin dışındaki HTTP isteği üstbilgileri yoksayılır ve veri hizmeti tarafından hiçbir zaman ayarlanmaz.  
  
 Tanımlama bilgileri kullanılabilir bir kimlik doğrulama şemasıyla bir parçası olarak gibi ile [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] form kimlik doğrulaması. Ancak, gelen bir istek üzerinde ayarlanan tüm HTTP tanımlama bilgileri tarafından göz ardı edilir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Bir veri hizmeti ana bilgisayarı tanımlama bilgisini işleyebilir, ancak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çalışma zamanı, hiçbir zaman analiz etmez veya tanımlama bilgilerini döndürür. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı de işlemez Yanıtta gönderilen tanımlama bilgileri.  
  
### <a name="custom-hosting-requirements"></a>Özel Barındırma Gereksinimleri  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] olarak oluşturulan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS'de barındırılan uygulama. Bu, veri hizmetinin bu platformun güvenli davranışlarını kullanmasını sağlar. Tanımlayabileceğiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] özel bir ana bilgisayar tarafından barındırılır. Daha fazla bilgi için [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Veri hizmetini barındıran bileşenler ve platform, veri hizmetine yapılan saldırıları önlemek için aşağıdaki güvenlik davranışlarını sağlamalıdır:  
  
-   Olası tüm işlemler için veri hizmeti isteğinde kabul edilen URI'nin uzunluğunu sınırlama.  
  
-   Hem gelen hem de giden HTTP iletilerinin boyutunu sınırlama.  
  
-   Herhangi bir zamanda bekleyen isteklerin toplam sayısını sınırlama.  
  
-   HTTP üstbilgilerinin ve değerlerinin boyutunu sınırlama ve sağlayan [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] üstbilgi verilerine erişim.  
  
-   TCP SYN ve ileti yeniden yürütme saldırıları gibi bilinen saldırıları algılama ve önleme.  
  
### <a name="values-are-not-further-encoded"></a>Değerler Daha Fazla Kodlanmaz  
 Veri hizmetine gönderilen özellik değerleri daha fazla kodlanmaz tarafından [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çalışma zamanı. Örneğin, bir varlığın dize özelliği biçimlendirilmiş HTML içeriği içerdiğinde, etiketler veri hizmeti tarafından kodlanmış HTML değildir. Veri hizmeti yanıttaki özellik değerlerini de kodlamaz. İstemci Kitaplığı da ek kodlama gerçekleştirmez.  
  
### <a name="considerations-for-client-applications"></a>İstemci Uygulamaları için Önemli Noktalar  
 Aşağıdaki güvenlik hususlarını kullanan uygulamalar için geçerli [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] erişmek için istemci [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Hizmetleri:  
  
-   İstemci kitaplığı, veri hizmetine erişmek için kullanılan protokollerin uygun düzeyde güvenlik sağladığını varsayar.  
  
-   İstemci kitaplığı, platform tarafından sağlanan temel taşıma yığınlarının zaman aşımları ve ayrıştırma seçenekleri için tüm varsayılan değerleri kullanır.  
  
-   İstemci kitaplığı, uygulama yapılandırma dosyalarından ayar okumaz.  
  
-   İstemci kitaplığı, etki alanları arasında erişim mekanizması uygulamaz. Bunun yerine, temel HTTP yığını tarafından sağlanan mekanizmalardan yararlanır.  
  
-   İstemci kitaplığının kullanıcı arabirimi öğesi yoktur ve hiçbir zaman aldığı veya gönderdiği verileri görüntülemeye veya oluşturmaya çalışmaz.  
  
-   İstemci uygulamalarının her zaman kullanıcı girişini ve güvenilmeyen hizmetlerden kabul edilen verileri doğrulamasını öneririz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
