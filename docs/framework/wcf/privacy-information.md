---
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: e278b28e5c0015eeab549b04d3870dfa247a57ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808877"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation Gizlilik Bilgileri
Microsoft, son kullanıcılar gizliliğinizi korumayı taahhüt eder. Sürüm 3.0, Windows Communication Foundation (WCF) kullanarak bir uygulama oluşturduğunuzda, uygulama, son kullanıcılarınızın gizlilik etkileyebilir. Örneğin, uygulamanızın açıkça kullanıcı bilgilerini toplayabilir veya istek veya Web sitenize Internet üzerinden bilgi gönderme olabilir. Bu teknoloji, uygulamanızda Microsoft teknolojisi katıştırılmış içerirse, gizlilik etkileyebilecek kendi davranışa sahip olabilir. Siz veya son kullanıcı seçmediğiniz sürece, bize göndermek WCF hiçbir bilgi Microsoft'a uygulamanızdan göndermez.  
  
## <a name="wcf-in-brief"></a>Kısa WCF'de  
 WCF, geliştiricilerin dağıtılmış uygulamalar oluşturmanıza olanak tanır Microsoft .NET Framework kullanılarak dağıtılmış bir Mesajlaşma çerçevedir. İki uygulama iletileri üstbilgi ve gövde bilgileri içerir.  
  
 Üstbilgiler, ileti yönlendirme, güvenlik bilgileri, işlemleri ve uygulama tarafından kullanılan hizmetler bağlı olarak daha fazla bilgi içerebilir. İletiler genellikle varsayılan olarak şifrelenir. Kullanıldığında bir özel durum `BasicHttpBinding`, güvenli olmayan, eski Web Hizmetleri ile kullanılmak üzere tasarlanmış. Uygulama Tasarımcısı, nihai tasarımı için sorumludur. SOAP gövdesi iletilerinde uygulamaya özgü verileri içerir; Ancak, bu veriler, uygulama tanımlı kişisel bilgiler gibi WCF şifreleme veya gizlilik özellikleri kullanarak güvenli hale getirilebilir. Aşağıdaki bölümlerde olası gizliliği etkileyen özellikleri açıklanmaktadır.  
  
## <a name="messaging"></a>İleti  
 İleti hedef belirten adres üstbilgisi her WCF ileti sahiptir ve yanıt nereye.  
  
 Uç nokta tanımlayan bir Tekdüzen Kaynak Tanımlayıcısı (URI) bir uç nokta adresi adresi bileşendir. Adresine bir ağ adresi veya bir mantıksal adresi olabilir. Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir. Geçici adresleme GUID'ler koleksiyonu her adresi keşfedilir için kullanılan veya uç nokta adresi, bir genel benzersiz tanımlayıcı (GUID) içerebilir. Her ileti bir GUID olan bir ileti kimliği içeriyor. Bu özellik WS adresleme başvuru standart izler.  
  
 WCF ileti katmanı, yerel makinede herhangi bir kişisel bilgi yazmaz. Bir hizmet geliştirici (örneğin, bir kişinin adını bir uç nokta adı kullanarak veya yaparak uç noktanın Web kişisel bilgiler dahil olmak üzere gibi bilgileri sunan bir hizmet oluşturduysanız ancak onu kişisel bilgileri ağ düzeyinde yay Açıklama Dili ancak WSDL erişmek için https kullanmak üzere istemcileri gerektirmeyen Hizmetleri). Ayrıca, bir geliştirici çalıştırıyorsa [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kişisel bilgiler, aracın çıkış kullanıma sunan bir uç nokta karşı aracı, bu bilgileri içerebilir ve çıktı dosyasına yazılır yerel sabit disk.  
  
## <a name="hosting"></a>Barındırma  
 WCF'de barındırma özelliği isteğe bağlı olarak başlatmak için veya birden çok uygulama arasında bağlantı noktası paylaşımı etkinleştirmek için uygulamaları sağlar. WCF uygulaması, Internet Information Services (IIS), benzer şekilde barındırılabilir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Barındırma ağdaki belirli bir bilgi kullanıma sunmuyor ve veri makinede korumaz.  
  
## <a name="message-security"></a>İleti Güvenliği  
 WCF güvenlik Mesajlaşma uygulamalar için güvenlik özellikleri sağlar. Kimlik doğrulama ve yetkilendirme sağlanan güvenlik işlevlerini içerir.  
  
 Kimlik doğrulaması istemcileri ve hizmetleri arasında kimlik bilgilerini geçirerek gerçekleştirilir. Kimlik doğrulama aktarım düzeyinde güvenlik yoluyla bulunabilir veya SOAP ileti güvenliği gibi düzeyi:  
  
-   SOAP iletisi güvenlik kimlik doğrulama kullanıcı adı/parola, X.509 sertifikaları, Kerberos biletleri ve bunların tümü veren bağlı olarak kişisel bilgiler içerebilir, SAML belirteçleri gibi kimlik bilgileri üzerinden gerçekleştirilir.  
  
-   Taşıma güvenliği kullanarak, kimlik doğrulaması yoluyla HTTP kimlik doğrulama şemasını gibi geleneksel aktarım kimlik doğrulama mekanizmaları yapılır (temel, Özet, anlaşma, tümleşik Windows kimlik doğrulaması, NTLM, None ve anonim) ve form kimlik doğrulaması.  
  
 Kimlik doğrulama iletişim kuran uç noktaları arasında kurulan güvenli bir oturum neden olabilir. Oturumun güvenlik oturumu yaşam süresi bir GUID ile tanımlanır. Aşağıdaki tabloda ne tutulur gösterir ve nerede.  
  
|Veri|Depolama|  
|----------|-------------|  
|Kullanıcı adı, X.509 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerini başvurular gibi sunu kimlik.|Windows kimlik bilgileri yönetim mekanizmalarını Windows sertifika deposunda gibi.|  
|Kullanıcı adları ve parolalar gibi kullanıcı üyelik bilgileri.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Üyelik sağlayıcısı.|  
|İstemci hizmetinin kimliğini doğrulamak için kullanılan hizmet kimlik bilgilerini.|Hizmet uç noktası adresi.|  
|Arayan bilgileri.|Denetim günlükleri.|  
  
## <a name="auditing"></a>Denetim  
 Denetim başarılı ve başarısız kimlik doğrulama ve yetkilendirme olayların kaydeder. Denetim kayıtlarını içeren aşağıdaki veriler: URI, eylem URI'si ve arayanın kimliği hizmet.  
  
 İleti günlüğe kaydetme, üstbilgiler ve gövdeleri uygulamaya özgü verileri günlüğe çünkü ayrıca Denetim zaman yönetici ileti günlüğe kaydetme, (Bu açma veya kapatma) yapılandırmasını değiştirir kaydeder. İçin [!INCLUDE[wxp](../../../includes/wxp-md.md)], bir kayıt uygulama olay günlüğüne kaydedilir. İçin [!INCLUDE[wv](../../../includes/wv-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], bir kayıt güvenlik olay günlüğüne kaydedilir.  
  
## <a name="transactions"></a>İşlemler  
 WCF uygulaması işlem hizmetleri işlemleri özelliği sağlar.  
  
 İşlem yayma işleminde kullanılan işlem üstbilgileri işlem kimlikleri veya guıd'lerdir kaydı kimlikleri içeriyor olabilir.  
  
 İşlemler özelliği, işlem durumu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem Yöneticisi'ni (Windows bileşeni) kullanır. Varsayılan olarak, işlem yöneticileri arasındaki iletişimler şifrelenir. İşlem yöneticileri uç nokta başvurular, işlem kimlikleri ve kaydı kimlikleri dayanıklı durumlarına bir parçası olarak oturum açabilir. Bu durum ömrü İşlem Yöneticisi'nin günlük dosyası ömrü tarafından belirlenir. MSDTC hizmeti sahibi ve bu günlük dosyası tutar.  
  
 İşlemler özelliği Web Hizmetleri koordinasyonu ve WS-Atomic işlem standartlarını uygular.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 Taşıma veya Ara hatalar oluştuğunda güvenilir oturumlar wcf'de ileti aktarımını sağlar. Sağladıkları bir tam olarak-temel Aktarımı'nın (örneğin, TCP bağlantısı bir kablosuz ağ üzerinde) bağlantısını keser veya bir ileti (bir HTTP proxy giden veya gelen ileti siliniyor) kaybeder olsa bile bir kez ileti aktarılması. Güvenilir oturumlar da iletisi (çok yollu yönlendirme söz konusu olduğunda olabilir gibi), hangi iletileri gönderilen sipariş koruma yeniden sıralama kurtarın.  
  
 Güvenilir oturumlar WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır. Bunlar, belirli bir güvenilir oturum ile ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üstbilgileri ekleyin. Her bir WS-RM oturumu bir GUID olan bir tanımlayıcı vardır.  
  
 Herhangi bir kişisel bilgi son kullanıcının makinede korunur.  
  
## <a name="queued-channels"></a>Sıraya alınan kanalları  
 Kuyruklar alıcı uygulamanın adına gönderen bir uygulamadan gelen iletileri depolamak ve daha sonra alıcı uygulamaya bu iletileri iletebilir. Bunlar, örneğin, alıcı uygulamanın geçici olduğunda, ileti aktarımını alıcı uygulamalar için Gönderen uygulamalardan sağlamaya yardımcı olur. WCF bir taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak queuing için destek sağlar.  
  
 Sıraya alınan kanalları özellik üstbilgi iletiye eklemez. Bunun yerine, uygun Message Queuing iletisi özellikler kümesi ile Message Queuing iletisi oluşturur ve ileti Message Queuing sırasına koymak için Message Queuing yöntemleri çağırır. Message Queuing, Windows ile birlikte gelen bir isteğe bağlı bir bileşenidir.  
  
 Hiçbir bilgi olarak queuing altyapı Message Queuing kullandığından son kullanıcının makinede sıraya alınan kanalları özelliği tarafından korunur.  
  
## <a name="com-integration"></a>COM+ Tümleştirme  
 Bu özellik, WCF hizmetleri ile uyumlu olan hizmetleri oluşturmak için varolan COM ve COM + işlevi sarmalar. Bu özellik belirli üstbilgileri kullanmaz ve son kullanıcının makinedeki verileri korumaz.  
  
## <a name="com-service-moniker"></a>COM hizmet bilinen adı  
 Bu, standart bir WCF istemcisi yönetilmeyen bir sarmalayıcı sağlar. Bu özellik belirli üstbilgileri kablo yok veya makinedeki verileri devam etmez.  
  
## <a name="peer-channel"></a>Eş Kanal  
 Eş kanal WCF kullanılarak taraflı uygulamaların geliştirilmesini sağlar. Çok taraflı Mesajlaşma kafes bağlamında oluşur. Kafesleri düğümleri katılabilirsiniz bir ad tarafından tanımlanır. Eş kanal içindeki her bir düğümün kullanıcı tanımlı bir bağlantı noktası TCP dinleyiciyi oluşturur ve dayanıklılık sağlamak için kafes içindeki diğer düğümlere bağlantılarla oluşturur. Kafes içindeki diğer düğümlere bağlanmak için düğümleri de dinleyici adresi ve kafes içindeki diğer düğümlere de makinenin IP adresleriyle gibi bazı veriler, exchange. Geçici kafes gönderilen iletileri ileti yanıltma ve üzerinde oynanmasını önlemek için gönderene ilgili güvenlik bilgileri içerebilir.  
  
 Herhangi bir kişisel bilgi son kullanıcının makinede depolanır.  
  
## <a name="it-professional-experience"></a>BT Uzmanı deneyimi  
  
### <a name="tracing"></a>İzleme  
 WCF altyapısının Tanılama özelliğini taşıma ve hizmet modeli katmanları ve etkinlikleri ve bu iletileriyle ilişkili olayları geçirir iletilerini günlüğe kaydeder. Bu özellik varsayılan olarak kapalıdır. Uygulama yapılandırma dosyası kullanarak etkindir ve izleme davranışı çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir. Etkinleştirildiğinde, izleme altyapısına iletileri, etkinlikler ve yapılandırılmış dinleyicileri için olayları işlemeyi içeren bir tanı izleme yayar. Çıktı konumunu ve biçim yöneticinin dinleyicisi yapılandırma seçeneklerine göre belirlenir, ancak genellikle bir XML biçimli dosyasıdır. Yönetici, izleme dosyaları üzerinde erişim denetimi listesi (ACL) ayarlanmasından sorumludur. Özellikle, Windows etkinleştirme sistem (WAS) tarafından barındırıldığında, yönetici dosya ortak sanal kök dizininden sunulan, bu değil istenirse değil emin olmanız gerekir.  
  
 İzleme iki tür vardır: ileti günlüğe kaydetme ve tanılama hizmet modeli aşağıdaki bölümde açıklanan izleme,. Her tür kendi izleme kaynağı yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel>. Bu günlük izleme kaynaklarının ikisinin uygulamayı yerel olarak veri yakalayın.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti izleme kaynağı günlüğe kaydetme (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) iletilerini günlüğe kaydetmek için bir yönetici sistemi aracılığıyla akan sağlar. Yapılandırma yoluyla, iletilerin tamamını veya yalnızca ileti üstbilgilerini, taşıma ve/veya hizmet modeli katmanına günlüğe ve hatalı biçimlendirilmiş iletileri dahil edilip edilmeyeceğini oturum kullanıcı karar verebilirsiniz. Ayrıca, kullanıcının hangi iletileri günlüğe kısıtlamak için filtreleme yapılandırabilirsiniz.  
  
 Varsayılan olarak, ileti günlüğe kaydetme devre dışıdır. Yerel Makine Yöneticisi oturum açma ileti uygulama düzeyinde yönetici önleyebilir.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Şifrelenmiş ve şifresi ileti günlüğe kaydetme  
 İletileri günlüğe, şifrelenmiş veya şifresi, aşağıdaki koşulları'nda açıklanan şekilde.  
  
 Günlük aktarma  
 Alınan ve aktarım düzeyinde gönderilen iletileri günlüğe kaydeder. Bu iletiler tüm başlıkları içerir ve kablo ve alınma zaman gönderilmeden önce şifrelenmelidir.  
  
 İletileri kablo gönderilmeden önce şifrelenir ve alındığında, günlüğe kaydedildikten de şifrelenir. Bir güvenlik protokolü kullanılan (https) bir özel durum olduğunda: Bunlar gönderilmeden önce ve kablo şifrelenmiş olsa bile alınma sonra şifresi sonra kaydedilir.  
  
 Hizmet günlüğü  
 Alınan veya hizmet modeli düzeyinde hemen önce ve kullanıcı kodu girdikten sonra kanal üstbilgi işlemeyi gerçekleştikten sonra gönderilen iletileri günlüğe kaydeder.  
  
 Güvenli ve kablo şifrelenmiş olsa bile bu düzeyde günlüğe kaydedilen iletileri şifresi çözülür.  
  
 Hatalı biçimlendirilmiş bir ileti günlüğe kaydetme  
 WCF altyapı anlamak veya işleyemiyor iletileri günlüğe kaydeder.  
  
 İletileri olarak kaydediliyor-diğer bir deyişle, veya şifrelenir  
  
 İletileri oturum açtığında şifresi çözülmüş veya şifrelenmemiş formunu WCF varsayılan güvenlik anahtarlarını ve potansiyel olarak kişisel bilgi gelen iletileri açmadan önce kaldırır. Hangi bilgilerin kaldırılır, sonraki bölümlerde açıklanmıştır ve ne zaman. Makine Yöneticisi ve uygulama dağıtıcı hem gerçekleştirmeniz gereken anahtarları ve büyük olasılıkla kişisel bilgileri günlüğe kaydetmek için varsayılan davranışı değiştirmek için belirli yapılandırma eylemleri.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Bilgi iletisi üstbilgileri şifresi çözülür ve şifrelenmemiş iletileri oturum açarken kaldırıldı  
 Ne zaman iletileri şifresi çözülür ve şifrelenmemiş formunda, güvenlik anahtarları günlüğe kaydedilir ve potansiyel olarak kişisel bilgiler kaldırılır ileti üstbilgilerini ve İleti gövdeleri varsayılan olarak günlüğe kaydedilen önce. Aşağıdaki liste, WCF anahtarları ve potansiyel olarak kişisel bilgi dikkate gösterir.  
  
 Kaldırılan anahtarları:  
  
 \- İçin xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 WST:Entropy  
  
 \- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:nonce  
  
 Kaldırılır potansiyel olarak kişisel bilgi:  
  
 \- İçin xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:  
  
 \<onaylama işlemi  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 Onaylama kimliği = "[ID]"  
  
 Veren = "[dize]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<NotBefore koşulları "[dateTime]" NotOnOrAfter = "[dateTime]" = >  
  
 \<AudienceRestrictionCondition >  
  
 \<Hedef kitle > [URI]\</Audience > +  
  
 \</ AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition / > *  
  
 <\!--soyut taban türü  
  
 \<Koşul / > *  
  
 -->  
  
 \</ Koşulları >?  
  
 \<Öneri >  
  
 \<AssertionIDReference > [kimlik]\</AssertionIDReference > *  
  
 \<Onaylama işlemi > [onaylama]\</Assertion > *  
  
 [herhangi bir] *  
  
 \</ Öneriler >?  
  
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
  
 \<SubjectConfirmationData > [herhangi bir]\</SubjectConfirmationData >?  
  
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
  
 AuthorityKind = "[QName]"  
  
 Konumu = "[URI]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</ AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Konu]  
  
 \<Özniteliği  
  
 AttributeName = "[dize]"  
  
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
  
 \<Eylem Namespace = "[URI]" > [dize] \< /eylem > +  
  
 \<Kanıt >  
  
 \<AssertionIDReference > [kimlik]\</AssertionIDReference > +  
  
 \<Onaylama işlemi > [onaylama]\</Assertion > +  
  
 \</ Kanıtlayan bilgiler >?  
  
 \</ AuthorizationDecisionStatement > *  
  
 \</ Onaylama >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>İleti gövdeleri şifresi çözülür ve şifrelenmemiş iletileri günlüğe kaydetme bırakırken kaldırılan bilgileri  
 Daha önce açıklandığı gibi WCF kaldırır anahtarları ve şifresi çözülür ve şifrelenmemiş günlüğe kaydedilen iletilere ileti üstbilgilerini bilinen büyük olasılıkla kişisel bilgileri. Ayrıca, WCF anahtarları ve bilinen potansiyel olarak kişisel bilgi İleti gövdeleri gövde öğeleri ve anahtar değişimi içinde yer alan güvenlik iletileri tanımlayan eylemleri aşağıdaki listeden kaldırır.  
  
 Aşağıdaki ad alanları için:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (örneğin, hiçbir eylem varsa kullanılabilir)  
  
 Bilgiler, anahtar değişimi içeren bu gövdesi öğelerini için kaldırılır:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Bilgi de her aşağıdaki eylemlerden birini kaldırılır:  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Hiçbir bilgi uygulamaya özgü üstbilgi ve gövde verileri kaldırılır.  
 WCF uygulamaya özgü üstbilgileri (örneğin, sorgu dizeleri) veya gövde verileri (örneğin, kredi kartı numarası) kişisel bilgilerin izlemez.  
  
 İleti günlüğe kaydetme açık olduğunda, uygulamaya özgü üstbilgilerindeki kişisel bilgileri ve gövde bilgileri günlüklerde görülebilir. Yeniden uygulama dağıtıcı ACL'leri yapılandırma ve günlük dosyalarını ayarlanmasından sorumludur. Kendisi ayrıca kendisinin görünür olması için bu bilgileri istemez veya günlüğe kaydedilir sonra ki bu günlük dosyalarındaki bilgileri filtrelemenize oturum kapatma etkinleştirebilirsiniz.  
  
### <a name="service-model-tracing"></a>Hizmet modeli izleme  
 Hizmet modeli izleme kaynağı (<xref:System.ServiceModel>) ilgili ileti işleme etkinliklerini ve olayları izlemeyi etkinleştirir. Bu özellik .NET Framework tanılama işlevlerini kullanır <xref:System.Diagnostics>. İle <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> özelliği, konumu ve onun ACL kullanıcı-.NET Framework uygulama yapılandırma dosyaları kullanılarak yapılandırılabilir. Yönetici izleme etkinleştirdiğinde ileti günlüğe kaydetme gibi dosya konumuna her zaman yapılandırılır; Bu nedenle, ACL yönetici denetler.  
  
 Bir ileti kapsamda olduğunda izlemeleri ileti üstbilgilerini içerir. Önceki bölümde ileti üstbilgilerini potansiyel olarak kişisel bilgilerinizi gizlemek için aynı kurallar geçerlidir: daha önce tanımlanan kişisel bilgiler izlemeleri üstbilgilerinde varsayılan olarak kaldırılır. Makine Yöneticisi ve uygulama dağıtıcı yapılandırmanın büyük olasılıkla kişisel bilgileri günlüğe kaydetmek için değiştirmeniz gerekir. Ancak, uygulamaya özgü üstbilgilerinde bulunan kişisel bilgileri içindeki günlüğe kaydedilir. Uygulama dağıtıcı, ACL'leri yapılandırma ve izleme dosyaları ayarlanmasından sorumludur. Kendisi ayrıca izlemeyi devre dışı kendisinin görünür olması için bu bilgileri istemediği ya da sonra günlüğe kaydedilir bu bilgileri izleme dosyalarından filtreleyebilirsiniz kapatabilirsiniz.  
  
 Farklı etkinlikler benzersiz kimlikler (etkinlik kimlikleri ve genellikle bir GUID denir) kapsamında ServiceModel izleme, bir ileti olarak birbirine bağlamak altyapısının farklı bölümleri aracılığıyla akar.  
  
#### <a name="custom-trace-listeners"></a>Özel izleme dinleyicileri  
 Günlüğe kaydetme ve izleme her iki ileti için özel İzleme dinleyicisi, hangi izlemeleri ve iletileri kablo (örneğin, bir uzak veritabanına) gönderebilir yapılandırılabilir. Uygulama dağıtıcı özel dinleyicileri yapılandırma veya bunu yapmak kullanıcıları etkinleştirme için sorumludur. Kendisi Ayrıca uzak konumda kullanıma sunulan herhangi bir kişisel bilgi ve bu konuma ACL'ler düzgün bir şekilde uygulamak için sorumlu değildir.  
  
### <a name="other-features-for-it-professionals"></a>BT uzmanları için diğer özellikleri  
 WCF WCF altyapı yapılandırma bilgileri (Windows ile birlikte gelen) WMI üzerinden kullanıma sunan bir WMI sağlayıcısı sahiptir. Varsayılan olarak, WMI arabirimi yöneticiler tarafından kullanılabilir.  
  
 WCF yapılandırması, .NET Framework yapılandırma mekanizması kullanır. Yapılandırma dosyaları makinede depolanır. Uygulama geliştiricisi ve yönetici yapılandırma dosyalarını ve ACL her uygulamanın gereksinimleri için oluşturun. Bir yapılandırma dosyası, uç nokta adresleri ve sertifika deposundaki sertifikalar bağlantılar içerebilir. Sertifikalar, uygulama tarafından kullanılan özellikler çeşitli özelliklerini yapılandırmak için uygulama verilerini sağlamak için kullanılabilir.  
  
 WCF de çağırarak .NET Framework işlem dökümü işlevselliğini kullanır <xref:System.Environment.FailFast%2A> yöntemi.  
  
### <a name="it-pro-tools"></a>BT Uzmanı araçlarını  
 WCF aynı zamanda Windows SDK'ın sevk aşağıdaki BT uzmanları araçları sağlar.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Görüntüleyici WCF izleme dosyaları görüntüler. Görüntüleyici ne olursa olsun bilgileri izlemeleri bulunan gösterir.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Düzenleyici WCF yapılandırma dosyalarını oluşturmak ve düzenlemek olanak tanır. Düzenleyici ne olursa olsun bilgileri yapılandırma dosyalarında bulunan gösterir. Aynı görevi bir metin düzenleyicisiyle gerçekleştirilebilir.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Bu aracı bir makinede ServiceModel yükler yönetmesine olanak tanır. Çalıştırır ve bu süreçte WCF yükleme yapılandırma hakkında bilgi görüntüleyebilir, aracı konsol penceresinde durum iletilerini görüntüler.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe ve WSATUI.dll  
 Bu araçlar, WCF birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırmak BT uzmanları olanak sağlar. Araçları görüntülemek ve kayıt defterinde depolanan en yaygın kullanılan WS-AtomicTransaction ayarlarının değerleri değiştirmek izin verin.  
  
## <a name="cross-cutting-features"></a>Çapraz kesme özellikleri  
 Çapraz kesme özellikleridir. Diğer bir deyişle, bunlar herhangi bir önceki özellikleri ile oluşturulmuş olabilir.  
  
### <a name="service-framework"></a>Hizmet Çerçevesi  
 Üstbilgiler, bir ileti CLR sınıfının bir örneği ile ilişkilendirir GUID'dir bir örnek kimliği içerebilir.  
  
 Web Hizmetleri Açıklama Dili (WSDL) bağlantı noktası bir tanım içeriyor. Her bağlantı noktası bir uç nokta adresi ve uygulama tarafından kullanılan hizmetler temsil eden bir bağlaması var. WSDL gösterme, yapılandırmayı kullanarak devre dışı açılabilir. Hiçbir bilgi makinede korunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation](http://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Güvenlik](../../../docs/framework/wcf/feature-details/security.md)
