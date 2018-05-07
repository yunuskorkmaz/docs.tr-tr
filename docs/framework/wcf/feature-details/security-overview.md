---
title: Güvenlik genel bakış 1
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6aff25547f02458d894de7235ecfb2f704d8664a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-overview"></a>Güvenlik Genel Bakış
Windows Communication Foundation (WCF) bir SOAP iletisi tabanlı dağıtılmış programlama platformudur ve istemcileri ve Hizmetleri arasındaki iletileri güvenli hale getirme verilerini korumak için önemlidir. WCF mevcut güvenlik altyapısı ve SOAP iletilerine tanınan güvenlik standartları temel güvenli ileti değiş tokuşu için çok yönlü ve birlikte çalışabilir bir platform sağlar.  
  
> [!NOTE]
>  WCF güvenlik kapsamlı bir kılavuzu için bkz: [WCF Güvenlik Kılavuzu](http://go.microsoft.com/fwlink/?LinkID=158912).  
  
 Güvenlik, veya kullanıcı adları ve parolalar kullanıcıların kimliklerini doğrulamak için güvenli, dağıtılmış uygulamaları HTTPS, Windows gibi mevcut teknolojiler ile oluşturulduysa bilginiz WCF kullanır kavramları tümleşik. WCF yalnızca var olan güvenlik altyapıları ile tümleşir ancak aynı zamanda yalnızca Windows etki alanları dışındaki dağıtılmış güvenlik güvenli SOAP iletileri kullanarak genişletir. WCF mevcut güvenlik mekanizmaları uygulaması varolan protokolleri yanı sıra protokol olarak SOAP kullanmanın ana avantajı ile göz önünde bulundurun. Örneğin, bir istemci veya kullanıcı adı ve parola veya X.509 sertifikaları gibi bir hizmet tanımlayan kimlik bilgileri birlikte çalışabilir XML tabanlı SOAP profilleri sahip. Bu profilleri kullanarak iletileri güvenli bir şekilde XML dijital imzaları ve XML şifreleme gibi açık belirtimleri yararlanarak değiştirilir. Belirtimleri listesi için bkz: [Web Hizmetleri protokolleri desteklenen System-Provided birlikte kullanılabilirlik bağlamaları ile](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Başka bir paralel güvenli, dağıtılmış uygulamalar sağlayan Windows platformunda Bileşen Nesne Modeli (COM) olur. COM yapabildiği güvenlik bağlamı bileşenler arasında aktarılan bir kapsamlı bir güvenlik mekanizması vardır; Bu mekanizma bütünlüğü, gizlilik ve kimlik doğrulaması zorlar. Ancak COM platformlar arası, WCF yaptığı gibi Mesajlaşma güvenli etkinleştirmez. WCF kullanarak, hizmetler ve Internet'te Windows etki alanlarından span istemcileri oluşturabilir. WCF birlikte çalışabilir iletileri yapı dinamik temeldir yardımcı iş temelli Hizmetleri güvenlik bilgilerinizi emin eşitleyerek.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation güvenlik yararları  
 WCF SOAP iletilerde temel dağıtılmış bir programlama platformudur. WCF kullanarak, hizmetleri ve oluşturma ve diğer hizmetler ve istemcileri sınırsız sayıda gelen iletileri işleme hizmeti istemcileri olarak uygulamalar bu işlev oluşturabilirsiniz. Bu tür bir dağıtılmış uygulamada iletileri düğümden düğüme, çok sayıda SOAP aracılar ve Internet üzerinde bir güvenlik duvarı aracılığıyla akabilir. Bu ileti güvenlik tehditlerini çeşitli tanıtır. Aşağıdaki örneklerde, WCF güvenlik varlıklar arasında ileti alışverişi sırasında azaltmaya yardımcı olabilecek bazı ortak tehditleri gösterilmektedir:  
  
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
  
 WCF güvenlik varolan Aktarım güvenlik modelleri ile tümleşir ve SOAP iletisi güvenliği göre daha yeni aktarımı güvenlik modelleri için mevcut altyapısını yararlanabilirsiniz.  
  
### <a name="integration-with-existing-authentication-models"></a>Varolan kimlik doğrulama modelleri ile tümleştirme  
 Tüm iletişimi güvenlik modelinin önemli bir bölümü tanımlamak ve iletişim varlıklarda kimlik doğrulaması özelliği ' dir. Bu varlıklar iletişimde ile iletişim kuran eş doğrulatmak için "dijital kimlikleri" veya kimlik bilgilerini kullanın. Dağıtılmış iletişimi platformları gelişen gibi çeşitli kimlik bilgilerinin ve ilgili güvenlik modelleri uygulanmıştır. Örneğin, bir kullanıcı adı ve kullanıcıları tanımlamak için parola kullanımını Internet'te yaygındır. İntranet üzerindeki kullanıcı ve hizmet kimlik doğrulama yedeklemek için bir Kerberos etki alanı denetleyicisi kullanımını ortak durumundadır. Belirli senaryolarda, gibi iki iş ortakları arasında ortakları karşılıklı kimlik doğrulaması için sertifikaların kullanılması.  
  
 Bu nedenle, burada aynı hizmeti de dış iş ortakları için dahili Kurumsal müşteriler veya Internet müşterilere sunulan, dünyada Web hizmetleri altyapısı bu varolan güvenlik ile tümleştirme sağlamak önemlidir kimlik doğrulama modeller. WCF güvenlik kimlik bilgisi türlerinin (kimlik doğrulaması modeller) dahil olmak üzere çok çeşitli destekler:  
  
-   Anonim çağırıcı.  
  
-   Kullanıcı adı istemci kimlik bilgileri.  
  
-   Sertifika istemci kimlik bilgileri.  
  
-   Windows (Kerberos protokolü ve NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standartlar ve birlikte çalışabilirlik  
 Büyük varolan dağıtımları bir dünyada benzer olmasına nadir görülen bir durumdur. Dağıtılmış bilgi işlem/iletişimleri platformları farklı satıcılar teklif teknolojilerle birlikte çalışmanız gerekir. Benzer şekilde, güvenlik de birlikte çalışabilir olmalıdır.  
  
 Birlikte çalışabilir güvenlik sistemleri etkinleştirmek için şirketler Web Hizmetleri sektördeki etkin standartları çeşitli yazmış. Özellikle güvenlik ile ilgili birkaç önemli standartları önerilen: WS güvenliği: SOAP iletisi (OASIS standartları gövde tarafından kabul edilir ve önceden WS-güvenlik biliniyordu) güvenlik, WS-Trust, WS-SecureConversation ve WS-SecurityPolicy.  
  
 WCF çok çeşitli birlikte çalışabilirlik senaryoları destekler. <xref:System.ServiceModel.BasicHttpBinding> Sınıfı temel güvenlik profili (BSP) konumunda hedeflenen ve <xref:System.ServiceModel.WSHttpBinding> sınıfı, WS-güvenlik 1.1 ve WS-SecureConversation gibi en son güvenlik standartları hedeflenmiştir. WCF güvenlik, bu standartlarına uygun olarak yüklemeyi çalışmanız ve işletim sistemleri ve Microsoft Windows dışındaki platformları üzerinde barındırılan Web Hizmetleri ile tümleştirebilirsiniz.  
  
## <a name="wcf-security-functional-areas"></a>WCF güvenlik işlevsel  
 WCF güvenlik üç işlevsel alanlara bölünmüş: güvenlik, erişim denetimi ve denetim aktarın. Aşağıdaki bölümlerde kısaca bu alanları ele almaktadır ve daha fazla bilgi için bağlantılar sağlar.  
  
### <a name="transfer-security"></a>Güvenlik Aktarım  
 Aktarım güvenlik üç ana güvenlik işlevleri kapsar: bütünlüğü, gizlilik ve kimlik doğrulaması. *Bütünlük* bir ileti oynanmış olup olmadığını algılamak için yeteneği. *Gizlilik* bir ileti hedeflenen alıcı; dışındaki bir kişiye tarafından okunamaz tutmak yeteneği bu şifreleme sağlanır. *Kimlik doğrulama* talep edilen kimlik doğrulama yeteneği. Birlikte, bu üç işlevler iletileri güvenli bir noktadan diğerine ulaşmasını sağlamak için yardımcı olur.  
  
#### <a name="transport-and-message-security-modes"></a>Taşıma ve ileti güvenlik modları  
 İki ana mekanizma aktarımı güvenlik WCF'de uygulamak için kullanılır: *aktarım* güvenlik modu ve *ileti* güvenlik modu.  
  
-   *Aktarım güvenlik modu* aktarımı güvenliği sağlamak için bir aktarım düzeyi Protokolü HTTPS, örneğin kullanır. Aktarım modu benimsenen yaygın olarak birçok platformda bulunur ve daha az pkı'ya karmaşık olan avantajına sahiptir. Ancak, yalnızca noktadan noktaya gelen iletileri güvenli hale getirme dezavantajı vardır.  
  
-   *İleti güvenlik modu*, diğer yandan, WS-güvenlik kullanır (ve diğer belirtimleri) aktarımı güvenlik uygulamak. İleti güvenliği doğrudan SOAP iletilerine uygulanır ve uygulama verilerini birlikte SOAP Zarflar içindedir çünkü Aktarım Protokolü bağımsız, fazla genişletilebilir ve sağlayarak uçtan uca güvenlik olma avantajına sahiptir (Noktadan noktaya karşı); SOAP iletilerine XML yapısı ile mücadele etmek içerdiğinden Aktarım güvenlik modu birkaç kez daha yavaş olan dezavantajı vardır.  
  
 Bu farklılıklar hakkında daha fazla bilgi için bkz: [güvenli hale getirme hizmetler ve istemcileri](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Üçüncü güvenlik modu önceki her iki mod kullanır ve her ikisi de avantajları beraberinde getirir. Bu mod adlı `TransportWithMessageCredential`. Bu modda, ileti güvenliği istemci kimlik doğrulaması için kullanılır ve taşıma güvenliği sunucunun kimliğini doğrulamak ve ileti gizliliği ve bütünlük sağlamak için kullanılır. Bu, sayesinde `TransportWithMessageCredential` güvenlik modu neredeyse Aktarım güvenlik modu gibi hızlı bir işlemdir ve istemci ile ileti güvenliği aynı şekilde kimlik doğrulaması genişletilebilirlik sağlar. Ancak, ileti güvenlik modu farklı olarak, tüm uçtan uca güvenlik sağlamaz.  
  
### <a name="access-control"></a>Erişim Denetimi  
 *Erişim denetimi* yetkilendirme olarak da bilinir. *Yetkilendirme* farklı kullanıcıların verileri görüntülemek için farklı ayrıcalıklara sahip olanak sağlar. Örneğin, bir şirketin İnsan Kaynakları dosyaları çalışanların hassas verileri içerdiğinden, yalnızca Yöneticiler çalışan verilerini görüntülemek için kullanılabilir. Ayrıca, yöneticileri doğrudan raporlarının yalnızca verilerini görüntüleyebilir. Bu durumda, erişim denetimi hem rolü ("Yöneticisi"), hem de belirli bir kimlik (bir yöneticiye başka bir yöneticinin çalışan kayıtları görünmesini önlemek için) Yöneticisi'ni temel alır.  
  
 Ortak dil çalışma zamanı (CLR) ile tümleştirme yoluyla sağlanan içinde WCF, erişim denetim özellikleri <xref:System.Security.Permissions.PrincipalPermissionAttribute> ve bir dizi olarak bilinen API aracılığıyla *kimlik modeli*. Erişim denetimi ve talep tabanlı yetkilendirme hakkında daha fazla ayrıntı için bkz: [genişletme güvenlik](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Denetim  
 *Denetim* Windows olay günlüğü için güvenlik olaylarının günlüğe kaydetme. Kimlik doğrulama hataları (veya başarıları) gibi güvenlikle ilgili olayları oturum açabilir. Daha fazla bilgi için bkz: [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programlama Ayrıntılar için bkz [nasıl yapılır: denetim güvenlik olaylarını](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Hizmetleri Güvenli Hale Getirme](../../../../docs/framework/wcf/securing-services.md)  
 [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Federasyon ve Verilen Belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Güvenlik Kılavuzu ve En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
