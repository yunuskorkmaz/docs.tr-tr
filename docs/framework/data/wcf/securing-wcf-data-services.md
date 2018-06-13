---
title: WCF Veri Hizmetleri güvenli hale getirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 468353d0cd4cc36507fe5f10a702450d2b516ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359268"
---
# <a name="securing-wcf-data-services"></a>WCF Veri Hizmetleri güvenli hale getirme
Bu konuda, geliştirme, dağıtmak ve çalıştırmak için belirli güvenlik konuları açıklanmaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ve Destek hizmetlerine erişmek uygulamaları [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Öneriler güvenli oluşturmak için izlemeniz gereken [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar.  
  
 Güvenli hale getirmek nasıl planlama yaparken bir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]-tabanlı [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti, bulmak ve bir sorumlusunun kimliğini doğrulama işleminin kimlik doğrulaması ve yetkilendirme, bir kimliği doğrulanmış olup olmadığını belirleme işlemi almalıdır Asıl istenen kaynaklara erişim izin verilmez. İletiyi SSL kullanarak şifrelenip şifrelenmeyeceğinizi de göz önünde bulundurmalısınız.  
  
## <a name="authenticating-client-requests"></a>İstemci İsteklerinde Kimlik Doğrulama  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bunun yerine veri hizmeti ana bilgisayar kimlik doğrulama sağlamasını yapar kullanır ancak kendi kimlik doğrulama her türlü uygulamaz. Bunun anlamı hizmeti aldığı herhangi bir istek ağ ana bilgisayar tarafından önceden doğrulanmış olduğunu varsayar ve konak doğru olduğunu ilkesine uygun şekilde tarafından sağlanan arabirimleri aracılığıyla istek için tanımlanan [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Bu kimlik doğrulama seçenekleri ve yaklaşımlar ayrıntıları [OData ve kimlik doğrulama serisi](http://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Veri Hizmeti için Kimlik Doğrulama Seçenekleri  
 Aşağıdaki tabloda, WCF Veri Hizmeti için isteklerin kimliğini doğrulamanıza yardımcı olacak kimlik doğrulama mekanizmalarından bazıları listelenmektedir.  
  
|Kimlik doğrulama seçenekleri|Açıklama|  
|----------------------------|-----------------|  
|Anonim kimlik doğrulama|HTTP anonim kimlik doğrulama etkinleştirildiğinde, herhangi bir ilke veri hizmetine bağlanabilir. Anonim erişim için kimlik bilgileri gerekmez. Bu seçeneği, yalnızca herkesin veri hizmetine erişmesini istediğinizde kullanın.|  
|Temel ve özet kimlik doğrulama|Kimlik doğrulama için bir kullanıcı adı ve paroladan oluşan kimlik bilgileri gereklidir. Windows olmayan istemcilerin kimlik doğrulamasını destekler. **Güvenlik Notu:** temel doğrulama kimlik bilgilerini (kullanıcı adı ve parola) açık bir şekilde gönderilir ve geçirilebilir. Özet kimlik doğrulama, sağlanan kimlik bilgilerini temel alan bir karma değer gönderir; bu nedenle temel kimlik doğrulamaya göre daha güvenlidir. Her ikisi de ortadaki adam saldırılarına maruz kalabilir. Bu kimlik doğrulama yöntemlerini kullanırken, Güvenli Yuva Katmanı (SSL) kullanarak istemci ile veri hizmeti arasındaki iletişimi şifrelemeyi göz önünde bulundurmanız gerekir. <br /><br /> Microsoft Internet Information Services (IIS) uygulaması hem de temel sağlar ve Özet kimlik doğrulaması için HTTP isteklerini bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Bu Windows Kimlik Doğrulama Sağlayıcısı uygulaması, Windows kullanıcısının kimlik doğrulaması üzerinde sorunsuz bir şekilde anlaşmaya varmak için veri hizmetine isteğin HTTP üstbilgisindeki kimlik bilgilerini sağlayan bir .NET Framework istemci uygulaması sağlar. Daha fazla bilgi için bkz: [Özet kimlik doğrulaması Teknik Başvurusu](http://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Bazı özel kimlik doğrulama hizmeti ve Windows kimlik göre veri hizmeti temel kimlik doğrulamasını kullan olmasını istediğinizde, özel bir uygulamalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP modülü kimlik doğrulama için.<br /><br /> Bir özel temel kimlik doğrulama şeması kullanma örneği için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], post bakın [özel temel kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=200388) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisi.|  
|Windows kimlik doğrulaması|Windows tabanlı kimlik bilgileri, NTLM veya Kerberos kullanılarak değiştirilir. Bu mekanizma, basit veya özet kimlik doğrulamaya göre daha güvenlidir, ancak istemcinin Windows tabanlı bir uygulama olmasını gerektirir. IIS Windows kimlik doğrulaması için HTTP isteklerinde uygulaması de sağlar bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Daha fazla bilgi için bkz: [ASP.NET formları kimlik doğrulamasına genel bakış](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Windows kimlik doğrulaması ile kullanmak nasıl bir örnek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], post bakın [Windows kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=200384) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisi.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Form kimlik doğrulaması|Forms kimlik doğrulaması, kullanıcıların kimliğini kendi kodunuzu kullanarak ve ardından bir tanımla bilgisinde veya sayfa URL'sinde bir kimlik doğrulama belirteci tutarak doğrulamanızı sağlar. Oluşturduğunuz bir oturum açma formunu kullanarak kullanıcılarınızın kullanıcı adını ve parolasını doğrularsanız. Kimliği doğrulanmamış istekler, kullanıcının kimlik bilgileri sağladığı ve formu gönderdiği bir oturum açma sayfasına yönlendirilir. Uygulama isteğin kimliğini doğrularsa, sistem sonraki istekler için kimliği yeniden oluşturabilecek bir anahtar içeren bir anahtar verir. Daha fazla bilgi için bkz: [form kimlik doğrulama sağlayıcısı](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Güvenlik Notu:** form kimlik doğrulaması kullandığınızda, varsayılan olarak, forms kimlik doğrulaması bileti içeren tanımlama bilgisi korunmuyorsa bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması. Hem kimlik doğrulama anahtarını hem de ilk oturum açma kimlik bilgilerini korumak için SSL kullanılmasını gerekli tutmayı dikkate almanız gerekir. <br /><br /> Forms kimlik doğrulaması ile nasıl kullanılacağına ilişkin bir örnek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], post bakın [form kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=200389) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisi.|  
|Beyana dayalı kimlik doğrulama|Talep tabanlı kimlik doğrulaması, kullanıcının kimliğini doğrulamak için bir güvenilen "üçüncü taraf" kimlik sağlayıcı hizmetine üzerinde veri hizmeti kullanır. Kimlik sağlayıcısı, veri hizmeti kaynaklarına erişmek isteyen kullanıcının kimliğini olumlu bir şekilde doğrular ve istenen kaynaklara erişim izni sağlayan bir belirteç verir. Bu belirteç, daha sonra veri hizmetine sunulur. Veri hizmeti, erişim belirtecini veren kimlik hizmetiyle kurulan güven ilişkisine göre kullanıcıya erişim sağlar.<br /><br /> Beyana dayalı kimlik doğrulama sağlayıcısı kullanmanın avantajı, güven etki alanları arasında çeşitli türden istemcilerin kimliğini doğrulamak için kullanılabilmeleridir. Veri hizmeti, böyle bir üçüncü taraf sağlayıcı kullanarak kullanıcıları koruma ve kimliklerini doğrulama gereksinimlerinden kurtulabilir. OAuth 2.0, hizmet olarak şirket dışı kimlik doğrulama için Microsoft Azure AppFabric Erişim Denetimi tarafından desteklenen beyana dayalı bir kimlik doğrulama protokolüdür. Bu protokol REST tabanlı hizmetleri destekler. OAuth 2.0 ile kullanma örneği için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], post bakın [OData ve OAuth](http://go.microsoft.com/fwlink/?LinkId=200514) içinde [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve kimlik doğrulama serisi.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>İstemci Kitaplığında kimlik doğrulama  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı için bir istek yaparken, kimlik bilgileri sağlamıyorsa bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmet. Olarak oturum açma kimlik bilgileri, bir kullanıcının kimliğini doğrulamak için veri hizmeti tarafından gerekliyse, bu kimlik bilgileri sağlanabilir bir <xref:System.Net.NetworkCredential> erişilen <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>, aşağıdaki örnekte olduğu gibi:  
  
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
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet isteği için istemci kimlik bilgilerini belirt](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Ne zaman veri hizmeti oturum açma kimlik bilgileri gerektiren belirtilemez kullanarak bir <xref:System.Net.NetworkCredential> nesne, bir belirteç talep tabanlı veya tanımlama bilgisi gibi el ile üstbilgileri HTTP istek genellikle ayarlamalısınız `Authorization` ve `Cookie` üstbilgileri. Post bu tür bir kimlik doğrulama senaryosu hakkında daha fazla bilgi için bkz: [OData ve kimlik doğrulaması: istemci tarafı Kancalarını](http://go.microsoft.com/fwlink/?LinkID=200385). İstek iletisinde HTTP üstbilgileri ayarlamak nasıl bir örnek için bkz: [nasıl yapılır: istemci isteğindeki üst bilgilerini ayarla](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Kimliğe bürünme  
 Genellikle veri hizmeti, veri hizmetini barındıran çalışan işleminin kimlik bilgilerini kullanarak sunucudaki veya veritabanındaki dosyalar gibi gerekli kaynaklara erişir. Kimliğe bürünme, kullanırken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar, istekte bulunan kullanıcının Windows kimliğini (kullanıcı hesabı) yürütebilir. Kimliğe bürünme, genel olarak kullanıcının kimliğini doğrulamak için IIS'den yararlanan uygulamalarda kullanılır ve gerekli kaynaklara erişmek için bu ilkenin kimlik bilgileri kullanılır. Daha fazla bilgi için bkz: [ASP.NET kimliğe bürünme](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Veri Hizmeti Yetkilendirmesini Yapılandırma  
 Yetkilendirme, uygulama kaynaklarının daha önce başarılı olan bir kimlik doğrulama temel alınarak belirlenen bir ilkeye veya işleme erişimini sağlamaktır. Genel bir uygulama olarak, yeterli hakları yalnızca istemci uygulamaları tarafından gerekli kılınan işlemleri gerçekleştirmek için veri hizmetinin kullanıcılarına vermeniz gerekir.  
  
### <a name="restrict-access-to-data-service-resources"></a>Veri Hizmeti Kaynaklarına Erişimi Kısıtlama  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ortak okuma ve yazma erişimi veri hizmeti kaynaklarına karşı vermenize olanak tanır (varlık kümesi ve hizmet işlemleri) veri hizmeti erişebiliyor herhangi bir kullanıcı için. Okuma ve yazma erişimini tanımlayan kurallar, veri hizmeti tarafından kullanılan ve hizmet işlemlerine sunulan her varlık kümesi için ayrı ayrı tanımlanabilir. Hem okuma hem de yazma erişimini yalnızca istemci uygulaması tarafından gerekli kılınan kaynaklarla sınırlamanızı öneririz. Daha fazla bilgi için bkz: [en az kaynak erişim gereksinimlerini](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Rol Tabanlı Kesiciler Uygulama  
 Kesiciler, istekleri veri hizmeti tarafından kullanılmadan önce veri hizmeti kaynaklarına karşı kesmenizi sağlar. Daha fazla bilgi için bkz: [dinleyiciler](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Kesiciler, isteği yapan kimliği doğrulanmış kullanıcıya göre yetkilendirme kararları vermenizi sağlar. Kimliği doğrulanmış kullanıcının kimliğine göre veri hizmeti kaynaklarına erişimi kısıtlamak nasıl bir örnek için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Kalıcı Veri Deposu ve Yerel Kaynaklara Erişimi Kısıtlama  
 Kalıcı depoya erişmek için kullanılan hesaplara, yalnızca veritabanı veya dosya sisteminde veri hizmetinin gereksinimlerini desteklemek için yeterli haklar verilmelidir. Bu, anonim kimlik doğrulama kullanıldığında barındırma uygulamasını çalıştırmak için kullanılan hesaptır. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Kimliğe bürünme kullanıldığında, kimliği doğrulanmış kullanıcıların genellikle Windows grubunun parçası olarak bu kaynaklara erişmesi sağlanmalıdır.  
  
## <a name="other-security-considerations"></a>Güvenlik Hakkında Diğer Önemli Noktalar  
  
### <a name="secure-the-data-in-the-payload"></a>Yükte Verileri Güvenli Hale Getirme  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] HTTP protokolünü temel alır. HTTP iletisinde, üstbilgi veri hizmeti tarafından uygulanan kimlik doğrulamaya bağlı olarak değerli kullanıcı kimlik bilgileri içerebilir. İleti gövdesi, korunması gereken değerli müşteri verileri de içerebilir. Her iki durumda da, bu bilgileri çevrimiçi olarak korumak için SSL'yi kullanmanızı öneririz.  
  
### <a name="ignored-message-headers-and-cookies"></a>Yoksayılan İleti Üstbilgileri ve Tanımlama Bilgileri  
 İçerik türleri ve kaynak konumları bildirenlerin dışındaki HTTP isteği üstbilgileri yoksayılır ve veri hizmeti tarafından hiçbir zaman ayarlanmaz.  
  
 Tanımlama bilgilerini bir kimlik doğrulama düzeni bir parçası olarak gibi birlikte kullanılabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] form kimlik doğrulaması. Ancak, bir gelen isteğe göre ayarlanmış hiçbir HTTP tanımlama bilgisi tarafından göz ardı edilir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Veri Hizmeti ana tanımlama bilgisi işleme ancak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çalışma zamanı hiçbir zaman çözümler veya tanımlama bilgilerini döndürür. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı da işlemez yanıt olarak gönderilen bir tanımlama bilgileri.  
  
### <a name="custom-hosting-requirements"></a>Özel Barındırma Gereksinimleri  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] olarak oluşturulan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS'de barındırılan uygulama. Bu, veri hizmetinin bu platformun güvenli davranışlarını kullanmasını sağlar. Tanımlayabileceğiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] özel bir ana bilgisayar tarafından barındırılır. Daha fazla bilgi için bkz: [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Veri hizmetini barındıran bileşenler ve platform, veri hizmetine yapılan saldırıları önlemek için aşağıdaki güvenlik davranışlarını sağlamalıdır:  
  
-   Olası tüm işlemler için veri hizmeti isteğinde kabul edilen URI'nin uzunluğunu sınırlama.  
  
-   Hem gelen hem de giden HTTP iletilerinin boyutunu sınırlama.  
  
-   Herhangi bir zamanda bekleyen isteklerin toplam sayısını sınırlama.  
  
-   HTTP üst bilgileri ve bunların değerleri boyutu sınırı ve sağlamak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] üstbilgi verilere erişim.  
  
-   TCP SYN ve ileti yeniden yürütme saldırıları gibi bilinen saldırıları algılama ve önleme.  
  
### <a name="values-are-not-further-encoded"></a>Değerler Daha Fazla Kodlanmaz  
 Veri hizmetine gönderilen özellik değerlerini daha fazla kodlanmamış tarafından [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çalışma zamanı. Örneğin, bir varlığın dize özelliği biçimlendirilmiş HTML içeriği içerdiğinde, etiketler veri hizmeti tarafından kodlanmış HTML değildir. Veri hizmeti yanıttaki özellik değerlerini de kodlamaz. İstemci Kitaplığı da ek kodlama gerçekleştirmez.  
  
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
