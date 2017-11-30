---
title: "Güvenlik genel bakış 1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
caps.latest.revision: "37"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74a2e5c15b25dc9958b74ddeb0abf9adcad10bc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a>Güvenlik Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir SOAP iletisi tabanlı dağıtılmış programlama platformudur ve istemcileri ve Hizmetleri arasındaki iletileri güvenli hale getirme verilerini korumak için önemlidir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]var olan güvenlik altyapısı ve SOAP iletilerine tanınan güvenlik standartları temel güvenli ileti değiş tokuşu için çok yönlü ve birlikte çalışabilir bir platform sağlar.  
  
> [!NOTE]
>  WCF güvenlik kapsamlı bir kılavuzu için bkz: [WCF Güvenlik Kılavuzu](http://go.microsoft.com/fwlink/?LinkID=158912).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik, veya kullanıcı adları ve parolalar kullanıcıların kimliklerini doğrulamak için güvenli, dağıtılmış uygulamaları HTTPS, Windows gibi mevcut teknolojiler ile oluşturulduysa bilginiz kullanır kavramları tümleşik. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]yalnızca var olan güvenlik altyapıları ile tümleşir ancak aynı zamanda yalnızca Windows etki alanları dışındaki dağıtılmış güvenlik güvenli SOAP iletileri kullanarak genişletir. Göz önünde bulundurun [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut güvenlik mekanizmaları uygulaması varolan protokolleri yanı sıra protokol olarak SOAP kullanmanın ana avantajı ile. Örneğin, bir istemci veya kullanıcı adı ve parola veya X.509 sertifikaları gibi bir hizmet tanımlayan kimlik bilgileri birlikte çalışabilir XML tabanlı SOAP profilleri sahip. Bu profilleri kullanarak iletileri güvenli bir şekilde XML dijital imzaları ve XML şifreleme gibi açık belirtimleri yararlanarak değiştirilir. Belirtimleri listesi için bkz: [Web Hizmetleri protokolleri desteklenen System-Provided birlikte kullanılabilirlik bağlamaları ile](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Başka bir paralel güvenli, dağıtılmış uygulamalar sağlayan Windows platformunda Bileşen Nesne Modeli (COM) olur. COM yapabildiği güvenlik bağlamı bileşenler arasında aktarılan bir kapsamlı bir güvenlik mekanizması vardır; Bu mekanizma bütünlüğü, gizlilik ve kimlik doğrulaması zorlar. COM platformlar arası etkinleştirmez ancak gibi Mesajlaşma güvenli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapar. Kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hizmetler ve Internet'te Windows etki alanlarından span istemcileri oluşturabilirsiniz. Birlikte çalışabilir iletilerinin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yardımcı yapı dinamik ve iş temelli Hizmetleri güvenlik bilgilerinizi emin eşitleyerek için gereklidir.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation güvenlik yararları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Dağıtılmış bir programlama platform SOAP iletilerde temel alır. Kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hizmetleri ve oluşturma ve diğer hizmetler ve istemcileri sınırsız sayıda gelen iletileri işleme hizmeti istemcileri, bu işlev uygulamalar oluşturabilirsiniz. Bu tür bir dağıtılmış uygulamada iletileri düğümden düğüme, çok sayıda SOAP aracılar ve Internet üzerinde bir güvenlik duvarı aracılığıyla akabilir. Bu ileti güvenlik tehditlerini çeşitli tanıtır. Aşağıdaki örnekler bazı göstermek ortak tehditler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik varlıklar arasında ileti alışverişi sırasında azaltmaya yardımcı olabilir:  
  
-   Gözlem hassas bilgileri almak için ağ trafiği. Örneğin, bir çevrimiçi bankacılık senaryoda bir istemci fon aktarımını bir hesaptan diğerine ister. Kötü niyetli bir kullanıcının ileti durdurur ve hesap numarası ve parola, daha sonra fon aktarımını güvenliği aşılan hesabından gerçekleştirir.  
  
-   Yanlış varlıklar Hizmetleri istemcisinin tanıma olmadan gibi davranır. Bu senaryoda, kötü niyetli bir kullanıcı (sahte) çevrimiçi bir hizmet olarak davranır ve hassas bilgileri almak için istemci iletilerini durdurur. Ardından dolandırıcı fon güvenliği aşılan hesabından aktarmak için çalınan verileri kullanır. Bu saldırı da bilinen bir *kimlik avı saldırı*.  
  
-   Hedeflenen çağıran daha farklı bir sonuç almak için iletileri değişikliğinin. Örneğin, teminat yapıldığı hesap numarası değiştiren bir dolandırıcı hesabınıza gitmek fon sağlar.  
  
-   Korsan yürütmelerini içinde zarar verici korsan aynı satın alma siparişi başlayarak yeniden oynatılır. Örneğin, bir çevrimiçi kitap siparişleri yüzlerce alır ve bunları sıralı olmayan bir müşteri için books gönderir.  
  
-   Bir istemci kimlik doğrulaması için bir hizmet bağlanamaması. Bu durumda, hizmet uygun kişi işlem gerçekleştirilen güvence altına almak olamaz.  
  
 Özet olarak, aşağıdaki çıkışların aktarımı güvenlik sağlar:  
  
-   Hizmet uç noktası (yanıtlayan) kimlik doğrulaması.  
  
-   İstemci asıl (Başlatıcı) kimlik doğrulaması.  
  
-   İleti bütünlüğü.  
  
-   İleti gizliliği.  
  
-   Yeniden yürütme algılaması.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Var olan güvenlik altyapısı ile tümleştirme  
 Genellikle, Web hizmeti dağıtımları mevcut güvenlik çözümlerini yerinde, örneğin, Güvenli Yuva Katmanı (SSL) veya Kerberos protokolü sahiptir. Bazı dağıtılmadıysa, bir güvenlik altyapısı Active Directory kullanarak Windows etki alanları gibi yararlanın. Genellikle, değerlendirme ve daha yeni olanları benimsenmesi mevcut teknolojiler ile tümleştirmek gereklidir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik varolan Aktarım güvenlik modelleri ile tümleşir ve SOAP iletisi güvenliği göre daha yeni aktarımı güvenlik modelleri için mevcut altyapısını yararlanabilirsiniz.  
  
### <a name="integration-with-existing-authentication-models"></a>Varolan kimlik doğrulama modelleri ile tümleştirme  
 Tüm iletişimi güvenlik modelinin önemli bir bölümü tanımlamak ve iletişim varlıklarda kimlik doğrulaması özelliği ' dir. Bu varlıklar iletişimde ile iletişim kuran eş doğrulatmak için "dijital kimlikleri" veya kimlik bilgilerini kullanın. Dağıtılmış iletişimi platformları gelişen gibi çeşitli kimlik bilgilerinin ve ilgili güvenlik modelleri uygulanmıştır. Örneğin, bir kullanıcı adı ve kullanıcıları tanımlamak için parola kullanımını Internet'te yaygındır. İntranet üzerindeki kullanıcı ve hizmet kimlik doğrulama yedeklemek için bir Kerberos etki alanı denetleyicisi kullanımını ortak durumundadır. Belirli senaryolarda, gibi iki iş ortakları arasında ortakları karşılıklı kimlik doğrulaması için sertifikaların kullanılması.  
  
 Bu nedenle, burada aynı hizmeti de dış iş ortakları için dahili Kurumsal müşteriler veya Internet müşterilere sunulan, dünyada Web hizmetleri altyapısı bu varolan güvenlik ile tümleştirme sağlamak önemlidir kimlik doğrulama modeller. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenlik kimlik bilgisi türlerinin (kimlik doğrulaması modeller) dahil olmak üzere çok çeşitli destekler:  
  
-   Anonim çağırıcı.  
  
-   Kullanıcı adı istemci kimlik bilgileri.  
  
-   Sertifika istemci kimlik bilgileri.  
  
-   Windows (Kerberos protokolü ve NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standartlar ve birlikte çalışabilirlik  
 Büyük varolan dağıtımları bir dünyada benzer olmasına nadir görülen bir durumdur. Dağıtılmış bilgi işlem/iletişimleri platformları farklı satıcılar teklif teknolojilerle birlikte çalışmanız gerekir. Benzer şekilde, güvenlik de birlikte çalışabilir olmalıdır.  
  
 Birlikte çalışabilir güvenlik sistemleri etkinleştirmek için şirketler Web Hizmetleri sektördeki etkin standartları çeşitli yazmış. Özellikle güvenlik ile ilgili birkaç önemli standartları önerilen: WS güvenliği: SOAP iletisi (OASIS standartları gövde tarafından kabul edilir ve önceden WS-güvenlik biliniyordu) güvenlik, WS-Trust, WS-SecureConversation ve WS-SecurityPolicy.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]çok çeşitli birlikte çalışabilirlik senaryoları destekler. <xref:System.ServiceModel.BasicHttpBinding> Sınıfı temel güvenlik profili (BSP) konumunda hedeflenen ve <xref:System.ServiceModel.WSHttpBinding> sınıfı, WS-güvenlik 1.1 ve WS-SecureConversation gibi en son güvenlik standartları hedeflenmiştir. Bu standartlar için uymak tarafından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik çalışmanız ve işletim sistemleri ve Microsoft Windows dışındaki platformları üzerinde barındırılan Web Hizmetleri ile tümleştirebilirsiniz.  
  
## <a name="wcf-security-functional-areas"></a>WCF güvenlik işlevsel  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik üç işlevsel alanlara bölünmüş: güvenlik, erişim denetimi ve denetim aktarın. Aşağıdaki bölümlerde kısaca bu alanları ele almaktadır ve daha fazla bilgi için bağlantılar sağlar.  
  
### <a name="transfer-security"></a>Güvenlik Aktarım  
 Aktarım güvenlik üç ana güvenlik işlevleri kapsar: bütünlüğü, gizlilik ve kimlik doğrulaması. *Bütünlük* bir ileti oynanmış olup olmadığını algılamak için yeteneği. *Gizlilik* bir ileti hedeflenen alıcı; dışındaki bir kişiye tarafından okunamaz tutmak yeteneği bu şifreleme sağlanır. *Kimlik doğrulama* talep edilen kimlik doğrulama yeteneği. Birlikte, bu üç işlevler iletileri güvenli bir noktadan diğerine ulaşmasını sağlamak için yardımcı olur.  
  
#### <a name="transport-and-message-security-modes"></a>Taşıma ve ileti güvenlik modları  
 Aktarım güvenlik uygulamak için kullanılan iki ana mekanizma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: *aktarım* güvenlik modu ve *ileti* güvenlik modu.  
  
-   *Aktarım güvenlik modu* aktarımı güvenliği sağlamak için bir aktarım düzeyi Protokolü HTTPS, örneğin kullanır. Aktarım modu benimsenen yaygın olarak birçok platformda bulunur ve daha az pkı'ya karmaşık olan avantajına sahiptir. Ancak, yalnızca noktadan noktaya gelen iletileri güvenli hale getirme dezavantajı vardır.  
  
-   *İleti güvenlik modu*, diğer yandan, WS-güvenlik kullanır (ve diğer belirtimleri) aktarımı güvenlik uygulamak. İleti güvenliği doğrudan SOAP iletilerine uygulanır ve uygulama verilerini birlikte SOAP Zarflar içindedir çünkü Aktarım Protokolü bağımsız, fazla genişletilebilir ve sağlayarak uçtan uca güvenlik olma avantajına sahiptir (Noktadan noktaya karşı); SOAP iletilerine XML yapısı ile mücadele etmek içerdiğinden Aktarım güvenlik modu birkaç kez daha yavaş olan dezavantajı vardır.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu farklılıklar bkz [güvenli hale getirme hizmetler ve istemcileri](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Üçüncü güvenlik modu önceki her iki mod kullanır ve her ikisi de avantajları beraberinde getirir. Bu mod adlı `TransportWithMessageCredential`. Bu modda, ileti güvenliği istemci kimlik doğrulaması için kullanılır ve taşıma güvenliği sunucunun kimliğini doğrulamak ve ileti gizliliği ve bütünlük sağlamak için kullanılır. Bu, sayesinde `TransportWithMessageCredential` güvenlik modu neredeyse Aktarım güvenlik modu gibi hızlı bir işlemdir ve istemci ile ileti güvenliği aynı şekilde kimlik doğrulaması genişletilebilirlik sağlar. Ancak, ileti güvenlik modu farklı olarak, tüm uçtan uca güvenlik sağlamaz.  
  
### <a name="access-control"></a>Erişim Denetimi  
 *Erişim denetimi* yetkilendirme olarak da bilinir. *Yetkilendirme* farklı kullanıcıların verileri görüntülemek için farklı ayrıcalıklara sahip olanak sağlar. Örneğin, bir şirketin İnsan Kaynakları dosyaları çalışanların hassas verileri içerdiğinden, yalnızca Yöneticiler çalışan verilerini görüntülemek için kullanılabilir. Ayrıca, yöneticileri doğrudan raporlarının yalnızca verilerini görüntüleyebilir. Bu durumda, erişim denetimi hem rolü ("Yöneticisi"), hem de belirli bir kimlik (bir yöneticiye başka bir yöneticinin çalışan kayıtları görünmesini önlemek için) Yöneticisi'ni temel alır.  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], erişim denetimi özellikleri, ortak dil çalışma zamanı (CLR) ile tümleştirme yoluyla sağlanan <xref:System.Security.Permissions.PrincipalPermissionAttribute> ve bir dizi olarak bilinen API aracılığıyla *kimlik modeli*. Erişim denetimi ve talep tabanlı yetkilendirme hakkında daha fazla ayrıntı için bkz: [genişletme güvenlik](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Denetim  
 *Denetim* Windows olay günlüğü için güvenlik olaylarının günlüğe kaydetme. Kimlik doğrulama hataları (veya başarıları) gibi güvenlikle ilgili olayları oturum açabilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programlama Ayrıntılar için bkz [nasıl yapılır: denetim güvenlik olaylarını](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Hizmetleri güvenli hale getirme](../../../../docs/framework/wcf/securing-services.md)  
 [Ortak Güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Bağlamalar ve güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Denetleme](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Güvenlik Kılavuzu ve en iyi yöntemler](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Yapılandırma dosyalarını kullanarak hizmetleri yapılandırma](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Sistem tarafından sağlanan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Uç noktası oluşturma genel bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Güvenliği genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
