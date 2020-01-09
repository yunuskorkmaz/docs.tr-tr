---
title: Güvenlik Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 58057709e2d5c5e34d0aa37158ea9b033840f840
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344699"
---
# <a name="windows-communication-foundation-security-overview"></a>Windows Communication Foundation güvenliğe genel bakış
Windows Communication Foundation (WCF), bir SOAP ileti tabanlı dağıtılmış programlama platformudur ve istemciler ve hizmetler arasındaki iletilerin güvenliğini korumak için gereklidir. WCF, hem mevcut güvenlik altyapısına hem de SOAP iletileri için tanınan güvenlik standartlarına dayalı olarak güvenli iletiler değiş tokuş eden, çok yönlü ve birlikte çalışabilen bir platform sağlar.  
  
> [!NOTE]
> WCF güvenliğine yönelik kapsamlı bir kılavuz için bkz. [WCF güvenlik kılavuzu](https://go.microsoft.com/fwlink/?LinkID=158912).  
  
 WCF, kullanıcıların kimliğini doğrulamak için HTTPS, Windows tümleşik güvenliği veya Kullanıcı adları ve parolalar gibi mevcut teknolojiler ile güvenli, dağıtılmış uygulamalar oluşturduysanız tanıdık kavramları kullanır. WCF yalnızca mevcut güvenlik altyapılarından tümleştirilemez, ancak güvenli SOAP iletileri kullanarak yalnızca Windows etki alanlarının ötesinde dağıtılmış güvenliği de genişletir. Var olan protokollerin yanı sıra protokol olarak SOAP kullanmanın önemli avantajlarından yararlanarak mevcut güvenlik mekanizmalarının bir uygulamasını WCF olarak değerlendirin. Örneğin, Kullanıcı adı ve parola veya X. 509.440 sertifikaları gibi bir istemciyi veya hizmeti tanımlayan kimlik bilgileri, birlikte çalışabilen XML tabanlı SOAP profillerine sahiptir. Bu profiller kullanılarak iletiler, XML dijital imzaları ve XML şifrelemesi gibi açık belirtimlerden yararlanarak güvenli bir şekilde değiştirilir. Belirtimlerin listesi için, bkz. [sistem tarafından sunulan birlikte çalışabilirlik bağlamaları tarafından desteklenen Web Hizmetleri protokolleri](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Diğer bir paralel, Windows platformunda güvenli, dağıtılmış uygulamalar sağlayan bileşen nesne modeli (COM) ' dir. COM, güvenlik bağlamının bileşenler arasında akışını yapabildiği kapsamlı bir güvenlik mekanizmasına sahiptir; Bu mekanizma bütünlük, gizlilik ve kimlik doğrulamayı zorlar. Ancak COM platformlar arası, WCF gibi güvenli mesajlaşma 'yı etkinleştirmez. WCF kullanarak, Internet üzerinden Windows etki alanlarından yayılan hizmetler ve istemciler oluşturabilirsiniz. Birlikte çalışabilen WCF iletileri, bilgilerinizin güvenliğine güvenmenizi sağlamanıza yardımcı olan dinamik ve iş odaklı hizmetler oluşturmak için gereklidir.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation güvenlik avantajları  
 WCF, SOAP iletilerini temel alan dağıtılmış bir programlama platformudur. WCF kullanarak her iki hizmet ve hizmet istemcisi olarak işlev gösteren uygulamalar oluşturabilir, sınırsız sayıda diğer hizmet ve istemciden ileti oluşturup bunları silebilirsiniz. Bu tür dağıtılmış bir uygulamada, iletiler düğümden düğüme, güvenlik duvarları, Internet üzerinden ve çok sayıda SOAP aracı üzerinden akabilir. Bu, çeşitli ileti güvenliği tehditleri sunar. Aşağıdaki örneklerde, varlıklar arasında ileti alışverişi yaparken WCF güvenliğinin azaltılmasına yardımcı olabilecek bazı genel tehditler gösterilmektedir:  
  
- Hassas bilgileri almak için ağ trafiğinin gözlemi. Örneğin, bir çevrimiçi bankacılık senaryosunda istemci, fonların bir hesaptan diğerine aktarılmasını ister. Kötü niyetli bir kullanıcı iletiyi keser ve hesap numarasına ve parolaya sahip olacak şekilde, daha sonra güvenliği aşılmış hesaptan fon aktarımı gerçekleştirir.  
  
- İstemci farkında olmadan hizmet olarak davranan standart dışı varlıklar. Bu senaryoda, kötü niyetli bir Kullanıcı (Standart dışı) bir çevrimiçi hizmet olarak çalışır ve hassas bilgileri almak için istemciden iletileri keser. Ardından, yanlış çalışan hesaptan fonları aktarmak için çalınmış verileri kullanır. Bu saldırıya bir *sızdırma saldırısı*da denir.  
  
- Çağıranın hedefinden farklı bir sonuç elde etmek için iletilerin değişikliği. Örneğin, bir depozito 'nin yaptığı hesap numarasını değiştirmek fonların bir standart dışı hesaba gitmesini sağlar.  
  
- Bilgisayar korsanının aynı satın alma siparişini yeniden oynadığı korsan yeniden oynatılır. Örneğin, çevrimiçi bir kitaplığı yüzlerce sipariş alır ve kitapları, siparişi olmayan bir müşteriye gönderir.  
  
- İstemcinin kimliğini doğrulamak için bir hizmetin olmaması. Bu durumda, hizmet uygun kişinin işlemi gerçekleştirmesinden emin olamaz.  
  
 Özet olarak, aktarım güvenliği aşağıdaki hedefleri sağlar:  
  
- Hizmet uç noktası (yanıtlayanın) kimlik doğrulaması.  
  
- İstemci sorumlusu (Başlatıcı) kimlik doğrulaması.  
  
- İleti bütünlüğü.  
  
- İleti gizliliği.  
  
- Yeniden yürütme algılaması.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Mevcut güvenlik altyapılarından tümleştirme  
 Genellikle, Web hizmeti dağıtımları için mevcut güvenlik çözümleri (örneğin, Güvenli Yuva Katmanı (SSL) veya Kerberos protokolü) vardır. Windows etki alanları gibi Active Directory kullanarak daha önce dağıtılmış bir güvenlik altyapısından yararlanın. Bu, genellikle yeni olanları değerlendirirken ve benimseirken bu mevcut teknolojilerle tümleştirilecek.  
  
 WCF güvenliği, mevcut aktarım güvenliği modelleriyle tümleştirilir ve SOAP iletisi güvenliğine göre daha yeni aktarım güvenlik modelleri için mevcut altyapıdan yararlanabilir.  
  
### <a name="integration-with-existing-authentication-models"></a>Mevcut kimlik doğrulama modelleriyle tümleştirme  
 İletişim güvenlik modelinin önemli bir bölümü, iletişimdeki varlıkları tanımlamak ve kimliklerini doğrulamak için kullanılır. İletişim içindeki bu varlıklar, iletişim meslektaşlarıyla kimlik doğrulaması yapmak için "Dijital kimlikler" veya kimlik bilgileri kullanır. Dağıtılmış iletişim platformları geliştirilmesinin yanı sıra çeşitli kimlik bilgileri kimlik doğrulaması ve ilgili güvenlik modelleri uygulanmıştır. Örneğin, Internet 'te kullanıcıları tanımlamak için Kullanıcı adı ve parola kullanımı yaygındır. İntranette, Kullanıcı ve hizmet kimlik doğrulamasını yedeklemek için bir Kerberos etki alanı denetleyicisinin kullanılması yaygın hale geliyor. İki iş ortağı gibi bazı senaryolarda, sertifikalar, iş ortaklarının birbirini karşılıklı olarak doğrulanması için kullanılabilir.  
  
 Bu nedenle, Web Hizmetleri dünyasında aynı hizmetin dahili kurumsal müşterilere ve dış iş ortaklarına veya Internet müşterilerine sunulabileceği durumlarda, altyapının bu mevcut güvenlikle tümleştirme sağlaması önemlidir kimlik doğrulama modelleri. WCF güvenliği, aşağıdakiler dahil olmak üzere çok çeşitli kimlik bilgisi türlerini (kimlik doğrulama modelleri) destekler:  
  
- Anonim arayan.  
  
- Kullanıcı adı istemci kimlik bilgileri.  
  
- Sertifika istemci kimlik bilgileri.  
  
- Windows (hem Kerberos protokolü hem de NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standartlar ve birlikte çalışabilirlik  
 Mevcut büyük dağıtımlara sahip bir dünyada, hogenelik nadir bir durumdur. Dağıtılmış bilgi işlem/iletişim platformları, farklı satıcıların sunduğu teknolojiyle birlikte çalışmalıdır. Benzer şekilde, güvenliğin de birlikte kullanılabilmelidir.  
  
 Birlikte çalışabilen güvenlik sistemlerini etkinleştirmek için, Web hizmetleri sektöründe etkin olan şirketler çeşitli standartlar yazdı. Özellikle güvenlikle ilgili olarak, bazı önemli standartlar önerilmiştir: WS-Security: SOAP Iletisi güvenliği (OASSıS standartları gövdesi tarafından kabul edilir ve eski adıyla WS-Security), WS-Trust, WS-SecureConversation ve WS-SecurityPolicy.  
  
 WCF, çok sayıda birlikte çalışabilirlik senaryosunu destekler. <xref:System.ServiceModel.BasicHttpBinding> sınıfı temel güvenlik profiline (BSP) yöneliktir ve <xref:System.ServiceModel.WSHttpBinding> sınıfı WS-Security 1,1 ve WS-SecureConversation gibi en son güvenlik standartlarına yöneliktir. WCF güvenliği, bu standartlara uygun olarak, Microsoft Windows dışındaki işletim sistemlerinde ve platformlarda barındırılan Web Hizmetleri ile birlikte çalışabilir ve tümleştirilebilir.  
  
## <a name="wcf-security-functional-areas"></a>WCF güvenlik Işlevsel bölgeleri  
 WCF güvenliği üç işlevsel alana ayrılmıştır: aktarım güvenliği, erişim denetimi ve denetim. Aşağıdaki bölümler, bu bölümleri kısaca ele alır ve daha fazla bilgi için bağlantılar sağlar.  
  
### <a name="transfer-security"></a>Güvenlik aktarma  
 Aktarım güvenliği üç önemli güvenlik işlevini kapsar: bütünlük, gizlilik ve kimlik doğrulama. *Bütünlük* , bir iletinin değiştirilip değiştirilmediğini tespit etme olanağıdır. *Gizlilik* , bir iletiyi amaçlanan alıcı dışında bir kişi tarafından okunamaz halde tutma olanağıdır; Bu, şifreleme üzerinden sağlanır. *Kimlik doğrulama* , istenen bir kimliği doğrulama yeteneğidir. Bu üç işlev birlikte, iletilerin bir noktadan diğerine güvenli bir şekilde ulaşmasını sağlamaya yardımcı olur.  
  
#### <a name="transport-and-message-security-modes"></a>Aktarım ve Ileti güvenliği modları  
 WCF 'de aktarım güvenliği uygulamak için iki ana mekanizma kullanılır: *Aktarım* güvenliği modu ve *ileti* güvenlik modu.  
  
- Aktarım *güvenliği modu* , aktarım güvenliğini sağlamak için https gibi bir aktarım düzeyi protokolü kullanır. Aktarım modu, çok sayıda platformda sunulan ve daha az hesaplama avantajına sahiptir. Ancak, iletilerin yalnızca noktadan noktaya güvenli hale getirilmesi olumsuz bir dezavantajı vardır.  
  
- Diğer yandan *ileti güvenliği modu*, aktarım güvenliği uygulamak için WS-Security (ve diğer belirtimleri) kullanır. İleti güvenliği doğrudan SOAP iletilerine uygulandığından ve SOAP zarfların içinde, uygulama verileriyle birlikte bulunduğundan, Aktarım Protokolü 'nün bağımsız, daha genişletilebilir ve uçtan uca güvenlik sağlama avantajına sahiptir. (noktadan noktaya karşılık); SOAP iletilerinin XML doğası ile uğraşmak gerektiğinden, aktarım güvenliği modundan birkaç kat daha yavaştır.  
  
 Bu farklılıklar hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Üçüncü bir güvenlik modu, önceki modlarını kullanır ve her ikisinin de avantajını getirir. Bu moda `TransportWithMessageCredential`denir. Bu modda, istemci kimliğini doğrulamak için ileti güvenliği kullanılır ve sunucunun kimliğini doğrulamak ve ileti gizliliği ve bütünlüğü sağlamak için aktarım güvenliği kullanılır. Bunun için, `TransportWithMessageCredential` güvenlik modu neredeyse aktarım güvenliği modu kadar hızlıdır ve ileti güvenliği ile aynı şekilde istemci kimlik doğrulaması genişletilebilirliği sağlar. Ancak, ileti güvenliği modunun aksine, uçtan uca tam güvenlik sağlamaz.  
  
### <a name="access-control"></a>Erişim Denetimi  
 *Erişim denetimi* de yetkilendirme olarak bilinir. *Yetkilendirme* , farklı kullanıcıların verileri görüntülemek için farklı ayrıcalıklara sahip olmasına izin verir. Örneğin, bir şirketin insan kaynakları dosyaları gizli çalışan verileri içerdiğinden, yalnızca yöneticilerin çalışan verilerini görüntülemesine izin verilir. Ayrıca, Yöneticiler yalnızca kendi raporlarının verilerini görüntüleyebilir. Bu durumda, erişim denetimi hem role ("Manager") hem de yöneticinin özel kimliğini (bir yöneticinin başka bir yöneticinin çalışan kayıtlarına bakmasını engellemek için) temel alır.  
  
 WCF 'de, erişim denetimi özellikleri, ortak dil çalışma zamanı (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> ve *kimlik modeli*olarak bilinen bir API kümesi ile tümleştirme yoluyla sağlanır. Erişim denetimi ve talep tabanlı yetkilendirme hakkında daha fazla bilgi için bkz. [güvenliği genişletme](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Denetim  
 *Denetim* , güvenlik olaylarının Windows olay günlüğüne kaydedilmesini sağlar. Kimlik doğrulama arızaları (veya başarıları) gibi güvenlikle ilgili olayları günlüğe kaydedebilirsiniz. Daha fazla bilgi için bkz. [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programlama ayrıntıları için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
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
- [Windows Server App Fabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
