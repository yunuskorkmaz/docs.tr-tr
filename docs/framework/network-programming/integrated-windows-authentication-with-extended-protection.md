---
title: Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: d69471f4be0f102381dee4fc5037e8f8b0c625c3
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144857"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
Tümleşik Windows kimlik doğrulamasının <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpListener> <xref:System.Net.Mail.SmtpClient> <xref:System.Net.Security.SslStream> <xref:System.Net.Security.NegotiateStream> <xref:System.Net> ve ilgili ad alanlarında,,,, ve ilgili sınıfların işlenme biçimini etkileyen geliştirmeler yapılmıştır. Güvenliği artırmak için genişletilmiş koruma için destek eklendi.  
  
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
  
 Ve ad alanlarında birden çok bileşen, <xref:System.Net> <xref:System.Net.Security> çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirir. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımıyla genişletilmiş koruma eklemek için System.Net bileşenlerinde yapılan değişiklikler açıklanmaktadır.  
  
 Genişletilmiş koruma Şu anda Windows 7 ' de desteklenmektedir. Bir mekanizma, uygulamanın işletim sisteminin genişletilmiş korumayı destekleyip desteklemediğini belirleyebilmesi için sağlanır.  
  
## <a name="changes-to-support-extended-protection"></a>Genişletilmiş korumayı destekleyen değişiklikler  
 Kullanılan kimlik doğrulama protokolüne bağlı olarak tümleşik Windows kimlik doğrulaması ile kullanılan kimlik doğrulama işlemi, genellikle hedef bilgisayar tarafından verilen bir sınama içerir ve istemci bilgisayara geri gönderilir. Genişletilmiş koruma bu kimlik doğrulama işlemine yeni özellikler ekler  
  
 <xref:System.Security.Authentication.ExtendedProtection>Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulaması için destek sağlar. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>Bu ad alanındaki sınıfı bir kanal bağlamasını temsil eder. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>Bu ad alanındaki sınıf, sunucu tarafından gelen istemci bağlantılarını doğrulamak için kullanılan genişletilmiş koruma ilkesini temsil eder. Diğer sınıf üyeleri genişletilmiş koruma ile kullanılır.  
  
 Sunucu uygulamaları için, bu sınıflar şunları içerir:  
  
 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>Aşağıdaki öğeleri içeren bir.:  
  
- <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A>İşletim sisteminin genişletilmiş koruma ile tümleşik Windows kimlik doğrulamasını destekleyip desteklemediğini gösteren bir özellik.  
  
- <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>Genişletilmiş koruma ilkesinin ne zaman uygulanacağını gösteren bir değer.  
  
- <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario>Dağıtım senaryosunu belirten bir değer. Bu, genişletilmiş korumanın nasıl denetlendiğini etkiler.  
  
- <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection>İstemci tarafından kimlik doğrulamanın amaçlanan hedefi olarak BELIRTILEN SPN ile eşleştirmek için kullanılan özel SPN listesini içeren isteğe bağlı.  
  
- <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>Doğrulama için kullanılacak özel bir kanal bağlamayı içeren isteğe bağlı. Bu senaryo ortak bir durum değildir  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulamanın yapılandırılması için destek sağlar.  
  
 Mevcut ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapılmıştır <xref:System.Net> . Bu değişiklikler şunları içerir:  
  
- <xref:System.Net.TransportContext> <xref:System.Net> Bir aktarım bağlamını temsil eden ad alanına eklenen yeni bir sınıf.  
  
- <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> <xref:System.Net.HttpWebRequest.GetRequestStream%2A> <xref:System.Net.HttpWebRequest> Sınıfında, <xref:System.Net.TransportContext> istemci uygulamaları için genişletilmiş korumayı desteklemek için ' a almaya imkan tanıyan yeni ve aşırı yükleme yöntemleri.  
  
- <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest> Sunucu uygulamalarını desteklemek için ve sınıflarına ekler.  
  
 Mevcut ad alanındaki SMTP istemci uygulamaları için genişletilmiş korumayı desteklemeye yönelik bir özellik değişikliği yapıldı <xref:System.Net.Mail> :  
  
- <xref:System.Net.Mail.SmtpClient.TargetName%2A>, <xref:System.Net.Mail.SmtpClient> SMTP istemci uygulamaları için genişletilmiş koruma kullanılırken kimlik doğrulaması için kullanılacak SPN 'yi temsil eden sınıfta bulunan bir özelliktir.  
  
 Mevcut ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapılmıştır <xref:System.Net.Security> . Bu değişiklikler şunları içerir:  
  
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> <xref:System.Net.Security.NegotiateStream> Sınıfında bir CBT 'nin istemci uygulamaları için genişletilmiş korumayı desteklemesini sağlayan yeni ve aşırı yükleme yöntemleri.  
  
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> <xref:System.Net.Security.NegotiateStream> Sınıfında <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> sunucu uygulamaları için genişletilmiş korumayı desteklemeye izin veren yeni ve aşırı yükleme yöntemleri.  
  
- <xref:System.Net.Security.SslStream.TransportContext%2A> <xref:System.Net.Security.SslStream> İstemci ve sunucu uygulamaları için genişletilmiş korumayı desteklemek için sınıfında yeni bir özellik.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement>Ad ALANıNDAKI SMTP istemcileri için genişletilmiş koruma yapılandırmasını desteklemek için bir özellik eklenmiştir <xref:System.Net.Security> .  
  
## <a name="extended-protection-for-client-applications"></a>Istemci uygulamaları için genişletilmiş koruma  
 Çoğu istemci uygulaması için genişletilmiş koruma desteği otomatik olarak gerçekleşir. <xref:System.Net.HttpWebRequest>Ve <xref:System.Net.Mail.SmtpClient> sınıfları, temel alınan Windows sürümü genişletilmiş korumayı desteklediğinde genişletilmiş korumayı destekler. Bir <xref:System.Net.HttpWebRequest> örnek, öğesinden oluşturulan BIR spn gönderir <xref:System.Uri> . Varsayılan olarak, bir <xref:System.Net.Mail.SmtpClient> örnek SMTP posta sunucusunun ana bilgisayar adından oluşturulmuş BIR spn gönderir.  
  
 Özel kimlik doğrulaması için, istemci uygulamaları, <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest> <xref:System.Net.TransportContext> yöntemini kullanarak ve CBT 'yi almaya izin veren sınıfında veya yöntemlerini kullanabilir <xref:System.Net.TransportContext.GetChannelBinding%2A> .  
  
 Belirli bir hizmete bir örnek tarafından gönderilen tümleşik Windows kimlik doğrulaması için kullanılacak SPN, <xref:System.Net.HttpWebRequest> özelliği ayarlanarak geçersiz kılınabilir <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> .  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A>Özelliği, SMTP bağlantısı için tümleşik Windows kimlik doğrulaması için kullanmak üzere özel bır SPN ayarlamak için kullanılabilir.  
  
## <a name="extended-protection-for-server-applications"></a>Sunucu uygulamaları için genişletilmiş koruma  
 <xref:System.Net.HttpListener>, HTTP kimlik doğrulaması gerçekleştirirken hizmet bağlamalarını doğrulamaya yönelik mekanizmalar otomatik olarak sağlar.  
  
 En güvenli senaryo, ön ekler için genişletilmiş korumayı etkinleştirmektir `HTTPS://` . Bu durumda, veya olarak <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> ayarlanan olarak <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ayarlayın <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> kısmen <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> sağlamlaştırılmış modda bir değer olarak ayarlayın.  
  
 Bu yapılandırmada, bir dış güvenli kanal üzerinden sunucuya bir istek yapıldığında, dış kanal bir kanal bağlaması için sorgulanır. Bu kanal bağlaması kimlik doğrulama SSPI çağrılarına geçirilir ve bu da kimlik doğrulama blobu içindeki kanal bağlamasının eşleştiğini doğrular. Üç olası sonuç vardır:  
  
1. Sunucunun temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
2. SSPI çağrısı, istemcinin dış kanaldan alınan beklenen değerle eşleşmeyen bir kanal bağlaması belirtmediğini veya sunucu üzerinde genişletilmiş koruma ilkesi yapılandırıldığında bir kanal bağlama sağlayamadığını belirten bir hata verir <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> . Her iki durumda da istek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
3. İstemci doğru kanal bağlamasını belirtir veya sunucu üzerindeki genişletilmiş koruma ilkesi, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> işlenmek üzere uygulamaya döndürüldüğünden bu yana bir kanal bağlaması belirtmeden bağlanmasına izin verilir. Hiçbir hizmet adı denetimi otomatik olarak gerçekleştirilmez. Bir uygulama, özelliğini kullanarak kendi hizmet adı doğrulamasını gerçekleştirmeyi tercih edebilir <xref:System.Net.HttpListenerRequest.ServiceName%2A> , ancak bu koşullarda gereksizdir.  
  
 Bir uygulama, bir HTTP isteği gövdesinde geri alınan bloblara dayalı olarak kimlik doğrulaması yapmak için kendi SSPI çağrılarını yapıyorsa ve kanal bağlamayı desteklemeye devam ediyorsanız, <xref:System.Net.HttpListener> yerel Win32 [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine geçirmek için kullanarak dış Güvenli kanaldan beklenen kanal bağlamasını alması gerekir. Bunu yapmak için, <xref:System.Net.HttpListenerRequest.TransportContext%2A> <xref:System.Net.TransportContext.GetChannelBinding%2A> CBT 'yi almak için özelliğini ve Call metodunu kullanın. Yalnızca uç nokta bağlamaları desteklenir. Başka bir şey <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> belirtilmişse, bir <xref:System.NotSupportedException> oluşturulur. Temeldeki işletim sistemi kanal bağlamayı destekliyorsa, <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> parametre Içinde geçirilen bir SecBuffer öğesinin pvBuffer üyesi olarak [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine geçirmek için uygun bir kanal bağlamasının işaretçisini döndürür `pInput` . <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A>Özelliği, kanal bağlamasının uzunluğunu bayt cinsinden içerir. Temeldeki işletim sistemi kanal bağlamalarını desteklemiyorsa, işlev döndürür `null` .  
  
 Diğer bir olası senaryo, `HTTP://` proxy 'ler kullanılmazsa ön ekler için genişletilmiş korumayı etkinleştirmektir. Bu durumda, veya olarak <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> ayarlanan olarak <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ayarlayın <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> kısmen <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> sağlamlaştırılmış modda bir değer olarak ayarlayın.  
  
 İzin verilen hizmet adlarının varsayılan listesi, ile kaydedilmiş ön ekler temel alınarak oluşturulur <xref:System.Net.HttpListener> . Bu varsayılan liste, özelliği aracılığıyla incelenebilir <xref:System.Net.HttpListener.DefaultServiceNames%2A> . Bu liste kapsamlı değilse, bir uygulama, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> varsayılan hizmet adı listesi yerine kullanılacak sınıf için oluşturucuda özel bir hizmet adı koleksiyonu belirtebilir.  
  
 Bu yapılandırmada, dış güvenli kanal kimlik doğrulaması olmadan sunucuya bir istek yapıldığında, bir kanal bağlama denetimi olmadan normal olarak devam eder. Kimlik doğrulaması başarılı olursa, içerik istemcinin tarafından sağlanmış ve kabul edilebilir hizmet adları listesine göre doğrulanan hizmet adı için sorgulanır. Dört olası sonuç vardır:  
  
1. Sunucunun temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
2. İstemcinin temel aldığı işletim sistemi, genişletilmiş korumayı desteklemiyor. <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported>Yapılandırmada kimlik doğrulama denemesi başarılı olur ve istek uygulamaya döndürülür. <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>Yapılandırmada kimlik doğrulama denemesi başarısız olur. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
3. İstemcinin temeldeki işletim sistemi genişletilmiş korumayı destekliyor, ancak uygulama bir hizmet bağlaması belirtmedi. İstek uygulamaya gösterilmez ve istemciye yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
4. İstemci bir hizmet bağlaması belirtti. Hizmet bağlama, izin verilen hizmet bağlamaları listesiyle karşılaştırılır. Eşleşiyorsa, istek uygulamaya döndürülür. Aksi takdirde, istek uygulamaya gösterilmez ve istemciye otomatik olarak bir yetkisiz (401) yanıtı döndürülür. <xref:System.Net.HttpListener>Hatanın nedenini belirten izleme kaynağına bir ileti kaydedilir.  
  
 Kabul edilebilir hizmet adlarının izin verilen bir listesini kullanan bu basit yaklaşım yetersizse, bir uygulama özelliği sorgulayarak kendi hizmet adı doğrulamasını sağlayabilir <xref:System.Net.HttpListenerRequest.ServiceName%2A> . Yukarıdaki 1 ve 2. durumlarda özelliği döndürülür `null` . 3. durumda, boş bir dize döndürür. 4. durumda, istemci tarafından belirtilen hizmet adı döndürülür.  
  
 Bu genişletilmiş koruma özellikleri, sunucu uygulamaları tarafından diğer istek türleri ve güvenilen proxy 'ler kullanıldığında kimlik doğrulaması için de kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
