---
title: "Talep tabanlı kimlik modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a96a9af-d980-43be-bf91-341a23401431
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: f675f75d6dfd51b5259748316864048562ee0452
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="claims-based-identity-model"></a>Talep tabanlı kimlik modeli
Talep kullanan uygulamalar oluştururken, kullanıcı kimliği uygulamanızda talepler kümesi olarak temsil edilir. Bir talep kullanıcının adını olabilir, başka bir e-posta adresi olabilir. Bunun ardında yatan fikir, bir dış kimlik sisteminin uygulamanıza yaptığı her istekle kullanıcı hakkında bilmesi gereken her şeyi ve aldığınız verilerin güvenilir bir kaynaktan geldiğine dair şifreleme güvencesini sağlayacak şekilde yapılandırılmış olmasıdır.  
  
 Bu modelde, çoklu oturum açma daha kolay bir şekilde gerçekleştirilir ve uygulamanız artık aşağıdakilerden sorumlu olmaz:  
  
-   Kullanıcıların kimliğini doğrulama.  
  
-   Kullanıcı hesaplarını ve parolalarını depolama.  
  
-   Kullanıcı kimliği ayrıntılarını bulmak için kurumsal dizinleri çağırma.  
  
-   Diğer platformlardaki veya şirketlerdeki kimlik sistemleriyle tümleşme.  
  
 Bu modelde, uygulamanız kullanıcınızın kimliğini doğrulayan sistem tarafından sağlanan taleplere göre kimlikle ilgili kararlar verir. Bu, kullanıcının adıyla basit uygulama kişiselleştirmesinden kullanıcıyı uygulamanızdaki daha değerli özelliklere ve kaynaklara erişmek için yetkilendirmeye kadar her şey olabilir.  
  
 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:  
  
-   [Talep tabanlı kimlik giriş](../../../docs/framework/security/claims-based-identity-model.md#BKMK_1)  
  
-   [Talep tabanlı kimlik modeli için temel senaryosu](../../../docs/framework/security/claims-based-identity-model.md#BKMK_2)  
  
<a name="BKMK_1"></a>   
## <a name="introduction-to-claims-based-identity"></a>Beyana Dayalı Kimliğe Giriş  
 Aşağıdaki terimler ve kavramlar, kimlik için bu yeni mimariyi anlamanıza yardımcı olabilir.  
  
### <a name="identity"></a>Kimlik  
 Windows Identity Foundation (WIF) programlama modeli açıklayan amacıyla, bir kullanıcı veya başka bir varlık korumak istediğiniz bir sistemde açıklayan öznitelikler kümesi temsil etmek için "kimlik" terimi kullanacağız.  
  
### <a name="claim"></a>Talep  
 Talep kimlik bilgilerini adı, e-posta adresi, geçerlilik süresi, Satış rolü üyeliği gibi bir parçası olarak düşünün. Uygulamanız ne kadar çok talep alırsa, kullanıcınız hakkında o kadar çok bilginiz olur. Neden bu kurumsal dizinleri tanımlamak için sık kullanılan olarak "öznitelikleri" yerine "talepler," denir merak ediyor olabilirsiniz. Bunun dağıtım yöntemiyle bir ilgisi yoktur. Bu modelde, uygulamanız bir dizinde kullanıcı özniteliklerini aramaz. Bunun yerine, kullanıcı talepleri uygulamanıza dağıtır ve uygulamanız bunları inceler. Her talep veren kişi tarafından yapılır ve talebe veren kişiye güvendiğiniz kadar güvenirsiniz. Örneğin, şirketinizin etki alanı denetleyicisi tarafından yapılan bir talebe kullanıcının kendisi tarafından yapılan bir talebe göre daha fazla güvenirsiniz. WIF içeren talepleri temsil eden bir <xref:System.Security.Claims.Claim> olan türü, bir <xref:System.Security.Claims.Claim.Issuer%2A> kimin Talep veren çıkışı bulmak izin veren özellik.  
  
### <a name="security-token"></a>Güvenlik Belirteci  
 Kullanıcı uygulamanıza istekle birlikte talepler kümesi dağıtır. Web hizmetinde, bu talepler SOAP zarfının güvenlik üstbilgisinde taşınır. Tarayıcı tabanlı bir Web uygulamasında, talepler kullanıcının tarayıcısından HTTP POST ile gelir ve oturum istenirse daha sonra tanımlama bilgisinde önbelleğe alınabilir. Bu talepler, nasıl geldiklerine bakılmaksızın güvenlik belirteçlerinin geldiği yerde seri hale getirilmelidir. Bir güvenlik belirteci, veren yetkili tarafından dijital olarak imzalanan seri hale getirilmiş bir talepler kümesidir. İmza önemlidir: kullanıcının yalnızca birkaç talep oluşturup size göndermediğinden emin olmanızı sağlar. Şifrelemenin gerekli olmadığı veya istenmediği düşük güvenlik düzeyine sahip durumlarda, imzalanmamış belirteçler kullanabilirsiniz, ancak bu senaryo bu konuda açıklanmamaktadır.  
  
 WIF'deki temel özelliklerden biri de güvenlik belirteçleri oluşturma ve okumadır. WIF ve .NET Framework şifreleme işinin tamamını gerçekleştirir ve uygulamanıza okuyabileceğiniz bir talepler kümesi sağlar.  
  
### <a name="issuing-authority"></a>Veren Yetkili  
 Kerberos anahtarları veren etki alanı denetleyicilerinden X.509 sertifikaları veren sertifika yetkililerine kadar çok sayıda farklı türden veren yetkili vardır, ancak bu konuda bahsedilen yetkili türü talep içeren güvenlik belirteçleri verir. Bu veren yetkili, güvenlik belirteçlerinin nasıl verileceğini bilen bir Web uygulaması veya Web hizmetidir. Hedef bağlı tarafı ve talepte bulunan kullanıcıyı göz önünde bulundurarak uygun talepleri verebilmek için yeterli bilgiye sahip olmalıdır ve talepleri aramak ve kullanıcıların kimliğini doğrulamak için kullanıcı depolarıyla etkileşim kurmaktan sorumlu olabilir.  
  
 Hangi veren yetkiliyi seçerseniz seçin, kimlik çözümünüzde temel bir rol oynar. Taleplere dayanarak uygulamanızdan kimlik doğrulamayı çıkardığınızda, sorumluluğu bu yetkiliye verirsiniz ve ondan sizin adınıza kullanıcıların kimliğini doğrulamasını istersiniz.  
  
### <a name="security-token-service-sts"></a>Güvenlik Belirteci Hizmeti (STS)  
 Güvenlik belirteci hizmeti (STS), WS-Güven ve WS-Federasyon protokollerine göre güvenlik belirteçleri oluşturan, imzalayan ve veren hizmet bileşenidir. Bu protokollerin uygulanması için yapılan birçok iş vardır, ancak WIF bunların tümünü sizin için yaparak protokollerde uzman olmayan bir kişinin STS'yi çok az bir çabayla çalışır duruma getirmesini sağlar. Önceden oluşturulmuş bir STS gibi kullanabilir [Active Directory® Federasyon Hizmetleri (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516), bulut STS gibi bir [Microsoft Azure erişim denetimi Hizmeti'nden (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517), veya özel belirteçleri veya sağlamak istiyorsanız Özel kimlik doğrulama veya yetkilendirme, WIF kullanarak kendi özel STS oluşturabilirsiniz. WIF, kendi STS'nizi oluşturmanızı kolaylaştırır.  
  
### <a name="relying-party-application"></a>Bağlı Taraf Uygulaması  
 Taleplere dayalı bir uygulama oluşturduğunuzda, bağlı taraf (RP) uygulaması oluşturursunuz. Bir RP için eş anlamlı sözcükleri "talep kullanan uygulama" ve "Talep tabanlı uygulama" içerir. Hem Web uygulamaları ve hem de Web hizmetleri RP olabilir. RP uygulaması, STS tarafından verilen belirteçleri kullanır ve talepleri kimlikle ilgili görevler için kullanmak üzere belirteçlerden ayıklar. WIF, RP uygulamaları oluşturmanıza yardımcı olacak işlevler sunar.  
  
### <a name="standards"></a>Standartlar  
 Bunların tümünü birlikte kullanılabilir hale getirmek için önceki senaryoda birkaç WS-* standardı kullanılır. İlke WS-MetadataExchange kullanarak alınır ve WS-Policy belirtimine göre yapılandırılır. STS, güvenlik belirteçlerinin nasıl isteneceğini ve alınacağını açıklayan WS-Güven belirtimini uygulayan uç noktalarını kullanır. Günümüzde Çoğu STS, Güvenlik Onaylama İşlemi Biçimlendirme Dili (SAML) ile biçimlendirilen belirteçler verir. SAML, talepleri birlikte çalışabilir bir şekilde temsil etmek için kullanılabilen sektörde tanınmış bir XML sözlüğüdür. Veya çok platformlu bir durumda bu, STS ile veya tamamen farklı bir platformla iletişim kurmanızı ve platform ne olursa olsun tüm uygulamalarınız arasında çoklu oturum açma gerçekleştirmenizi sağlar.  
  
### <a name="browser-based-applications"></a>Tarayıcı Tabanlı Uygulamalar  
 Beyana dayalı kimlik modelini yalnızca akıllı istemciler kullanmazlar. Tarayıcı tabanlı uygulamalar (edilgen istemciler de denir) kullanabilir. Aşağıdaki senaryoda bunun nasıl çalıştığı anlatılmaktadır:  
  
 İlk olarak, kullanıcı talep kullanan bir Web uygulamasında (bağlı taraf uygulaması) bir tarayıcıyı işaret eder. Web uygulaması, kullanıcının kimliğinin doğrulanabilmesi için tarayıcıyı STS'ye yönlendirir. STS gelen isteği okuyan basit bir web uygulamasında barındırılır, standart HTTP mekanizmaları kullanarak kullanıcının kimliğini doğrular ve ardından SAML belirteci oluşturup tarayıcının SAML belirtecini RP'ye geri gönderen bir HTTP POST başlatmasına neden olan JavaScript kodu ile değiştirir. Bu POST'un gövdesi, RP'nin istediği talepleri içerir. Bu noktada, kullanıcının her istekte yeniden yönlendirilmemesi için RP'nin talepleri bir tanımla bilgisinde paketlemesi normaldir.  
  
<a name="BKMK_2"></a>   
## <a name="basic-scenario-for-a-claims-based-identity-model"></a>Beyana Dayalı Kimlik Modeli için Temel Senaryo  
 Aşağıdaki bir beyana dayalı sistem örneğidir.  
  
 ![Bağlı olan iş ortağı kimlik doğrulaması akışı](../../../docs/framework/security/media/conc-relying-partner-processc.png "conc_relying_partner_processc")  
  
 Bu diyagram, kimlik doğrulama için WIF ve bu siteyi kullanmak isteyen bir istemci olarak web tarayıcısı kullanacak şekilde yapılandırılmış bir Web sitesini (bağlı taraf uygulaması, RP) göstermektedir.  
  
1.  Kimliği doğrulanmamış bir kullanıcı bir sayfa istediğinde, tarayıcısı kimlik sağlayıcısı (IP) sayfalarına yönlendirilir.  
  
2.  IP, kullanıcının kullanıcı adı/parola, Kerberos gibi kimlik bilgilerini sağlamasını gerektirir.  
  
3.  IP, tarayıcıya döndürülen bir belirteç verir.  
  
4.  Tarayıcı, artık başlangıçta istenen sayfaya geri yönlendirilir. Burada WIF, belirtecin sayfaya erişim gereksinimlerini karşılayıp karşılamadığını belirler. Karşılıyorsa, kimlik doğrulamanın yalnızca bir kez gerçekleşmesini ve denetimin uygulamaya geçirilmesini sağlamak üzere bir oturum oluşturmak için bir tanımlama bilgisi verilir.
