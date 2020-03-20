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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048611"
---
# <a name="deriving-from-webrequest"></a>WebRequest’ten Türetme
Sınıf, <xref:System.Net.WebRequest> .NET Framework takılabilir protokol modeline uyan protokole özgü bir istek işleyicisi oluşturmak için temel yöntemleri ve özellikleri sağlayan soyut bir taban sınıfıdır. **Webİstek** sınıfını kullanan uygulamalar, kullanılan protokolü belirtmeye gerek kalmadan desteklenen herhangi bir protokolü kullanarak veri isteyebilir.  
  
 Protokole özgü bir sınıfın takılabilir bir protokol olarak kullanılabilmesi için iki ölçüt <xref:System.Net.IWebRequestCreate> karşılanmalıdır: Sınıf arabirimi uygulamalı ve <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemle kaydolmalıdır. Sınıf takılabilir arabirimi sağlamak için **WebRequest'in** tüm soyut yöntemlerini ve özelliklerini geçersiz kılmalıdır.  
  
 **WebRequest** örnekleri tek seferlik kullanım için tasarlanmıştır; başka bir istekte bulunmak istiyorsanız, yeni bir **Webİstek**oluşturun. **WebRequest,** <xref:System.Runtime.Serialization.ISerializable> geliştiricilerin bir şablon **UYR'u** seri hale getirmek ve ardından ek istekler için şablonu yeniden oluşturmak için arabirimi destekler.  
  
## <a name="iwebrequest-create-method"></a>iWebRequest Oluşturma Yöntemi  
 Yöntem, <xref:System.Net.IWebRequestCreate.Create%2A> protokole özgü sınıfın yeni bir örneğini başlatmadan sorumludur. Yeni bir **WebRequest** oluşturulduğunda, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntem istenen URI ile **RegisterPrefix** yöntemine kayıtlı URI önekleri ile eşleşir. Uygun protokole özgü soyundan gelen in oluşturma **yöntemi,** protokol için protokol için standart bir istek/yanıt hareketi gerçekleştirme yeteneğine sahip soyundan gelenin, protokole özgü alanlara gerek kalmadan başlatılması gereken bir örneğini döndürmelidir.  
  
## <a name="connectiongroupname-property"></a>BağlantıGroupName Özelliği  
 Özellik, <xref:System.Net.WebRequest.ConnectionGroupName%2A> tek bir bağlantı üzerinden birden çok istek yapIlebilmek için bir kaynağa bağlantı grubu adlandırmak için kullanılır. Bağlantı paylaşımını uygulamak için, bağlantıları birleştirme ve atama protokolüne özgü bir yöntem kullanmanız gerekir. Örneğin, sağlanan <xref:System.Net.ServicePointManager> sınıf <xref:System.Net.HttpWebRequest> sınıf için bağlantı paylaşımı uygular. **ServicePointManager** sınıfı, her <xref:System.Net.ServicePoint> bağlantı grubu için belirli bir sunucuya bağlantı sağlayan bir bağlantı oluşturur.  
  
## <a name="contentlength-property"></a>İçerik Uzunluğu Özelliği  
 Özellik, <xref:System.Net.WebRequest.ContentLength%2A> veri yüklerken sunucuya gönderilecek bayt veri sayısını belirtir.  
  
 Genellikle <xref:System.Net.WebRequest.Method%2A> **özellik, ContentLength** özelliği sıfırdan büyük bir değere ayarlandığında bir yüklemenin gerçekleştiğini gösterecek şekilde ayarlanmalıdır.  
  
## <a name="contenttype-property"></a>İçerikTürü Özelliği  
 Özellik, <xref:System.Net.WebRequest.ContentType%2A> protokolünüzün gönderdiğiniz içerik türünü belirlemek için sunucuya göndermenizi gerektirdiği özel bilgileri sağlar. Genellikle bu yüklenen herhangi bir verinin MIME içerik türüdür.  
  
## <a name="credentials-property"></a>Kimlik Bilgileri Özelliği  
 Özellik, <xref:System.Net.WebRequest.Credentials%2A> isteğin sunucuyla doğruluğunu doğrulamak için gereken bilgileri içerir. Protokolünüz için kimlik doğrulama işleminin ayrıntılarını uygulamanız gerekir. Sınıf, <xref:System.Net.AuthenticationManager> isteklerin doğrulanmasından ve kimlik doğrulama belirteci nin sağlanmasından sorumludur. Protokolünüz tarafından kullanılan kimlik bilgilerini sağlayan <xref:System.Net.ICredentials> sınıfın arabirimi uygulaması gerekir.  
  
## <a name="headers-property"></a>Üstbilgi Özelliği  
 Özellik, <xref:System.Net.WebRequest.Headers%2A> istekle ilişkili meta verilerin ad/değer çiftleri rasgele bir koleksiyon içerir. Protokol tarafından ad/değer çifti olarak ifade edilebilen meta veriler **Üstbilgi** özelliğine dahil edilebilir. Genellikle bu bilgiler veya <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest.GetResponse%2A> yöntemleri çağırmadan önce ayarlanmalıdır; istek yapıldıktan sonra, meta veriler salt okunur olarak kabul edilir.  
  
 Üstbilgi meta verilerini kullanmak için **Üstbilgiler** özelliğini kullanmanız gerekmez. Protokole özgü meta veriler özellik olarak ortaya çıkabilir; örneğin, <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> özellik **Kullanıcı-Aracı** HTTP üstbilgisini ortaya çıkarır. Üstbilgi meta verilerini bir özellik olarak ortaya çıkarırken, aynı özelliğin **Üstbilgi** özelliğikullanılarak ayarlanabilmesine izin vermemelisiniz.  
  
## <a name="method-property"></a>Yöntem Özelliği  
 Özellik, <xref:System.Net.WebRequest.Method%2A> isteğin sunucudan gerçekleştirmesini istediği fiil veya eylemi içerir. **Yöntem** özelliği için varsayılan, protokole özgü özelliklerin ayarlanmasına gerek kalmadan standart bir istek/yanıt eylemini etkinleştirmelidir. Örneğin, <xref:System.Net.HttpWebResponse.Method%2A> yöntem, bir Web sunucusundan kaynak isteyen ve yanıtı döndüren GET varsayılan olarak karşılar.  
  
 Genellikle **ContentLength** özelliği, **Yöntem** özelliği bir yüklemenin gerçekleştiğini gösteren bir fiil veya eyleme ayarlandığında sıfırdan büyük bir değere ayarlanmalıdır.  
  
## <a name="preauthenticate-property"></a>PreAuthenticate Özelliği  
 <xref:System.Net.WebRequest.PreAuthenticate%2A> Uygulamalar, kimlik doğrulama itirazı beklemek yerine kimlik doğrulama bilgilerinin ilk istekle gönderilmesi gerektiğini belirtmek için özelliği ayarlar. **PreAuthenticate** özelliği yalnızca protokol ilk istekle birlikte gönderilen kimlik doğrulama kimlik bilgilerini destekliyorsa anlamlıdır.  
  
## <a name="proxy-property"></a>Proxy Özelliği  
 Özellik, <xref:System.Net.WebRequest.Proxy%2A> istenen <xref:System.Net.IWebProxy> kaynağa erişmek için kullanılan bir arabirim içerir. **Proxy** özelliği yalnızca protokolünüz yakın istekleri destekliyorsa anlamlıdır. Protokolünüz tarafından gerekli yse varsayılan proxy'yi ayarlamanız gerekir.  
  
 Kurumsal güvenlik duvarının arkasında olduğu gibi bazı ortamlarda, iletişim kuralınızın proxy kullanması gerekebilir. Bu durumda, protokolünüz için çalışacak bir proxy sınıfı oluşturmak için **IWebProxy** arabirimini uygulamanız gerekir.  
  
## <a name="requesturi-property"></a>Requesturi Mülkiyet  
 Özellik, <xref:System.Net.WebRequest.RequestUri%2A> **WebRequest.Create** yöntemine geçirilen URI'yi içerir. Salt okunur ve **Web İsteği** oluşturulduktan sonra değiştirilemez. Protokolünüz yeniden yönlendirmeyi destekliyorsa, yanıt farklı bir URI tarafından tanımlanan bir kaynaktan gelebilir. Yanıtlayan URI'ye erişim sağlamanız gerekiyorsa, bu URI'yi içeren ek bir özellik sağlamanız gerekir.  
  
## <a name="timeout-property"></a>Zaman Ara Özelliği  
 Özellik, <xref:System.Net.WebRequest.Timeout%2A> istek zamanları dolmadan önce beklemek ve bir özel durum atar milisaniye cinsinden, süreyi içerir. **Zaman alameti** yalnızca <xref:System.Net.WebRequest.GetResponse%2A> yöntemle yapılan eşzamanlı istekler için geçerlidir; asynchronous istekleri bekleyen <xref:System.Net.WebRequest.Abort%2A> bir isteği iptal etmek için yöntemi kullanmanız gerekir.  
  
 Zaman **Ayırma** özelliğini ayarlamak, yalnızca protokole özgü sınıf bir zaman ayırma işlemi uygularsa anlamlıdır.  
  
## <a name="abort-method"></a>Abort Yöntemi  
 Yöntem, <xref:System.Net.WebRequest.Abort%2A> sunucuya bekleyen bir eşzamanlı isteği iptal eder. İstek iptal edildikten sonra **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, BeginGetRequestStream <xref:System.Net.WebException> , <xref:System.Net.WebException.Status%2A> veya <xref:System.Net.WebExceptionStatus> **EndGetRequestStream**arama özelliği ile bir atar . **EndGetRequestStream**  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream ve EndGetRequestStream Yöntemleri  
 Yöntem, <xref:System.Net.WebRequest.BeginGetRequestStream%2A> sunucuya veri yüklemek için kullanılan akış için bir eşzamanlı istek başlatır. Yöntem, <xref:System.Net.WebRequest.EndGetRequestStream%2A> eşzamanlı isteği tamamlar ve istenen akışı döndürür. Bu yöntemler, standart .NET Framework asynchronous deseni kullanarak **GetRequestStream** yöntemini uygular.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse ve EndGetResponse Yöntemleri  
 Yöntem, <xref:System.Net.WebRequest.BeginGetResponse%2A> bir sunucuya bir eşzamanlı istek başlatır. Yöntem, <xref:System.Net.WebRequest.EndGetResponse%2A> eşzamanlı isteği tamamlar ve istenen yanıtı döndürür. Bu yöntemler, standart .NET Framework asynchronous deseni kullanarak **GetResponse** yöntemini uygular.  
  
## <a name="getrequeststream-method"></a>GetRequestStream Yöntemi  
 Yöntem, <xref:System.Net.WebRequest.GetRequestStream%2A> istenen sunucuya veri yazmak için kullanılan bir akışı döndürür. Döndürülen akış, aramayan yalnızca yazma akışı olmalıdır; sunucuya yazılmış tek yönlü veri akışı olarak tasarlanmıştır. Akış, özellikler <xref:System.IO.Stream.CanRead%2A> ve <xref:System.IO.Stream.CanSeek%2A> özellikler için yanlış <xref:System.IO.Stream.CanWrite%2A> ve özellik için doğru döndürür.  
  
 **GetRequestStream** yöntemi genellikle sunucuya bir bağlantı açar ve akışı döndürmeden önce, verilerin sunucuya gönderildiğini gösteren üstbilgi bilgileri gönderir. **GetRequestStream** isteği başladığından, **GetRequestStream'i**aradıktan sonra genellikle **üstbilgi** özelliklerini veya **ContentLength** özelliğini ayarlamaya izin verilmez.  
  
## <a name="getresponse-method"></a>GetResponse Yöntemi  
 Yöntem, <xref:System.Net.WebRequest.GetResponse%2A> sunucudan gelen yanıtı <xref:System.Net.WebResponse> temsil eden sınıfın protokole özgü bir soyundan gelenleri döndürür. İstek **GetRequestStream** yöntemi tarafından başlatılmamışsa, **GetResponse** yöntemi **RequestUri**tarafından tanımlanan kaynağa bir bağlantı oluşturur, yapılan istek türünü belirten üstbilgi bilgileri gönderir ve ardından yanıtı kaynaktan alır.  
  
 **GetResponse** yöntemi çağrıldıktan sonra, tüm özellikler salt okunur olarak kabul edilmelidir. **WebRequest** örnekleri tek seferlik kullanım için tasarlanmıştır; başka bir istekte bulunmak istiyorsanız, yeni bir **Webİsteği**oluşturmanız gerekir.  
  
 **GetResponse** yöntemi, gelen yanıtı içerecek şekilde uygun bir **WebResponse** soyundan gelen oluşturmaktan sorumludur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
- [WebResponse’tan Türetme](deriving-from-webresponse.md)
