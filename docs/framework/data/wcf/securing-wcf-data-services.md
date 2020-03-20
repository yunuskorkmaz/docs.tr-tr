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
ms.openlocfilehash: e09007e786772e838a9aaa76eb8ef7a3fe2b7cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174660"
---
# <a name="securing-wcf-data-services"></a>WCF Veri Hizmetlerinin Güvenliğini Sağlama
Bu konu, WCF Veri Hizmetleri ve Açık Veri Protokolü 'nü (OData) destekleyen hizmetlere erişen uygulamalar geliştirmeye, dağıtmaya ve çalıştırmaya özgü güvenlik hususlarını açıklar. Güvenli .NET Framework uygulamaları oluşturmak için önerileri de izlemeniz gerekir.  
  
WCF Veri Hizmetleri tabanlı bir OData hizmetinin nasıl güvence altına alınamayacağını planlarken, hem kimlik doğrulamayı, hem bir asıl adın kimliğini bulma ve doğrulama işlemini hem de yetkilendirmeyi, kimlik doğrulaması yapılan bir müdürün kimlik doğrulaması olup olmadığını belirleme işlemini ele almalısınız. istenen kaynaklara erişmesine izin verilir. İletiyi SSL kullanarak şifrelenip şifrelenmeyeceğinizi de göz önünde bulundurmalısınız.  
  
## <a name="authenticating-client-requests"></a>İstemci İsteklerinde Kimlik Doğrulama  
WCF Veri Hizmetleri kendi kimlik doğrulamasını uygulamaz, ancak veri hizmeti ana bilgisayarının kimlik doğrulama hükümlerine dayanır. Bu, hizmetin aldığı herhangi bir isteğin ağ ana bilgisayarı tarafından zaten doğrulanmış olduğunu ve ana bilgisayar, WCF Veri Hizmetleri tarafından sağlanan arabirimler aracılığıyla istek ilkesini doğru şekilde tanımladığını varsayar. Bu kimlik doğrulama seçenekleri ve yaklaşımları çok parçalı [OData ve Kimlik Doğrulama serisinde](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)ayrıntılı olarak açıklanmaktadır.  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Veri Hizmeti için Kimlik Doğrulama Seçenekleri  
 Aşağıdaki tabloda, WCF Veri Hizmeti için isteklerin kimliğini doğrulamanıza yardımcı olacak kimlik doğrulama mekanizmalarından bazıları listelenmektedir.  
  
|Kimlik Doğrulama Seçenekleri|Açıklama|  
|----------------------------|-----------------|  
|Anonim kimlik doğrulama|HTTP anonim kimlik doğrulama etkinleştirildiğinde, herhangi bir ilke veri hizmetine bağlanabilir. Anonim erişim için kimlik bilgileri gerekmez. Bu seçeneği, yalnızca herkesin veri hizmetine erişmesini istediğinizde kullanın.|  
|Temel ve özet kimlik doğrulama|Kimlik doğrulama için bir kullanıcı adı ve paroladan oluşan kimlik bilgileri gereklidir. Windows olmayan istemcilerin kimlik doğrulamasını destekler. **Güvenlik Notu:**  Temel kimlik doğrulama kimlik bilgileri (kullanıcı adı ve parola) açık olarak gönderilir ve ele geçirilebilir. Özet kimlik doğrulama, sağlanan kimlik bilgilerini temel alan bir karma değer gönderir; bu nedenle temel kimlik doğrulamaya göre daha güvenlidir. Her ikisi de ortadaki adam saldırılarına maruz kalabilir. Bu kimlik doğrulama yöntemlerini kullanırken, Güvenli Yuva Katmanı (SSL) kullanarak istemci ile veri hizmeti arasındaki iletişimi şifrelemeyi göz önünde bulundurmanız gerekir. <br /><br /> Microsoft Internet Information Services (IIS), ASP.NET bir uygulamada HTTP istekleri için hem temel hem de özet kimlik doğrulama uygulaması sağlar. Bu Windows Kimlik Doğrulama Sağlayıcısı uygulaması, Windows kullanıcısının kimlik doğrulaması üzerinde sorunsuz bir şekilde anlaşmaya varmak için veri hizmetine isteğin HTTP üstbilgisindeki kimlik bilgilerini sağlayan bir .NET Framework istemci uygulaması sağlar. Daha fazla bilgi için [Bkz. Özet Kimlik Doğrulama Teknik Başvurusu.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10))<br /><br /> Veri hizmetinizin Windows kimlik bilgilerini değil, bazı özel kimlik doğrulama hizmetini temel kimlik doğrulamayı kullanmasını istediğinizde, kimlik doğrulaması için özel bir ADP.NET HTTP Modülü uygulamanız gerekir.<br /><br /> WCF Veri Hizmetleri ile özel bir temel kimlik doğrulama şemasının nasıl kullanılacağına bir örnek için, Blog yazısı [OData ve Kimlik Doğrulama - Bölüm 6 – Özel Temel Kimlik Doğrulama'ya](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/)bakın.|  
|Windows kimlik doğrulaması|Windows tabanlı kimlik bilgileri, NTLM veya Kerberos kullanılarak değiştirilir. Bu mekanizma, basit veya özet kimlik doğrulamaya göre daha güvenlidir, ancak istemcinin Windows tabanlı bir uygulama olmasını gerektirir. IIS, bir ASP.NET uygulamasında HTTP istekleri için Windows kimlik doğrulamasını da sağlar. Daha fazla bilgi için ASP.NET [Formlar Kimlik Doğrulama Genel Bakış'a](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100))bakın.<br /><br /> WCF Veri Hizmetleri ile Windows kimlik doğrulamasının nasıl kullanılacağına bir örnek için, Blog gönderisi [OData ve Authentication – Bölüm 2 – Windows Kimlik Doğrulama'ya](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/)bakın.|  
|ASP.NET kimlik doğrulaması oluşturur|Formkimlik doğrulaması, kendi kodunuzu kullanarak kullanıcıların kimliğini doğrulamanızı sağlar ve ardından çerezde veya sayfa URL'sinde kimlik doğrulama belirteci nizi korumanızı sağlar. Oluşturduğunuz bir oturum açma formunu kullanarak kullanıcılarınızın kullanıcı adını ve parolasını doğrularsanız. Kimliği doğrulanmamış istekler, kullanıcının kimlik bilgileri sağladığı ve formu gönderdiği bir oturum açma sayfasına yönlendirilir. Uygulama isteğin kimliğini doğrularsa, sistem sonraki istekler için kimliği yeniden oluşturabilecek bir anahtar içeren bir anahtar verir. Daha fazla bilgi için [Formkimlik Doğrulama Sağlayıcısı'na](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100))bakın. **Güvenlik Notu:**  Varsayılan olarak, formkimlik doğrulama biletini içeren çerez, ASP.NET bir Web uygulamasında form kimlik doğrulaması kullandığınızda güvenli hale gelmez. Hem kimlik doğrulama anahtarını hem de ilk oturum açma kimlik bilgilerini korumak için SSL kullanılmasını gerekli tutmayı dikkate almanız gerekir. <br /><br /> WCF Veri Hizmetleri ile form kimlik doğrulamasının nasıl kullanılacağına bir örnek için, Blog yazısı [OData ve Authentication – Bölüm 7 – Formlar Kimlik Doğrulaması](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/)bölümüne bakın.|  
|Beyana dayalı kimlik doğrulama|Talep tabanlı kimlik doğrulamada, veri hizmeti kullanıcının kimliğini doğrulamak için güvenilir bir "üçüncü taraf" kimlik sağlayıcısı hizmetine dayanır. Kimlik sağlayıcısı, veri hizmeti kaynaklarına erişmek isteyen kullanıcının kimliğini olumlu bir şekilde doğrular ve istenen kaynaklara erişim izni sağlayan bir belirteç verir. Bu belirteç, daha sonra veri hizmetine sunulur. Veri hizmeti, erişim belirtecini veren kimlik hizmetiyle kurulan güven ilişkisine göre kullanıcıya erişim sağlar.<br /><br /> Beyana dayalı kimlik doğrulama sağlayıcısı kullanmanın avantajı, güven etki alanları arasında çeşitli türden istemcilerin kimliğini doğrulamak için kullanılabilmeleridir. Veri hizmeti, böyle bir üçüncü taraf sağlayıcı kullanarak kullanıcıları koruma ve kimliklerini doğrulama gereksinimlerinden kurtulabilir. OAuth 2.0, hizmet olarak şirket dışı kimlik doğrulama için Microsoft Azure AppFabric Erişim Denetimi tarafından desteklenen beyana dayalı bir kimlik doğrulama protokolüdür. Bu protokol REST tabanlı hizmetleri destekler. WCF Veri Hizmetleri ile OAuth 2.0'ın nasıl kullanılacağına bir örnek için, OData ve Authentication adlı blog gönderisine bakın [– Bölüm 8 – OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>
### <a name="authentication-in-the-client-library"></a>İstemci Kitaplığında kimlik doğrulama  
 Varsayılan olarak, WCF Veri Hizmetleri istemci kitaplığı, Bir OData hizmetine istekte bulunurken kimlik bilgileri sağlamaz. Bir kullanıcının kimliğini doğrulamak için veri hizmeti tarafından oturum açma kimlik bilgileri <xref:System.Net.NetworkCredential> gerektiğinde, bu <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> kimlik <xref:System.Data.Services.Client.DataServiceContext>bilgileri aşağıdaki örnekte olduğu gibi, aşağıdaki örnekte olduğu gibi, erişilen bir özellikte sağlanabilir:  
  
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
  
 Daha fazla bilgi için [bkz: Veri Hizmeti İsteği için İstemci Kimlik Bilgilerini Belirtin.](specify-client-creds-for-a-data-service-request-wcf.md)  
  
 Veri hizmeti, talep tabanlı bir belirteç <xref:System.Net.NetworkCredential> veya çerez gibi bir nesne kullanılarak belirtilemeyen oturum açma kimlik bilgilerini gerektiriyorsa, başlangıçları genellikle `Authorization` ve `Cookie` üstbilgiler olmak üzere, HTTP isteğine el ile ayarlamanız gerekir. Kimlik doğrulama senaryosu bu tür hakkında daha fazla bilgi için, blog yazısı OData ve Kimlik Doğrulama - [Bölüm 3 - ClientSide Hooks](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/)bakın. HTTP üstbilgilerinin istek iletisinde nasıl ayarlanabildiğini öğrenmek için [bkz.](how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
## <a name="impersonation"></a>Kimliğe bürünme  
 Genellikle veri hizmeti, veri hizmetini barındıran çalışan işleminin kimlik bilgilerini kullanarak sunucudaki veya veritabanındaki dosyalar gibi gerekli kaynaklara erişir. Kimliğe bürünme kullanırken, ASP.NET uygulamaları isteği yapan kullanıcının Windows kimliği (kullanıcı hesabı) ile yürütebilir. Kimliğe bürünme, genel olarak kullanıcının kimliğini doğrulamak için IIS'den yararlanan uygulamalarda kullanılır ve gerekli kaynaklara erişmek için bu ilkenin kimlik bilgileri kullanılır. Daha fazla bilgi için [ASP.NET Kimliğe Bürünme'ye](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100))bakın.  
  
## <a name="configuring-data-service-authorization"></a>Veri Hizmeti Yetkilendirmesini Yapılandırma  
 Yetkilendirme, uygulama kaynaklarının daha önce başarılı olan bir kimlik doğrulama temel alınarak belirlenen bir ilkeye veya işleme erişimini sağlamaktır. Genel bir uygulama olarak, yeterli hakları yalnızca istemci uygulamaları tarafından gerekli kılınan işlemleri gerçekleştirmek için veri hizmetinin kullanıcılarına vermeniz gerekir.  
  
### <a name="restrict-access-to-data-service-resources"></a>Veri Hizmeti Kaynaklarına Erişimi Kısıtlama  
 Varsayılan olarak, WCF Veri Hizmetleri, veri hizmeti hizmetine erişebilen herhangi bir kullanıcıya veri hizmeti kaynaklarına (varlık kümesi ve hizmet işlemleri) karşı ortak okuma ve yazma erişimi sağlamanıza olanak tanır. Okuma ve yazma erişimini tanımlayan kurallar, veri hizmeti tarafından kullanılan ve hizmet işlemlerine sunulan her varlık kümesi için ayrı ayrı tanımlanabilir. Hem okuma hem de yazma erişimini yalnızca istemci uygulaması tarafından gerekli kılınan kaynaklarla sınırlamanızı öneririz. Daha fazla bilgi [için, Minimum Kaynak Erişim Gereksinimleri'ne](configuring-the-data-service-wcf-data-services.md#accessRequirements)bakın.  
  
### <a name="implement-role-based-interceptors"></a>Rol Tabanlı Kesiciler Uygulama  
 Kesiciler, istekleri veri hizmeti tarafından kullanılmadan önce veri hizmeti kaynaklarına karşı kesmenizi sağlar. Daha fazla bilgi için [Interceptors](interceptors-wcf-data-services.md)'a bakın. Kesiciler, isteği yapan kimliği doğrulanmış kullanıcıya göre yetkilendirme kararları vermenizi sağlar. Kimlik doğrulaması kullanıcı kimliğine dayalı olarak veri hizmeti kaynaklarına erişimi nasıl kısıtlarsanız, [bkz.](how-to-intercept-data-service-messages-wcf-data-services.md)  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Kalıcı Veri Deposu ve Yerel Kaynaklara Erişimi Kısıtlama  
 Kalıcı depoya erişmek için kullanılan hesaplara, yalnızca veritabanı veya dosya sisteminde veri hizmetinin gereksinimlerini desteklemek için yeterli haklar verilmelidir. Bu, anonim kimlik doğrulama kullanıldığında barındırma uygulamasını çalıştırmak için kullanılan hesaptır. Daha fazla bilgi için [bkz: IIS'de çalışan bir WCF Veri Hizmeti geliştirin.](how-to-develop-a-wcf-data-service-running-on-iis.md) Kimliğe bürünme kullanıldığında, kimliği doğrulanmış kullanıcıların genellikle Windows grubunun parçası olarak bu kaynaklara erişmesi sağlanmalıdır.  
  
## <a name="other-security-considerations"></a>Güvenlik Hakkında Diğer Önemli Noktalar  
  
### <a name="secure-the-data-in-the-payload"></a>Yükte Verileri Güvenli Hale Getirme  
OData, HTTP protokolüne dayanmaktadır. HTTP iletisinde, üstbilgi veri hizmeti tarafından uygulanan kimlik doğrulamaya bağlı olarak değerli kullanıcı kimlik bilgileri içerebilir. İleti gövdesi, korunması gereken değerli müşteri verileri de içerebilir. Her iki durumda da, bu bilgileri çevrimiçi olarak korumak için SSL'yi kullanmanızı öneririz.  
  
### <a name="ignored-message-headers-and-cookies"></a>Yoksayılan İleti Üstbilgileri ve Tanımlama Bilgileri  
 İçerik türleri ve kaynak konumları bildirenlerin dışındaki HTTP isteği üstbilgileri yoksayılır ve veri hizmeti tarafından hiçbir zaman ayarlanmaz.  
  
 Tanımlama bilgileri, ASP.NET Formkimlik Doğrulama gibi bir kimlik doğrulama düzeninin parçası olarak kullanılabilir. Ancak, gelen istek üzerine ayarlanan tüm HTTP çerezleri WCF DataServices tarafından yoksayılır. Bir veri hizmetinin ana bilgisayarı çerezi işleyebilir, ancak WCF Veri Hizmetleri çalışma zamanı çerezleri hiçbir zaman analiz edemez veya döndürmez. WCF Veri Hizmetleri istemci kitaplığı da yanıt olarak gönderilen çerezleri işlemez.  
  
### <a name="custom-hosting-requirements"></a>Özel Barındırma Gereksinimleri  
 Varsayılan olarak, WCF Veri Hizmetleri IIS'de barındırılan bir ASP.NET uygulaması olarak oluşturulur. Bu, veri hizmetinin bu platformun güvenli davranışlarını kullanmasını sağlar. Özel bir ana bilgisayar tarafından barındırılan WCF Veri Hizmetleri tanımlayabilirsiniz. Daha fazla bilgi için Veri [Hizmetini Barındırma'ya](hosting-the-data-service-wcf-data-services.md)bakın. Veri hizmetini barındıran bileşenler ve platform, veri hizmetine yapılan saldırıları önlemek için aşağıdaki güvenlik davranışlarını sağlamalıdır:  
  
- Olası tüm işlemler için veri hizmeti isteğinde kabul edilen URI'nin uzunluğunu sınırlama.  
  
- Hem gelen hem de giden HTTP iletilerinin boyutunu sınırlama.  
  
- Herhangi bir zamanda bekleyen isteklerin toplam sayısını sınırlama.  
  
- HTTP üstbilgilerinin boyutunu ve değerlerini sınırlandırın ve WCF Veri Hizmetleri'nin üstbilgi verilerine erişimini sağlayın.  
  
- TCP SYN ve ileti yeniden yürütme saldırıları gibi bilinen saldırıları algılama ve önleme.  
  
### <a name="values-are-not-further-encoded"></a>Değerler Daha Fazla Kodlanmaz  
 Veri hizmetine gönderilen özellik değerleri, WCF Veri Hizmetleri çalışma zamanı tarafından başka bir şekilde kodlanmaz. Örneğin, bir varlığın dize özelliği biçimlendirilmiş HTML içeriği içerdiğinde, etiketler veri hizmeti tarafından kodlanmış HTML değildir. Veri hizmeti yanıttaki özellik değerlerini de kodlamaz. İstemci Kitaplığı da ek kodlama gerçekleştirmez.  
  
### <a name="considerations-for-client-applications"></a>İstemci Uygulamaları için Önemli Noktalar  
 OData hizmetlerine erişmek için WCF Veri Hizmetleri istemcisini kullanan uygulamalar için aşağıdaki güvenlik hususları geçerlidir:  
  
- İstemci kitaplığı, veri hizmetine erişmek için kullanılan protokollerin uygun düzeyde güvenlik sağladığını varsayar.  
  
- İstemci kitaplığı, platform tarafından sağlanan temel taşıma yığınlarının zaman aşımları ve ayrıştırma seçenekleri için tüm varsayılan değerleri kullanır.  
  
- İstemci kitaplığı, uygulama yapılandırma dosyalarından ayar okumaz.  
  
- İstemci kitaplığı, etki alanları arasında erişim mekanizması uygulamaz. Bunun yerine, temel HTTP yığını tarafından sağlanan mekanizmalardan yararlanır.  
  
- İstemci kitaplığının kullanıcı arabirimi öğesi yoktur ve hiçbir zaman aldığı veya gönderdiği verileri görüntülemeye veya oluşturmaya çalışmaz.  
  
- İstemci uygulamalarının her zaman kullanıcı girişini ve güvenilmeyen hizmetlerden kabul edilen verileri doğrulamasını öneririz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
