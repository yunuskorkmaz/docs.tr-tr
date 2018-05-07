---
title: WebRequest türetme
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1a1dd850c6534443603fbefb2c1444c85f84a31b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deriving-from-webrequest"></a>WebRequest türetme
<xref:System.Net.WebRequest> Sınıfı, .NET Framework takılabilir Protokolü modeli uygun bir protokole özgü istek işleyicisi oluşturmak için temel yöntemleri ve özellikleri sağlayan bir Özet temel sınıf. Kullanan uygulamalar **WebRequest** sınıfı, kullanılan protokolü belirtmek için gerek kalmadan herhangi bir desteklenen protokolünü kullanarak veri isteyebilir.  
  
 İki ölçütleri karşılar, takılabilir bir protokol olarak kullanılacak bir protokole özgü sınıf için sırayla: sınıf uygulamalıdır <xref:System.Net.IWebRequestCreate> arabirimi ve kaydetmeniz gerekir ile <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi. Sınıfı, tüm soyut yöntemler ve özelliklerini geçersiz kılmanız gerekir **WebRequest** takılabilir arabirimi sağlamak için.  
  
 **WebRequest** örnekleri tek seferlik kullanılmak üzere tasarlanmıştır; başka bir istek yapmak istiyorsanız Yeni Oluştur **WebRequest**. **WebRequest** destekleyen <xref:System.Runtime.Serialization.ISerializable> şablon seri hale getirmek, geliştiricilerin arabirimi **WebRequest** ve ek istekler için şablonu yeniden yapılandırma.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest oluşturma yöntemi  
 <xref:System.Net.IWebRequestCreate.Create%2A> Yöntemdir protokole özgü sınıfının yeni bir örneğini başlatmak için sorumlu. Yeni bir **WebRequest** oluşturulur, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi ile kayıtlı URI öneklerle istenen URI'yi eşleşen **RegisterPrefix** yöntemi. **Oluşturma** uygun protokole özgü alt öğesi yöntemi döndürmelidir descendant başlatılmış örneği herhangi gerek kalmadan protokol için standart istek/yanıt işlem gerçekleştirme yeteneğine protokole özgü alanları değiştirdi.  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName özelliği  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Özelliği, böylece birden fazla isteği tek bir bağlantı üzerinden yapılabilir bağlantı için bir kaynak grubunun adı için kullanılır. Bağlantı Paylaşımı uygulamak için havuzu ve bağlantıları atama bir protokole özgü yöntemini kullanmanız gerekir. Örneğin, sağlanan <xref:System.Net.ServicePointManager> sınıfı uygulayan paylaşımı için bağlantı <xref:System.Net.HttpWebRequest> sınıfı. **ServicePointManager** sınıfı oluşturur bir <xref:System.Net.ServicePoint> , her bağlantı grubu için belirli bir sunucuya bağlantı sağlar.  
  
## <a name="contentlength-property"></a>ContentLength özelliğinin  
 <xref:System.Net.WebRequest.ContentLength%2A> Özelliği, sunucuya gönderilir, verileri karşıya yüklenirken veri bayt sayısını belirtir.  
  
 Genellikle <xref:System.Net.WebRequest.Method%2A> özelliğini ayarlayın, bir yükleme sürüyor belirtmek için ne zaman yerleştirin **ContentLength** özelliği ayarlanmış bir değer sıfırdan büyük.  
  
## <a name="contenttype-property"></a>ContentType özelliği  
 <xref:System.Net.WebRequest.ContentType%2A> Özelliği, protokol, göndermekte olduğunuz içerik türünü tanımlamak için sunucuya göndermenizi gerektirdiği herhangi bir özel bilgiyi sağlar. Genellikle bu MIME içerik karşıya herhangi bir veri türüdür.  
  
## <a name="credentials-property"></a>Kimlik bilgileri özelliği  
 <xref:System.Net.WebRequest.Credentials%2A> Özelliği, sunucu ile istek kimliğini doğrulamak için gereken bilgileri içerir. Kimlik doğrulama işleminin ayrıntılarını protokolü için uygulamalıdır. <xref:System.Net.AuthenticationManager> Sınıftır istekleri kimlik doğrulaması ve kimlik doğrulama belirtecini sağlama sorumlu. Protokolü tarafından kullanılan kimlik bilgilerini sağlayan sınıf uygulamalıdır <xref:System.Net.ICredentials> arabirimi.  
  
## <a name="headers-property"></a>Üstbilgiler özelliği  
 <xref:System.Net.WebRequest.Headers%2A> Özelliği, istekle ilişkili meta verileri ad/değer çiftlerini rastgele bir koleksiyonunu içerir. Ad/değer çifti eklenebilir olarak ifade edilebilir protokol için gerekli herhangi bir meta veri **üstbilgileri** özelliği. Genellikle bu bilgileri çağırmadan önce ayarlamalısınız <xref:System.Net.WebRequest.GetRequestStream%2A> veya <xref:System.Net.WebRequest.GetResponse%2A> yöntemleri; istek gerçekleştirildikten sonra meta veriler salt okunur olarak kabul edilir.  
  
 Kullanmak için gerekli **üstbilgileri** üstbilgi meta veriyi kullanmak için özelliği. Protokol özgü meta veriler özellikleri olarak gösterilebilir; Örneğin, <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> özelliği çıkarır **User-Agent** HTTP üstbilgisi. Üstbilgi meta veri özelliği olarak kullanıma sunmak, kullanarak ayarlamak aynı özelliğe izin vermemelisiniz **üstbilgileri** özelliği.  
  
## <a name="method-property"></a>Yöntem özelliği  
 <xref:System.Net.WebRequest.Method%2A> Fiil veya isteği gerçekleştirmek için sunucu isteyen eylem özelliği içerir. İçin varsayılan **yöntemi** özelliği, bir standart istek/yanıt eylemi ayarlanacak herhangi bir protokole özgü özellik gerek kalmadan etkinleştirmelisiniz. Örneğin, <xref:System.Net.HttpWebResponse.Method%2A> yöntemi varsayılan olarak, bir kaynak Web sunucusundan gelen istekleri ve yanıt döndüren GET.  
  
 Genellikle **ContentLength** özelliği için bir değer sıfır olduğunda büyük ayarlanmalıdır **yöntemi** bir fiil veya karşıya yükleme yer aldığını gösteren işlem özelliğini ayarlayın.  
  
## <a name="preauthenticate-property"></a>Özellik preAuthenticate  
 Uygulamaları kümesi <xref:System.Net.WebRequest.PreAuthenticate%2A> bu kimlik doğrulama bilgilerini belirtmek için özelliği ilk istekle gönderilmesi gerektiğini yerine bir kimlik doğrulaması sınaması için bekleniyor. **PreAuthenticate** özelliği Protokolü kimlik doğrulama bilgilerini ilk istekle birlikte gönderilen destekliyorsa anlamlı yalnızca.  
  
## <a name="proxy-property"></a>Proxy özelliği  
 <xref:System.Net.WebRequest.Proxy%2A> Özelliği içeren bir <xref:System.Net.IWebProxy> istenen kaynağa erişmek için kullanılan arabirim. **Proxy** özelliği yalnızca, Protokolü yönlendirilirken istekleri destekliyorsa anlamlı. Bir protokolü tarafından gerekirse varsayılan proxy ayarlamanız gerekir.  
  
 Bazı ortamlarda gibi kurumsal bir güvenlik duvarı, protokolü bir proxy sunucu kullanmak için gerekli olabilir. Bu durumda, uygulamanız gereken **IWebProxy** protokolü için çalışacak bir proxy sınıfı oluşturmak için arabirimi.  
  
## <a name="requesturi-property"></a>RequestUri özelliği  
 <xref:System.Net.WebRequest.RequestUri%2A> Özelliği için geçirilen URI içeren **WebRequest.Create** yöntemi. Salt okunur olduğundan ve bir kez değiştirilemez **WebRequest** oluşturuldu. Yeniden yönlendirme, Protokolü destekliyorsa, yanıt farklı bir URI tarafından tanımlanan bir kaynaktan gelebilir. Yanıt URI'si erişim sağlamak gerekiyorsa, bu URI içeren bir ek özellik sağlamanız gerekir.  
  
## <a name="timeout-property"></a>Zaman aşımı özelliği  
 <xref:System.Net.WebRequest.Timeout%2A> Özelliği, milisaniye cinsinden istek zaman aşımına uğradı ve bir özel durum oluşturur önce beklenecek süreyi içerir. **Zaman aşımı** ile yapılan yalnızca çok zaman uyumlu istekleri geçerlidir <xref:System.Net.WebRequest.GetResponse%2A> yöntemi; zaman uyumsuz istekleri kullanmalıdır <xref:System.Net.WebRequest.Abort%2A> bekleyen isteği iptal etmek için yöntem.  
  
 Ayarı **zaman aşımı** özelliği yalnızca protokole özgü sınıfı bir zaman aşımı işlem uyguluyorsa anlamlı.  
  
## <a name="abort-method"></a>Abort Yöntemi  
 <xref:System.Net.WebRequest.Abort%2A> Yöntemi bir sunucu için bekleyen bir zaman uyumsuz isteği iptal eder. İstek iptal edildikten sonra çağırma **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**,  **BeginGetRequestStream**, veya **EndGetRequestStream** özel durum oluşturacak bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> özelliğini <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream ve EndGetRequestStream yöntemleri  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Yöntemi verileri sunucuya yüklemek için kullanılan akış için zaman uyumsuz isteği başlatır. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Yöntemi zaman uyumsuz istek tamamlandıktan ve istenen akışı döndürür. Bu yöntemleri uygulamak **GetRequestStream** standart .NET Framework zaman uyumsuz desen kullanma yöntemi.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse ve EndGetResponse yöntemleri  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Yöntemi bir sunucu için zaman uyumsuz isteği başlatır. <xref:System.Net.WebRequest.EndGetResponse%2A> Yöntemi zaman uyumsuz istek tamamlandıktan ve istenen yanıtı döndürür. Bu yöntemleri uygulamak **GetResponse** standart .NET Framework zaman uyumsuz desen kullanma yöntemi.  
  
## <a name="getrequeststream-method"></a>GetRequestStream yöntemi  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Yöntemi, istenen sunucuya veri yazmak için kullanılan bir akış döndürür. Döndürülen akış arama değil yalnızca yazma akışı olmalıdır; tek yönlü bir sunucuya yazılan veri akışı olarak tasarlanmıştır. Akış için false döndürür <xref:System.IO.Stream.CanRead%2A> ve <xref:System.IO.Stream.CanSeek%2A> özellikleri ve için true <xref:System.IO.Stream.CanWrite%2A> özelliği.  
  
 **GetRequestStream** yöntemi genellikle sunucunun bir bağlantı açar ve akış göndermeden önce bu verileri gösterir gönderir üst bilgileri sunucuya gönderiliyor. Çünkü **GetRequestStream** herhangi bir ayarı isteğini başlatır **üstbilgi** özellikleri veya **ContentLength** özelliği genellikle izin verilmeyen çağrıldıktansonra**GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse yöntemi  
 <xref:System.Net.WebRequest.GetResponse%2A> Yöntemi döndürür protokole özgü alt öğesi <xref:System.Net.WebResponse> sunucudan gelen yanıtı temsil eden sınıf. İstek tarafından zaten başlatıldı sürece **GetRequestStream** yöntemi, **GetResponse** yöntemi, bir bağlantı tarafından tanımlanan kaynağa oluşturur **RequestUri**yapılan bir istek türünü belirten üst bilgileri gönderir ve ardından kaynak yanıtı alır.  
  
 Bir kez **GetResponse** yöntemi çağrıldığında, tüm özellikleri salt okunur olarak düşünülmelidir. **WebRequest** örnekleri tek seferlik kullanıma yöneliktir; başka bir istek yapmak istiyorsanız, yeni bir oluşturmalısınız **WebRequest**.  
  
 **GetResponse** yöntemdir uygun bir oluşturmaktan sorumlu **WebResponse** gelen yanıtı içeren alt.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.FileWebRequest>  
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [WebResponse’tan Türetme](../../../docs/framework/network-programming/deriving-from-webresponse.md)
