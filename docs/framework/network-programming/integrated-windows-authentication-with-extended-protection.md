---
title: Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: c4afc008f600c9be0040f8d7623f5e20623dfd7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444238"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
Tümleşik Windows kimlik doğrulamasının, <xref:System.Net.Security.NegotiateStream>ve ilgili ad alanlarında <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net> ve ilgili sınıflar tarafından nasıl işlendiğini etkileyen geliştirmeler yapılmıştır. Güvenliği artırmak için genişletilmiş koruma için destek eklendi.  
  
 Bu değişiklikler, Web istekleri yapmak ve tümleşik Windows kimlik doğrulamasının kullanıldığı durumlarda yanıtları almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış Web sunucularını ve istemci uygulamalarını da etkileyebilir.  
  
 Bu değişiklikler Ayrıca, diğer istek türlerini yapmak ve tümleşik Windows kimlik doğrulamasının kullanıldığı yanıtları almak için bu sınıfları kullanan uygulamaları etkileyebilir.  
  
 Genişletilmiş korumayı destekleyen değişiklikler yalnızca Windows 7 ve Windows Server 2008 R2 'deki uygulamalar için kullanılabilir. Genişletilmiş koruma özellikleri Windows 'un önceki sürümlerinde bulunmaz.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulamasının tasarımı, bazı kimlik bilgileri sınama yanıtlarının evrensel olmasına olanak sağlar, yani yeniden kullanılabilir veya iletilebilirler. Sınama yanıtlarının, hedef özel bilgilerle en az bir şekilde oluşturulması gerekir ve tercihen kanala özgü bilgiler de vardır. Hizmetler, kimlik bilgisi sınama yanıtlarının hizmet asıl adı (SPN) gibi hizmet özel bilgilerini içermesini sağlamak için genişletilmiş koruma sağlayabilir. Kimlik bilgileri değişimlerinde bu bilgilerle hizmetler, yanlış şekilde kullanılmamış olabilecek kimlik bilgisi sınama yanıtlarının kötü amaçlı kullanımına karşı daha iyi koruma sağlayabiliyor.  
  
 Genişletilmiş koruma tasarımı, kimlik doğrulama geçiş saldırılarını azaltmak için tasarlanan kimlik doğrulama protokollerine yönelik bir geliştirmedir. Kanal ve hizmet bağlama bilgileri kavramının etrafında döner.  
  
 Genel amaçlar şunlardır:  
  
1. İstemci genişletilmiş korumayı destekleyecek şekilde güncelleştirilirse, uygulamalar desteklenen tüm kimlik doğrulama protokollerine bir kanal bağlama ve hizmet bağlama bilgisi sağlamalıdır. Kanal bağlama bilgileri yalnızca bağlanacak bir kanal (TLS) olduğunda sağlanabilir. Hizmet bağlama bilgileri her zaman sağlanmalıdır.  
  
2. Düzgün şekilde yapılandırılan güncelleştirilmiş sunucular, istemci kimlik doğrulaması belirtecinde mevcut olduğunda kanal ve hizmet bağlama bilgilerini doğrulayamaz ve kanal bağlamaları eşleşmezse kimlik doğrulama denemesini reddeder. Dağıtım senaryosuna bağlı olarak, sunucular kanal bağlamayı, hizmet bağlamasını veya her ikisini de doğrulayamayabilir.  
  
3. Güncelleştirilmiş sunucular, ilke temelinde kanal bağlama bilgilerini içermeyen alt düzey istemci isteklerini kabul etme veya reddetme özelliğine sahiptir.  
  
 Genişletilmiş koruma tarafından kullanılan bilgiler, aşağıdaki iki bölümden birini veya her ikisini oluşur:  
  
1. Bir kanal bağlama belirteci veya CBT.  
  
2. Hizmet ana adı veya SPN biçimindeki hizmet bağlama bilgileri.  
  
 Hizmet bağlama bilgileri, bir istemcinin belirli bir hizmet uç noktasında kimlik doğrulama amacını belirtir. Aşağıdaki özelliklerle istemciden sunucuya iletilir:  
  
- SPN değeri, istemci kimlik doğrulamasını açık metin biçiminde gerçekleştiren sunucu için kullanılabilir olmalıdır.  
  
- SPN 'nin değeri geneldir.  
  
- SPN, bir ortadaki adam saldırısı tarafından bir değeri ekleyemiyor, kaldıramadığı veya değiştiremeyeceğiniz için şifreli olarak iletimde korunmalıdır.  
  
 CBT, iç, istemci tarafından kimliği doğrulanmış bir kanaldan konuşmaya bağlamak (örneğin, TLS) için kullanılan dış güvenli kanalın bir özelliğidir. CBT 'nin aşağıdaki özellikleri olması gerekir (IETF RFC 5056 tarafından da tanımlanmıştır):  
  
- Bir dış kanal varsa, CBT 'nin değeri, bir konuşmanın hem istemci hem de sunucu taraflarından bağımsız olarak gelen dış kanalı veya sunucu uç noktasını tanımlayan bir özellik olmalıdır.  
  
- İstemci tarafından gönderilen CBT 'nin değeri bir saldırganın etkileyebilecek bir şey olmamalıdır.  
  
- CBT değerinin gizliliği hakkında hiçbir garanti yapılmaz. Bu, ancak hizmet bağlamasının ve kanal bağlama bilgilerinin değerinin her zaman, CBT 'yi taşıyan protokol şifrelediğinden, kimlik doğrulaması gerçekleştiren sunucu tarafından her zaman incelenbileceği anlamına gelir.  
  
- CBT, bir saldırganın değerini ekleyemiyor, kaldıramadığı veya değiştiremeyeceğiniz için, aktarımda şifreli olarak korunması gerekir.  
  
 Kanal bağlama, istemci tarafından, bir WBT 'yi bir WBT 'nin bir WBT düzeltme ile sunucuya aktardığından elde edilir. Sunucu, ilke ile uyumlu olarak kanal bağlama bilgilerini doğrular ve kendisine amaçlanan hedefe inanmadığını düşünmediği kimlik doğrulama girişimlerini reddeder. Bu şekilde, iki kanal şifreli olarak birbirine bağlanır.  
  
 Mevcut istemciler ve uygulamalarla uyumluluğu korumak için bir sunucu, henüz genişletilmiş korumayı desteklemeyen istemciler tarafından yapılan kimlik doğrulama girişimlerine izin verecek şekilde yapılandırılabilir. Bu, "tamamen sağlamlaştırılmış" bir yapılandırmanın aksine "kısmen sağlamlaştırılmış" bir yapılandırma olarak adlandırılır.  
  
 <xref:System.Net> ve <xref:System.Net.Security> ad alanlarındaki birden çok bileşen, çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirir. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımıyla genişletilmiş koruma eklemek için System.Net bileşenlerinde yapılan değişiklikler açıklanmaktadır.  
  
 Genişletilmiş koruma Şu anda Windows 7 ' de desteklenmektedir. Bir mekanizma, uygulamanın işletim sisteminin genişletilmiş korumayı destekleyip desteklemediğini belirleyebilmesi için sağlanır.  
  
## <a name="changes-to-support-extended-protection"></a>Genişletilmiş korumayı destekleyen değişiklikler  
 Kullanılan kimlik doğrulama protokolüne bağlı olarak tümleşik Windows kimlik doğrulaması ile kullanılan kimlik doğrulama işlemi, genellikle hedef bilgisayar tarafından verilen bir sınama içerir ve istemci bilgisayara geri gönderilir. Genişletilmiş koruma bu kimlik doğrulama işlemine yeni özellikler ekler  
  
 <xref:System.Security.Authentication.ExtendedProtection> ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulaması için destek sağlar. Bu ad alanındaki <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> sınıfı bir kanal bağlamasını temsil eder. Bu ad alanındaki <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> sınıfı, sunucu tarafından gelen istemci bağlantılarını doğrulamak için kullanılan genişletilmiş koruma ilkesini temsil eder. Diğer sınıf üyeleri genişletilmiş koruma ile kullanılır.  
  
 Sunucu uygulamaları için, bu sınıflar şunları içerir:  
  
 Aşağıdaki öğelere sahip bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>:  
  
- İşletim sisteminin genişletilmiş koruma ile tümleşik Windows kimlik doğrulamasını destekleyip desteklemediğini gösteren <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> özelliği.  
  
- Genişletilmiş koruma ilkesinin ne zaman uygulanacağını gösteren <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> değeri.  
  
- Dağıtım senaryosunu belirten bir <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> değeri. Bu, genişletilmiş korumanın nasıl denetlendiğini etkiler.  
  
- İstemci tarafından kimlik doğrulamanın amaçlanan hedefi olarak belirtilen SPN ile eşleştirmek için kullanılan özel SPN listesini içeren isteğe bağlı bir <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection>.  
  
- Doğrulama için kullanılacak özel bir kanal bağlamayı içeren isteğe bağlı bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>. Bu senaryo ortak bir durum değildir  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulamanın yapılandırılması için destek sağlar.  
  
 Mevcut <xref:System.Net> ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapılmıştır. Bu değişiklikler şunları içerir:  
  
- Bir aktarım bağlamını temsil eden <xref:System.Net> ad alanına eklenen yeni bir <xref:System.Net.TransportContext> sınıfı.  
  
- <xref:System.Net.HttpWebRequest> sınıfında, istemci uygulamaları için genişletilmiş korumayı desteklemek için <xref:System.Net.TransportContext> almaya izin veren yeni <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> ve <xref:System.Net.HttpWebRequest.GetRequestStream%2A> aşırı yükleme yöntemleri.  
  
- Sunucu uygulamalarını desteklemek için <xref:System.Net.HttpListener> ve <xref:System.Net.HttpListenerRequest> sınıflarına ekler.  
  
 Mevcut <xref:System.Net.Mail> ad alanındaki SMTP istemci uygulamaları için genişletilmiş korumayı desteklemeye yönelik bir özellik değişikliği yapılmıştır:  
  
- SMTP istemci uygulamaları için genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılacak SPN 'YI temsil eden <xref:System.Net.Mail.SmtpClient> sınıfında bir <xref:System.Net.Mail.SmtpClient.TargetName%2A> özelliği.  
  
 Mevcut <xref:System.Net.Security> ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapılmıştır. Bu değişiklikler şunları içerir:  
  
- Bir CBT 'nin istemci uygulamaları için genişletilmiş korumayı desteklemeye izin veren <xref:System.Net.Security.NegotiateStream> sınıfında yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> aşırı yükleme yöntemleri.  
  
- Yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A>, sunucu uygulamaları için genişletilmiş korumayı desteklemeye <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> izin veren <xref:System.Net.Security.NegotiateStream> sınıfında aşırı yükleme yöntemleri.  
  
- İstemci ve sunucu uygulamaları için genişletilmiş korumayı desteklemek üzere <xref:System.Net.Security.SslStream> sınıfında yeni bir <xref:System.Net.Security.SslStream.TransportContext%2A> özelliği.  
  
 <xref:System.Net.Security> ad alanındaki SMTP istemcileri için genişletilmiş koruma yapılandırmasını desteklemek için bir <xref:System.Net.Configuration.SmtpNetworkElement> özelliği eklenmiştir.  
  
## <a name="extended-protection-for-client-applications"></a>Istemci uygulamaları için genişletilmiş koruma  
 Çoğu istemci uygulaması için genişletilmiş koruma desteği otomatik olarak gerçekleşir. <xref:System.Net.HttpWebRequest> ve <xref:System.Net.Mail.SmtpClient> sınıfları, Windows 'un temeldeki sürümü genişletilmiş korumayı her desteklediğinde genişletilmiş korumayı destekler. Bir <xref:System.Net.HttpWebRequest> örnek, <xref:System.Uri>oluşturulan bir SPN gönderir. Varsayılan olarak, bir <xref:System.Net.Mail.SmtpClient> örneği SMTP posta sunucusunun ana bilgisayar adından oluşturulmuş bir SPN gönderir.  
  
 Özel kimlik doğrulaması için istemci uygulamaları, <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemini kullanarak <xref:System.Net.TransportContext> ve CBT 'yi almaya izin veren <xref:System.Net.HttpWebRequest> sınıfında <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> veya <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> yöntemlerini kullanabilir.  
  
 Bir <xref:System.Net.HttpWebRequest> örneği tarafından verilen bir hizmete gönderilen tümleşik Windows kimlik doğrulaması için kullanılacak SPN, <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özelliği ayarlanarak geçersiz kılınabilir.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> özelliği, SMTP bağlantısı için tümleşik Windows kimlik doğrulaması için kullanmak üzere özel bir SPN ayarlamak için kullanılabilir.  
  
## <a name="extended-protection-for-server-applications"></a>Sunucu uygulamaları için genişletilmiş koruma  
 <xref:System.Net.HttpListener> otomatik olarak HTTP kimlik doğrulaması gerçekleştirirken hizmet bağlamalarını doğrulamaya yönelik mekanizmalar sağlar.  
  
 En güvenli senaryo, HTTPS://önekleri için genişletilmiş korumayı etkinleştirmektir. Bu durumda, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>olarak ayarlanmış bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> ayarlayın ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> bir <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> bir değeri <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, tamamen sağlamlaştırılmış moda karşılık gelen olarak ayarlayın.  
  
 Bu yapılandırmada, bir dış güvenli kanal üzerinden sunucuya bir istek yapıldığında, dış kanal bir kanal bağlaması için sorgulanır. Bu kanal bağlaması kimlik doğrulama SSPI çağrılarına geçirilir ve bu da kimlik doğrulama blobu içindeki kanal bağlamasının eşleştiğini doğrular. Üç olası sonuç vardır:  
  
1. Sunucunun temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
2. SSPI çağrısı, istemcinin dış kanaldan alınan beklenen değerle eşleşmeyen bir kanal bağlaması belirtmediğini veya sunucudaki genişletilmiş koruma ilkesi <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>için yapılandırıldığında bir kanal bağlama sağlayamadığını belirten başarısız olur. Her iki durumda da istek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
3. İstemci doğru kanal bağlamasını belirtir veya sunucu üzerindeki genişletilmiş koruma ilkesi <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> ile yapılandırıldığından, istek işlenmek üzere uygulamaya döndürüldüğünden, bir kanal bağlaması belirtmeden bağlanmasına izin verilir. Hiçbir hizmet adı denetimi otomatik olarak gerçekleştirilmez. Bir uygulama <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliğini kullanarak kendi hizmet adı doğrulamasını gerçekleştirmeyi tercih edebilir, ancak bu koşullarda gereksizdir.  
  
 Bir uygulama, bir HTTP isteği gövdesinde geri alınan bloblara dayalı olarak kimlik doğrulaması yapmak için kendi SSPI çağrılarını yapıyorsa ve kanal bağlamayı desteklemeye devam ediyorsanız, yerel Win32 [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine geçirmek için <xref:System.Net.HttpListener> kullanarak dış Güvenli kanaldan beklenen kanal bağlamasını alması gerekir. Bunu yapmak için <xref:System.Net.HttpListenerRequest.TransportContext%2A> özelliğini kullanın ve CBT 'yi almak için <xref:System.Net.TransportContext.GetChannelBinding%2A> metodunu çağırın. Yalnızca uç nokta bağlamaları desteklenir. Başka herhangi bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> belirtilirse, bir <xref:System.NotSupportedException> oluşturulur. Temeldeki işletim sistemi kanal bağlamayı destekliyorsa, <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi, `pInput` parametresine geçirilen bir SecBuffer yapısının pvBuffer üyesi olarak [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine geçiş için uygun bir kanal bağlamasının işaretçisini sarmaladığı bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>döndürür <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> özelliği, kanal bağlamasının uzunluğunu bayt cinsinden içerir. Temeldeki işletim sistemi kanal bağlamalarını desteklemiyorsa, işlev `null`döndürür.  
  
 Diğer bir olası senaryo, proxy 'ler kullanılmazsa HTTP://ön ekleri için genişletilmiş korumayı etkinleştirmektir. Bu durumda, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>olarak ayarlanmış bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> ayarlayın ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> bir <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> bir değeri <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, tamamen sağlamlaştırılmış moda karşılık gelen olarak ayarlayın.  
  
 İzin verilen hizmet adlarının varsayılan listesi, <xref:System.Net.HttpListener>kayıtlı olan öneklere göre oluşturulur. Bu varsayılan liste <xref:System.Net.HttpListener.DefaultServiceNames%2A> özelliği aracılığıyla incelenebilir. Bu liste kapsamlı değilse, bir uygulama, varsayılan hizmet adı listesi yerine kullanılacak <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> sınıfı için oluşturucuda özel bir hizmet adı koleksiyonu belirtebilir.  
  
 Bu yapılandırmada, dış güvenli kanal kimlik doğrulaması olmadan sunucuya bir istek yapıldığında, bir kanal bağlama denetimi olmadan normal olarak devam eder. Kimlik doğrulaması başarılı olursa, içerik istemcinin tarafından sağlanmış ve kabul edilebilir hizmet adları listesine göre doğrulanan hizmet adı için sorgulanır. Dört olası sonuç vardır:  
  
1. Sunucunun temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
2. İstemcinin temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> yapılandırmasında, kimlik doğrulama denemesi başarılı olur ve istek uygulamaya döndürülür. <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> yapılandırmasında, kimlik doğrulama denemesi başarısız olur. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
3. İstemcinin temeldeki işletim sistemi genişletilmiş korumayı destekliyor, ancak uygulama bir hizmet bağlaması belirtmedi. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
4. İstemci bir hizmet bağlaması belirtti. Hizmet bağlama, izin verilen hizmet bağlamaları listesiyle karşılaştırılır. Eşleşiyorsa, istek uygulamaya döndürülür. Aksi takdirde, istek uygulamaya gösterilmez ve istemciye otomatik olarak bir yetkisiz (401) yanıtı döndürülür. Hatanın nedenini belirten <xref:System.Net.HttpListener> izleme kaynağına bir ileti kaydedilir.  
  
 Kabul edilebilir hizmet adlarının izin verilen bir listesini kullanan bu basit yaklaşım yetersizse, bir uygulama <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliğini sorgulayarak kendi hizmet adı doğrulamasını sağlayabilir. Yukarıdaki 1 ve 2. durumlarda, özelliği `null`döndürür. 3\. durumda, boş bir dize döndürür. 4\. durumda, istemci tarafından belirtilen hizmet adı döndürülür.  
  
 Bu genişletilmiş koruma özellikleri, sunucu uygulamaları tarafından diğer istek türleri ve güvenilen proxy 'ler kullanıldığında kimlik doğrulaması için de kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
