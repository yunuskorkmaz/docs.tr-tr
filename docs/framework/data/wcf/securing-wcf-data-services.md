---
title: WCF Veri Hizmetlerinin Güvenliğini Sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 1e134d877c45af00e2a2fb7e7ef0882ffd7ddc48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875738"
---
# <a name="securing-wcf-data-services"></a>WCF Veri Hizmetlerinin Güvenliğini Sağlama
Bu konuda, geliştirme, dağıtma ve WCF Veri Hizmetleri ve uygulamaları, açık veri Protokolü (OData) destekleyen, erişim Hizmetleri'ni çalıştırmak için belirli güvenlik konuları açıklanmaktadır. Güvenli .NET Framework uygulamaları oluşturmaya yönelik önerileri de izlemelidir.  
  
Bir WCF veri hizmetleri tabanlı OData hizmeti güvenli hale getirmeyi planlarken, kimlik doğrulaması, bulma ve bir sorumlunun kimliğini doğrulama işlemi hem de yetkilendirme kimliği doğrulanmış bir sorumlunun olup olmadığını belirleme işlemi adresi olmalıdır İstenen kaynaklara erişmesine izin verilir. İletiyi SSL kullanarak şifrelenip şifrelenmeyeceğinizi de göz önünde bulundurmalısınız.  
  
## <a name="authenticating-client-requests"></a>İstemci İsteklerinde Kimlik Doğrulama  
WCF Veri Hizmetleri herhangi bir türden kendi kimlik doğrulaması uygulamaz, ancak bunun yerine sağladığı kimlik doğrulamadan veri hizmeti ana bilgisayarı üzerinde kullanır. Bu, hizmet aldığı herhangi bir istek ağ ana bilgisayar tarafından önceden doğrulanmış olduğunu varsayar ve ana bilgisayarın ilkesine uygun şekilde WCF Veri Hizmetleri tarafından sağlanan arabirimleri aracılığıyla istek için tanımlanan anlamına gelir. Bu kimlik doğrulama seçenekleri ve yaklaşımları içinde multipart ayrıntılandırılmıştır [OData ve kimlik doğrulama serisinde](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Veri Hizmeti için Kimlik Doğrulama Seçenekleri  
 Aşağıdaki tabloda, WCF Veri Hizmeti için isteklerin kimliğini doğrulamanıza yardımcı olacak kimlik doğrulama mekanizmalarından bazıları listelenmektedir.  
  
|Kimlik doğrulama seçenekleri|Açıklama|  
|----------------------------|-----------------|  
|Anonim kimlik doğrulama|HTTP anonim kimlik doğrulama etkinleştirildiğinde, herhangi bir ilke veri hizmetine bağlanabilir. Anonim erişim için kimlik bilgileri gerekmez. Bu seçeneği, yalnızca herkesin veri hizmetine erişmesini istediğinizde kullanın.|  
|Temel ve özet kimlik doğrulama|Kimlik doğrulama için bir kullanıcı adı ve paroladan oluşan kimlik bilgileri gereklidir. Windows olmayan istemcilerin kimlik doğrulamasını destekler. **Güvenlik Notu:**  Temel kimlik doğrulama kimlik bilgileri (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir. Özet kimlik doğrulama, sağlanan kimlik bilgilerini temel alan bir karma değer gönderir; bu nedenle temel kimlik doğrulamaya göre daha güvenlidir. Her ikisi de ortadaki adam saldırılarına maruz kalabilir. Bu kimlik doğrulama yöntemlerini kullanırken, Güvenli Yuva Katmanı (SSL) kullanarak istemci ile veri hizmeti arasındaki iletişimi şifrelemeyi göz önünde bulundurmanız gerekir. <br /><br /> Microsoft Internet Information Services (IIS) hem de temel bir uygulamasını sağlar ve bir ASP.NET uygulamasında HTTP için Özet kimlik doğrulaması ister. Bu Windows Kimlik Doğrulama Sağlayıcısı uygulaması, Windows kullanıcısının kimlik doğrulaması üzerinde sorunsuz bir şekilde anlaşmaya varmak için veri hizmetine isteğin HTTP üstbilgisindeki kimlik bilgilerini sağlayan bir .NET Framework istemci uygulaması sağlar. Daha fazla bilgi için [Özet kimlik doğrulaması Teknik Başvurusu](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Bazı özel kimlik doğrulama hizmeti ve değil Windows kimlik bilgilerini temel alan, veri hizmeti temel kimlik doğrulama kullanmasını istediğinizde, kimlik doğrulaması için özel bir ADP.NET HTTP modülü uygulamanız gerekir.<br /><br /> Bir özel temel kimlik doğrulama düzeni ile WCF veri hizmetlerini kullanma örneği için blog gönderisine bakın [OData ve kimlik doğrulaması – Bölüm 6: özel temel kimlik doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Windows kimlik doğrulaması|Windows tabanlı kimlik bilgileri, NTLM veya Kerberos kullanılarak değiştirilir. Bu mekanizma, basit veya özet kimlik doğrulamaya göre daha güvenlidir, ancak istemcinin Windows tabanlı bir uygulama olmasını gerektirir. IIS Windows kimlik doğrulaması için bir ASP.NET uygulamasında HTTP istekleri uygulaması de sağlar. Daha fazla bilgi için [ASP.NET formları kimlik doğrulamasına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Windows kimlik doğrulaması ile WCF veri hizmetlerini kullanma örneği için blog gönderisine bakın [OData ve kimlik doğrulaması – bölüm 2-Windows kimlik doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|ASP.NET formları kimlik doğrulaması|Form kimlik doğrulaması kullanıcılar kendi kodunuzu kullanarak kimlik doğrulaması ve ardından bir tanımla bilgisinde veya sayfa URL'sinde bir kimlik doğrulama belirteci tutmanıza olanak tanır. Oluşturduğunuz bir oturum açma formunu kullanarak kullanıcılarınızın kullanıcı adını ve parolasını doğrularsanız. Kimliği doğrulanmamış istekler, kullanıcının kimlik bilgileri sağladığı ve formu gönderdiği bir oturum açma sayfasına yönlendirilir. Uygulama isteğin kimliğini doğrularsa, sistem sonraki istekler için kimliği yeniden oluşturabilecek bir anahtar içeren bir anahtar verir. Daha fazla bilgi için [form kimlik doğrulama sağlayıcısı](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Güvenlik Notu:**  Form kimlik doğrulaması bir ASP.NET Web uygulamasında kullandığınızda varsayılan olarak, forms kimlik doğrulaması bileti içeren tanımlama bilgisinin güvenli değildir. Hem kimlik doğrulama anahtarını hem de ilk oturum açma kimlik bilgilerini korumak için SSL kullanılmasını gerekli tutmayı dikkate almanız gerekir. <br /><br /> WCF Veri Hizmetleri ile kimlik doğrulaması nasıl kullanılacağına ilişkin bir örnek forms için blog gönderisine bakın [OData ve kimlik doğrulaması – Bölüm 7 – form kimlik doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Beyana dayalı kimlik doğrulama|Talep tabanlı kimlik doğrulaması, veri hizmeti kullanıcının kimliğini doğrulamak için bir güvenilen "üçüncü taraf" kimlik sağlayıcı hizmetinden yararlanır. Kimlik sağlayıcısı, veri hizmeti kaynaklarına erişmek isteyen kullanıcının kimliğini olumlu bir şekilde doğrular ve istenen kaynaklara erişim izni sağlayan bir belirteç verir. Bu belirteç, daha sonra veri hizmetine sunulur. Veri hizmeti, erişim belirtecini veren kimlik hizmetiyle kurulan güven ilişkisine göre kullanıcıya erişim sağlar.<br /><br /> Beyana dayalı kimlik doğrulama sağlayıcısı kullanmanın avantajı, güven etki alanları arasında çeşitli türden istemcilerin kimliğini doğrulamak için kullanılabilmeleridir. Veri hizmeti, böyle bir üçüncü taraf sağlayıcı kullanarak kullanıcıları koruma ve kimliklerini doğrulama gereksinimlerinden kurtulabilir. OAuth 2.0, hizmet olarak şirket dışı kimlik doğrulama için Microsoft Azure AppFabric Erişim Denetimi tarafından desteklenen beyana dayalı bir kimlik doğrulama protokolüdür. Bu protokol REST tabanlı hizmetleri destekler. OAuth 2.0 ile WCF veri hizmetlerini kullanma örneği için blog gönderisine bakın [OData ve OAuth kimlik doğrulaması – bölüm 8 – kaydırma](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>İstemci Kitaplığında kimlik doğrulama  
 Bir OData hizmetine istek yaparken, varsayılan olarak, WCF Veri Hizmetleri istemci kitaplığı kimlik bilgileri sağlamaz. Bir kullanıcının kimliğini doğrulamak için veri hizmeti tarafından oturum açma kimlik bilgileri gereklidir, bu kimlik bilgileri sağlanabilir bir <xref:System.Net.NetworkCredential> erişilen <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>, aşağıdaki örnekte olduğu gibi:  
  
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
  
 Daha fazla bilgi için [nasıl yapılır: İstemci kimlik bilgileri belirtmek için veri hizmeti isteği](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Veri hizmeti oturum açma kimlik bilgilerini gerektirdiğinde belirtilemez kullanarak bir <xref:System.Net.NetworkCredential> nesne, beyana dayalı belirteç veya kimlik bilgisi gibi el ile üst bilgileri HTTP isteğinde genellikle ayarlamalısınız `Authorization` ve `Cookie` üstbilgileri. Bu tür bir kimlik doğrulama senaryosu hakkında daha fazla bilgi için blog gönderisine bakın [ OData ve kimlik doğrulaması – 3. Kısım-istemci tarafı kancaları](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). İstek iletisinde HTTP üstbilgilerini ayarlama örneği için bkz: [nasıl yapılır: İstemci isteğinde üst bilgileri ayarlama](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Kimliğe bürünme  
 Genellikle veri hizmeti, veri hizmetini barındıran çalışan işleminin kimlik bilgilerini kullanarak sunucudaki veya veritabanındaki dosyalar gibi gerekli kaynaklara erişir. Kimliğe bürünme kullanılırken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamaları isteği yapan kullanıcının Windows kimliğiyle (kullanıcı hesabı) yürütebilir. Kimliğe bürünme, genel olarak kullanıcının kimliğini doğrulamak için IIS'den yararlanan uygulamalarda kullanılır ve gerekli kaynaklara erişmek için bu ilkenin kimlik bilgileri kullanılır. Daha fazla bilgi için [ASP.NET kimliğe bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Veri Hizmeti Yetkilendirmesini Yapılandırma  
 Yetkilendirme, uygulama kaynaklarının daha önce başarılı olan bir kimlik doğrulama temel alınarak belirlenen bir ilkeye veya işleme erişimini sağlamaktır. Genel bir uygulama olarak, yeterli hakları yalnızca istemci uygulamaları tarafından gerekli kılınan işlemleri gerçekleştirmek için veri hizmetinin kullanıcılarına vermeniz gerekir.  
  
### <a name="restrict-access-to-data-service-resources"></a>Veri Hizmeti Kaynaklarına Erişimi Kısıtlama  
 Varsayılan olarak, WCF Veri Hizmetleri ortak okuma ve yazma erişimi veri hizmeti kaynaklarına karşı vermenizi sağlar (varlık kümesi ve hizmet işlemleri) için veri hizmetine erişebilen herhangi bir kullanıcı. Okuma ve yazma erişimini tanımlayan kurallar, veri hizmeti tarafından kullanılan ve hizmet işlemlerine sunulan her varlık kümesi için ayrı ayrı tanımlanabilir. Hem okuma hem de yazma erişimini yalnızca istemci uygulaması tarafından gerekli kılınan kaynaklarla sınırlamanızı öneririz. Daha fazla bilgi için [en az kaynak erişim gereksinimlerini](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Rol Tabanlı Kesiciler Uygulama  
 Kesiciler, istekleri veri hizmeti tarafından kullanılmadan önce veri hizmeti kaynaklarına karşı kesmenizi sağlar. Daha fazla bilgi için [dinleyicileri](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Kesiciler, isteği yapan kimliği doğrulanmış kullanıcıya göre yetkilendirme kararları vermenizi sağlar. Bir kimliği doğrulanmış kullanıcı kimliğine göre veri hizmeti kaynaklarına erişimi kısıtlamak nasıl bir örnek için bkz [nasıl yapılır: Veri hizmeti iletilerini ıntercept](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Kalıcı Veri Deposu ve Yerel Kaynaklara Erişimi Kısıtlama  
 Kalıcı depoya erişmek için kullanılan hesaplara, yalnızca veritabanı veya dosya sisteminde veri hizmetinin gereksinimlerini desteklemek için yeterli haklar verilmelidir. Bu, anonim kimlik doğrulama kullanıldığında barındırma uygulamasını çalıştırmak için kullanılan hesaptır. Daha fazla bilgi için [nasıl yapılır: IIS üzerinde çalışan bir WCF veri hizmeti geliştirme](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Kimliğe bürünme kullanıldığında, kimliği doğrulanmış kullanıcıların genellikle Windows grubunun parçası olarak bu kaynaklara erişmesi sağlanmalıdır.  
  
## <a name="other-security-considerations"></a>Güvenlik Hakkında Diğer Önemli Noktalar  
  
### <a name="secure-the-data-in-the-payload"></a>Yükte Verileri Güvenli Hale Getirme  
OData HTTP protokolünü temel alır. HTTP iletisinde, üstbilgi veri hizmeti tarafından uygulanan kimlik doğrulamaya bağlı olarak değerli kullanıcı kimlik bilgileri içerebilir. İleti gövdesi, korunması gereken değerli müşteri verileri de içerebilir. Her iki durumda da, bu bilgileri çevrimiçi olarak korumak için SSL'yi kullanmanızı öneririz.  
  
### <a name="ignored-message-headers-and-cookies"></a>Yoksayılan İleti Üstbilgileri ve Tanımlama Bilgileri  
 İçerik türleri ve kaynak konumları bildirenlerin dışındaki HTTP isteği üstbilgileri yoksayılır ve veri hizmeti tarafından hiçbir zaman ayarlanmaz.  
  
 Tanımlama bilgilerini bir kimlik doğrulama şemasıyla bir parçası olarak gibi ASP.NET Forms kimlik doğrulaması ile kullanılabilir. Ancak, gelen bir istek üzerinde ayarlanan tüm HTTP tanımlama bilgileri, WCF DataServices tarafından göz ardı edilir. Bir veri hizmeti ana bilgisayarı tanımlama bilgisini işleyebilir, ancak WCF Veri Hizmetleri çalışma zamanı, hiçbir zaman analiz etmez veya tanımlama bilgilerini döndürür. WCF Veri Hizmetleri istemci kitaplığı Yanıtta gönderilen tanımlama bilgilerini de işlemez.  
  
### <a name="custom-hosting-requirements"></a>Özel Barındırma Gereksinimleri  
 Varsayılan olarak, WCF Veri Hizmetleri, IIS'de barındırılan ASP.NET uygulaması olarak oluşturulur. Bu, veri hizmetinin bu platformun güvenli davranışlarını kullanmasını sağlar. Özel bir ana bilgisayar tarafından barındırılan bir WCF Veri Hizmetleri tanımlayabilirsiniz. Daha fazla bilgi için [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Veri hizmetini barındıran bileşenler ve platform, veri hizmetine yapılan saldırıları önlemek için aşağıdaki güvenlik davranışlarını sağlamalıdır:  
  
- Olası tüm işlemler için veri hizmeti isteğinde kabul edilen URI'nin uzunluğunu sınırlama.  
  
- Hem gelen hem de giden HTTP iletilerinin boyutunu sınırlama.  
  
- Herhangi bir zamanda bekleyen isteklerin toplam sayısını sınırlama.  
  
- HTTP üstbilgilerinin ve değerlerinin boyutunu sınırlama ve üstbilgi verilerine WCF Veri Hizmetleri erişim sağlar.  
  
- TCP SYN ve ileti yeniden yürütme saldırıları gibi bilinen saldırıları algılama ve önleme.  
  
### <a name="values-are-not-further-encoded"></a>Değerler Daha Fazla Kodlanmaz  
 Veri hizmetine gönderilen özellik değerleri WCF Veri Hizmetleri çalışma zamanı tarafından daha fazla kodlanmaz. Örneğin, bir varlığın dize özelliği biçimlendirilmiş HTML içeriği içerdiğinde, etiketler veri hizmeti tarafından kodlanmış HTML değildir. Veri hizmeti yanıttaki özellik değerlerini de kodlamaz. İstemci Kitaplığı da ek kodlama gerçekleştirmez.  
  
### <a name="considerations-for-client-applications"></a>İstemci Uygulamaları için Önemli Noktalar  
 Aşağıdaki güvenlik hususlarını WCF Veri Hizmetleri istemci OData hizmetlere erişmek için kullandıkları uygulamalar için geçerlidir:  
  
- İstemci kitaplığı, veri hizmetine erişmek için kullanılan protokollerin uygun düzeyde güvenlik sağladığını varsayar.  
  
- İstemci kitaplığı, platform tarafından sağlanan temel taşıma yığınlarının zaman aşımları ve ayrıştırma seçenekleri için tüm varsayılan değerleri kullanır.  
  
- İstemci kitaplığı, uygulama yapılandırma dosyalarından ayar okumaz.  
  
- İstemci kitaplığı, etki alanları arasında erişim mekanizması uygulamaz. Bunun yerine, temel HTTP yığını tarafından sağlanan mekanizmalardan yararlanır.  
  
- İstemci kitaplığının kullanıcı arabirimi öğesi yoktur ve hiçbir zaman aldığı veya gönderdiği verileri görüntülemeye veya oluşturmaya çalışmaz.  
  
- İstemci uygulamalarının her zaman kullanıcı girişini ve güvenilmeyen hizmetlerden kabul edilen verileri doğrulamasını öneririz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
