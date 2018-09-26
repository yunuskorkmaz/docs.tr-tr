---
title: Webrequest'ten türetme
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
ms.openlocfilehash: 9f4f1756d42e8931a5265017088021b5f4022044
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170723"
---
# <a name="deriving-from-webrequest"></a>Webrequest'ten türetme
<xref:System.Net.WebRequest> .NET Framework takılabilir Protokolü modeli uyan bir protokole özgü istek işleyicisi oluşturmak için temel yöntemleri ve özellikleri sağlayan soyut bir temel sınıfı. Kullanan uygulamalar **WebRequest** sınıfı, kullanılan protokolü belirtmek için gerek kalmadan herhangi bir desteklenen protokolünü kullanarak veri isteyebilir.  
  
 İki ölçütleri karşılar, takılabilir bir protokolü olarak kullanılmak üzere bir protokole özgü sınıfı için sırayla: sınıf uygulamalıdır <xref:System.Net.IWebRequestCreate> arabirimi ve kaydetmeniz gerekir ile <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi. Sınıfı, tüm soyut yöntemlerini ve özelliklerini geçersiz kılmanız gerekir **WebRequest** takılabilir arabirim sağlamak için.  
  
 **WebRequest** örnekleri tek seferlik kullanılmak üzere tasarlanmıştır; başka bir istekte bulunmak istiyorsanız yeni bir oluşturma **WebRequest**. **WebRequest** destekler <xref:System.Runtime.Serialization.ISerializable> geliştiricilerin şablon serileştirmek bir arabirim **WebRequest** ve ardından ek istekler için şablonu yeniden.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest oluşturma yöntemi  
 <xref:System.Net.IWebRequestCreate.Create%2A> Yöntemi, protokole özgü sınıfının yeni bir örneğini başlatmak için sorumludur. Yeni bir **WebRequest** oluşturulan <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi kayıtlı URI ön ekine sahip istenen URI'yi eşleşen **RegisterPrefix** yöntemi. **Oluştur** uygun protokole özgü alt yöntemi döndürmelidir alt başlatılmış bir örneğini özellikli herhangi gerek kalmadan protokol için bir standart istek/yanıt işlem gerçekleştirme protokole özgü alanlar değiştirdi.  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName özelliği  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Özelliği, birden çok isteği tek bir bağlantı üzerinden yapılabilir, böylece bağlantı için bir kaynak grubunun adı için kullanılır. Bağlantı Paylaşımı uygulamak için havuzu ve bağlantıları atayarak protokole özgü yöntemi kullanmanız gerekir. Örneğin, sağlanan <xref:System.Net.ServicePointManager> sınıfın uyguladığı için paylaşım bağlantısı <xref:System.Net.HttpWebRequest> sınıfı. **ServicePointManager** sınıfı oluşturur bir <xref:System.Net.ServicePoint> , her bağlantı grubu için belirli bir sunucu için bir bağlantı sağlar.  
  
## <a name="contentlength-property"></a>ContentLength özelliğinin  
 <xref:System.Net.WebRequest.ContentLength%2A> Özellik sunucuya gönderilir, veriler karşıya yüklenirken veri bayt sayısını belirtir.  
  
 Genellikle <xref:System.Net.WebRequest.Method%2A> özelliğini ayarlayın, karşıya yükleme sürüyor belirtmek için ne zaman yerleştirin **ContentLength** özelliği ayarlanmış bir değer sıfırdan büyük.  
  
## <a name="contenttype-property"></a>ContentType özelliği  
 <xref:System.Net.WebRequest.ContentType%2A> Özelliği protokolünüzü gönderdiğiniz içerik türünü tanımlamak için sunucuya göndermek için gerektirdiği herhangi bir özel bilgiyi sağlar. Karşıya yüklenen tüm verilerin MIME içerik türü genellikle budur.  
  
## <a name="credentials-property"></a>Kimlik özelliği  
 <xref:System.Net.WebRequest.Credentials%2A> Özelliği istekle birlikte sunucu kimlik doğrulaması için gereken bilgileri içerir. Kimlik doğrulama işleminin ayrıntılarını protokolünüzü için uygulamanız gerekir. <xref:System.Net.AuthenticationManager> Sınıftır isteklerine kimlik doğrulaması ve kimlik doğrulama belirteci sağlayan sorumlu. Protokolü tarafından kullanılan kimlik bilgilerini sağlar sınıfını uygulamalıdır <xref:System.Net.ICredentials> arabirimi.  
  
## <a name="headers-property"></a>Üst özellik  
 <xref:System.Net.WebRequest.Headers%2A> Özelliği, rastgele bir istekle ilişkili meta verilerin adı/değer çiftleri koleksiyonu içerir. Ad/değer çifti eklenebilir olarak ifade edilebilir protokolü için gerekli tüm meta verilere **üstbilgileri** özelliği. Çağırmadan önce bu bilgiler genellikle ayarlanmalıdır <xref:System.Net.WebRequest.GetRequestStream%2A> veya <xref:System.Net.WebRequest.GetResponse%2A> yöntemleri; istek yapıldıktan sonra meta veriler salt okunur olarak değerlendirilir.  
  
 Kullanmak için gerekli **üstbilgileri** özelliğinin üstbilgi meta verileri kullanmak için. Protokole özgü meta veriler özellik olarak kullanıma sunulabilecek; Örneğin, <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> özelliği kullanıma sunan **User-Agent** HTTP üstbilgisi. Üst bilgi meta verilerini bir özellik olarak kullanıma sunduğunuzda, kullanarak ayarlamak aynı özellik vermemelidir **üstbilgileri** özelliği.  
  
## <a name="method-property"></a>Yöntem özelliği  
 <xref:System.Net.WebRequest.Method%2A> Fiilin veya eylemin, isteği gerçekleştirmek için sunucu isteme özelliği içerir. İçin varsayılan **yöntemi** özelliği ayarlamak için herhangi bir protokole özgü özellikleri gerek kalmadan bir standart istek/yanıt eylemi etkinleştirmelidir. Örneğin, <xref:System.Net.HttpWebResponse.Method%2A> yöntemi varsayılan olarak, bir kaynağı bir Web sunucusundan istek ve yanıt döndüren GET.  
  
 Genellikle **ContentLength** özelliği ayarlanmalıdır bir değer sıfır olduğunda büyük **yöntemi** bir fiil ya da bir karşıya yükleme yer aldığını gösteren eylem özelliğini ayarlayın.  
  
## <a name="preauthenticate-property"></a>Özellik preAuthenticate  
 Uygulamaları kümesi <xref:System.Net.WebRequest.PreAuthenticate%2A> bu kimlik doğrulama bilgilerini belirtmek için özelliği ilk istekle gönderilmesi yerine bir kimlik doğrulaması sınaması için bekleniyor. **PreAuthenticate** özelliği yalnızca protokol ilk isteğiyle gönderilen kimlik doğrulama bilgilerini destekliyorsa, anlamlı.  
  
## <a name="proxy-property"></a>Proxy özelliği  
 <xref:System.Net.WebRequest.Proxy%2A> Özelliği içeren bir <xref:System.Net.IWebProxy> istenen kaynağa erişmek için kullanılan arabirim. **Proxy** özelliği yalnızca protokolünüzü proxy istekleri destekliyorsa anlamlı. Bir protokolünüzü tarafından gerekirse varsayılan ara sunucu ayarlamanız gerekir.  
  
 Bazı ortamlarda gibi kurumsal bir güvenlik duvarı protokolünüzü bir ara sunucu kullanmak için gerekli olabilir. Bu durumda, uygulamanız gereken **IWebProxy** protokolünüzü için çalışır bir proxy sınıfı oluşturmak için arabirim.  
  
## <a name="requesturi-property"></a>RequestUri özelliği  
 <xref:System.Net.WebRequest.RequestUri%2A> Özelliği içerir URI'yi geçildi **WebRequest.Create** yöntemi. Salt okunur ve bir kez değiştirilemez **WebRequest** oluşturuldu. Yeniden yönlendirme, protokol destekliyorsa, farklı bir URI tarafından tanımlanan bir kaynaktan yanıt gelebilir. Yanıt URI'si için erişim sağlamanız gerekiyorsa, bu URI içeren ek bir özellik sağlamanız gerekir.  
  
## <a name="timeout-property"></a>Zaman aşımı özelliği  
 <xref:System.Net.WebRequest.Timeout%2A> Özelliği, milisaniye cinsinden istek zaman aşımına uğrar ve bir özel durum oluşturur önce beklenecek süreyi içerir. **Zaman aşımı** ile yalnızca çok zaman uyumlu istekleri geçerlidir <xref:System.Net.WebRequest.GetResponse%2A> yöntemi; zaman uyumsuz istekler kullanmalıdır <xref:System.Net.WebRequest.Abort%2A> bekleyen isteği iptal etmek için yöntemi.  
  
 Ayarı **zaman aşımı** özelliği yalnızca bir zaman aşımı işlem protokole özgü sınıfı kullanılıyorsa, anlamlı.  
  
## <a name="abort-method"></a>Abort Yöntemi  
 <xref:System.Net.WebRequest.Abort%2A> Yöntemi, bir sunucu için bekleyen zaman uyumsuz isteğini iptal eder. İstek iptal edildikten sonra çağırma **GetResponse yanıtına**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**,  **BeginGetRequestStream**, veya **EndGetRequestStream** oluşturmaz bir <xref:System.Net.WebException> ile <xref:System.Net.WebException.Status%2A> özelliğini <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream ve EndGetRequestStream yöntemleri  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Yöntemi verileri sunucuya yüklemek için kullanılan akış için zaman uyumsuz isteği başlatır. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Yöntemi zaman uyumsuz istek tamamlanır ve istenen akış döndürür. Bu yöntemleri uygulamak **GetRequestStream** yöntemi Standart .NET Framework zaman uyumsuz desen kullanma.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse ve EndGetResponse yöntemleri  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Yöntemi zaman uyumsuz isteği sunucuya başlatır. <xref:System.Net.WebRequest.EndGetResponse%2A> Yöntemi zaman uyumsuz istek tamamlanır ve istenen yanıt verir. Bu yöntemleri uygulamak **GetResponse yanıtına** yöntemi Standart .NET Framework zaman uyumsuz desen kullanma.  
  
## <a name="getrequeststream-method"></a>GetRequestStream yöntemi  
 <xref:System.Net.WebRequest.GetRequestStream%2A> İstenen sunucuya veri yazmak için kullanılan bir akış yöntemi döndürür. Döndürülen akış zararı tazmin salt yazılır stream olmalıdır; tek yönlü bir sunucu için yazılan veri akışı olarak tasarlanmıştır. Akış için false döndürür <xref:System.IO.Stream.CanRead%2A> ve <xref:System.IO.Stream.CanSeek%2A> özellikleri ve için doğru <xref:System.IO.Stream.CanWrite%2A> özelliği.  
  
 **GetRequestStream** yöntemi genellikle sunucunun bir bağlantı açar ve akış göndermeden önce bu verileri gösteren gönderir başlık bilgilerini sunucuya gönderiliyor. Çünkü **GetRequestStream** herhangi bir ayarı isteğini başlatır **üstbilgi** özellikleri veya **ContentLength** özelliği genellikle izin verilmiyor çağrıldıktansonra**GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse yanıtına yöntemi  
 <xref:System.Net.WebRequest.GetResponse%2A> Yöntemi döndürür protokole özgü alt öğesi <xref:System.Net.WebResponse> sunucu yanıtı temsil eden sınıf. İstek tarafından zaten başlatıldı sürece **GetRequestStream** yöntemi **GetResponse yanıtına** yöntemi tarafından tanımlanan kaynağa bağlantı oluşturur **RequestUri**yapılan bir istek türünü belirten bir başlık bilgilerini gönderir ve sonra kaynak yanıtı alır.  
  
 Bir kez **GetResponse yanıtına** yöntemi çağrıldığında, tüm özellikleri salt okunur olarak düşünülmelidir. **WebRequest** örnekleri, tek seferlik kullanım yöneliktir; başka bir istekte bulunmak istiyorsanız, yeni bir oluşturmalısınız **WebRequest**.  
  
 **GetResponse yanıtına** yöntemdir uygun bir oluşturmaktan sorumlu **WebResponse** gelen yanıtı içeren alt.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.FileWebRequest>  
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [WebResponse’tan Türetme](../../../docs/framework/network-programming/deriving-from-webresponse.md)
