---
title: Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: c4afc008f600c9be0040f8d7623f5e20623dfd7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74444238"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
Tümleşik <xref:System.Net.HttpWebRequest>Windows kimlik doğrulamasının, ilgili ad <xref:System.Net.HttpListener>alanlarındaki , <xref:System.Net.Mail.SmtpClient>, , <xref:System.Net.Security.SslStream> <xref:System.Net.Security.NegotiateStream> <xref:System.Net> , ve ilgili sınıflar tarafından nasıl işleneceğini etkileyen geliştirmeler yapıldı. Güvenliği artırmak için genişletilmiş koruma için destek eklendi.  
  
 Bu değişiklikler, web istekleri yapmak ve tümleşik Windows kimlik doğrulaması kullanıldığında yanıt almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılan web sunucularını ve istemci uygulamalarını da etkileyebilir.  
  
 Bu değişiklikler, diğer istek türlerini yapmak ve tümleşik Windows kimlik doğrulaması kullanıldığında yanıt almak için bu sınıfları kullanan uygulamaları da etkileyebilir.  
  
 Genişletilmiş korumayı destekleyen değişiklikler yalnızca Windows 7 ve Windows Server 2008 R2'deki uygulamalar için kullanılabilir. Genişletilmiş koruma özellikleri Windows'un önceki sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulamasının tasarımı, bazı kimlik bilgisi meydan okuma yanıtlarının evrensel olmasını sağlar, bu da yeniden kullanılabilir veya iletilebilir. Meydan okuma yanıtları en azından hedefe özgü bilgilerle ve tercihen de bazı kanala özgü bilgilerle oluşturulmalıdır. Hizmetler daha sonra, kimlik bilgisi meydan okuma yanıtlarının Hizmet Ana Adı (SPN) gibi hizmete özgü bilgiler içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi alışverişindeki bu bilgilerle, hizmetler yanlış kullanılmış olabilecek kimlik bilgisi zoru yanıtlarının kötü amaçlı kullanımına karşı daha iyi koruma sağlayabilir.  
  
 Genişletilmiş koruma tasarımı, kimlik doğrulama röle saldırılarını azaltmak için tasarlanmış kimlik doğrulama protokolleri için bir geliştirmedir. Kanal ve hizmet bağlayıcı bilgi kavramı etrafında döner.  
  
 Genel hedefler şunlardır:  
  
1. İstemci genişletilmiş korumayı destekleyecek şekilde güncelleştirilirse, uygulamalar desteklenen tüm kimlik doğrulama protokollerine bir kanal bağlama ve hizmet bağlama bilgileri sağlamalıdır. Kanal bağlama bilgileri yalnızca bağlanacak bir kanal (TLS) olduğunda sağlanabilir. Hizmet bağlama bilgileri her zaman sağlanmalıdır.  
  
2. Düzgün şekilde yapılandırılan güncelleştirilmiş sunucular, istemci kimlik doğrulama belirtecinde bulunduğunda kanal ve hizmet bağlama bilgilerini doğrulayabilir ve kanal bağlamaları eşleşmiyorsa kimlik doğrulama girişimini reddedebilir. Dağıtım senaryosuna bağlı olarak, sunucular kanal bağlamayı, hizmet bağlamayı veya her ikisini birden doğrulayabilir.  
  
3. Güncelleştirilmiş sunucular, ilke yi temel alan kanal bağlama bilgilerini içermeyen alt düzey istemci isteklerini kabul etme veya reddetme yeteneğine sahiptir.  
  
 Genişletilmiş koruma tarafından kullanılan bilgiler aşağıdaki iki bölümden birini veya her ikisini birden oluşur:  
  
1. Kanal Bağlama Belirteci veya TCMB.  
  
2. Hizmet Ana Adı veya SPN biçiminde Hizmet Bağlama bilgileri.  
  
 Hizmet Bağlama bilgileri, istemcinin belirli bir hizmet bitiş noktasına kimlik doğrulama niyetinin bir göstergesidir. Aşağıdaki özelliklere sahip istemciden sunucuya iletilir:  
  
- SPN değeri, istemci kimlik doğrulamasını net metin biçiminde gerçekleştiren sunucu tarafından kullanılabilir olmalıdır.  
  
- SPN değeri herkese açıktır.  
  
- SPN, ortadaki adam saldırısının değerini ekleyememesi, kaldıramayacağı veya değiştiremeyeceği şekilde, geçiş sırasında şifreleme açısından korunmalıdır.  
  
 CBT, iç, istemci kimlik doğrulaması yapılan bir kanal üzerinden bir konuşmaya bağlamak (bağlamak) için kullanılan dış güvenli kanalın (TLS gibi) bir özelliğidir. TCMB aşağıdaki özelliklere sahip olmalıdır (Ayrıca IETF RFC 5056 tarafından tanımlanan):  
  
- Bir dış kanal varsa, TCMB'nin değeri, bir konuşmanın hem istemci hem de sunucu tarafları tarafından bağımsız olarak gelen dış kanalı veya sunucu bitiş noktasını tanımlayan bir özellik olmalıdır.  
  
- İstemci tarafından gönderilen TCMB değeri bir saldırganın etkileyebileceği bir şey olmamalıdır.  
  
- TCMB değerinin gizliliği konusunda hiçbir garanti yapılmaz. Ancak bu, hizmet bağlama nın değerinin yanı sıra kanal bağlama bilgilerinin, TCMB'yi taşıyan protokol şifreleniyor olabileceğinden, kimlik doğrulaması yapan sunucu dışında her zaman başka bir sunucu tarafından incelenebileceği anlamına gelmez.  
  
- TCMB, bir saldırganın değerini ekleyememesi, kaldıramayacağı veya değiştiremeyeceği şekilde, geçiş sırasında şifreleme bütünlüğü korunmalıdır.  
  
 Kanal bağlama, istemcinin SPN ve TCMB'yi kurcalamayan bir şekilde sunucuya aktarmasıyla gerçekleştirilir. Sunucu, kanal bağlama bilgilerini ilkesine uygun olarak doğrular ve kendisinin hedef olduğuna inanmadığı kimlik doğrulama girişimlerini reddeder. Bu şekilde, iki kanal şifreleme ile birbirine bağlıdır.  
  
 Varolan istemciler ve uygulamalarla uyumluluğu korumak için, bir sunucu henüz genişletilmiş korumayı desteklemeyen istemcilerin kimlik doğrulama girişimlerine izin verecek şekilde yapılandırılabilir. Bu, "tamamen sertleştirilmiş" yapılandırmanın aksine "kısmen sertleştirilmiş" yapılandırma olarak adlandırılır.  
  
 Ad <xref:System.Net> alanlarındave <xref:System.Net.Security> ad alanlarındaki birden çok bileşen, bir arama uygulaması adına tümleşik Windows kimlik doğrulaması gerçekleştirir. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımında genişletilmiş koruma eklemek için System.Net bileşenlerine yapılan değişiklikler açıklanmaktadır.  
  
 Genişletilmiş koruma şu anda Windows 7'de desteklenir. Bir uygulamanın işletim sisteminin genişletilmiş korumayı destekleyip desteklemeyebileceğini belirleyebilmeleri için bir mekanizma sağlanır.  
  
## <a name="changes-to-support-extended-protection"></a>Genişletilmiş Korumayı Destekleme Değişiklikleri  
 Kullanılan kimlik doğrulama protokolüne bağlı olarak tümleşik Windows kimlik doğrulamasıyla kullanılan kimlik doğrulama işlemi, genellikle hedef bilgisayar tarafından verilen ve istemci bilgisayara geri gönderilen bir meydan okuma içerir. Genişletilmiş koruma, bu kimlik doğrulama işlemine yeni özellikler ekler  
  
 Ad <xref:System.Security.Authentication.ExtendedProtection> alanı, uygulamalar için genişletilmiş koruma yı kullanarak kimlik doğrulama desteği sağlar. Bu <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> ad alanındaki sınıf bir kanal bağlamayı temsil eder. Bu <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ad alanındaki sınıf, sunucu tarafından gelen istemci bağlantılarını doğrulamak için kullanılan genişletilmiş koruma ilkesini temsil eder. Diğer sınıf üyeleri genişletilmiş koruma ile kullanılır.  
  
 Sunucu uygulamaları için bu sınıflar şunlardır:  
  
 Aşağıdaki <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> öğelere sahip a:  
  
- İşletim sisteminin genişletilmiş korumayla tümleşik windows kimlik doğrulamasını destekleyip desteklemediğini belirten bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> özellik.  
  
- Genişletilmiş <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> koruma ilkesinin ne zaman uygulanması gerektiğini belirten bir değer.  
  
- Dağıtım <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> senaryosunu gösteren bir değer. Bu, genişletilmiş korumanın nasıl denetlenir etkieder.  
  
- Kimlik <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> doğrulamanın amaçlanan hedefi olarak istemci tarafından sağlanan SPN ile eşleşmek için kullanılan özel SPN listesini içeren isteğe bağlı bir isteğe bağlı.  
  
- Doğrulama <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> için kullanılacak özel bir kanal bağlama içeren isteğe bağlı bir isteğe bağlı. Bu senaryo sık karşılaşılan bir durum değildir  
  
 Ad <xref:System.Security.Authentication.ExtendedProtection.Configuration> alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama yapılandırması için destek sağlar.  
  
 Varolan <xref:System.Net> ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapıldı. Bu değişiklikler şunlardır:  
  
- Aktarım <xref:System.Net.TransportContext> bağlamını <xref:System.Net> temsil eden ad alanına yeni bir sınıf eklendi.  
  
- İstemci <xref:System.Net.HttpWebRequest> uygulamaları için genişletilmiş korumayı desteklemek <xref:System.Net.TransportContext> için alma sağlayan sınıfta yeni <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> ve <xref:System.Net.HttpWebRequest.GetRequestStream%2A> aşırı yükleme yöntemleri.  
  
- Sunucu uygulamalarını <xref:System.Net.HttpListener> desteklemek <xref:System.Net.HttpListenerRequest> için eklemeler ve sınıflar.  
  
 Varolan <xref:System.Net.Mail> ad alanındaki SMTP istemci uygulamaları için genişletilmiş korumayı desteklemek için bir özellik değişikliği yapıldı:  
  
- SMTP <xref:System.Net.Mail.SmtpClient> istemci uygulamaları için genişletilmiş koruma kullanırken kimlik doğrulaması için kullanılacak SPN'yi temsil eden sınıftaki bir <xref:System.Net.Mail.SmtpClient.TargetName%2A> özellik.  
  
 Varolan <xref:System.Net.Security> ad alanında genişletilmiş korumayı desteklemek için bir dizi özellik değişikliği yapıldı. Bu değişiklikler şunlardır:  
  
- İstemci <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> <xref:System.Net.Security.NegotiateStream> uygulamaları için genişletilmiş korumayı desteklemek için bir CBT'nin geçmesini sağlayan sınıftaki yeni ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> aşırı yükleme yöntemleri.  
  
- Sunucu <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> uygulamaları için genişletilmiş korumayı desteklemek <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> için bir geçiş sağlayan sınıfta yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> ve aşırı yükleme yöntemleri. <xref:System.Net.Security.NegotiateStream>  
  
- İstemci <xref:System.Net.Security.SslStream.TransportContext%2A> <xref:System.Net.Security.SslStream> ve sunucu uygulamaları için genişletilmiş korumayı desteklemek için sınıfta yeni bir özellik.  
  
 Ad alanında SMTP istemcileri için genişletilmiş koruma yapılandırmasını desteklemek için bir <xref:System.Net.Configuration.SmtpNetworkElement> özellik eklendi. <xref:System.Net.Security>  
  
## <a name="extended-protection-for-client-applications"></a>İstemci Uygulamaları için Genişletilmiş Koruma  
 Çoğu istemci uygulaması için genişletilmiş koruma desteği otomatik olarak gerçekleşir. Windows'un <xref:System.Net.HttpWebRequest> temel sürümü genişletilmiş korumayı desteklediğinde ve <xref:System.Net.Mail.SmtpClient> sınıflar genişletilmiş korumayı destekler. Bir <xref:System.Net.HttpWebRequest> örnek, <xref:System.Uri>'den oluşturulmuş bir SPN gönderir. Varsayılan olarak, <xref:System.Net.Mail.SmtpClient> bir örnek SMTP posta sunucusunun ana bilgisayar adından oluşturulmuş bir SPN gönderir.  
  
 Özel kimlik doğrulaması için, istemci <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> uygulamaları, <xref:System.Net.HttpWebRequest> <xref:System.Net.TransportContext.GetChannelBinding%2A> bu yöntemi kullanarak cbt <xref:System.Net.TransportContext> ve alma sağlayan sınıfta veya yöntemleri kullanabilirsiniz.  
  
 Belirli bir hizmete bir <xref:System.Net.HttpWebRequest> örnek tarafından gönderilen tümleşik Windows kimlik doğrulaması için <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> kullanılacak SPN özelliği ayarlayarak geçersiz kılınabilir.  
  
 Özellik, <xref:System.Net.Mail.SmtpClient.TargetName%2A> SMTP bağlantısı için tümleşik Windows kimlik doğrulaması için kullanılacak özel bir SPN ayarlamak için kullanılabilir.  
  
## <a name="extended-protection-for-server-applications"></a>Sunucu Uygulamaları için Genişletilmiş Koruma  
 <xref:System.Net.HttpListener>http kimlik doğrulaması gerçekleştirirken hizmet bağlamalarını doğrulamak için otomatik olarak mekanizmalar sağlar.  
  
 En güvenli senaryo, HTTPS:// önekleri için genişletilmiş koruma yı etkinleştirmektir. Bu durumda, <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> tamamen sertleştirilmiş <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> moda <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>karşılık <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> gelirken, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> kısmen sertleştirilmiş modda koyar bir değer kümesi veya , ve a değeri ne ayarlanmış.  
  
 Bu yapılandırmada, bir dış güvenli kanal üzerinden sunucuya bir istek yapıldığında, dış kanal bir kanal bağlama için sorgulanır. Bu kanal bağlama, kimlik doğrulama blob eşleşen kanal bağlama doğrulamak kimlik doğrulama SSPI çağrıları, geçirilir. Üç olası sonuç vardır:  
  
1. Sunucunun temel işletim sistemi genişletilmiş korumayı desteklemez. İstek uygulamaya açıklanmaz ve yetkisiz (401) yanıt istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
2. SSPI çağrısı, istemcinin dış kanaldan alınan beklenen değerle eşleşmeyan bir kanal bağlama sı belirtileni veya sunucudaki genişletilmiş koruma ilkesi için <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>yapılandırıldığında kanal bağlama sağlamada başarısız olduğunu belirten başarısız oldu. Her iki durumda da, istek uygulamaya maruz kalınmaz ve yetkisiz (401) yanıt istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
3. İstemci doğru kanal bağlama belirtir veya sunucuda genişletilmiş koruma ilkesi ile yapılandırılan <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> bir kanal bağlama belirtmeden bağlanmak için izin verilir İstek işleme için uygulamaya döndürülür. Hiçbir hizmet adı denetimi otomatik olarak gerçekleştirilir. Bir uygulama <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliği kullanarak kendi hizmet adı doğrulama gerçekleştirmek için seçebilirsiniz, ancak bu koşullar altında gereksizdir.  
  
 Bir uygulama, bir HTTP isteğinin gövdesi içinde ileri geri aktarılan lekelere dayalı kimlik doğrulamasını gerçekleştirmek için kendi SSPI çağrılarını yaparsa ve kanal <xref:System.Net.HttpListener> bağlamayı desteklemek isterse, yerel Win32 [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine aktarmak için dış güvenli kanaldan beklenen kanalı bağlamayı alması gerekir. Bunu yapmak için, <xref:System.Net.HttpListenerRequest.TransportContext%2A> CBT <xref:System.Net.TransportContext.GetChannelBinding%2A> almak için özellik ve arama yöntemini kullanın. Yalnızca uç nokta bağlamaları desteklenir. Başka <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> bir şey belirtilirse, bir <xref:System.NotSupportedException> atılır. Altta yatan işletim sistemi kanal <xref:System.Net.TransportContext.GetChannelBinding%2A> bağlamayı destekliyorsa, yöntem, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> `pInput` parametrede geçirilen bir SecBuffer yapısının pvBuffer üyesi olarak [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) işlevine geçmeye uygun bir kanal bağlamasına bir işaretçiyi döndürür. Özellik, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> kanal bağlama uzunluğu, bayt, içerir. Temel işletim sistemi kanal bağlamalarını desteklemiyorsa, `null`işlev geri döner.  
  
 Başka bir olası senaryo, yakınlıklar kullanılmadığında HTTP:// önekleri için genişletilmiş koruma yı etkinleştirmektir. Bu durumda, <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> tamamen sertleştirilmiş <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> moda <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>karşılık <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> gelirken, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Net.HttpListener> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> kısmen sertleştirilmiş modda koyar bir değer kümesi veya , ve a değeri ne ayarlanmış.  
  
 İzin verilen hizmet adlarının varsayılan <xref:System.Net.HttpListener>listesi, 'ye kayıtlı olan önekleri temel alınarak oluşturulur. Bu varsayılan liste <xref:System.Net.HttpListener.DefaultServiceNames%2A> özellik üzerinden incelenebilir. Bu liste kapsamlı değilse, bir uygulama varsayılan hizmet adı listesi yerine <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> kullanılacak sınıf için oluşturucuya özel bir hizmet adı koleksiyonu belirtebilir.  
  
 Bu yapılandırmada, bir dış güvenli kanal kimlik doğrulaması olmadan sunucuya bir istek yapıldığında normalde kanal bağlama denetimi olmadan ilerler. Kimlik doğrulaması başarılı olursa, istemcinin sağladığı hizmet adı için bağlam sorgulanır ve kabul edilebilir hizmet adları listesine göre doğrulanır. Dört olası sonuç vardır:  
  
1. Sunucunun temel işletim sistemi genişletilmiş korumayı desteklemez. İstek uygulamaya açıklanmaz ve yetkisiz (401) yanıt istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
2. Müşterinin temel işletim sistemi genişletilmiş korumayı desteklemez. Yapılandırmada, <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> kimlik doğrulama denemesi başarılı olur ve istek uygulamaya döndürülür. Yapılandırmada <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> kimlik doğrulama denemesi başarısız olur. İstek uygulamaya açıklanmaz ve yetkisiz (401) yanıt istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
3. İstemcinin temel işletim sistemi genişletilmiş korumayı destekler, ancak uygulama bir hizmet bağlama belirtmedi. İstek uygulamaya açıklanmaz ve yetkisiz (401) yanıt istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
4. İstemci bir hizmet bağlama belirtti. Hizmet bağlama, izin verilen hizmet bağlamaları listesiyle karşılaştırılır. Eşleşirse, istek uygulamaya döndürülür. Aksi takdirde, istek uygulamaya maruz kalınmaz ve yetkisiz (401) yanıt otomatik olarak istemciye iade edilir. Hatanın <xref:System.Net.HttpListener> nedenini belirten izleme kaynağına bir ileti günlüğe kaydedilir.  
  
 Kabul edilebilir hizmet adlarının izin verilen bir listesini kullanarak bu basit yaklaşım yetersizse, <xref:System.Net.HttpListenerRequest.ServiceName%2A> bir uygulama özelliği sorgulayarak kendi hizmet adı doğrulama sağlayabilir. Yukarıdaki 1 ve 2'deki durumlarda, özellik geri `null`verecektir. 3' ün ikinci halinde, boş bir dize döndürecektir. 4' ün durumunda, istemci tarafından belirtilen hizmet adı iade edilecektir.  
  
 Bu genişletilmiş koruma özellikleri, sunucu uygulamaları tarafından diğer istek türleri ile kimlik doğrulama için ve güvenilen yakınlıklar kullanıldığında da kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
