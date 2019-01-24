---
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: ea3ff1e8ec4234e75b937cfef81b55bb8f71fa12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683979"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation Gizlilik Bilgileri
Microsoft, son kullanıcılar gizlilik korumayı taahhüt eder. Sürüm 3.0, Windows Communication Foundation (WCF) kullanarak bir uygulamayı derlerken, uygulamanızı kullanıcılarınıza gizlilik etkileyebilir. Örneğin, uygulamanızın açıkça kullanıcı bilgilerini toplayabilir veya istek veya Web sitenize Internet üzerinden bilgi göndermek olabilir. Uygulamanızda Microsoft teknolojisini eklemek, bu teknoloji gizlilik etkileyebilecek kendi davranışını olabilir. Sizin veya son kullanıcı seçmediğiniz sürece farklı bize göndermek WCF bilgileri Microsoft'a uygulamanızdan göndermez.  
  
## <a name="wcf-in-brief"></a>WCF kısaca  
 WCF, dağıtılmış uygulamalar oluşturmalarını sağlayan bir Microsoft .NET Framework kullanarak dağıtılmış bir Mesajlaşma çerçevedir. İki uygulama arasında iletileri üstbilgi ve gövde bilgileri içerir.  
  
 İleti yönlendirme, güvenlik bilgileri, işlemlerin ve uygulama tarafından kullanılan hizmetlere bağlı olarak daha fazla üst bilgiler içerebilir. İletileri, genellikle varsayılan olarak şifrelenir. Kullanıldığında bir özel durum `BasicHttpBinding`, hangi güvenli olmayan, eski Web Hizmetleri ile kullanılmak üzere tasarlanmıştır. Uygulama Tasarımcısı nihai tasarımı için sorumlu olursunuz. İletiler SOAP'daki, uygulamaya özgü verileri içerir; Ancak, bu veriler, uygulama tanımlı kişisel bilgiler gibi WCF şifreleme veya gizliliği özelliklerini kullanarak güvenliği sağlanabilir. Aşağıdaki bölümlerde, büyük olasılıkla gizliliği etkileyen özellikleri açıklanmaktadır.  
  
## <a name="messaging"></a>İleti  
 Her WCF ileti belirten bir ileti hedef adres üstbilgisi sahiptir ve yanıt nereye.  
  
 Uç nokta tanımlayan bir Tekdüzen Kaynak Tanımlayıcısı (URI), bir uç nokta adresi adresi bileşenidir. Adresi, bir ağ adresi veya mantıksal bir adres olabilir. Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir. Uç nokta adresini bir genel benzersiz tanıtıcısı (GUID) de içerebilir veya geçici adresleme GUID'lerini koleksiyonu her adresi ayrım için kullanılır. Her ileti bir ileti kimliği bir GUID içerir. Bu özellik, WS-Addressing başvuru standart izler.  
  
 WCF ileti katmanı herhangi bir kişisel bilgi yerel makineye yazmaz. Bir hizmet geliştirici (örneğin, bir kişinin adını kullanarak bir uç nokta adı veya göre uç noktanın Web kişisel bilgiler dahil olmak üzere bu tür bilgiler sunan bir hizmet oluşturduysanız ancak bunu kişisel bilgileri ağ düzeyinde yay Açıklama Dili ancak istemcilerin WSDL erişmek için https kullanmasını gerektirmeyen Hizmetleri). Ayrıca, bir geliştirici çalıştırıyorsa [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kişisel bilgiler, Aracı'nın çıkış kullanıma sunduğu bir uç nokta aracı, bu bilgileri içerebilir ve çıktı dosyasına yazılır yerel sabit disk.  
  
## <a name="hosting"></a>Barındırma  
 Wcf'de barındırma özellik uygulamalarını isteğe bağlı olarak Başlat veya birden çok uygulama arasında bağlantı noktası paylaşma olanağı sağlar. WCF uygulaması, Internet Information Services (IIS), benzer şekilde barındırılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Barındırma belirli bilgilere ağda kullanıma sunmuyor ve makinede verileri korumaz.  
  
## <a name="message-security"></a>İleti Güvenliği  
 WCF güvenlik Mesajlaşma uygulamaları için güvenlik olanaklarını sağlar. Kimlik doğrulama ve yetkilendirme sağlanan güvenlik işlevlerini içerir.  
  
 Kimlik doğrulaması, istemciler ve hizmetler arasında kimlik bilgilerini geçirerek gerçekleştirilir. Kimlik doğrulaması aktarım düzeyi güvenlik ile aşağıdakilerden biri olması veya SOAP ileti güvenlik gibi düzeyi:  
  
-   SOAP ileti güvenliğinde, kimlik doğrulama kullanıcı adı/parola, X.509 sertifikaları, Kerberos biletleri ve her biri, dağıtımcı bağlı olarak kişisel bilgiler içerebilir, SAML belirteçlerini gibi kimlik bilgileri aracılığıyla gerçekleştirilir.  
  
-   Aktarım güvenliği kullanarak, HTTP kimlik doğrulama düzenleri gibi geleneksel aktarım kimlik doğrulama mekanizmaları kimlik doğrulaması yapılır (temel, Digest, Negotiate, tümleşik Windows kimlik doğrulaması, None, NTLM ve anonim) ve form kimlik doğrulaması.  
  
 Kimlik doğrulaması iletişim uç noktaları arasında kurulan güvenli oturum neden olabilir. Oturum, güvenlik oturumu ömrünü süren bir GUID ile tanımlanır. Aşağıdaki tabloda neler tutulur gösterir ve burada.  
  
|Veri|Depolama|  
|----------|-------------|  
|Kullanıcı adı, X.509 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerini başvurular gibi sunu kimlik.|Windows kimlik bilgisi yönetimi mekanizmalarını Windows sertifika deposu gibi.|  
|Kullanıcı adları ve parolalar gibi kullanıcı üyelik bilgileri.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Üyelik sağlayıcısı.|  
|İstemci hizmetinin kimliğini doğrulamak için kullanılan hizmet kimlik bilgilerini.|Hizmet uç noktası adresi.|  
|Arayan bilgileri.|Denetim günlükleri.|  
  
## <a name="auditing"></a>Denetim  
 Denetim başarılı ve başarısız kimlik doğrulama ve yetkilendirme olayları kaydeder. Denetim kayıtları aşağıdaki verileri içerir: hizmet URI'si, eylemi URI'si ve arayanın kimliği.  
  
 Ayrıca denetim iletileri günlüğe kaydetme, üst bilgiler ve gövdeleri uygulamaya özgü verileri oturum açabilir çünkü zaman yönetici (bunu açma veya kapatma) ileti günlük kaydı yapılandırmasını değiştirir kaydeder. İçin [!INCLUDE[wxp](../../../includes/wxp-md.md)], bir kaydı uygulama olay günlüğüne kaydedilir. İçin [!INCLUDE[wv](../../../includes/wv-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], bir kayıt güvenlik olay günlüğüne kaydedilir.  
  
## <a name="transactions"></a>İşlemler  
 İşlem özelliği, bir WCF uygulaması işlem hizmetleri sağlar.  
  
 İşlem yayma kullanılan işlem üst işlem kimliği veya guıd'lerdir kaydı kimlikleri içerebilir.  
  
 İşlem özelliği, işlem durumu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem yöneticisi (bir Windows bileşeni) kullanır. Varsayılan olarak, işlem yöneticileri arasındaki iletişimler şifrelenir. Uç nokta başvuruları, işlem kimlikleri ve liste işlem yöneticileri durumlarını kalıcı bir parçası olarak oturum açabilir. Bu durum ömrünü İşlem Yöneticisi'nin günlük dosyası ömrünü tarafından belirlenir. MSDTC hizmetinin sahibi ve bu günlüğünü tutar.  
  
 İşlem özellik WS-düzenleme ve WS-Atomic işlem standartlarını uygular.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Taşıma veya Ara hatalar oluştuğunda güvenilir oturumları wcf'de ileti aktarımını sağlar. Sağladıkları bir tam olarak-temel alınan aktarımda (örneğin, kablosuz ağ üzerinde bir TCP bağlantı) bağlantısını keser veya bir ileti (bir HTTP Proxy'si giden veya gelen bir ileti bırakılıyor) kaybeder olsa bile bir kez iletileri aktarmak. Güvenilir oturumlar da iletisi (çoklu yol yönlendirmesi olması durumunda gerçekleşebilir gibi), iletiler, gönderilen sıralamasını korur yeniden sıralama kurtarın.  
  
 Güvenilir oturumlar WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır. Bunlar, belirli bir güvenilir oturum ile ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üst bilgileri ekleyin. Her WS-RM oturumu bir GUID olan bir tanımlayıcı vardır.  
  
 Herhangi bir kişisel bilgi son kullanıcı makinesinde korunur.  
  
## <a name="queued-channels"></a>Sıraya alınan kanallar  
 Kuyruklar, alıcı uygulamanın adına bir gönderen uygulamayı iletileri depolamak ve daha sonra bu alıcı uygulamasına iletileri iletebilir. Bunlar, örneğin, alıcı uygulamanın geçici olduğunda, alıcı uygulamaların Gönderen uygulamalardan ileti aktarımını sağlanmasına yardımcı olur. WCF aktarım olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma için destek sağlar.  
  
 Sıraya alınan kanalları özellik üst bilgiler iletiye eklemez. Bunun yerine, uygun Message Queuing iletisi özellikleri kümesi ile bir Message Queuing iletisi oluşturur ve ileti Message Queuing sırasına koymak için Message Queuing yöntemleri çağırır. Message Queuing, Windows ile birlikte gelen bir isteğe bağlı bir bileşendir.  
  
 Message Queuing sıraya alma altyapısı kullandığı için hiçbir bilgi kuyruğa alınmış kanalları özelliğiyle son kullanıcı makinesinde tutulmaz.  
  
## <a name="com-integration"></a>COM+ Tümleştirme  
 Bu özellik, WCF hizmetleri ile uyumlu olan hizmetleri oluşturmak için mevcut COM ve COM + işlevi sarmalar. Bu özellik belirli üst bilgiler kullanmayan ve son kullanıcının makinedeki veriler korunmaz.  
  
## <a name="com-service-moniker"></a>COM hizmet bilinen adı  
 Bu, standart bir WCF istemcisi için yönetilmeyen bir sarmalayıcı sağlar. Bu özellik, kablo özel üst bilgiler yok ya da makinedeki veriler devam etmez.  
  
## <a name="peer-channel"></a>Eş Kanal  
 Eş kanal WCF kullanarak misyonumuz uygulamaların geliştirilmesini sağlar. Misyonumuz Mesajlaşma kafes bağlamında gerçekleşir. Kafes düğümleri katılabilir bir ad tarafından tanımlanır. Eş kanal içindeki her bir düğümün bir kullanıcı tarafından belirtilen bağlantı noktası TCP dinleyicisi oluşturur ve diğer düğümleri dayanıklılık sağlamak için ağ bağlantı kurar. Kafes diğer düğümlere bağlanmak için düğümleri de dinleyici adresi ve makinenin IP adresleri, diğer düğümlerle ağ dahil olmak üzere bazı veriler, exchange. Geçici ağ içinde gönderilen iletileri göndereni kurcalama ve ileti kimlik sahtekarlığı önlemek için ilgili güvenlik bilgileri içerebilir.  
  
 Herhangi bir kişisel bilgi, son kullanıcının makinede depolanır.  
  
## <a name="it-professional-experience"></a>BT Uzmanı deneyimi  
  
### <a name="tracing"></a>İzleme  
 WCF altyapısının tanılama özelliği, taşıma ve hizmet modeli katmanları ve etkinlikleri ve bu iletileri ile ilişkili olayları geçişine iletileri günlüğe kaydeder. Bu özellik varsayılan olarak kapalıdır. Uygulamanın yapılandırma dosyası kullanılarak etkinleştirilir ve izleme davranışı, çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir. Etkinleştirildiğinde, izleme altyapısına iletileri, etkinlikleri ve olayları işlemeyi yapılandırılmış dinleyicilerine içeren bir Tanılama izleme yayar. Çıktı konumunu ve biçim yöneticinin dinleyici yapılandırma seçeneklerine göre belirlenir, ancak genellikle bir XML biçimli dosyasıdır. Yönetici, izleme dosyaları üzerinde erişim denetim listesi (ACL) ayarlamaktan sorumludur. Özellikle, Windows etkinleştirme sistem (WAS) tarafından barındırıldığında, yönetici dosyaları ortak sanal kök dizininden sunulur, bu fırça istenen değilse değil emin olmanız gerekir.  
  
 İzlemenin iki tür vardır: İleti günlüğe kaydetme ve tanılama hizmet modeli, izleme, aşağıdaki bölümde açıklanan. Her kendi izleme kaynağı yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel>. Bu günlük izleme kaynakları her iki uygulamada yerel olarak veri yakalayın.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti izleme kaynağı günlüğe kaydetme (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) sistemi üzerinden akan iletilerini günlüğe kaydetmek için bir yöneticinin sağlar. Yapılandırma yoluyla, kullanıcının tüm iletileri veya yalnızca ileti üstbilgileri, aktarımı ve/veya hizmet modeli katmanına kaydedilip edilmeyeceğini ve yanlış biçimlendirilmiş iletiler eklenip eklenmeyeceğini oturum karar verebilirsiniz. Ayrıca, kullanıcının hangi iletilerin kaydedilip kısıtlamak için filtreleme yapılandırabilirsiniz.  
  
 Varsayılan olarak, ileti günlüğe kaydetmeyi devre dışıdır. Yerel Makine Yöneticisi oturum açma ileti uygulama düzeyi yönetici önleyebilir.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Şifrelenmiş ve şifresi çözülen ileti günlüğe kaydetme  
 İletileri günlüğe, şifrelenmiş veya şifresi aşağıdaki koşulları'nda açıklanan şekilde.  
  
 Günlük aktarma  
 Taşıma düzeyinde gönderilen ve alınan iletileri günlüğe kaydeder. Bu iletiler, tüm üst bilgilerini içeren ve kablo ve alınan olduğunda gönderilmeden önce şifrelenmelidir.  
  
 İletileri kablo gönderilmeden önce şifrelenir ve alındığında, oturum de şifrelenir. Bir güvenlik protokolü (https) kullanılan olduğunda, bir özel durumdur: Bunlar gönderilmeden önce sonra bile kablo şifrelenmiş alınan şifresi ardından kaydedilir.  
  
 Hizmet günlüğü  
 Hemen önce ve kullanıcı kodu girdikten sonra kanal üst bilgi işlem gerçekleştikten sonra hizmet modeli düzeyinde gönderilen veya alınan iletileri günlüğe kaydeder.  
  
 Güvenli ve kablo şifrelenmiş olsa bile bu düzeyde günlüğe ileti şifresi çözülür.  
  
 Hatalı biçimlendirilmiş ileti günlüğe kaydetme  
 WCF altyapısı anlamak veya işleyemiyor iletileri günlüğe kaydeder.  
  
 İletileri halinde günlüğe kaydedilir-diğer bir deyişle, şifrelenmiş olup  
  
 İletileri günlüğe kaydedildiğinde şifresi çözülmüş veya şifrelenmemiş form, varsayılan olarak WCF güvenlik anahtarları ve büyük olasılıkla kişisel bilgi gelen iletileri açmadan önce kaldırır. Hangi bilgilerin kaldırılır, sonraki bölümlerde açıklamak ve ne zaman. Makine Yöneticisi ve uygulama dağıtıcı hem gerçekleştirmeniz gereken belirli yapılandırma eylemleri, anahtarları ve olası kişisel bilgileri günlüğe kaydetmek için varsayılan davranışı değiştirmek için.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Bilgi iletisi üst bilgiler şifresi çözülür ve şifrelenmemiş iletileri günlüğe kaydedilirken kaldırıldı  
 Ne zaman şifresi çözülür ve şifrelenmemiş formunda güvenlik anahtarları iletileri günlüğe kaydedilir ve büyük olasılıkla kişisel bilgi kaldırıldığına varsayılan ileti üstbilgileri ve İleti gövdeleri önce günlüğe kaydedilir. Aşağıdaki liste, WCF anahtarları ve büyük olasılıkla kişisel bilgi dikkate gösterir.  
  
 Kaldırılan anahtarları:  
  
 \- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 WST:Entropy  
  
 \- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:nonce  
  
 Kaldırılır, olası kişisel bilgileri:  
  
 \- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:  
  
 \<onaylama  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 Onaylama kimliği = "[ID]"  
  
 Veren = "[string]"  
  
 IssueInstant="[dateTime]"  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition >  
  
 \<Hedef kitle > [URI]\</Audience > +  
  
 \</ AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition />*  
  
 <\!--soyut temel tür  
  
 \<Koşul / > *  
  
 -->  
  
 \</ Koşulları >?  
  
 \<Öneri >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > *  
  
 \<Onaylama işlemi > [onaylama]\</Assertion > *  
  
 [any] *  
  
 \</ Öneri >?  
  
 <\!--Soyut taban türleri  
  
 \<Deyimi / > *  
  
 \<SubjectStatement >  
  
 \<Konu >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyURI]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [any]\</SubjectConfirmationData >?  
  
 \<DS:KeyInfo >... \</ds:KeyInfo >?  
  
 \</ SubjectConfirmation >?  
  
 \</ Konu >  
  
 \</ SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod = "[URI]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 [Konu]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind="[QName]"  
  
 Konumu = "[URI]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</ AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Konu]  
  
 \<Özniteliği  
  
 AttributeName = "[string]"  
  
 AttributeNamespace = "[URI]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</ Öznitelik > +  
  
 \</ AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Kaynak = "[URI]"  
  
 Karar = "[izin&#124;Reddet&#124;belirsiz]"  
  
 >  
  
 [Konu]  
  
 \<Eylem Namespace = "[URI]" > [string] \< /eylem > +  
  
 \<Kanıt >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > +  
  
 \<Onaylama işlemi > [onaylama]\</Assertion > +  
  
 \</ Kanıt >?  
  
 \</ AuthorizationDecisionStatement > *  
  
 \</ Onaylama >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Bilgi iletileri şifresi çözülür ve şifrelenmemiş açarken İleti gövdeleri kaldırıldı  
 Daha önce açıklandığı gibi WCF kaldırır anahtarları ve bilinen olası kişisel bilgileri günlüğe kaydedilen iletilere şifresi çözülür ve şifrelenmemiş ileti üstbilgileri. Ayrıca, WCF anahtarları ve bilinen olası kişisel bilgileri gövdesi öğeleri ve anahtar değişimi içinde yer alan güvenlik iletileri açıklayan eylemleri aşağıdaki listede, İleti gövdeleri kaldırır.  
  
 Aşağıdaki ad alanları için:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (örneğin, hiçbir eylem varsa kullanılabilir)  
  
 Bilgiler, anahtar değişimi içeren bu gövdesi öğeler için kaldırılır:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Bilgi de aşağıdaki eylemlerin her birine kaldırılır:  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Hiçbir bilgi uygulamaya özgü üstbilgi ve gövde verilerini kaldırılır.  
 WCF uygulamaya özel üst bilgiler (örneğin, sorgu dizeleri) veya gövde verilerini (örneğin, kredi kartı numarası) kişisel bilgiler izlemez.  
  
 Günlüğe ileti kaydetme açık olduğunda, uygulamaya özgü üst bilgilerinde kişisel bilgileri ve gövde bilgileri günlüklerde görülebilir. Yeniden uygulama dağıtıcı ACL'leri yapılandırma ve günlük dosyalarını ayarlamaktan sorumludur. Kendisi ayrıca kendisi bu bilgileri görünür olmasını istemez veya günlüğe sonra o günlük dosyalarından bu bilgiyi filtreleyebilirsiniz kapatmadan kapatabilirsiniz.  
  
### <a name="service-model-tracing"></a>Hizmet modeli izleme  
 Hizmet modeli izleme kaynağı (<xref:System.ServiceModel>) ilgili ileti işleme için izlemeyi etkinliklerini ve olayları etkinleştirir. Bu özellik .NET Framework tanılama işlevlerini kullanır <xref:System.Diagnostics>. Olduğu gibi <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> özelliği, konumu ve kendi ACL kullanıcı-.NET Framework uygulama yapılandırma dosyaları kullanılarak yapılandırılabilir. Yönetici izleme etkinleştirdiğinde ileti günlüğe kaydetme gibi dosya konumu her zaman yapılandırılır; Bu nedenle, ACL yönetici denetler.  
  
 Kapsam içinde bir ileti olduğunda ileti üstbilgileri izlemelerini içerir. Önceki bölümde iletisi üst bilgilerinde olası kişisel bilgileri gizlemek için aynı kurallar geçerlidir: önceden tanımlanmış kişisel bilgileri varsayılan olarak izlemeleri üstbilgilerinde kaldırılır. Makine Yöneticisi hem uygulama dağıtıcı yapılandırma, olası kişisel bilgileri günlüğe kaydetmek için değiştirmeniz gerekir. Ancak, uygulamaya özgü üstbilgisinde bulunan kişisel bilgileri izlemelerinde günlüğe kaydedilir. Uygulama dağıtıcısı, ACL'leri yapılandırma ve izleme dosyalarını ayarlamaktan sorumludur. Kendisi ayrıca izlemeyi devre dışı kendisi bu bilgileri görünür olmasını istemez veya günlüğe sonra o izleme dosyalarını bu bilgiyi filtreleyebilirsiniz kapatabilirsiniz.  
  
 Farklı etkinlikler benzersiz kimliklerinin (etkinlik kimlikleri ve genellikle bir GUID olarak adlandırılır) ServiceModel izleme işleminin bir parçası olarak bir ileti olarak birbirine bağlama altyapısı farklı kısımlarını akar.  
  
#### <a name="custom-trace-listeners"></a>Özel izleme dinleyicileri  
 Günlüğe kaydetme ve izleme her iki ileti için özel İzleme dinleyicisi, hangi izlemeleri ve iletileri kablo (örneğin, bir uzak veritabanına) gönderebilir yapılandırılabilir. Özel dinleyicilerini yapılandırmaya veya bunun kullanıcıların uygulama dağıtıcı sorumludur. Kendisi Ayrıca uzak konumu gösterilen herhangi bir kişisel bilgi ve düzgün şekilde bu konuma ACL uygulamak sorumludur.  
  
### <a name="other-features-for-it-professionals"></a>BT uzmanları için diğer özellikler  
 WCF WCF altyapısı yapılandırma bilgileri (Windows ile birlikte gelen) WMI üzerinden kullanıma sunan bir WMI sağlayıcısı var. Varsayılan olarak, WMI arabirimini yöneticiler tarafından kullanılabilir.  
  
 WCF yapılandırma, .NET Framework yapılandırma mekanizması kullanır. Yapılandırma dosyalarını, makinenizde depolanır. Uygulama geliştiricisi ve yönetici ACL ve yapılandırma dosyaları her uygulamanın gereksinimleri için oluşturun. Bir yapılandırma dosyası, uç nokta adresleri ve sertifika deposundaki sertifikalar bağlantılar içerebilir. Sertifikalar, uygulama tarafından kullanılan özellikler çeşitli özelliklerini yapılandırmak için uygulama verilerini sağlamak için kullanılabilir.  
  
 WCF de çağırarak .NET Framework işlem dökümü işlevselliğini kullanır <xref:System.Environment.FailFast%2A> yöntemi.  
  
### <a name="it-pro-tools"></a>BT Uzmanı araçlarını  
 WCF de Windows SDK'yı sevk aşağıdaki BT profesyonel araçları sağlar.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Görüntüleyici WCF izleme dosyaları görüntüler. Görüntüleyici izlemelerinde bulunan hangi bilgileri gösterir.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Düzenleyici, WCF yapılandırma dosyalarını oluşturmak ve düzenlemek kullanıcının sağlar. Düzenleyici, yapılandırma dosyalarında bulunan hangi bilgileri gösterir. Aynı görevi, bir metin düzenleyicisi ile gerçekleştirilebilir.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Bu araç, bir makinedeki ServiceModel yükler yönetmesine olanak sağlar. Çalıştırır ve bu süreçte WCF yükleme yapılandırması hakkında daha fazla bilgi görüntüleyebilir, araç, konsol penceresinde durum iletilerini görüntüler.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe ve WSATUI.dll  
 Bu araçlar, BT uzmanlarının WCF'de birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırma olanak sağlar. Araçları görüntüleyebilir ve kayıt defterinde depolanan en yaygın kullanılan WS-AtomicTransaction ayarları değerlerini değiştirmesine izin verin.  
  
## <a name="cross-cutting-features"></a>Çapraz özellikleri  
 Çapraz kesme özellikleridir. Diğer bir deyişle, bunlar önceki özelliklerden hiçbirini ile oluşturulmuş olabilir.  
  
### <a name="service-framework"></a>Hizmet Çerçevesi  
 Üst bilgiler iletiye bir CLR sınıfının bir örneği ile ilişkilendirir GUID'dir bir örnek kimliği içerebilir.  
  
 Web Hizmetleri Açıklama Dili (WSDL), bağlantı noktasının bir tanım içeriyor. Her bağlantı noktası bir uç nokta adresi ve uygulama tarafından kullanılan hizmetler temsil eden bir bağlaması var. WSDL gösterme, yapılandırma kullanrak kapatılabilir. Makinede hiçbir bilgi tutulmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Communication Foundation'a](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)
- [Güvenlik](../../../docs/framework/wcf/feature-details/security.md)
