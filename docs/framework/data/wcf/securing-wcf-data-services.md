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
ms.openlocfilehash: 642ff5fe3427509a4d4782fb8640f4b755d58459
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790336"
---
# <a name="securing-wcf-data-services"></a>WCF Veri Hizmetlerinin Güvenliğini Sağlama
Bu konuda, açık veri Protokolü 'Nü (OData) destekleyen hizmetlere erişen WCF Veri Hizmetleri ve uygulamalar geliştirmeye, dağıtmaya ve çalıştırmaya özgü güvenlik konuları açıklanmaktadır. Ayrıca, güvenli .NET Framework uygulamalar oluşturmaya yönelik önerileri de izlemeniz gerekir.  
  
WCF Veri Hizmetleri tabanlı bir OData hizmetini nasıl güvenli hale getirmek için planlama yaparken, her iki kimlik doğrulamasını da ele almalıdır, bir Sorumlunun kimliğini bulma ve doğrulama işlemi ve yetkilendirme, kimliği doğrulanmış bir sorumlunun olup olmadığını belirleme işlemi istenen kaynaklara erişmesine izin verildi. İletiyi SSL kullanarak şifrelenip şifrelenmeyeceğinizi de göz önünde bulundurmalısınız.  
  
## <a name="authenticating-client-requests"></a>İstemci İsteklerinde Kimlik Doğrulama  
WCF Veri Hizmetleri, kendi kendine herhangi bir tür kimlik doğrulaması uygulamaz, ancak bunun yerine veri hizmeti ana bilgisayarının kimlik doğrulama sağlamasını kullanır. Bu, hizmetin aldığı tüm istekleri ağ ana bilgisayarı tarafından zaten doğrulanmış olduğunu ve konağın WCF Veri Hizmetleri tarafından belirtilen arabirimler aracılığıyla istek için ilkeyi doğru bir şekilde tanımladığını varsaydığı anlamına gelir. Bu kimlik doğrulama seçenekleri ve yaklaşımları, çok parçalı [OData ve kimlik doğrulama serisinde](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)ayrıntılı olarak açıklanmıştır.  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Veri Hizmeti için Kimlik Doğrulama Seçenekleri  
 Aşağıdaki tabloda, WCF Veri Hizmeti için isteklerin kimliğini doğrulamanıza yardımcı olacak kimlik doğrulama mekanizmalarından bazıları listelenmektedir.  
  
|Kimlik doğrulama seçenekleri|Açıklama|  
|----------------------------|-----------------|  
|Anonim kimlik doğrulama|HTTP anonim kimlik doğrulama etkinleştirildiğinde, herhangi bir ilke veri hizmetine bağlanabilir. Anonim erişim için kimlik bilgileri gerekmez. Bu seçeneği, yalnızca herkesin veri hizmetine erişmesini istediğinizde kullanın.|  
|Temel ve özet kimlik doğrulama|Kimlik doğrulama için bir kullanıcı adı ve paroladan oluşan kimlik bilgileri gereklidir. Windows olmayan istemcilerin kimlik doğrulamasını destekler. **Güvenlik Notno:**  Temel kimlik doğrulama kimlik bilgileri (kullanıcı adı ve parola) açık bir şekilde gönderilir ve kesilebilir. Özet kimlik doğrulama, sağlanan kimlik bilgilerini temel alan bir karma değer gönderir; bu nedenle temel kimlik doğrulamaya göre daha güvenlidir. Her ikisi de ortadaki adam saldırılarına maruz kalabilir. Bu kimlik doğrulama yöntemlerini kullanırken, Güvenli Yuva Katmanı (SSL) kullanarak istemci ile veri hizmeti arasındaki iletişimi şifrelemeyi göz önünde bulundurmanız gerekir. <br /><br /> Microsoft Internet Information Services (IIS), bir ASP.NET uygulamasındaki HTTP istekleri için hem temel hem de Özet kimlik doğrulamasının uygulanmasını sağlar. Bu Windows Kimlik Doğrulama Sağlayıcısı uygulaması, Windows kullanıcısının kimlik doğrulaması üzerinde sorunsuz bir şekilde anlaşmaya varmak için veri hizmetine isteğin HTTP üstbilgisindeki kimlik bilgilerini sağlayan bir .NET Framework istemci uygulaması sağlar. Daha fazla bilgi için bkz. [Özet kimlik doğrulaması teknik başvurusu](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Veri hizmetinizin Windows kimlik bilgileri değil, bazı özel kimlik doğrulama hizmetine göre temel kimlik doğrulaması kullanmasını istediğinizde, kimlik doğrulaması için özel bir ADP.NET HTTP modülü uygulamanız gerekir.<br /><br /> WCF Veri Hizmetleri ile özel bir temel kimlik doğrulama düzeninin nasıl kullanılacağına ilişkin bir örnek için, bkz. Web günlüğü gönderi [OData ve kimlik doğrulaması – Bölüm 6 – özel temel kimlik doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Windows kimlik doğrulaması|Windows tabanlı kimlik bilgileri, NTLM veya Kerberos kullanılarak değiştirilir. Bu mekanizma, basit veya özet kimlik doğrulamaya göre daha güvenlidir, ancak istemcinin Windows tabanlı bir uygulama olmasını gerektirir. IIS Ayrıca bir ASP.NET uygulamasındaki HTTP istekleri için Windows kimlik doğrulamasının uygulanmasını sağlar. Daha fazla bilgi için bkz. [ASP.NET Forms kimlik doğrulamasına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Windows kimlik doğrulamasının WCF Veri Hizmetleri ile nasıl kullanılacağına ilişkin bir örnek için bkz. Web günlüğü gönderi [OData ve kimlik doğrulaması – Bölüm 2 – Windows kimlik doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|ASP.NET Forms kimlik doğrulaması|Form kimlik doğrulaması, kendi kodunuzu kullanarak ve sonra bir tanımlama bilgisinde veya sayfa URL 'sinde bir kimlik doğrulama belirteci bulundurarak kullanıcıların kimliğini doğrulayabilmenizi sağlar. Oluşturduğunuz bir oturum açma formunu kullanarak kullanıcılarınızın kullanıcı adını ve parolasını doğrularsanız. Kimliği doğrulanmamış istekler, kullanıcının kimlik bilgileri sağladığı ve formu gönderdiği bir oturum açma sayfasına yönlendirilir. Uygulama isteğin kimliğini doğrularsa, sistem sonraki istekler için kimliği yeniden oluşturabilecek bir anahtar içeren bir anahtar verir. Daha fazla bilgi için bkz. [Forms kimlik doğrulama sağlayıcısı](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Güvenlik Notno:**  Form kimlik doğrulamasını bir ASP.NET Web uygulamasında kullandığınızda, varsayılan olarak, Forms kimlik doğrulama biletini içeren tanımlama bilgisi güvenli değildir. Hem kimlik doğrulama anahtarını hem de ilk oturum açma kimlik bilgilerini korumak için SSL kullanılmasını gerekli tutmayı dikkate almanız gerekir. <br /><br /> Forms kimlik doğrulamasının WCF Veri Hizmetleri ile nasıl kullanılacağına ilişkin bir örnek için bkz. Web günlüğü Post [OData ve authentication – bölüm 7 – Forms Authentication](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Beyana dayalı kimlik doğrulama|Talep tabanlı kimlik doğrulamasında, veri hizmeti kullanıcının kimliğini doğrulamak için güvenilir bir "üçüncü taraf" kimlik sağlayıcısı hizmetini kullanır. Kimlik sağlayıcısı, veri hizmeti kaynaklarına erişmek isteyen kullanıcının kimliğini olumlu bir şekilde doğrular ve istenen kaynaklara erişim izni sağlayan bir belirteç verir. Bu belirteç, daha sonra veri hizmetine sunulur. Veri hizmeti, erişim belirtecini veren kimlik hizmetiyle kurulan güven ilişkisine göre kullanıcıya erişim sağlar.<br /><br /> Beyana dayalı kimlik doğrulama sağlayıcısı kullanmanın avantajı, güven etki alanları arasında çeşitli türden istemcilerin kimliğini doğrulamak için kullanılabilmeleridir. Veri hizmeti, böyle bir üçüncü taraf sağlayıcı kullanarak kullanıcıları koruma ve kimliklerini doğrulama gereksinimlerinden kurtulabilir. OAuth 2.0, hizmet olarak şirket dışı kimlik doğrulama için Microsoft Azure AppFabric Erişim Denetimi tarafından desteklenen beyana dayalı bir kimlik doğrulama protokolüdür. Bu protokol REST tabanlı hizmetleri destekler. WCF Veri Hizmetleri ile OAuth 2,0 kullanma hakkında bir örnek için bkz. Web günlüğü gönderi [OData ve kimlik doğrulaması – 5. Bölüm – OAuth sarması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>İstemci Kitaplığında kimlik doğrulama  
 Varsayılan olarak, WCF Veri Hizmetleri istemci kitaplığı, bir OData hizmetine istek yaparken kimlik bilgileri sağlamaz. Veri hizmetinin bir kullanıcının kimliğini doğrulamak için oturum açma kimlik bilgileri gerektiğinde, bu kimlik bilgileri, aşağıdaki örnekte olduğu gibi <xref:System.Net.NetworkCredential> öğesinin <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> <xref:System.Data.Services.Client.DataServiceContext>özelliğinden erişilebilen öğesine sağlanabilir:  
  
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
  
 Daha fazla bilgi için [nasıl yapılır: Bir veri hizmeti Isteği](specify-client-creds-for-a-data-service-request-wcf.md)Için istemci kimlik bilgilerini belirtin.  
  
 Veri hizmeti, talep tabanlı bir belirteç veya tanımlama bilgisi gibi bir <xref:System.Net.NetworkCredential> nesne kullanılarak belirtilemez oturum açma kimlik bilgileri gerektirdiğinde, `Authorization` genellikle ve `Cookie` üst bilgileri http isteğinde el ile ayarlamanız gerekir. Bu tür bir kimlik doğrulama senaryosu hakkında daha fazla bilgi için bkz. Web günlüğü gönderi [OData ve kimlik doğrulaması – 3. Bölüm – Istemci tarafı kancaları](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). İstek iletisinde http üst bilgilerinin nasıl ayarlanacağı hakkında bir örnek için bkz [. nasıl yapılır: Istemci Isteğindeki](how-to-set-headers-in-the-client-request-wcf-data-services.md)üst bilgileri ayarlayın.  
  
## <a name="impersonation"></a>Kimliğe bürünme  
 Genellikle veri hizmeti, veri hizmetini barındıran çalışan işleminin kimlik bilgilerini kullanarak sunucudaki veya veritabanındaki dosyalar gibi gerekli kaynaklara erişir. Kimliğe bürünme kullanılırken, ASP.NET uygulamaları, isteği yapan kullanıcının Windows kimliğiyle (Kullanıcı hesabı) çalıştırılabilir. Kimliğe bürünme, genel olarak kullanıcının kimliğini doğrulamak için IIS'den yararlanan uygulamalarda kullanılır ve gerekli kaynaklara erişmek için bu ilkenin kimlik bilgileri kullanılır. Daha fazla bilgi için bkz. [ASP.NET Kimliğe bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Veri Hizmeti Yetkilendirmesini Yapılandırma  
 Yetkilendirme, uygulama kaynaklarının daha önce başarılı olan bir kimlik doğrulama temel alınarak belirlenen bir ilkeye veya işleme erişimini sağlamaktır. Genel bir uygulama olarak, yeterli hakları yalnızca istemci uygulamaları tarafından gerekli kılınan işlemleri gerçekleştirmek için veri hizmetinin kullanıcılarına vermeniz gerekir.  
  
### <a name="restrict-access-to-data-service-resources"></a>Veri Hizmeti Kaynaklarına Erişimi Kısıtlama  
 Varsayılan olarak, WCF Veri Hizmetleri veri hizmeti kaynaklarına (varlık kümesi ve hizmet işlemleri) veri hizmetine erişebilen tüm kullanıcılara genel okuma ve yazma erişimi sağlamanıza olanak sağlar. Okuma ve yazma erişimini tanımlayan kurallar, veri hizmeti tarafından kullanılan ve hizmet işlemlerine sunulan her varlık kümesi için ayrı ayrı tanımlanabilir. Hem okuma hem de yazma erişimini yalnızca istemci uygulaması tarafından gerekli kılınan kaynaklarla sınırlamanızı öneririz. Daha fazla bilgi için bkz. [En düşük kaynak erişim gereksinimleri](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Rol Tabanlı Kesiciler Uygulama  
 Kesiciler, istekleri veri hizmeti tarafından kullanılmadan önce veri hizmeti kaynaklarına karşı kesmenizi sağlar. Daha fazla bilgi için bkz. [yakalayıcılar](interceptors-wcf-data-services.md). Kesiciler, isteği yapan kimliği doğrulanmış kullanıcıya göre yetkilendirme kararları vermenizi sağlar. Kimliği doğrulanmış bir kullanıcı kimliğine göre veri hizmeti kaynaklarına erişimin nasıl kısıtlanacağını gösteren bir örnek için bkz [. nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Kalıcı Veri Deposu ve Yerel Kaynaklara Erişimi Kısıtlama  
 Kalıcı depoya erişmek için kullanılan hesaplara, yalnızca veritabanı veya dosya sisteminde veri hizmetinin gereksinimlerini desteklemek için yeterli haklar verilmelidir. Bu, anonim kimlik doğrulama kullanıldığında barındırma uygulamasını çalıştırmak için kullanılan hesaptır. Daha fazla bilgi için [nasıl yapılır: IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)ÜZERINDE çalışan bir WCF veri hizmeti geliştirin. Kimliğe bürünme kullanıldığında, kimliği doğrulanmış kullanıcıların genellikle Windows grubunun parçası olarak bu kaynaklara erişmesi sağlanmalıdır.  
  
## <a name="other-security-considerations"></a>Güvenlik Hakkında Diğer Önemli Noktalar  
  
### <a name="secure-the-data-in-the-payload"></a>Yükte Verileri Güvenli Hale Getirme  
OData, HTTP protokolünü temel alır. HTTP iletisinde, üstbilgi veri hizmeti tarafından uygulanan kimlik doğrulamaya bağlı olarak değerli kullanıcı kimlik bilgileri içerebilir. İleti gövdesi, korunması gereken değerli müşteri verileri de içerebilir. Her iki durumda da, bu bilgileri çevrimiçi olarak korumak için SSL'yi kullanmanızı öneririz.  
  
### <a name="ignored-message-headers-and-cookies"></a>Yoksayılan İleti Üstbilgileri ve Tanımlama Bilgileri  
 İçerik türleri ve kaynak konumları bildirenlerin dışındaki HTTP isteği üstbilgileri yoksayılır ve veri hizmeti tarafından hiçbir zaman ayarlanmaz.  
  
 Tanımlama bilgileri, ASP.NET Forms kimlik doğrulaması gibi bir kimlik doğrulama düzeninin bir parçası olarak kullanılabilir. Ancak, gelen istek üzerinde ayarlanan HTTP tanımlama bilgileri WCF veri Hizmetleri tarafından yok sayılır. Veri hizmetinin ana bilgisayarı tanımlama bilgisini işleyebilir, ancak WCF Veri Hizmetleri çalışma zamanı tanımlama bilgilerini hiçbir şekilde analiz edebilir veya döndürmez. WCF Veri Hizmetleri istemci kitaplığı, yanıtta gönderilen tanımlama bilgilerini de işlemez.  
  
### <a name="custom-hosting-requirements"></a>Özel Barındırma Gereksinimleri  
 Varsayılan olarak, WCF Veri Hizmetleri IIS 'de barındırılan bir ASP.NET uygulaması olarak oluşturulur. Bu, veri hizmetinin bu platformun güvenli davranışlarını kullanmasını sağlar. Özel bir ana bilgisayar tarafından barındırılan WCF Veri Hizmetleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini barındırma](hosting-the-data-service-wcf-data-services.md). Veri hizmetini barındıran bileşenler ve platform, veri hizmetine yapılan saldırıları önlemek için aşağıdaki güvenlik davranışlarını sağlamalıdır:  
  
- Olası tüm işlemler için veri hizmeti isteğinde kabul edilen URI'nin uzunluğunu sınırlama.  
  
- Hem gelen hem de giden HTTP iletilerinin boyutunu sınırlama.  
  
- Herhangi bir zamanda bekleyen isteklerin toplam sayısını sınırlama.  
  
- HTTP üstbilgilerinin ve değerlerinin boyutunu sınırlayın ve üst bilgi verisine WCF Veri Hizmetleri erişim sağlayın.  
  
- TCP SYN ve ileti yeniden yürütme saldırıları gibi bilinen saldırıları algılama ve önleme.  
  
### <a name="values-are-not-further-encoded"></a>Değerler Daha Fazla Kodlanmaz  
 Veri hizmetine gönderilen özellik değerleri WCF Veri Hizmetleri çalışma zamanı tarafından daha fazla kodlanmaz. Örneğin, bir varlığın dize özelliği biçimlendirilmiş HTML içeriği içerdiğinde, etiketler veri hizmeti tarafından kodlanmış HTML değildir. Veri hizmeti yanıttaki özellik değerlerini de kodlamaz. İstemci Kitaplığı da ek kodlama gerçekleştirmez.  
  
### <a name="considerations-for-client-applications"></a>İstemci Uygulamaları için Önemli Noktalar  
 OData hizmetlerine erişmek için WCF Veri Hizmetleri istemcisini kullanan uygulamalar için aşağıdaki güvenlik konuları geçerlidir:  
  
- İstemci kitaplığı, veri hizmetine erişmek için kullanılan protokollerin uygun düzeyde güvenlik sağladığını varsayar.  
  
- İstemci kitaplığı, platform tarafından sağlanan temel taşıma yığınlarının zaman aşımları ve ayrıştırma seçenekleri için tüm varsayılan değerleri kullanır.  
  
- İstemci kitaplığı, uygulama yapılandırma dosyalarından ayar okumaz.  
  
- İstemci kitaplığı, etki alanları arasında erişim mekanizması uygulamaz. Bunun yerine, temel HTTP yığını tarafından sağlanan mekanizmalardan yararlanır.  
  
- İstemci kitaplığının kullanıcı arabirimi öğesi yoktur ve hiçbir zaman aldığı veya gönderdiği verileri görüntülemeye veya oluşturmaya çalışmaz.  
  
- İstemci uygulamalarının her zaman kullanıcı girişini ve güvenilmeyen hizmetlerden kabul edilen verileri doğrulamasını öneririz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
