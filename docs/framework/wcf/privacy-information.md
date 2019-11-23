---
title: Windows Communication Foundation Gizlilik Bilgileri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 0b277728d2f2c224d5e45e3990ab2fd588bc81d3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318690"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation Gizlilik Bilgileri
Microsoft, son kullanıcıların gizliliğini korumayı taahhüt etmektedir. Windows Communication Foundation (WCF), sürüm 3,0 kullanarak bir uygulama oluşturduğunuzda, uygulamanız son kullanıcılarınızın gizliliğini etkileyebilir. Örneğin, uygulamanız kullanıcı iletişim bilgilerini açıkça toplayabilir veya Internet üzerinden Web sitenize bilgi talep edebilir veya gönderebilir. Uygulamanıza Microsoft teknolojisi eklerseniz, bu teknolojinin gizliliği etkileyebilecek kendi davranışı olabilir. WCF, siz veya son kullanıcı tarafından bize göndermek için seçim yapmadıkça Microsoft 'a herhangi bir bilgi göndermez.  
  
## <a name="wcf-in-brief"></a>WCF kısaca  
 WCF, geliştiricilerin dağıtılmış uygulamalar oluşturmalarına olanak tanıyan Microsoft .NET çerçevesini kullanan dağıtılmış bir mesajlaşma çerçevesidir. İki uygulama arasında iletilen iletiler, üst bilgi ve gövde bilgilerini içerir.  
  
 Üst bilgiler, uygulama tarafından kullanılan hizmetlere bağlı olarak ileti yönlendirme, güvenlik bilgileri, işlemler ve daha fazlasını içerebilir. İletiler genellikle varsayılan olarak şifrelenir. Tek istisna, güvenli olmayan, eski Web hizmetleriyle kullanılmak üzere tasarlanan `BasicHttpBinding`kullanmaktır. Uygulama Tasarımcısı olarak son tasarımdan siz sorumlusunuz. SOAP gövdesindeki iletiler uygulamaya özgü verileri içerir; Ancak, uygulama tanımlı kişisel bilgiler gibi bu veriler, WCF şifreleme veya gizlilik özellikleri kullanılarak güvenliği sağlanmış olabilir. Aşağıdaki bölümlerde gizliliği potansiyel olarak etkileyebilecek özellikler açıklanır.  
  
## <a name="messaging"></a>İleti  
 Her WCF iletisinde, ileti hedefini belirten ve yanıtın gitmesi gereken bir adres üst bilgisi vardır.  
  
 Bir uç nokta adresinin adres bileşeni, uç noktasını tanımlayan bir Tekdüzen kaynak tanımlayıcısıdır (URI). Adres bir ağ adresi veya mantıksal adres olabilir. Adres, makine adı (ana bilgisayar adı, tam etki alanı adı) ve bir IP adresi içerebilir. Uç nokta adresi bir genel benzersiz tanımlayıcı (GUID) veya her bir adresi ayırt etmek için kullanılan geçici adresleme için GUID 'lerin bir koleksiyonunu da içerebilir. Her ileti, GUID olan bir ileti KIMLIĞI içerir. Bu özellik, WS-Addressing başvuru standardını izler.  
  
 WCF mesajlaşma katmanı, yerel makineye herhangi bir kişisel bilgi yazmaz. Ancak, bir hizmet geliştiricisi bu bilgileri açığa çıkaran bir hizmet (örneğin, bir uç nokta adında bir kişinin adını kullanarak ya da uç noktanın Web 'e kişisel bilgiler dahil) bir hizmet oluşturarsa, kişisel bilgileri ağ düzeyinde yayabilir. Hizmetler açıklaması dili, ancak istemcilerin WSDL 'ye erişmek için HTTPS kullanmasını gerektirmemelidir). Ayrıca bir geliştirici, kişisel bilgiler sunan bir uç noktaya karşı [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırıyorsa, aracın çıktısı bu bilgileri içerebilir ve çıkış dosyası yerel sabit diske yazılır.  
  
## <a name="hosting"></a>Barındırma  
 WCF 'deki barındırma özelliği, uygulamaların isteğe bağlı olarak başlamasını veya birden çok uygulama arasında bağlantı noktası paylaşımını etkinleştirmesini sağlar. WCF uygulaması, ASP.NET benzeri Internet Information Services (IIS) içinde barındırılabilir.  
  
 Barındırma, ağ üzerinde belirli bilgileri açığa çıkarır ve makinede veri bulundurmaz.  
  
## <a name="message-security"></a>İleti Güvenliği  
 WCF güvenliği, Mesajlaşma uygulamalarına yönelik güvenlik özellikleri sağlar. Belirtilen güvenlik işlevleri kimlik doğrulaması ve yetkilendirme içerir.  
  
 Kimlik doğrulaması, istemciler ve hizmetler arasında kimlik bilgileri geçirerek gerçekleştirilir. Kimlik doğrulaması, aktarım düzeyi güvenlik aracılığıyla veya SOAP ileti düzeyi güvenliği aracılığıyla aşağıdaki gibi olabilir:  
  
- SOAP iletisi güvenliği 'nde kimlik doğrulaması, Kullanıcı adı/parolalar, X. 509.440 sertifikaları, Kerberos biletleri ve SAML belirteçleri gibi kimlik bilgileri aracılığıyla yapılır; bu, verenlere bağlı olarak kişisel bilgiler içerebilir.  
  
- Aktarım güvenliğini kullanarak, kimlik doğrulaması HTTP kimlik doğrulama şemaları (temel, Özet, anlaşma, tümleşik Windows yetkilendirmesi, NTLM, hiçbiri ve anonim) ve form kimlik doğrulaması gibi geleneksel aktarım kimlik doğrulama mekanizmaları aracılığıyla yapılır.  
  
 Kimlik doğrulama, iletişim noktaları arasında kurulan güvenli bir oturumun oluşmasına neden olabilir. Oturum, güvenlik oturumunun ömrünü sürdüeden bir GUID ile tanımlanır. Aşağıdaki tabloda neler olduğu ve nerede tutulduğu gösterilmektedir.  
  
|Veri|Depolama|  
|----------|-------------|  
|Kullanıcı adı, X. 509.440 sertifikaları, Kerberos belirteçleri ve kimlik bilgilerine yapılan başvurular gibi sunum kimlik bilgileri.|Windows sertifika deposu gibi standart Windows kimlik bilgisi yönetim mekanizmaları.|  
|Kullanıcı üyeliği bilgileri, örneğin Kullanıcı adları ve parolalar.|ASP.NET üyelik sağlayıcıları.|  
|Hizmetin istemcilere kimliğini doğrulamak için kullanılan hizmet hakkındaki kimlik bilgileri.|Hizmetin uç nokta adresi.|  
|Çağıran bilgileri.|Denetim günlükleri.|  
  
## <a name="auditing"></a>Denetim  
 Denetim, kimlik doğrulama ve yetkilendirme olaylarının başarısını ve başarısızlığını kaydeder. Denetim kayıtları şu verileri içerir: hizmet URI 'SI, eylem URI 'SI ve arayanın kimliği.  
  
 Ayrıca Denetim, yönetici ileti günlüğe kaydetme yapılandırmasını değiştirdiğinde (açık veya kapalı), ileti günlüğü, uygulamaya özgü verileri üst bilgilerde ve gövdelerde günlüğe kaydeder. [!INCLUDE[wxp](../../../includes/wxp-md.md)]için, uygulama olay günlüğüne bir kayıt kaydedilir. [!INCLUDE[wv](../../../includes/wv-md.md)] ve [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]için, güvenlik olay günlüğüne bir kayıt kaydedilir.  
  
## <a name="transactions"></a>İşlemler  
 İşlemler özelliği bir WCF uygulamasına işlem hizmetleri sağlar.  
  
 İşlem yayma işleminde kullanılan işlem üstbilgileri, GUID 'Leri olan Işlem kimliklerini veya kayıt kimliklerini içerebilir.  
  
 Işlemler özelliği, işlem durumunu yönetmek için Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) Işlem yöneticisi 'Ni (bir Windows bileşeni) kullanır. Varsayılan olarak, Işlem yöneticileri arasındaki iletişimler şifrelenir. İşlem yöneticileri, sürekli durumunun bir parçası olarak uç nokta başvurularını, Işlem kimliklerini ve kayıt kimliklerini günlüğe kaydetmeyebilir. Bu durumun ömrü, Işlem yöneticisinin günlük dosyasının ömrü ile belirlenir. MSDTC hizmeti, bu günlüğün sahibi ve bakımını yapar.  
  
 Işlemler özelliği, WS-koordinasyon ve WS Atomik Işlem standartları uygular.  
  
## <a name="reliable-sessions"></a>Güvenilir oturumlar  
 WCF 'de güvenilir oturumlar, aktarım veya aracı arızalarının oluşması durumunda iletilerin aktarılmasını sağlar. Bu kişiler, temeldeki taşımanın bağlantısı kesildiğinde (örneğin, kablosuz ağ üzerinde bir TCP bağlantısı) veya bir iletiyi kaybettiğinde (bir HTTP proxy 'si giden veya gelen bir iletiyi bırakırken) iletilerin tam olarak bir kez aktarılmasını sağlar. Güvenilir oturumlar Ayrıca iletilerin gönderilme sırasını koruyarak ileti yeniden sıralamasını (çok yollu yönlendirme durumunda olabileceği gibi) de kurtarır.  
  
 Güvenilir Oturumlar, WS-ReliableMessaging (WS-RM) protokolü kullanılarak uygulanır. Bunlar, belirli bir güvenilir oturumla ilişkili tüm iletileri tanımlamak için kullanılan oturum bilgilerini içeren WS-RM üst bilgilerini ekler. Her WS-RM oturumunun bir GUID olan bir tanımlayıcısı vardır.  
  
 Son kullanıcının makinesinde kişisel bilgi korunmaz.  
  
## <a name="queued-channels"></a>Sıraya alınan kanallar  
 Kuyruklar iletileri alıcı uygulama adına gönderen uygulamadan depolar ve daha sonra bu iletileri alıcı uygulamasına iletir. Bu kişiler, örneğin, alıcı uygulama geçici olduğunda, uygulamaları almaya yönelik uygulamalar gönderen iletiler aktarımının sağlanmasına yardımcı olur. WCF, taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma desteği sağlar.  
  
 Sıraya alınan kanallar özelliği bir iletiye üst bilgi eklemez. Bunun yerine, uygun Message Queuing ileti özellikleri ayarlanmış Message Queuing bir ileti oluşturur ve iletiyi Message Queuing kuyruğuna koymak için Message Queuing yöntemleri çağırır. Message Queuing, Windows ile birlikte gelen isteğe bağlı bir bileşendir.  
  
 Kuyruğa alma altyapısı olarak Message Queuing kullandığından, son kullanıcının makinesinde sıraya alınan kanallar özelliği korunmaz.  
  
## <a name="com-integration"></a>COM+ Tümleştirme  
 Bu özellik, WCF hizmetleriyle uyumlu hizmetler oluşturmak için mevcut COM ve COM+ işlevlerini sarmalanmış. Bu özellik belirli üst bilgileri kullanmaz ve son kullanıcının makinesinde verileri korumaz.  
  
## <a name="com-service-moniker"></a>COM hizmeti bilinen adı  
 Bu, standart bir WCF istemcisine yönetilmeyen bir sarmalayıcı sağlar. Bu özellik, hat üzerinde belirli üst bilgilere sahip değildir ve makinede verileri kalıcı hale getiremez.  
  
## <a name="peer-channel"></a>Eş Kanal  
 Eş kanal, WCF kullanarak çok taraflı uygulamaların geliştirilmesini mümkün. Çok taraflı mesajlaşma, bir ağ bağlamında meydana gelir. Kafesler, düğümlerin katılabilme adı tarafından tanımlanır. Eş kanaldaki her düğüm, Kullanıcı tarafından belirtilen bağlantı noktasında bir TCP dinleyicisi oluşturur ve esneklik sağlamak için kafesteki diğer düğümlerle bağlantı kurar. Kafesteki diğer düğümlere bağlanmak için, düğümler aynı zamanda dinleyici adresi ve makinenin IP adresleri de dahil olmak üzere, ağ üzerindeki diğer düğümlerle birlikte bazı verileri de değiş tokuş eder. Ağ üzerinden gönderilen iletiler, ileti sızdırma ve izinsiz değişiklik yapılmasını engellemek için gönderiyle ilgili güvenlik bilgilerini içerebilir.  
  
 Son kullanıcının makinesinde kişisel bilgi depolanmaz.  
  
## <a name="it-professional-experience"></a>BT uzmanı deneyimi  
  
### <a name="tracing"></a>İzleme  
 WCF altyapısının tanılama özelliği, aktarım ve hizmet modeli katmanlarından geçen iletileri ve bu iletilerle ilişkili etkinlikleri ve olayları günlüğe kaydeder. Bu özellik varsayılan olarak kapalıdır. Uygulamanın yapılandırma dosyası kullanılarak etkinleştirilir ve izleme davranışı, çalışma zamanında WCF WMI sağlayıcısı kullanılarak değiştirilebilir. Etkinleştirildiğinde, izleme altyapısı, yapılandırılan dinleyicilerine ileti, etkinlik ve işleme olaylarını içeren bir tanılama izlemesi yayar. Çıktının biçimi ve konumu yöneticinin dinleyici yapılandırma seçeneklerine göre belirlenir, ancak genellikle XML biçimli bir dosyadır. Yönetici, izleme dosyalarındaki erişim denetim listesini (ACL) ayarlamaktan sorumludur. Özellikle, Windows etkinleştirme sistemi (WAS) tarafından barındırıldığında, yönetici, bu istenmiyorsa, dosyaların ortak sanal kök dizinden sunulmadığından emin olmalıdır.  
  
 İki tür izleme vardır: Ileti günlüğü ve hizmet modeli Tanılama izleme, aşağıdaki bölümde açıklanmıştır. Her tür kendi izleme kaynağı aracılığıyla yapılandırılır: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> ve <xref:System.ServiceModel>. Bu günlüğe kaydetme izleme kaynaklarından her ikisi de, uygulamada yerel olan verileri yakalar.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti günlüğü izleme kaynağı (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>), yöneticinin sistem üzerinden akan iletileri günlüğe kaydetmeye izin verir. Yapılandırma sayesinde, Kullanıcı yalnızca tüm iletileri veya ileti üstbilgilerini günlüğe kaydetmek, aktarım ve/veya hizmet modeli katmanlarında günlüğe kaydedilip edilmeyeceğini ve hatalı biçimlendirilmiş iletilerin eklenip eklenmeyeceğini belirtir. Ayrıca Kullanıcı, hangi iletilerin günlüğe kaydedileceğini kısıtlamak için filtrelemeyi yapılandırabilir.  
  
 Varsayılan olarak, ileti günlüğe kaydetme devre dışıdır. Yerel Makine Yöneticisi, uygulama düzeyinde yöneticinin ileti oturumunu açmasını önleyebilir.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Şifrelenmiş ve şifresi çözülmüş Ileti günlüğe kaydetme  
 Aşağıdaki koşullarda açıklandığı gibi iletiler günlüğe kaydedilir, şifrelenir veya çözülür.  
  
 Aktarım günlüğü  
 Aktarım düzeyinde alınan ve gönderilen iletileri günlüğe kaydeder. Bu iletiler tüm üst bilgileri içerir ve bu, hatta gönderilirken ve alındığında şifrelenir.  
  
 İletiler, Tel gönderilmeden ve alındıkları sırada şifrelenirse, bunlar da şifreli olarak kaydedilir. Bir güvenlik protokolünün kullanıldığı bir özel durum (https): daha sonra, bu dosyalar, kablo üzerinde şifrelenseler bile gönderilmeden ve alındıktan sonra günlüğe çözülür.  
  
 Hizmet günlüğü  
 İleti üst bilgisi işleme gerçekleştirildikten sonra, Kullanıcı kodu girildikten hemen önce ve sonra, hizmet modeli düzeyinde alınan veya gönderilen iletileri günlüğe kaydeder.  
  
 Bu düzeyde günlüğe kaydedilen iletiler, güvenli olsalar ve kabloda şifrelendiğinden bile çözülür.  
  
 Hatalı biçimlendirilmiş Ileti günlüğü  
 WCF altyapısının anlayabileceği veya işleyebileceğini iletileri günlüğe kaydeder.  
  
 İletiler olduğu gibi kaydedilir, yani şifrelenir veya değildir  
  
 İletiler, şifresi çözülmüş veya şifrelenmemiş biçimde günlüğe kaydedildiğinde, varsayılan olarak WCF güvenlik anahtarlarını ve bilgileri günlüğe kaydedilmeden önce iletilerden kaldırır. Sonraki bölümlerde hangi bilgilerin kaldırıldığı ve ne zaman olduğu açıklanır. Makine Yöneticisi ve uygulama dağıtıcısı, varsayılan davranışı günlük anahtarlarına ve potansiyel olarak kişisel bilgilere değiştirecek şekilde, her ikisi de belirli yapılandırma eylemlerini almalıdır.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti başlıklarından kaldırılan bilgiler  
 İletiler, şifresi çözülmüş/şifrelenmemiş biçiminde günlüğe kaydedildiğinde, güvenlik anahtarları ve potansiyel olarak kişisel bilgiler, günlüğe kaydedilmeden önce ileti başlıklarından ve ileti gövdelerinde varsayılan olarak kaldırılır. Aşağıdaki listede, anahtarların ve potansiyel olarak kişisel bilgilerin hangi WCF tarafından kabul olduğu gösterilmektedir.  
  
 Kaldırılan anahtarlar:  
  
 xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns: WST = "http://schemas.xmlsoap.org/ws/2005/02/trust" Için \-  
  
 wst:BinarySecret  
  
 Wst: entropi  
  
 xmlns Için \-: ws& = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns: WSO = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 WSS: parola  
  
 WSS: nonce  
  
 Kaldırılan potansiyel kişisel bilgiler:  
  
 xmlns Için \-: ws& = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" ve xmlns: WSO = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 WSS: Kullanıcı adı  
  
 WSS: BinarySecurityToken  
  
 \- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:  
  
 \<onaylama  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId 'si = "[KIMLIK]"  
  
 Issuer = "[dize]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<koşullar NotBefore = "[TarihSaat]" NotOnOrAfter = "[dateTime]" >  
  
 \<AudienceRestrictionCondition >  
  
 \<hedef kitle > [Uri]\</Audience > +  
  
 \</AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition/> *  
  
 <\!--soyut temel tür  
  
 \<koşulu/> *  
  
 -->  
  
 \</Conditions >?  
  
 \<önerileri >  
  
 \<AssertionIDReference > [KIMLIK]\</AssertionIDReference > *  
  
 \<onaylama > [onaylama]\</assertion > *  
  
 [any] *  
  
 \</tavsiyeler >?  
  
 <\!--soyut temel türler  
  
 \<deyimin/> *  
  
 \<Subjectdeyimin >  
  
 \<konu >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [any]\</SubjectConfirmationData >?  
  
 \<DS: KeyInfo >...\</DS: KeyInfo >?  
  
 \</SubjectConfirmation >?  
  
 \</Subject >  
  
 \</Subjectdeyimin > *  
  
 -->  
  
 \<Authenticationdeyimin  
  
 AuthenticationMethod = "[Uri]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 Konusuna  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind = "[QName]"  
  
 Konum = "[Uri]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</Authenticationdeyimin > *  
  
 \<Attributedeyimin >  
  
 Konusuna  
  
 \<özniteliği  
  
 AttributeName = "[dize]"  
  
 AttributeNamespace = "[Uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute > +  
  
 \</Attributedeyimin > *  
  
 \<AuthorizationDecisionStatement  
  
 Resource = "[Uri]"  
  
 Karar = "[reddetme&#124;&#124;belirsiz izin ver]"  
  
 >  
  
 Konusuna  
  
 \<Action namespace = "[Uri]" > [dize]\</Action > +  
  
 \<bulgu >  
  
 \<AssertionIDReference > [KIMLIK]\</AssertionIDReference > +  
  
 \<onaylama > [onaylama]\</assertion > +  
  
 /Kanıt > \<?  
  
 \</AuthorizationDecisionStatement > *  
  
 \</assertion >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Şifresi çözülmüş/şifrelenmemiş Iletileri günlüğe kaydederken Ileti gövdelerinde kaldırılan bilgiler  
 Daha önce açıklandığı gibi, WCF anahtarları ve bilinen potansiyel olarak kişisel bilgileri, günlüğe kaydedilen ve şifrelenmemiş iletiler için ileti başlıklarından kaldırır. Ayrıca, WCF anahtarlar ve bilinen potansiyel kişisel bilgileri, anahtar değişimine dahil olan güvenlik iletilerini açıklayan aşağıdaki listede bulunan gövde öğeleri ve eylemler için ileti gövdesinden kaldırır.  
  
 Aşağıdaki ad alanları için:  
  
 xmlns: WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" ve xmlns: WST = "http://schemas.xmlsoap.org/ws/2005/02/trust" (örneğin, kullanılabilir bir eylem yoksa)  
  
 Bu gövde öğeleri için, anahtar değişimini içeren bilgiler kaldırılır:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Bilgiler aşağıdaki eylemlerin her biri için de kaldırılır:  
  
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
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Uygulamaya özgü üst bilgilerden ve gövde verilerinden hiçbir bilgi kaldırılmadı  
 WCF, uygulamaya özgü üst bilgilerde (örneğin, sorgu dizeleri) veya gövde verilerinde (örneğin, kredi kartı numarası) kişisel bilgileri izlemez.  
  
 İleti günlüğe kaydetme açık olduğunda, uygulamaya özgü üst bilgiler ve gövde bilgilerindeki kişisel bilgilere günlüklerde görünebilir. Daha sonra, yapılandırma ve günlük dosyalarındaki ACL 'Leri ayarlamaktan uygulama dağıtıcı sorumludur. Ayrıca, bu bilgilerin görünür olmasını istemediyse günlüğe kaydetmeyi kapatabilir veya günlüğe kaydedildikten sonra bu bilgileri günlük dosyalarından filtreleyebiliriz.  
  
### <a name="service-model-tracing"></a>Hizmet modeli Izleme  
 Hizmet modeli izleme kaynağı (<xref:System.ServiceModel>), ileti işlemeyle ilgili etkinliklerin ve olayların izlenmesini sağlar. Bu özellik <xref:System.Diagnostics>.NET Framework tanılama işlevini kullanır. <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> özelliğinde olduğu gibi, konum ve ACL 'SI, .NET Framework uygulama yapılandırma dosyaları kullanılarak Kullanıcı tarafından yapılandırılabilir. İleti günlüğe kaydetme sırasında, yönetici izlemeyi etkinleştirse de dosya konumu her zaman yapılandırılır; Bu nedenle, yönetici ACL 'yi denetler.  
  
 İzlemeler, bir ileti kapsamda olduğunda ileti üst bilgileri içerir. Önceki bölümde bulunan ileti üstbilgilerinde kişisel bilgilerini gizlemek için de aynı kurallar geçerlidir: daha önce tanımlanan kişisel bilgiler, izlemelerin üst bilgilerinden varsayılan olarak kaldırılır. Makine Yöneticisi ve uygulama dağıtıcısı, olası kişisel bilgileri günlüğe kaydetmek için yapılandırmayı değiştirmeli. Bununla birlikte, uygulamaya özgü üst bilgilerde yer alan kişisel bilgilere izlemeler de kaydedilir. Uygulama dağıtıcı, yapılandırma ve izleme dosyalarındaki ACL 'Leri ayarlamaktan sorumludur. Ayrıca, bu bilgilerin görünür olmasını istememesi durumunda izlemeyi kapatabilir veya günlüğe kaydedildikten sonra bu bilgileri izleme dosyalarından filtreleyebilirler.  
  
 ServiceModel Izlemenin bir parçası olarak, benzersiz kimlikler (etkinlik kimlikleri olarak adlandırılır ve tipik olarak bir GUID), altyapının farklı bölümleriyle bir ileti akışı olarak farklı etkinlikleri birbirine bağlar.  
  
#### <a name="custom-trace-listeners"></a>Özel Izleme dinleyicileri  
 İleti günlüğe kaydetme ve izleme için, bir özel izleme dinleyicisi yapılandırılabilir ve bu da, hatta (örneğin, uzak bir veritabanına) izlemeleri ve iletileri gönderebilirler. Uygulama dağıtıcı, özel dinleyicileri yapılandırmadan veya kullanıcıların bunu yapabilmesini sağlamaktan sorumludur. Ayrıca, uzak konumda sunulan kişisel bilgilerden da sorumludur ve ACL 'Leri bu konuma doğru şekilde uygulamak için de sorumludur.  
  
### <a name="other-features-for-it-professionals"></a>BT uzmanlarına yönelik diğer özellikler  
 WCF, WMI aracılığıyla WCF altyapı yapılandırma bilgilerini kullanıma sunan bir WMI sağlayıcısına sahiptir (Windows ile gönderilir). Varsayılan olarak, WMI arabirimi Yöneticiler tarafından kullanılabilir.  
  
 WCF yapılandırması .NET Framework yapılandırma mekanizmasını kullanır. Yapılandırma dosyaları makinede depolanır. Uygulama geliştiricisi ve Yöneticisi, uygulama gereksinimlerinin her biri için yapılandırma dosyalarını ve ACL 'yi oluşturur. Yapılandırma dosyası, uç nokta adreslerini ve sertifika deposundaki sertifikalara bağlantıları içerebilir. Sertifikalar, uygulama tarafından kullanılan özelliklerin çeşitli özelliklerini yapılandırmak için uygulama verileri sağlamak üzere kullanılabilir.  
  
 WCF Ayrıca, <xref:System.Environment.FailFast%2A> yöntemini çağırarak .NET Framework işlem dökümü işlevini kullanır.  
  
### <a name="it-pro-tools"></a>BT uzmanı araçları  
 WCF Ayrıca, Windows SDK teslim eden aşağıdaki BT uzmanı araçlarını da sağlar.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Görüntüleyici, WCF izleme dosyalarını görüntüler. Görüntüleyici, izlemelerde hangi bilgilerin yer aldığı bilgisini gösterir.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Düzenleyici, kullanıcının WCF yapılandırma dosyalarını oluşturmasına ve düzenlemesine izin verir. Düzenleyici, yapılandırma dosyalarında hangi bilgilerin yer aldığı bilgisini gösterir. Aynı görev bir metin Düzenleyicisi ile gerçekleştirilebilir.  
  
#### <a name="servicemodel_reg"></a>ServiceModel_Reg  
 Bu araç, kullanıcının bir makinedeki ServiceModel yüklemelerini yönetmesine olanak tanır. Araç, çalışırken bir konsol penceresinde durum iletilerini görüntüler ve süreçte, WCF yüklemesinin yapılandırmasıyla ilgili bilgileri görüntüleyebilir.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig. exe ve WSATUı. dll  
 Bu araçlar, BT uzmanlarının WCF 'de birlikte çalışabilen WS-AtomicTransaction ağ desteğini yapılandırmasına izin verir. Araçlar, kullanıcının kayıt defterinde depolanan en sık kullanılan WS-AtomicTransaction ayarlarının değerlerini değiştirmesine ve değiştirmesine izin verir.  
  
## <a name="cross-cutting-features"></a>Çapraz kesme özellikleri  
 Aşağıdaki özellikler çapraz kesme. Diğer bir deyişle, önceki özelliklerden herhangi biri ile birleştirilebilir.  
  
### <a name="service-framework"></a>Hizmet Çerçevesi  
 Üst bilgiler bir CLR sınıfının örneğiyle bir iletiyi ilişkilendiren GUID olan bir örnek KIMLIĞI içerebilir.  
  
 Web Hizmetleri Açıklama Dili (WSDL), bağlantı noktasının tanımını içerir. Her bağlantı noktasının bir uç nokta adresi ve uygulama tarafından kullanılan hizmetleri temsil eden bir bağlaması vardır. WSDL 'nin kullanıma sunulmasına yapılandırma kullanılarak kapatılabilir. Makinede bilgi korunmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation](index.md)
- [Güvenlik](./feature-details/security.md)
