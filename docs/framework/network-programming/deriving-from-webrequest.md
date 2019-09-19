---
title: WebRequest’ten Türetme
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
ms.openlocfilehash: 6bee864f8d24076d16f226c29d61801e856739d9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048611"
---
# <a name="deriving-from-webrequest"></a>WebRequest’ten Türetme
<xref:System.Net.WebRequest> Sınıfı, .NET Framework takılabilir protokol modeline uyan protokole özgü bir istek işleyicisi oluşturmak için temel yöntemleri ve özellikleri sağlayan bir soyut temel sınıftır. **WebRequest** sınıfını kullanan uygulamalar, kullanılan protokolü belirtmeye gerek kalmadan desteklenen herhangi bir protokolü kullanarak veri isteyebilir.  
  
 Protokolüne özgü bir sınıfın takılabilir protokol olarak kullanılabilmesi için iki ölçüt sağlanmalıdır: Sınıfın <xref:System.Net.IWebRequestCreate> arabirimini uygulaması ve <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi ile kaydetmesi gerekir. Sınıf, eklenebilir arabirimi sağlamak için **WebRequest** 'in tüm soyut yöntemlerini ve özelliklerini geçersiz kılmalıdır.  
  
 **WebRequest** örnekleri bir kerelik kullanım için tasarlanmıştır; başka bir istek yapmak istiyorsanız, yeni bir **WebRequest**oluşturun. **WebRequest** , <xref:System.Runtime.Serialization.ISerializable> geliştiricilerin bir şablon **WebRequest** 'i Serileştirmeyi ve daha sonra ek istekler için şablonu yeniden oluşturmasını sağlamak için arabirimi destekler.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest oluşturma yöntemi  
 <xref:System.Net.IWebRequestCreate.Create%2A> Yöntemi, protokole özgü bir sınıfın yeni bir örneğini başlatmaktan sorumludur. Yeni bir **WebRequest** oluşturulduğunda, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi istenen URI ile, **RegisterPrefix** yöntemiyle kayıtlı URI önekleri ile eşleşir. Doğru protokole özgü alt öğenin **Create** yöntemi, hiçbir protokole özgü alana gerek duymadan protokol için standart bir istek/yanıt işlemi gerçekleştirmeye uygun olan başlatılmış bir örneğini döndürmelidir .  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName özelliği  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Özelliği, tek bir bağlantı üzerinden birden çok isteğin yapılabilmesi için bir kaynağa yönelik bir bağlantı grubunu adlandırmak üzere kullanılır. Bağlantı paylaşımını uygulamak için, havuza ve bağlantı atamaya yönelik protokole özgü bir yöntem kullanmanız gerekir. Örneğin, belirtilen <xref:System.Net.ServicePointManager> sınıf <xref:System.Net.HttpWebRequest> sınıfı için bağlantı paylaşımını uygular. **ServicePointManager** sınıfı, her bağlantı <xref:System.Net.ServicePoint> grubu için belirli bir sunucuya bağlantı sağlayan bir oluşturur.  
  
## <a name="contentlength-property"></a>ContentLength özelliği  
 Özelliği <xref:System.Net.WebRequest.ContentLength%2A> , verileri karşıya yüklerken sunucuya gönderilecek verilerin bayt sayısını belirtir.  
  
 Genellikle, <xref:System.Net.WebRequest.Method%2A> **ContentLength** özelliği sıfırdan büyük bir değere ayarlandığında yükleme işleminin gerçekleşeceğini göstermek için özelliği ayarlanmalıdır.  
  
## <a name="contenttype-property"></a>ContentType özelliği  
 Özelliği <xref:System.Net.WebRequest.ContentType%2A> , gönderdiğiniz içerik türünü tanımlamak için protokolizin için sunucuya göndermenizi gerektiren özel bilgileri sağlar. Bu, genellikle karşıya yüklenen verilerin MIME içerik türüdür.  
  
## <a name="credentials-property"></a>Credentials özelliği  
 <xref:System.Net.WebRequest.Credentials%2A> Özelliği, isteğin sunucuyla doğrulanması için gereken bilgileri içerir. Protokolde kimlik doğrulama işleminin ayrıntılarını uygulamanız gerekir. <xref:System.Net.AuthenticationManager> Sınıfı, isteklerin kimlik doğrulamasından ve kimlik doğrulama belirtecinin sağlanmasından sorumludur. Protokolde kullanılan kimlik bilgilerini sağlayan sınıf <xref:System.Net.ICredentials> arabirimini uygulamalıdır.  
  
## <a name="headers-property"></a>Headers özelliği  
 <xref:System.Net.WebRequest.Headers%2A> Özelliği, istekle ilişkili meta verilerin ad/değer çiftlerinin rastgele bir koleksiyonunu içerir. Protokol için gereken tüm meta **veriler, bir** ad/değer çifti olarak ifade edilebilir. Genellikle bu bilgiler, <xref:System.Net.WebRequest.GetRequestStream%2A> veya <xref:System.Net.WebRequest.GetResponse%2A> yöntemleri çağrılmadan önce ayarlanmalıdır; istek yapıldıktan sonra meta veriler salt okunurdur.  
  
 Üst bilgi meta verilerini kullanmak için **üstbilgiler** özelliğini kullanmanız gerekli değildir. Protokole özgü meta veriler, özellikler olarak gösterilebilir; Örneğin, <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> özelliği **Kullanıcı Aracısı** http üst bilgisini gösterir. Üst bilgi meta verilerini özellik olarak kullanıma sundığınızda, **üst bilgiler** özelliği kullanılarak aynı özelliğin belirtilmesine izin vermeniz gerekir.  
  
## <a name="method-property"></a>Method özelliği  
 <xref:System.Net.WebRequest.Method%2A> Özelliği, isteğin sunucudan gerçekleştirmesini istediği fiil veya eylemi içerir. **Method** özelliği için varsayılan değer, herhangi bir protokole özgü özelliğin ayarlanmasına gerek kalmadan standart bir istek/yanıt eylemini etkinleştirmelidir. Örneğin, <xref:System.Net.HttpWebResponse.Method%2A> yöntemi, bir Web sunucusundan kaynak isteyen ve yanıtı döndüren varsayılan olarak Get ' dir.  
  
 **Yöntem** özelliği, bir yükleme işleminin gerçekleşdiğini gösteren bir fiil veya eyleme ayarlandığında, genellikle **ContentLength** özelliğinin sıfırdan büyük bir değere ayarlanması gerekir.  
  
## <a name="preauthenticate-property"></a>Ön kimlik doğrulaması özelliği  
 Uygulamalar, <xref:System.Net.WebRequest.PreAuthenticate%2A> kimlik doğrulama bilgilerinin bir kimlik doğrulama sınaması beklemek yerine başlangıç isteğiyle gönderilmesi gerektiğini belirtmek için özelliğini ayarlar. **Ön** kimlik doğrulama özelliği yalnızca protokol ilk istekle gönderilen kimlik doğrulama kimlik bilgilerini destekliyorsa anlamlıdır.  
  
## <a name="proxy-property"></a>Proxy özelliği  
 Özelliği <xref:System.Net.WebRequest.Proxy%2A> , istenen kaynağa <xref:System.Net.IWebProxy> erişmek için kullanılan bir arabirim içerir. **Ara sunucu** özelliği, yalnızca protokolleriniz proxy kullanan istekleri destekliyorsa anlamlıdır. Protokolde bir tane gerekliyse varsayılan proxy 'yi ayarlamanız gerekir.  
  
 Kurumsal güvenlik duvarının arkasında olduğu gibi bazı ortamlarda, protokolünün bir proxy kullanması gerekebilir. Bu durumda, protokolizin için çalışacak bir proxy sınıfı oluşturmak için **IWebProxy** arabirimini uygulamalısınız.  
  
## <a name="requesturi-property"></a>RequestUri özelliği  
 Özelliği, **WebRequest. Create** metoduna geçirilen URI 'yi içerir. <xref:System.Net.WebRequest.RequestUri%2A> Salt okunurdur ve **WebRequest** oluşturulduktan sonra değiştirilemez. Protokolde yeniden yönlendirmeyi destekliyorsa, yanıt farklı bir URI tarafından tanımlanan bir kaynaktan gelebilir. Yanıt veren URI 'ye erişim sağlamanız gerekiyorsa, o URI 'yi içeren ek bir özellik sağlamanız gerekir.  
  
## <a name="timeout-property"></a>Timeout özelliği  
 <xref:System.Net.WebRequest.Timeout%2A> Özelliği, istek zaman aşımına uğramadan önce beklenecek sürenin uzunluğunu milisaniye cinsinden içerir ve bir özel durum oluşturur. **Zaman aşımı** yalnızca <xref:System.Net.WebRequest.GetResponse%2A> yöntemiyle yapılan zaman uyumlu istekler için geçerlidir; zaman uyumsuz <xref:System.Net.WebRequest.Abort%2A> isteklerin bekleyen bir isteği iptal etmek için yöntemini kullanması gerekir.  
  
 **Timeout** özelliğinin ayarlanması yalnızca, protokole özgü bir zaman aşımı işlemi uygularsa anlamlı olur.  
  
## <a name="abort-method"></a>Abort Yöntemi  
 Yöntemi <xref:System.Net.WebRequest.Abort%2A> , bir sunucuya bekleyen bir zaman uyumsuz isteği iptal eder. İstek iptal edildikten sonra **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, **BeginGetRequestStream**veya **EndGetRequestStream** çağrısı ile bir <xref:System.Net.WebException> ile oluşturulur <xref:System.Net.WebException.Status%2A> özelliği olarak<xref:System.Net.WebExceptionStatus>ayarlanır.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream ve EndGetRequestStream yöntemleri  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Yöntemi, sunucuya veri yüklemek için kullanılan akış için zaman uyumsuz bir istek başlatır. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Yöntemi, zaman uyumsuz isteği tamamlar ve istenen akışı döndürür. Bu yöntemler, standart .NET Framework zaman uyumsuz düzenlerini kullanarak **GetRequestStream** metodunu uygular.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse ve EndGetResponse yöntemleri  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Yöntemi bir sunucuya zaman uyumsuz istek başlatır. <xref:System.Net.WebRequest.EndGetResponse%2A> Yöntemi, zaman uyumsuz isteği tamamlar ve istenen yanıtı döndürür. Bu yöntemler, standart .NET Framework zaman uyumsuz düzenlerini kullanarak **GetResponse** metodunu uygular.  
  
## <a name="getrequeststream-method"></a>GetRequestStream yöntemi  
 Yöntemi <xref:System.Net.WebRequest.GetRequestStream%2A> , istenen sunucuya veri yazmak için kullanılan bir akış döndürür. Döndürülen akış, aranmayan salt yazılır bir akış olmalıdır; sunucuya yazılan tek yönlü veri akışı olarak tasarlanmıştır. Akış, <xref:System.IO.Stream.CanRead%2A> ve <xref:System.IO.Stream.CanSeek%2A>özellikleriiçin false, özelliğiiçintruedöndürür.<xref:System.IO.Stream.CanWrite%2A>  
  
 **GetRequestStream** yöntemi genellikle sunucuya bir bağlantı açar ve akışı döndürmeden önce, verilerin sunucuya gönderildiğini belirten üst bilgi bilgilerini gönderir. **GetRequestStream** isteği başladığından, **GetRequestStream**çağrıldıktan sonra herhangi bir **başlık** özelliğinin veya **ContentLength** özelliğinin ayarlanmasına genellikle izin verilmez.  
  
## <a name="getresponse-method"></a>GetResponse yöntemi  
 Yöntemi, sunucusundan gelen yanıtı temsil eden <xref:System.Net.WebResponse> sınıfın protokolüne özgü bir alt öğesi döndürür. <xref:System.Net.WebRequest.GetResponse%2A> İstek, **GetRequestStream** yöntemi tarafından zaten başlatılmamışsa **GetResponse** yöntemi **requesturı**tarafından tanımlanan kaynağa bir bağlantı oluşturur, yapılan istek türünü gösteren üst bilgi bilgilerini gönderir ve sonra kaynağın yanıtını alır.  
  
 **GetResponse** yöntemi çağrıldıktan sonra tüm özellikler salt okunurdur. **WebRequest** örnekleri bir kerelik kullanım için tasarlanmıştır; başka bir istek yapmak istiyorsanız, yeni bir **WebRequest**oluşturmanız gerekir.  
  
 **GetResponse** yöntemi, gelen yanıtı içermesi için uygun bir **WebResponse** öğesi oluşturmaktan sorumludur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
- [WebResponse’tan Türetme](deriving-from-webresponse.md)
