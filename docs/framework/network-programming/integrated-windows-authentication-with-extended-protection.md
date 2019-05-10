---
title: Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: 672737471c7c73e7ddd03d26d00d30cff3e23ec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647403"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması
Geliştirmeler, tümleşik Windows kimlik doğrulaması tarafından işlenir etkileyen yapıldı <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, ve ilgili sınıflar <xref:System.Net> ve ilgili ad alanları. Güvenliği geliştirmek genişletilmiş koruma için destek eklendi.  
  
 Bu değişiklikler, tümleşik Windows kimlik doğrulaması kullanıldığı web isteklerinde bulunmak ve yanıt almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik, ayrıca web sunucuları ve tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış istemci uygulamaları etkileyebilir.  
  
 Bu değişiklikler, tümleşik Windows kimlik doğrulaması kullanıldığı diğer türde istekler olun ve yanıtları almak için bu sınıflar kullanan uygulamalar olarak da etkileyebilir.  
  
 Genişletilmiş korumayı desteklemek için değişiklikler yalnızca Windows 7 ve Windows Server 2008 R2 üzerinde uygulamalar için kullanılabilir. Genişletilmiş koruma özellikleri, önceki Windows sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulaması tasarımını bazı kimlik bilgileri sınaması yanıtları bunlar yeniden kullanılan veya iletilmesi yani evrensel olmasını sağlar. Sınama yanıtları hedef belirli bilgileri ve tercihen en azından bazı kanal belirli bilgileri ile oluşturulmalıdır. Hizmetleri, ardından kimlik bilgisi sınama yanıtları hizmet belirli bilgileri gibi bir hizmet asıl adı (SPN) içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi değişimleri bu bilgilere sahip olarak Hizmetleri hatalı kullanılmış kimlik bilgisi sınama yanıtları kötü niyetli kullanımına karşı daha iyi koruma olanağına sahip olursunuz.  
  
 Genişletilmiş Koruma tasarım, kimlik doğrulama protokollerine kimlik doğrulama geçiş saldırıları azaltmak için tasarlanmış bir geliştirmedir. Bu kavramı kanal ve hizmet bağlama bilgileri geçici olarak döner.  
  
 Genel amaçları şunlardır:  
  
1. İstemcinin genişletilmiş korumayı desteklemek için güncelleştirdiyseniz, uygulamaları bir kanal bağlama ve tüm desteklenen kimlik doğrulama protokolleri için hizmet bağlama bilgileri vermeniz gerekir. Kanal bağlama bilgileri yalnızca bağlamak için (TLS) kanalı olduğunda sağlanabilir. Hizmet bağlama bilgileri her zaman sağlanmalıdır.  
  
2. Düzgün şekilde yapılandırıldığından güncelleştirilmiş sunucuları istemci kimlik doğrulaması belirtecinde mevcut olduğunda kanal ve hizmet bağlama bilgileri doğrulayın ve kanal bağlamaları eşleşmiyorsa, kimlik doğrulama girişimi reddet. Dağıtım senaryosuna bağlı olarak sunucularına kanal bağlama, hizmet bağlama veya her ikisi de doğrulayabilirsiniz.  
  
3. Güncelleştirilmiş sunucuları, kabul etme veya reddetme ilkesini temel alarak kanal bağlama bilgileri içermeyen alt düzey istemci isteklerini olanağına sahip.  
  
 Genişletilmiş koruma tarafından kullanılan bilgileri birini veya her ikisi de aşağıdaki iki bölümden oluşur:  
  
1. Bir kanal bağlama belirteci veya CBT.  
  
2. Bir hizmet asıl adı veya SPN biçiminde bağlama bilgileri hizmeti.  
  
 Hizmet bağlantı bilgilerini belirli hizmet uç noktası kimlik doğrulaması için bir istemcinin hedefi göstergesidir. İstemciden sunucuya aşağıdaki özelliklerle bildiriliyor:  
  
- SPN değeri sunucunun düz metin biçiminde istemci kimlik doğrulaması gerçekleştirmek için kullanılabilir olmalıdır.  
  
- SPN değeri büyük/küçük harf geneldir.  
  
- Bir adam-de-ortadaki adam saldırısı eklemek, kaldırmak veya değerini değiştirmek gibi SPN Aktarımdaki şifreli olarak korunmalıdır.  
  
 Bir CBT bağlamak için kullanılan dış güvenli kanal (TLS gibi) (bağlama) bir özelliğidir, iç, istemci kimliği doğrulanmış bir kanal üzerinden bir görüşme. CBT (Ayrıca IETF RFC 5056 tarafından tanımlanan) aşağıdaki özelliklere sahip olmanız gerekir:  
  
- Dış bir kanal var, CBT değerini dış kanal ya da bağımsız olarak konuşma istemci ve sunucu tarafında tarafından gelen sunucu uç noktasını tanımlayan bir özelliği olmalıdır.  
  
- İstemci tarafından gönderilen CBT değeri, bir saldırganın etkileyebilir olmamalıdır.  
  
- Garanti CBT değerin gizliliği hakkında yapılır. Bu ancak CBT taşıyan protokolü, şifreleme olarak kanal bağlama bilgileri yanı sıra hizmet bağlama değeri her zaman diğer ancak sunucu kimlik doğrulaması gerçekleştirme incelenebilir olduğunu anlamına gelmez.  
  
- CBT şifreli olarak bütünlüğü, bir saldırganın eklemek, kaldırmak veya değerini değiştirmek gibi Aktarımdaki korumalı olmalıdır.  
  
 Kanal bağlama SPN ve CBT tamperproof biçimde sunucusuna aktarılması istemci tarafından gerçekleştirilir. Sunucunun kanal bağlama bilgileri kendi ilkesine uygun olarak doğrular ve kendisi için bu hedef değerinin kendisine düşünüyor olmayan kimlik doğrulama girişimlerini reddeder. Bu şekilde iki kanalları şifreli olarak birlikte bağlı olur.  
  
 Var olan istemciler ve uygulamalar ile uyumluluğu korumak için bir sunucu kimlik doğrulama girişimlerini izin vermek için genişletilmiş koruma henüz desteklemeyen istemciler tarafından yapılandırılabilir. Bunun aksine, "tam olarak sağlamlaştırılmış" yapılandırma "kısmen sağlamlaştırılmış" bir yapılandırma olarak adlandırılır.  
  
 Birden çok bileşeni <xref:System.Net> ve <xref:System.Net.Security> ad alanları, çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirin. Bu bölümde, değişiklikleri genişletilmiş koruma, tümleşik Windows kimlik doğrulaması kullanımını eklemek için System.Net bileşenlerine açıklanmaktadır.  
  
 Genişletilmiş koruma, şu anda Windows 7'de desteklenir. Uygulamanın işletim sistemi için genişletilmiş koruma destekleyip desteklemediğini belirlemek için bir mekanizma sağlar.  
  
## <a name="changes-to-support-extended-protection"></a>Genişletilmiş korumayı desteklemek için değişiklikler  
 Kimlik doğrulama işlemi ile tümleşik Windows kimlik doğrulaması, kimlik doğrulama protokolü bağlı olarak kullanılan kullanılan, genellikle hedef bilgisayar tarafından verilen ve istemci bilgisayarına geri gönderilen bir sınama içerir. Genişletilmiş Koruma bu kimlik doğrulama işlemi için yeni özellikler ekler.  
  
 <xref:System.Security.Authentication.ExtendedProtection> Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulaması için destek sağlar. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Sınıfı bu ad alanındaki bir kanal bağlama temsil eder. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Sınıfı bu ad alanındaki gelen istemci bağlantılarını doğrulamak için sunucu tarafından kullanılan genişletilmiş koruma İlkesi temsil eder. Diğer sınıf üyeleri, genişletilmiş koruma ile kullanılır.  
  
 Sunucu uygulamaları için bu sınıflar aşağıdakileri içerir:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> , aşağıdaki öğelere sahiptir:  
  
- Bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> işletim sistemi için genişletilmiş koruma ile tümleşik windows kimlik doğrulamasını destekleyip desteklemediğini belirten bir özellik.  
  
- A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> genişletilmiş koruma İlkesi zaman zorlanıp zorlanmayacağını belirten değer.  
  
- A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> dağıtım senaryosuna belirten değer. Bu nasıl genişletilmiş koruma etkiler denetlenir.  
  
- İsteğe bağlı <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> istemci tarafından istenen kimlik doğrulaması hedefi olarak sağlanan SPN eşleştirilecek kullanılan özel SPN listesini içerir.  
  
- İsteğe bağlı <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> doğrulama için kullanılacak bir özel kanal bağlama içerir. Bu senaryo, ortak bir durumda değil  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama yapılandırması için destek sağlar.  
  
 Mevcut genişletilmiş korumayı desteklemek için bir dizi özellik değişiklik yapıldı <xref:System.Net> ad alanı. Bu değişiklikler şunları içerir:  
  
- Yeni bir <xref:System.Net.TransportContext> eklenen sınıfı <xref:System.Net> ad alanını taşıma bağlamını temsil eder.  
  
- Yeni <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> ve <xref:System.Net.HttpWebRequest.GetRequestStream%2A> yöntemleri aşırı <xref:System.Net.HttpWebRequest> alınırken izin sınıfı <xref:System.Net.TransportContext> istemci uygulamalar için genişletilmiş korumayı desteklemek için.  
  
- Eklemeler <xref:System.Net.HttpListener> ve <xref:System.Net.HttpListenerRequest> sunucu uygulamaları desteklemek için sınıflar.  
  
 Mevcut SMTP istemci uygulamaları için genişletilmiş korumayı desteklemek için bir özellik değişiklik yapıldı <xref:System.Net.Mail> ad alanı:  
  
- A <xref:System.Net.Mail.SmtpClient.TargetName%2A> özelliğinde <xref:System.Net.Mail.SmtpClient> SPN kullanarak kimlik doğrulaması için kullanılacak temsil eden sınıf genişletilmiş koruma için SMTP istemci uygulamaları.  
  
 Mevcut genişletilmiş korumayı desteklemek için bir dizi özellik değişiklik yapıldı <xref:System.Net.Security> ad alanı. Bu değişiklikler şunları içerir:  
  
- Yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> yöntemleri aşırı <xref:System.Net.Security.NegotiateStream> istemci uygulamalar için genişletilmiş korumayı desteklemek için bir CBT geçirilmesine izin ver sınıfı.  
  
- Yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> yöntemleri aşırı <xref:System.Net.Security.NegotiateStream> geçirilmesine izin verildi sınıfı bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> sunucu uygulamaları için genişletilmiş korumayı desteklemek için.  
  
- Yeni bir <xref:System.Net.Security.SslStream.TransportContext%2A> özelliğinde <xref:System.Net.Security.SslStream> istemci ve sunucu uygulamaları için genişletilmiş korumayı desteklemek için sınıf.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> özelliği SMTP istemciler için genişletilmiş koruma yapılandırmasını desteklemek için eklenen <xref:System.Net.Security> ad alanı.  
  
## <a name="extended-protection-for-client-applications"></a>İstemci uygulamaları için genişletilmiş koruma  
 Genişletilmiş koruma desteği çoğu istemci uygulamaları için otomatik olarak gerçekleşir. <xref:System.Net.HttpWebRequest> Ve <xref:System.Net.Mail.SmtpClient> sınıfları, genişletilmiş koruma temel alınan Windows sürümünü destekleyen her genişletilmiş korumayı destekler. Bir <xref:System.Net.HttpWebRequest> örneği oluşturulan bir SPN gönderir <xref:System.Uri>. Varsayılan olarak, bir <xref:System.Net.Mail.SmtpClient> örneği, SMTP posta sunucusu konak adından oluşturulmuş bir SPN gönderir.  
  
 Özel kimlik doğrulaması için istemci uygulamaları kullanabilir <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> veya <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> yöntemleri <xref:System.Net.HttpWebRequest> alınırken izin sınıfı <xref:System.Net.TransportContext> ve CBT kullanarak <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi.  
  
 SPN tarafından gönderilen tümleşik Windows kimlik doğrulaması için kullanılacak bir <xref:System.Net.HttpWebRequest> verili hizmet örneğine ayarlayarak kılınabilir <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özelliği.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Özelliği, SMTP bağlantı için tümleşik Windows kimlik doğrulaması için kullanılacak özel bir SPN'sini ayarlamak için kullanılabilir.  
  
## <a name="extended-protection-for-server-applications"></a>Sunucu uygulamaları için genişletilmiş koruma  
 <xref:System.Net.HttpListener> otomatik olarak HTTP kimlik doğrulaması yapılırken hizmet bağlamaları doğrulama mekanizmaları sağlar.  
  
 HTTPS:// ön ekleri için genişletilmiş korumayı etkinleştirmek için en güvenli senaryodur bakın. Bu durumda <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> için bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ile <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> kümesine <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> kümesine <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> değerini <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> koyar <xref:System.Net.HttpListener> sırasındakısmensağlamlaştırılmışmodda<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> tam olarak sağlamlaştırılmış moduna karşılık gelir.  
  
 Bu yapılandırmada bir dış güvenli kanal aracılığıyla sunucuya bir istekte bulunulduğunda dış kanal için bir kanal bağlama sorgulanır. Bu kanal bağlama doğrulamak kimlik doğrulama SSPI çağrıları kanal bağlama kimlik doğrulaması blob eşleşmeleri geçirilir. Üç sonuçtan vardır:  
  
1. Server'ın temel işletim sistemi genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
2. Dış kanaldan beklenen değerle eşleşmedi bir kanal bağlama alınan istemci belirtilen veya sunucunun genişletilmiş koruma İlkesi yapılandırıldığında, bir kanal bağlama sağlamak istemci başarısız belirten SSPI çağrı başarısız olur için <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. Her iki durumda da istek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
3. İstemci doğru kanal bağlama belirtir veya sunucunun genişletilmiş koruma İlkesi ile yapılandırılmış olduğundan bir kanal bağlama belirtmeden bağlanmasına izin <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> istek işleme için uygulamaya döndürülür. Hiçbir hizmet adı denetimi otomatik olarak gerçekleştirilir. Kendi hizmet adı doğrulama kullanarak gerçekleştirmek bir uygulama seçebilirsiniz <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliği, ancak şu durumlarda yedekli.  
  
 Bir uygulamayı sürekli bir HTTP isteğinin gövdesi içinde geçirilen BLOB'ları temel kimlik doğrulaması gerçekleştirmek için kendi SSPI çağrıları yapar ve kanal bağlamayı desteklemek istediği, beklenen kanal bağlama kullanarakdışgüvenlikanaldanalmakgerekiyor<xref:System.Net.HttpListener> yerel Win32'ye geçirmek için [AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) işlevi. Bunu yapmak için <xref:System.Net.HttpListenerRequest.TransportContext%2A> özelliği ve çağrı <xref:System.Net.TransportContext.GetChannelBinding%2A> CBT almak için yöntemi. Yalnızca endpoint bağlamaları desteklenir. Herhangi bir şey varsa diğer <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> belirtilen bir <xref:System.NotSupportedException> oluşturulur. Temel işletim sistemi kanal bağlama destekliyorsa <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi döndürür bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> bir kanal iletilecek uygun bağlama bir işaretçi sarmalama [AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) işlevi bir SecBuffer yapının üyesi pvBuffer geçirilen `pInput` parametresi. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> , Bayt cinsinden uzunluğu kanal bağlama özelliği içerir. Temel işletim sistemi kanal bağlamaları desteklemiyor ise, işlev döndürür `null`.  
  
 Başka bir olası senaryo proxy'leri kullanılmadığı HTTP:// ön ekleri için genişletilmiş koruma etkinleştirmektir. Bu durumda <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> için bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ile <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> kümesine <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> kümesine <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> değerini <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> koyar <xref:System.Net.HttpListener> sırasındakısmensağlamlaştırılmışmodda<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> tam olarak sağlamlaştırılmış moduna karşılık gelir.  
  
 İzin verilen hizmet adları varsayılan listesi ile kayıtlı önekleri temel alınarak oluşturulur <xref:System.Net.HttpListener>. Bu varsayılan liste aracılığıyla incelenebilir <xref:System.Net.HttpListener.DefaultServiceNames%2A> özelliği. Bu liste kapsamlı değildir, bir uygulama bir özel hizmet adı koleksiyonu için oluşturucu belirtebilirsiniz <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> varsayılan hizmet adı listesi yerine kullanılacak sınıfı.  
  
 Bir istek sunucuya bir dış olmadan güvenli yapıldığında bu yapılandırmada, kanal kimlik doğrulaması normalde bir kanal denetimi bağlama devam eder. Doğrulama başarılı olursa, içerik istemci sağlanan ve kabul edilebilir hizmet adları listesini karşı doğrulandı hizmet adı için sorgulanır. Olası dört sonuçları vardır:  
  
1. Server'ın temel işletim sistemi genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
2. İstemcinin temel işletim sistemi genişletilmiş korumayı desteklemiyor. İçinde <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> yapılandırma, kimlik doğrulama girişimi başarısız olur ve istek uygulamaya döndürülür. İçinde <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> yapılandırma, kimlik doğrulama girişimi başarısız olur. İstek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
3. İstemcinin temel işletim sistemi genişletilmiş korumayı destekler, ancak uygulama, hizmet bağlaması belirtmedi. İstek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
4. İstemci hizmet bağlama belirtildi. Hizmet bağlaması, izin verilen hizmet bağlamaları listesine karşılaştırılır. Eşleşirse, isteğin uygulamaya döndürülür. Aksi takdirde istek uygulamaya gösterilmeyen ve bir yetkisiz (401) yanıtı istemciye otomatik olarak döndürülür. Bir ileti günlüğe kaydedilir <xref:System.Net.HttpListener> başarısızlığın nedenini belirten bir izleme kaynağı.  
  
 İzin verilen bir kabul edilebilir hizmet adları listesini kullanarak bu basit yaklaşım yetersizse, uygulamanın kendi hizmet adı doğrulama sorgulayarak sağlayabilir <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliği. Yukarıdaki 1 ve 2 durumda da, özellik döndürür `null`. 3. durumda, boş bir dize döndürür. 4 durumda, istemci tarafından belirtilen hizmet adı döndürülür.  
  
 İsteklerin ve güvenilen proxy'leri kullanıldığında diğer türleri ile kimlik doğrulaması için bu genişletilmiş koruma özellikleri de sunucu uygulamaları tarafından kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
