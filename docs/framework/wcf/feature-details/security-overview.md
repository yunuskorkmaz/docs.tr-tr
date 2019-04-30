---
title: Güvenlik Overview1
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 94f1284e864bc63c321e004ac4a20843b191711d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748544"
---
# <a name="security-overview"></a>Güvenlik Genel Bakış
Windows Communication Foundation (WCF) bir SOAP ileti tabanlı dağıtılmış programlama platformudur ve istemciler ve hizmetler arasında iletileri güvenli hale getirme verileri korumak için gereklidir. WCF güvenlik altyapınız hem SOAP iletilerini tanınan güvenlik standartlarını temel güvenli ileti değişimi için verimli ve birlikte çalışabilen bir platform sağlar.  
  
> [!NOTE]
>  WCF güvenlik kapsamlı bir kılavuz için bkz: [WCF Güvenlik Kılavuzu](https://go.microsoft.com/fwlink/?LinkID=158912).  
  
 Oluşturduysanız, güvenli ve dağıtılmış uygulamalar HTTPS, Windows gibi mevcut teknolojileri ile ilgili bilgi sahibi olduğunuz WCF kullanan kavramları, güvenlik veya kullanıcı adları ve parolalar, kullanıcıların kimliklerini doğrulamak için tümleşik. WCF yalnızca var olan güvenlik altyapıları ile tümleştirilir, ancak güvenli SOAP iletileri kullanarak dağıtılmış güvenlik yalnızca Windows etki alanları da genişletir. WCF güvenlik mekanizmalar uygulaması SOAP protokolü mevcut protokolleri ek olarak kullanmanın ana avantajı ile göz önünde bulundurun. Örneğin, bir istemci veya kullanıcı adı ve parola veya X.509 sertifikaları gibi bir hizmet tanımlayan kimlik bilgileri birlikte çalışabilen SOAP XML tabanlı profilleri sahip. Bu profilleri kullanarak iletileri güvenli bir şekilde XML dijital imzalar ve XML şifreleme gibi açık belirtimleri avantajlarından yararlanarak değiştirilir. Belirtimleri listesi için bkz. [Web Hizmetleri protokolleri desteklenen System-Provided birlikte kullanılabilirlik bağlamaları ile](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Başka bir paralel güvenli, dağıtılmış uygulamaları etkinleştiren Windows platformunda Bileşen Nesne Modeli (COM) olur. COM bileşenleri arasında güvenlik bağlamı ile geçirilebilir bir kapsamlı bir güvenlik mekanizması vardır; Bu mekanizma, kimlik doğrulaması bütünlüğü ve gizliliği zorlar. Ancak COM platformlar arası, WCF gibi Mesajlaşma güvenli etkinleştirmez. WCF kullanarak, hizmetler ve istemcileri Internet üzerinden Windows etki alanlarından yayılan oluşturabilirsiniz. WCF birlikte çalışabilen iletileri dinamik derleme için gerekli olan yardımcı olmak ve iş temelli Hizmetleri Güvenlik bilgilerinizin kalacağından.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation güvenlik avantajları  
 WCF SOAP iletileri göre dağıtılmış bir programlama platformudur. WCF kullanarak, hem hizmet hem de oluşturma ve diğer hizmetler ve istemcileri, sınırsız sayıda gelen iletileri işleme hizmeti istemcileri olarak uygulamalar bu işlev oluşturabilirsiniz. Böyle bir dağıtılmış uygulamada iletileri düğümden düğüme, Internet üzerinde bir güvenlik duvarı aracılığıyla ve çok sayıda SOAP aracıları üzerinden akabilir. Bu ileti güvenlik tehditlerini çeşitli tanıtır. Aşağıdaki örnekler, WCF güvenlik varlıklar arasında mesaj alışverişleri sırasında azaltmaya yardımcı olabilecek bazı yaygın tehditleri gösterir:  
  
- Gözlem hassas bilgileri almak için ağ trafiği. Örneğin, bir çevrimiçi bankacılık senaryoda bir istemci para aktarımı bir hesaptan diğerine ister. Kötü niyetli bir kullanıcı iletisi durdurur ve, parola ve hesap numarası sahip daha sonra para aktarımını güvenliği aşılmış hesabından gerçekleştirir.  
  
- Hizmetler olmadan istemcinin tanıma gibi davranan düzenleyen varlıklar. Bu senaryoda, kötü niyetli bir kullanıcı (sahte) çevrimiçi bir hizmet olarak çalışır ve hassas bilgileri almak için istemci iletileri durdurur. Ardından sahte çalınan veri güvenliği aşılmış hesaptan para aktarımı için kullanır. Bu saldırı da bilinen bir *avı kurbanı*.  
  
- Birçok özelliğe iletileri hedeflenen arayan değerinden farklı bir sonuç elde edilir. Örneğin, bir havale yapıldığı hesap numarası değiştirme için bir dolandırıcı hesabı gitmek fon sağlar.  
  
- Korsanın olumsuzlukları sıkıntı korsanın aynı satınalma siparişi yeniden yürütür. Örneğin, bir çevrimiçi kitaplığı siparişler yüzlerce alıp bunları sıralı olmayan bir müşteri için books gönderir.  
  
- Bir istemcinin kimliğini doğrulamak için bir hizmet yükleyememesine. Bu durumda, hizmet uygun kişi işlem gerçekleştirilen sağlanması olamaz.  
  
 Özet olarak, aşağıdaki Güvenceleri aktarım güvenliği sağlar:  
  
- Hizmet uç noktası (yanıtlayan) kimlik doğrulaması.  
  
- İstemci (Başlatıcı) asıl kimlik doğrulaması.  
  
- İleti bütünlüğü.  
  
- İleti gizliliği.  
  
- Yeniden yürütme algılaması.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Mevcut güvenlik altyapıları ile tümleştirme  
 Genellikle, Web hizmeti dağıtımları yerinde, örneğin, Güvenli Yuva Katmanı (SSL) veya Kerberos protokolü mevcut güvenlik çözümleri sahiptir. Bazı zaten dağıtılmış olan bir güvenlik altyapısı Active Directory kullanarak Windows etki alanı gibi yararlanın. Genellikle, değerlendirme ve yeni olanlara benimseme bu mevcut teknolojileri ile tümleştirme gereklidir.  
  
 WCF güvenlik mevcut aktarım güvenliği modelleriyle tümleştirilebiliyor ve SOAP ileti güvenliği dayalı yeni Aktarım güvenlik modelleri için var olan altyapıdan yararlanıyor.  
  
### <a name="integration-with-existing-authentication-models"></a>Mevcut kimlik doğrulaması modelleri ile tümleştirme  
 Tüm iletişimi güvenlik modelinin önemli bir parçası tanımlamak ve iletişim varlıklarda kimlik doğrulaması özelliği ' dir. Bu varlıkların iletişim ile iletişim kuran eşleri doğrulatmak için "sayısal kimlikleri" veya kimlik bilgilerini kullanın. Dağıtılmış iletişim platformları gelişerek gibi çeşitli kimlik bilgilerinin ve ilgili güvenlik modelleri uygulanmıştır. Örneğin, Internet'te, bir kullanıcı adı ve parola, kullanıcıları tanımlamak için kullanımı yaygındır. İntranet üzerindeki kullanıcı ve hizmet kimlik doğrulaması yedeklemek için bir Kerberos etki alanı denetleyicisi kullanımı yaygın hale gelmektedir. Belirli senaryolarda gibi iki iş ortakları arasında sertifikaları iş ortakları karşılıklı kimlik doğrulaması için kullanılabilir.  
  
 Bu nedenle, burada aynı hizmet dış iş ortakları için de dahili kurumsal müşterilere veya Internet müşterilere açık olabileceği, dünyasında Web Hizmetleri bu mevcut güvenlik ile tümleştirme için olan altyapının sağlanması önemlidir kimlik doğrulaması modelleri. WCF güvenlik kimlik bilgisi türlerinin (kimlik doğrulaması modelleri) dahil olmak üzere çok çeşitli destekler:  
  
- Arayan anonim.  
  
- Kullanıcı adının istemci kimlik bilgileri.  
  
- Sertifika istemci kimlik bilgileri.  
  
- Windows (Kerberos protokolü ve NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standartlar ve birlikte çalışabilirlik  
 Var olan büyük dağıtımları ile bir dünyada, homojenlik ilkesinden nadir olarak rastlanıyor. Farklı satıcıların teklif teknolojileri ile çalışmak dağıtılmış bilgi işlem/iletişimleri platformları gerekir. Benzer şekilde, güvenlik de birlikte çalışabilir olmalıdır.  
  
 Birlikte çalışabilen güvenlik sistemleri etkinleştirmek için şirket Web Hizmetleri sektörün etkin standartları çeşitli oluşturdunuz. Özellikle güvenlik ile ilgili birkaç önemli standartları önerilen: WS-güvenlik: SOAP ileti güvenliği (OASIS standartları gövdesi kabul edilir ve daha önce WS-güvenlik bilinen), WS-Trust, WS-SecureConversation ve WS-SecurityPolicy.  
  
 WCF çok çeşitli birlikte çalışabilirlik senaryolarında destekler. <xref:System.ServiceModel.BasicHttpBinding> Sınıfı, temel güvenlik profili (BSP) adresindeki hedeflediği ve <xref:System.ServiceModel.WSHttpBinding> sınıfı, WS-güvenlik 1.1 ve WS-SecureConversation gibi en son güvenlik standartları hedeflenmiştir. WCF güvenlik, bu standartlara uygun olarak çalışmak ve işletim sistemleri ve Microsoft Windows dışındaki platformları üzerinde barındırılan Web Hizmetleri ile tümleştirin.  
  
## <a name="wcf-security-functional-areas"></a>WCF güvenlik işlevsel alanları  
 WCF güvenlik üç işlevsel alanlara bölünmüş: güvenlik, erişim denetimi ve denetim aktarın. Aşağıdaki bölümlerde, kısa bir süre bu alanlar tartışın ve daha fazla bilgi için bağlantılar sağlar.  
  
### <a name="transfer-security"></a>Aktarım güvenliği  
 Aktarım güvenliği üç önemli güvenlik işlevleri kapsar: kimlik doğrulaması bütünlüğü ve gizliliği. *Bütünlük* bir ileti ile oynanmış olup olmadığını algılamak için olanağıdır. *Gizlilik* bir ileti hedeflenen alıcı; dışındaki hiç kimse tarafından okunamaz tutmak yeteneği bu şifreleme sağlanır. *Kimlik doğrulaması* talep kimliğini doğrulamak için olanağıdır. Birlikte, bu üç işlev iletileri güvenli bir noktadan başka birine ulaşmasını sağlamak için yardımcı olur.  
  
#### <a name="transport-and-message-security-modes"></a>Taşıma ve ileti güvenlik modu  
 WCF'de aktarım güvenliği uygulamak için kullanılan iki ana mekanizma: *aktarım* güvenlik modu ve *ileti* güvenlik modu.  
  
- *Transport güvenlik modunu* HTTPS gibi bir aktarım düzeyi protokolü, aktarım güvenliği sağlamak için kullanır. Aktarım modu, yaygın olarak benimsenen, birçok platformda bulunur ve hesaplama açısından daha az karmaşık olan avantajına sahiptir. Bununla birlikte, yalnızca, noktadan noktaya gelen iletileri güvenli hale getirme dezavantajı vardır.  
  
- *İleti güvenlik modunu*, diğer yandan, WS-güvenlik kullanır (ve diğer özellikleri) aktarım güvenliği uygulamak için. İleti güvenliği SOAP iletileri doğrudan uygulanır ve uygulama verilerini birlikte SOAP Zarf içinde yer alan çünkü Aktarım Protokolü bağımsız, daha genişletilebilir ve kalmasını sağlama uçtan uca güvenlik olan avantajı vardır. (Noktadan noktaya karşı); SOAP iletilerini XML yapısı ile dağıtılacak olduğundan transport güvenlik modunu birkaç kez daha yavaş olan olumsuz var.  
  
 Bu farklılıklar hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Üçüncü bir güvenlik modu, önceki her iki mod kullanır ve her ikisi de avantajları getirir. Bu modu olarak adlandırılır `TransportWithMessageCredential`. Bu modda, ileti güvenliği istemcinin kimliğini doğrulamak için kullanılır ve aktarım güvenliği, ileti gizliliği ve bütünlüğü sağlamak ve sunucunun kimliğini doğrulamak için kullanılır. Bu, sayesinde `TransportWithMessageCredential` güvenlik modu neredeyse transport güvenlik modunu olabildiğince hızlı ve istemci ile ileti güvenliği aynı şekilde kimlik doğrulaması genişletilebilirlik sağlar. Ancak, ileti güvenlik modunu, tam uçtan uca güvenlik sağlamaz.  
  
### <a name="access-control"></a>Erişim Denetimi  
 *Erişim denetimi* de yetkilendirme denir. *Yetkilendirme* farklı kullanıcıların verileri görüntülemek için farklı ayrıcalıklara sahip olanak tanır. Örneğin, bir şirketin İnsan Kaynakları dosyaları çalışanların hassas verileri içerdiğinden, yalnızca Yöneticiler çalışan verilerini görüntülemek için izin verilir. Ayrıca, yöneticileri doğrudan raporlarının yalnızca verileri görüntüleyebilirsiniz. Bu durumda, erişim denetimi hem ' % s'rolü ("Yönetici"), hem de belirli bir kimlik (başka bir yöneticinin çalışan kayıtları bakarak bir yöneticiye önlemek için) Yöneticisi'ni temel alır.  
  
 WCF'de, ortak dil çalışma zamanı (CLR) ile tümleştirme yoluyla erişim denetimi özellikleri sağlanır <xref:System.Security.Permissions.PrincipalPermissionAttribute> ve bir dizi olarak bilinen bir API aracılığıyla *kimlik modeli*. Erişim denetimi ve beyana dayalı yetkilendirme hakkında daha fazla ayrıntı için bkz: [genişletme güvenlik](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Denetim  
 *Denetim* Windows olay günlüğüne güvenlik olayları günlüğe kaydetme işlemi. Kimlik doğrulama hataları (veya başarılar) gibi güvenlikle ilgili olayları oturum açabilirsiniz. Daha fazla bilgi için [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programlama için bilgi [nasıl yapılır: Güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Hizmetleri Güvenli Hale Getirme](../../../../docs/framework/wcf/securing-services.md)
- [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Doğrulaması](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
- [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Federasyon ve Verilen Belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Güvenlik Kılavuzu ve En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
