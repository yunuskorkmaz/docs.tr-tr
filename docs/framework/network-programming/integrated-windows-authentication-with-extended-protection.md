---
title: Genişletilmiş koruma ile tümleşik Windows kimlik doğrulaması
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 88170162e4149580d532129666348d226540aced
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398137"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Genişletilmiş koruma ile tümleşik Windows kimlik doğrulaması
Geliştirmeler nasıl tümleşik Windows kimlik doğrulaması tarafından işlenir etkileyen yapıldı <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, ilgili sınıflar ve <xref:System.Net> ve ilgili ad alanları. Güvenliği artırmak genişletilmiş koruma için destek eklendi.  
  
 Bu değişiklikler, tümleşik Windows kimlik doğrulaması kullanıldığı web isteği yapmak ve yanıtları almak için bu sınıfları kullanan uygulamaları etkileyebilir. Bu değişiklik Ayrıca web sunucuları ve tümleşik Windows kimlik doğrulaması kullanmak üzere yapılandırılmış istemci uygulamaları etkileyebilir.  
  
 Bu değişiklikler, tümleşik Windows kimlik doğrulaması kullanıldığı isteklerinin diğer türleri olmasını sağlayın ve yanıtları almak için bu sınıfları kullanan uygulamalar da etkileyebilir.  
  
 Genişletilmiş korumayı desteklemek için değişiklikler yalnızca Windows 7 ve Windows Server 2008 R2 üzerinde uygulamalar için kullanılabilir. Genişletilmiş Koruma özellikler önceki Windows sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Tümleşik Windows kimlik doğrulaması tasarımını bazı kimlik bilgileri sınama yanıtlarının bunlar yeniden kullanılan iletilen veya anlamı Evrensel olmasına izin verir. Sınama yanıtları hedef belirli bilgileri ve tercihen en az bazı kanal belirli bilgiler ile oluşturulmalıdır. Hizmetleri sonra kimlik bilgisi sınama yanıtları hizmet belirli bilgileri gibi bir hizmet asıl adı (SPN) içerdiğinden emin olmak için genişletilmiş koruma sağlayabilir. Kimlik bilgisi alışverişleri bu bilgilerle, hizmetleri yanlış kullanılmış kimlik bilgisi sınama yanıtları kötü niyetli kullanımına karşı daha iyi koruyabilir.  
  
 Genişletilmiş Koruma tasarım, kimlik doğrulama geçiş saldırıları azaltmak için tasarlanmış kimlik doğrulama protokolleri için bir yeniliktir. Kanal ve hizmet bağlama bilgileri kavramı döner.  
  
 Genel hedefleri şunlardır:  
  
1.  İstemcinin genişletilmiş korumayı desteklemek için güncelleştirilirse, uygulamalar bir kanal bağlama ve tüm desteklenen kimlik doğrulama protokolleri için hizmet bağlama bilgileri vermeniz gerekir. Bir kanal bağlamak için (TLS) olduğunda kanal bağlama bilgileri yalnızca sağlanabilir. Hizmet bağlama bilgileri her zaman sağlanmalıdır.  
  
2.  Düzgün yapılandırıldığından da güncelleştirilmiş sunucu, istemci kimlik doğrulaması belirteçte mevcut olduğunda kanalı ve hizmet bağlama bilgileri doğrulayın ve kanal bağlamaları eşleşmiyorsa kimlik doğrulama girişimini reddet. Dağıtım senaryosuna bağlı olarak, kanal bağlama, hizmet bağlama veya her ikisini sunucuları doğrulayabilirsiniz.  
  
3.  Güncelleştirilmiş sunucuları kabul edin veya reddedin ilkesini temel alarak kanal bağlama bilgileri içermez alt düzey istemci isteklerini seçeneğine sahipsiniz.  
  
 Genişletilmiş koruma tarafından kullanılan bilgileri birini veya her ikisini aşağıdaki iki bölümden oluşur:  
  
1.  Bir kanal bağlama belirteci veya CBT.  
  
2.  Bir hizmet asıl adı ya da SPN hizmet bağlama bilgileri.  
  
 Hizmet bağlama bilgileri belirli bir hizmet uç noktası için kimlik doğrulaması için bir istemcinin hedefinin göstergesidir. Aşağıdaki özelliklerle sunucuya istemciden bildirilir:  
  
-   SPN değeri sunucunun düz metin biçiminde istemci kimlik doğrulaması gerçekleştirmek için kullanılabilir olmalıdır.  
  
-   SPN ortak değeri.  
  
-   ADAM-in--middle saldırı eklemek, kaldırmak veya değiştiremezsiniz değerini şekilde SPN aktarım sırasında şifreleme açısından korunması gerekir.  
  
 Bir CBT bağlamanın kullanılan dış güvenli kanal (örneğin, TLS) (BIND) özelliğidir iç ve istemci kimliği doğrulanmış bir kanal üzerinden bir konuşma için. CBT (Ayrıca IETF RFC 5056 tarafından tanımlanan) aşağıdaki özelliklere sahip olmanız gerekir:  
  
-   Bir dış kanal mevcut olduğunda CBT değerini dış kanalına veya bağımsız olarak bir konuşma hem istemci hem de sunucu tarafında tarafından gelen sunucusu uç noktası tanımlayan bir özellik olması gerekir.  
  
-   İstemci tarafından gönderilen CBT değerini bir saldırganın etkileyebilir olmaması gerekir.  
  
-   Garanti CBT değeri gizliliği hakkında yapılır. Bu ancak CBT taşıyan protokolü, şifreleme olarak hizmet bağlama yanı sıra kanal bağlama bilgileri değeri her zaman diğer ancak sunucu kimlik doğrulaması gerçekleştirme incelenebilir olduğunu anlamına gelmez.  
  
-   CBT şifreleme açısından bir saldırganın eklemek, kaldırmak veya değiştiremezsiniz değeri, aktarım sırasında korumalı bütünlüğü olması gerekir.  
  
 Kanal bağlama SPN ve CBT tamperproof şekilde sunucuya aktarma istemci tarafından gerçekleştirilir. Sunucunun kanal bağlama bilgileri kendi ilke uygun olarak doğrular ve kimlik doğrulama girişimleri için hedef silinmiş kendisine düşünüyorsanız değil reddeder. Bu şekilde, iki kanalı şifreleme açısından birbirine bağlı olur.  
  
 Var olan istemciler ve uygulamalar ile uyumluluğu korumak için bir sunucu kimlik doğrulama girişimlerini izin vermek için genişletilmiş koruma henüz desteklemeyen istemciler tarafından yapılandırılabilir. Bu bir "tam sağlamlaştırılmış" yapılandırma aksine "kısmen sağlamlaştırılmış" bir yapılandırma olarak adlandırılır.  
  
 Birden çok bileşeni <xref:System.Net> ve <xref:System.Net.Security> ad alanları çağıran bir uygulama adına tümleşik Windows kimlik doğrulaması gerçekleştirin. Bu bölümde, tümleşik Windows kimlik doğrulaması kullanımları genişletilmiş koruma eklenecek System.Net bileşenleri değişiklikler açıklanmaktadır.  
  
 Genişletilmiş koruma, şu anda Windows 7'de desteklenir. Bir uygulamayı işletim sistemi genişletilmiş koruma destekleyip desteklemediğini belirlemek için bir mekanizma sağlanır.  
  
## <a name="changes-to-support-extended-protection"></a>Genişletilmiş Koruma destekleyen değişiklikler  
 Tümleşik Windows kimlik doğrulaması, kimlik doğrulama protokolü bağlı olarak kullanılan kimlik doğrulama işleminde kullanılan, genellikle istemci bilgisayarına geri gönderilen ve hedef bilgisayar tarafından verilen bir sınama içerir. Genişletilmiş koruma için bu kimlik doğrulama işlemi yeni özellikleri ekler  
  
 <xref:System.Security.Authentication.ExtendedProtection> Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulaması için destek sağlar. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Sınıfı bu ad alanındaki bir kanal bağlama temsil eder. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Sınıfı bu ad alanındaki gelen istemci bağlantılarını doğrulamak için sunucu tarafından kullanılan genişletilmiş koruma ilkesini temsil eder. Diğer sınıf üyeleri ile genişletilmiş koruma kullanılır.  
  
 Sunucu uygulamaları için bu sınıfları şunlardır:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> aşağıdaki öğelere sahiptir:  
  
-   Bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> işletim sistemi genişletilmiş koruma ile tümleşik windows kimlik doğrulamasını destekleyip desteklemediğini belirten özellik.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> genişletilmiş koruma İlkesi zaman zorlanıp zorlanmayacağını belirten değer.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> dağıtım senaryosuna belirten değer. Bu nasıl genişletilmiş koruma etkilediğini denetlenir.  
  
-   İsteğe bağlı bir <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> kimlik doğrulamasının hedeflenen hedefi olarak istemci tarafından sağlanan SPN eşleştirilecek kullanılan özel SPN listesini içerir.  
  
-   İsteğe bağlı bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> doğrulama için kullanılacak bir özel kanal bağlama içerir. Bu senaryo karşılaşılan bir durumda değil  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Ad alanı, uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulaması yapılandırması için destek sağlar.  
  
 Özellik değişiklikleri sayısı varolan genişletilmiş korumayı desteklemek için yapılan <xref:System.Net> ad alanı. Bu değişiklikler şunları içerir:  
  
-   Yeni bir <xref:System.Net.TransportContext> eklenen sınıfı <xref:System.Net> taşıma bağlamını temsil eder ad alanı.  
  
-   Yeni <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> ve <xref:System.Net.HttpWebRequest.GetRequestStream%2A> yöntemlerini aşırı yükleme <xref:System.Net.HttpWebRequest> alma izin sınıfı <xref:System.Net.TransportContext> istemci uygulamalar için genişletilmiş korumayı desteklemek için.  
  
-   Eklemeler <xref:System.Net.HttpListener> ve <xref:System.Net.HttpListenerRequest> sunucu uygulamalarını desteklemek için sınıflar.  
  
 Mevcut olan SMTP istemci uygulamaları için genişletilmiş korumayı desteklemek için bir özellik değişiklik yapılmıştır <xref:System.Net.Mail> ad alanı:  
  
-   A <xref:System.Net.Mail.SmtpClient.TargetName%2A> özelliğinde <xref:System.Net.Mail.SmtpClient> kullanırken kimlik doğrulaması için kullanılacak SPN temsil eden sınıf genişletilmiş koruma için SMTP istemci uygulamaları.  
  
 Özellik değişiklikleri sayısı varolan genişletilmiş korumayı desteklemek için yapılan <xref:System.Net.Security> ad alanı. Bu değişiklikler şunları içerir:  
  
-   Yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> yöntemlerini aşırı yükleme <xref:System.Net.Security.NegotiateStream> istemci uygulamalar için genişletilmiş korumayı desteklemek için CBT geçirme izni sınıfı.  
  
-   Yeni <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> ve <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> yöntemlerini aşırı yükleme <xref:System.Net.Security.NegotiateStream> geçirme izin sınıfı bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> sunucu uygulamaları için genişletilmiş korumayı desteklemek için.  
  
-   Yeni bir <xref:System.Net.Security.SslStream.TransportContext%2A> özelliğinde <xref:System.Net.Security.SslStream> istemci ve sunucu uygulamaları için genişletilmiş korumayı desteklemek için sınıf.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> özelliği, SMTP istemcileri için genişletilmiş koruma yapılandırmasını desteklemek için eklenen <xref:System.Net.Security> ad alanı.  
  
## <a name="extended-protection-for-client-applications"></a>İstemci uygulamaları için genişletilmiş koruma  
 Çoğu istemci uygulamaları için genişletilmiş koruma desteği otomatik olarak gerçekleşir. <xref:System.Net.HttpWebRequest> Ve <xref:System.Net.Mail.SmtpClient> sınıfları, genişletilmiş koruma temel alınan Windows sürümünü destekleyen her genişletilmiş korumayı destekler. Bir <xref:System.Net.HttpWebRequest> örneği gönderir gelen oluşturulan bir SPN <xref:System.Uri>. Varsayılan olarak, bir <xref:System.Net.Mail.SmtpClient> örneği SMTP posta sunucusunun ana bilgisayar adından oluşturulmuş bir SPN gönderir.  
  
 Özel kimlik doğrulaması için istemci uygulamaları kullanabilir <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> veya <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> yöntemleri <xref:System.Net.HttpWebRequest> alma izin sınıfı <xref:System.Net.TransportContext> ve CBT kullanarak <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi.  
  
 SPN tarafından gönderilen tümleşik Windows kimlik doğrulaması için kullanılacak bir <xref:System.Net.HttpWebRequest> belirli bir hizmeti örneğine ayarlayarak geçersiz kılınmış <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> özelliği.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Özelliği, SMTP bağlantı için tümleşik Windows kimlik doğrulaması için kullanılacak özel bir SPN ayarlamak için kullanılabilir.  
  
## <a name="extended-protection-for-server-applications"></a>Sunucu uygulamaları için genişletilmiş koruma  
 <xref:System.Net.HttpListener> otomatik olarak hizmet bağlamaları HTTP kimlik doğrulaması gerçekleştirirken doğrulama mekanizmaları sağlar.  
  
 HTTPS:// önekler için genişletilmiş koruma özelliğini etkinleştirmek için en güvenli senaryodur bakın. Bu durumda, ayarlamak <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> için bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ile <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> kümesine <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> kümesine <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> değerini <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> koyar <xref:System.Net.HttpListener> sırasındakısmensağlamlaştırılmışmodda<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> tam sağlamlaştırılmış moduna karşılık gelir.  
  
 Dış bir güvenli kanal üzerinden sunucusuna bir istek yapıldığında bu yapılandırmada dış kanal için bir kanal bağlama sorgulanır. Bu kanal bağlama doğrulamak kimlik doğrulaması SSPI çağrıları kimlik doğrulaması blob eşleşmeleri kanal bağlamasında geçirilir. Üç olası sonuçları vardır:  
  
1.  Sunucunun temel işletim sistemi genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
2.  Dış kanaldan beklenen değerle eşleşmedi bir kanal bağlama alınan istemci belirtilen veya sunucusundaki genişletilmiş koruma İlkesi yapılandırıldığında bir kanal bağlama sağlamak istemci başarısız belirten SSPI çağrısı başarısız oluyor için <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. Her iki durumda da istek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
3.  İstemci doğru kanal bağlama belirtir veya sunucusundaki genişletilmiş koruma İlkesi ile yapılandırıldıktan sonra bir kanal bağlama belirtmeden bağlanmasına izin <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> istek işleme için uygulama döndürülür. Hizmet adı onay otomatik olarak gerçekleştirilir. Kendi hizmet adını doğrulama kullanarak gerçekleştirmek bir uygulama seçebilirsiniz <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliği, ancak bu koşullarda gereksiz.  
  
 Bir uygulama ve geriye bir HTTP isteğinin gövdesi içinde geçirilen BLOB'ları temel kimlik doğrulaması gerçekleştirmek için kendi SSPI çağrıları yapar ve kanal bağlama desteklemek istediği, beklenen kanal bağlama kullanarakdışgüvenlikanaldanalmakgereken<xref:System.Net.HttpListener> yerel Win32'ye geçirmek için [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) işlevi. Bunu yapmak için kullanın <xref:System.Net.HttpListenerRequest.TransportContext%2A> özelliği ve çağrı <xref:System.Net.TransportContext.GetChannelBinding%2A> CBT alma yöntemi. Yalnızca endpoint bağlamaları desteklenir. Herhangi bir şey varsa diğer <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> belirtilirse, bir <xref:System.NotSupportedException> oluşturulur. Kanal bağlama, temel işletim sistemini destekleyip desteklemediğini <xref:System.Net.TransportContext.GetChannelBinding%2A> yöntemi döndürür bir <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> bir kanal geçişine uygun bağlama için bir işaretçi kaydırma [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) işlevi SecBuffer yapısı üyesi pvBuffer geçirilen `pInput` parametresi. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> Özelliği, bayt cinsinden uzunluğu kanal bağlama içerir. Altta yatan işletim sistemi kanal bağlamaları desteklemiyor varsa, işlev döndürülecek `null`.  
  
 Başka bir olası proxy'leri kullanılmadığı HTTP:// önekler için genişletilmiş koruma özelliğini etkinleştirmek için bir senaryodur. Bu durumda, ayarlamak <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> için bir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ile <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> kümesine <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> veya <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, ve <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> kümesine <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> değerini <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> koyar <xref:System.Net.HttpListener> sırasındakısmensağlamlaştırılmışmodda<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> tam sağlamlaştırılmış moduna karşılık gelir.  
  
 İzin verilen hizmet adlarını varsayılan listesi ile kayıtlı önekleri temel alınarak oluşturulur <xref:System.Net.HttpListener>. Bu varsayılan liste üzerinden incelenebilir <xref:System.Net.HttpListener.DefaultServiceNames%2A> özelliği. Bu liste kapsamlı değilse, bir uygulama bir özel hizmet adı koleksiyon Oluşturucusu belirtebilirsiniz <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> varsayılan hizmet adı listesi yerine kullanılacak sınıfı.  
  
 Bir istek bir dış olmadan sunucuya güvenli yapıldığında bu yapılandırmada, kanal kimlik doğrulaması normalde bir kanal onay bağlama devam eder. Doğrulama başarılı olursa, bağlam istemci sağlanan ve kabul edilebilir hizmet adları listesi karşı hizmet adı için sorgulanır. Dört olası sonuçları vardır:  
  
1.  Sunucunun temel işletim sistemi genişletilmiş korumayı desteklemiyor. İstek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
2.  İstemcinin temel işletim sistemi genişletilmiş korumayı desteklemiyor. İçinde <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> yapılandırma, kimlik doğrulama girişimi başarısız olur ve istek uygulamaya döndürülür. İçinde <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> yapılandırma, kimlik doğrulama girişimi başarısız olur. İstek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
3.  İstemcinin temel işletim sistemi genişletilmiş korumayı destekler, ancak uygulama hizmet bağlama belirtmedi. İstek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
4.  İstemci hizmet bağlama belirtildi. Hizmet bağlama izin verilen hizmet bağlamaları listesine karşılaştırılır. Eşleşirse, istek uygulamaya döndürülür. Aksi takdirde, istek uygulamaya gösterilmeyen ve yetkisiz (401) yanıt istemciye otomatik olarak döndürülür. Bir ileti için oturum <xref:System.Net.HttpListener> başarısızlığın nedenini belirten izleme kaynağı.  
  
 Kabul edilebilir hizmet adlarına izin verilen bir listesini kullanarak bu basit bir yaklaşım yetersizse, uygulamanın kendi hizmet adı doğrulama sorgulayarak sağlayabilir <xref:System.Net.HttpListenerRequest.ServiceName%2A> özelliği. Yukarıdaki 1 ve 2 durumda da, özellik döndürülecek `null`. 3. durumda, boş bir dize döndürür. 4 durumda, istemci tarafından belirtilen hizmet adı döndürülür.  
  
 Bu genişletilmiş koruma özellikleri, ayrıca diğer türleri isteklerinin ve güvenilir proxy'leri kullanıldığında kimlik doğrulaması için sunucu uygulamaları tarafından kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
