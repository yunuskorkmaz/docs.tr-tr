---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c29b3900a36d8d5c41fee49c408a2e3fdf67680b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991425"
---
# <a name="handling-exceptions-and-faults"></a>Özel Durum ve Hataları İşleme
Özel durumlar, yerel hizmet veya istemci uygulamaları içindeki hataları iletişim kurmak için kullanılır. Hataları, diğer taraftan, hataları hizmet sınırları arasında olduğu gibi sunucudan istemciye ya da tam tersi iletişim kurmak için kullanılır. Hataları ek olarak, taşıma kanalları çoğunlukla aktarım özgü mekanizmaları aktarım düzeyi hataları iletişim kurmak için kullanır. Örneğin, HTTP aktarımı 404 gibi durum kodları (bir hata geri göndermek için uç nokta yok) bir mevcut olmayan uç nokta URL'si iletişim kurmak için kullanır. Bu belgenin özel kanal yazarları için rehberlik üç bölüm oluşur. İlk bölüm ne zaman ve nasıl tanımlamak ve özel durumlar rehberlik sağlar. İkinci bölüm oluşturma ve hataları kullanma yönergeleri sağlar. Özel kanal kullanıcısı çalışan uygulamaları giderilmesine yardımcı olmak için izleme bilgisi sağlamak üzere nasıl üçüncü bölümünde açıklanmaktadır.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir özel durum oluştururken akılda tutulması gereken iki şey vardır: İlk tepki verebilir doğru kodu uygun şekilde özel durumu yazma olanağı tanıyan bir türde olması gerekir. İkinci olarak, neyin yanlış gittiğini anlamak için kullanıcı, hata etki ve sorunun nasıl için yeterli bilgi sağlamak vardır. Aşağıdaki bölümlerde, özel durum türlerini ve Windows Communication Foundation (WCF) kanalları iletileri Rehber sağlar. .NET özel durumları belge için tasarım yönergeleri ile özel durumları genel Rehber de mevcuttur.  
  
### <a name="exception-types"></a>Özel Durum Türleri  
 Kanal tarafından oluşturulan tüm özel durumlar olmalıdır bir <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, veya türetilmiş bir tür <xref:System.ServiceModel.CommunicationException>. (Özel durumlar gibi <xref:System.ObjectDisposedException> Ayrıca, ancak yalnızca çağıran kod kanal kötüye kullanımını göstermek için oluşturulabilir. Bir kanal doğru kullanılıyorsa, yalnızca belirli özel durumlar gerekir.) WCF sağlar öğesinden türetilen özel durum türleri yedi <xref:System.ServiceModel.CommunicationException> ve kanalları tarafından kullanılmak üzere tasarlanmıştır. Diğer vardır <xref:System.ServiceModel.CommunicationException>-sistemin diğer parçaları tarafından kullanılmak üzere tasarlanmış özel durumları türetilmiş. Bu özel durum türleri şunlardır:  
  
|Özel Durum Türü|Açıklama|İç özel duruma içeriği|Kurtarma stratejisi|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Dinlemek üzere belirtilen uç nokta adresi zaten kullanılıyor.|Varsa, bu özel duruma neden olan aktarım hata hakkında daha fazla ayrıntı sağlar. Örneğin. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, veya <xref:System.Net.Sockets.SocketException>.|Farklı bir adres deneyin.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|İşlem dinlemek üzere belirtilen uç nokta adresi erişmesine izin verilmiyor.|Varsa, bu özel duruma neden olan aktarım hata hakkında daha fazla ayrıntı sağlar. Örneğin, <xref:System.IO.PipeException>, veya <xref:System.Net.HttpListenerException>.|Farklı kimlik bilgileri ile deneyin.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılmakta olduğundan hatalı durumunda (daha fazla bilgi için [durum değişikliklerini anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Bir nesne, hatalı durumuna çağrıları geçişleri bekleyen birden çok hata ve geri kalanı çağrıları throw ilgili bir özel durum yalnızca bir çağrı oluşturur Not bir <xref:System.ServiceModel.CommunicationObjectFaultedException>. Bir uygulamanın bazı özel durumu gözden ve özgün özel durum yakalandı farklı bir iş parçacığında büyük olasılıkla zaten hatalı nesneyi kullanmayı dener çünkü bu özel durum genellikle atılır.|Varsa iç özel durum hakkında ayrıntılar sağlar.|Yeni bir nesne oluşturun. Bağlı olarak neyin neden olduğunu unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta hata için diğer işleri kurtarmak için gerekli olabilir.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılan iptal edildi (daha fazla bilgi için [durum değişikliklerini anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Benzer şekilde <xref:System.ServiceModel.CommunicationObjectFaultedException>, kendi özel durum uygulama adlı sahiptir gösterir <xref:System.ServiceModel.ICommunicationObject.Abort%2A> nesneden, büyük olasılıkla başka bir iş parçacığı üzerinde ve nesne artık bu nedenle kullanılamaz.|Varsa iç özel durum hakkında ayrıntılar sağlar.|Yeni bir nesne oluşturun. Bağlı olarak neyin neden olduğunu unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta iptal etmek için diğer iş kurtarmak için gerekli olabilir.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Hedef uzak uç nokta dinleme yapmıyor. Bu, yanlış, çözümlenemeyen olan uç nokta adresi ya da basılı olan uç nokta herhangi bir bölümünden sonuçlanabilir. DNS hatası, kuyruk Yöneticisi kullanılabilir değil ve hizmet çalışmıyor örneklerindendir.|İç özel durum ayrıntıları, genellikle temel alınan aktarımda sağlar.|Farklı bir adres deneyin. Alternatif olarak, gönderici bir süre bekleyin ve hizmet çöktü durumunda yeniden deneyin.|  
|<xref:System.ServiceModel.ProtocolException>|İletişim protokolleri, uç noktanın İlkesi tarafından açıklandığı uç noktaları arasında eşleşmiyor. Örneğin, çerçeveleme içerik türü uyuşmazlığı veya en büyük ileti boyutu aşıldı.|Varsa belirli protokol hatası hakkında daha fazla bilgi sağlar. Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedenini MaxReceivedMessageSize aşıldığında iç istisnadır.|Kurtarma: Gönderen ve alınan Protokolü ayarlarla eşleştiğinden emin olun. Bunu yapmanın bir yolu, hizmet uç noktasının meta veri (ilke) yeniden içeri aktarın ve kanal yeniden oluşturmak için oluşturulan bağlama kullanmaktır.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Uzak uç nokta dinliyor, ancak iletileri işlemeye hazır değil.|Varsa, iç özel duruma bir SOAP hatası veya aktarım düzeyinde hata ayrıntıları sağlar.|Kurtarma: Bekleyin ve daha sonra işlemi yeniden deneyin.|  
|<xref:System.TimeoutException>|İşlem zaman aşımı süresi içinde tamamlayamadı.|Zaman aşımı hakkında ayrıntılar sağlayabilir.|Bekleyin ve daha sonra işlemi yeniden deneyin.|  
  
 Yalnızca bu türdeki tüm var olan özel durum türleri farklı bir belirli kurtarma stratejisine karşılık gelen, yeni bir özel durum türü tanımlar. Yeni bir özel durum türü tanımlarsanız, öğesinden türetilmelidir <xref:System.ServiceModel.CommunicationException> veya ondan türetilen sınıflardan biri.  
  
### <a name="exception-messages"></a>Özel durum iletileri  
 Özel durum iletileri kullanıcının hedeflenen kullanıcı anlamanıza ve sorunu çözmeye yardımcı olmak için yeterli bilgi sağlamanız gerekir böylece programın değil. Bir iyi özel durum iletisi üç önemli bölümleri şunlardır:  
  
 Ne oldu. Kullanıcı deneyimi ile ilgili terimleri kullanarak sorunu hakkında NET bir açıklama sağlayın. Örneğin, hatalı bir özel durum iletisi "Geçersiz yapılandırma bölümü" olacaktır. Bu kullanıcının hangi yapılandırma bölümü yanlış ve neden yanlış olduğunu mu merak ediyorsunuz bırakır. Geliştirilmiş bir ileti olacaktır "Geçersiz yapılandırma bölümü \<customBinding >". Daha da iyi bir ileti olacaktır "adlı myTransport myBinding çünkü adlı bağlama için Aktarım eklenemiyor bağlama myTransport adlı bir aktarım zaten". Bu, uygulamanın yapılandırma dosyasında hüküm ve kullanıcı bir kolayca belirleyebilirsiniz adları kullanarak belirli bir iletidir. Ancak, yine de birkaç anahtar bileşenler eksik vardır.  
  
 Hatanın önemi. İleti açıkça hatası ne anlama geldiğini belirtilmedikçe, kullanıcı yoksayılabilir varsa ya da önemli bir hata olup olmadığını merak ediyor olasıdır. Genel olarak, iletileri anlamı veya anlam hatası ile müşteri adayı. Önceki örnekte geliştirmek için ileti olabilir "ServiceHost başarısız bir yapılandırma hatası nedeniyle açmak için: Çünkü myBinding adlı bağlama için myTransport adlı aktarım eklenemiyor bağlama myTransport adlı bir aktarım zaten ".  
  
 Nasıl kullanıcı sorunu düzeltmeniz gerekir. İletinin en önemli parçası kullanıcı düzeltme sorun yardımcı oluyor. İletinin bazı yönergeler veya denetleyin veya sorunu çözmek düzeltme konusunda ipuçları içermelidir. Örneğin, "ServiceHost başarısız bir yapılandırma hatası nedeniyle açmak için: Çünkü myBinding adlı bağlama için myTransport adlı aktarım eklenemiyor bağlama myTransport adlı bir aktarım zaten. Lütfen yalnızca bir aktarım bağlama bulunmasını".  
  
## <a name="communicating-faults"></a>İletişim hataları  
 SOAP 1.1 ve SOAP 1.2 hataları için belirli bir yapı tanımlar. İki özellikleri arasında bazı farklar vardır, ancak genel olarak, ileti ve MessageFault türleri oluşturma ve tüketme hataları için kullanılır.  
  
 ![Özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1 1AndSOAP1 2FaultComparisonc")  
1.2 hata (solda) ve SOAP 1.1 (sağda) hatası SOAP. SOAP 1.1 tam ad alanı yalnızca hata öğe olduğuna dikkat edin.  
  
 SOAP bir hata iletisi yalnızca bir hataya öğe içeren bir ileti tanımlar (adı olan bir öğe `<env:Fault>`) bir alt öğesi olarak `<env:Body>`. Hata öğe içeriklerinin, biraz Şekil 1 ' gösterildiği gibi SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir. Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıfı normalleştirir bir nesne modeline Bu farklılıklar:  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 `Code` Karşılık gelen özellik `env:Code` (veya `faultCode` SOAP 1.1 içinde) ve hata türünü tanımlar. SOAP 1.2 tanımlar için beş izin verilen değerler `faultCode` (örneğin, gönderen ve alıcı) ve tanımlayan bir `Subcode` herhangi bir alt değer içeren öğe. (Bkz [SOAP 1.2 belirtimi](https://go.microsoft.com/fwlink/?LinkId=95176) izin verilen hata kodları ve anlamları listesi.) SOAP 1.1 biraz farklı bir mekanizma vardır: Dört tanımlar `faultCode` tamamen yeni olanlara tanımlayarak ya da daha belirli oluşturmak için noktalı gösterim kullanılarak genişletilebilir değerleri (örneğin, istemci ve sunucu) `faultCodes`, örneğin, Client.Authentication.  
  
 Ne zaman MessageFault FaultCode.Name program hataları için kullanın ve SOAP 1.2 ad alanı ve ad için FaultCode.Namespace eşler `env:Code` veya SOAP 1.1 `faultCode`. FaultCode.SubCode eşlendiği `env:Subcode` SOAP 1.2 ve SOAP 1.1 için null.  
  
 Yeni hata kodlarını (veya SOAP 1.1 kullanıyorsanız yeni hata kodları) oluşturmalısınız program aracılığıyla bir hataya ayırt etmek ilginç değilse. Bu, yeni bir özel durum türü oluşturma işlemiyle benzerdir. SOAP 1.1 hata kodlarıyla noktalı gösterim kullanılarak kaçınmanız gerekir. ( [WS-ı temel profil](https://go.microsoft.com/fwlink/?LinkId=95177) da hata kodunu nokta gösterimi kullanımını zorlaştırır.)  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 `Reason` Karşılık gelen özellik `env:Reason` (veya `faultString` SOAP 1.1 içinde) bir özel durumun iletiye benzer bir hata koşulu okunabilir bir açıklaması. `FaultReason` Sınıfı (ve SOAP `env:Reason/faultString`) sahip birden çok çevirileri açısından Genelleştirme için yerleşik destek sunmaktadır.  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 Hata ayrıntı içeriği de dahil olmak üzere çeşitli yöntemlerle MessageFault üzerinde sunulan `GetDetail` \<T > ve `GetReaderAtDetailContents`(). Hata ayrıntı, hata hakkında ek ayrıntılar taşıma için donuk bir öğedir. Bu hata ile gerçekleştirmek istediğiniz bazı rastgele yapılandırılmış ayrıntı varsa yararlı olur.  
  
### <a name="generating-faults"></a>Oluşturma hataları  
 Bu bölümde bir hatasına yanıt olarak bir kanal ya da kanal tarafından oluşturulan bir ileti özelliği algılanan bir hata koşulu oluşturma işlemi açıklanmaktadır. Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak bir hata geri gönderiyor.  
  
 Bir hata oluştururken, özel kanal hata doğrudan göndermemelisiniz, bunun yerine, bir özel durum ve bu özel durum bir hata için dönüştürülüp dönüştürülmeyeceğini göndermek nasıl karar verdikten sonra katmanın üzerinde izin. Bu dönüştürme yardımcı olmak için kanal sağlamalıdır bir `FaultConverter` uygun hata için özel bir kanal tarafından oluşturulan özel durum dönüştürebilirsiniz uygulaması. `FaultConverter` olarak tanımlanır:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 Özel hatalar oluşturan her kanal uygulamalıdır `FaultConverter` ve bir çağrıdan dönüş `GetProperty<FaultConverter>`. Özel `OnTryCreateFaultMessage` uygulama özel durum için bir hataya Dönüştür veya iç kanal için temsilci `FaultConverter`. Kanal aktarım ise bu özel durumun dönüştürme veya temsilci kodlayıcıya ait `FaultConverter` veya varsayılan `FaultConverter` WCF'de sağlanan. Varsayılan `FaultConverter` WS-Addressing ve SOAP tarafından belirtilen hata iletileri karşılık gelen hataları dönüştürür. İşte bir örnek `OnTryCreateFaultMessage` uygulaması.  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Bu düzenin bir olduğu çıkarımında hataları gerektiren hata koşulları için Katmanlar arasında oluşturulan özel durumları doğru hata oluşturmak ilgili hataya Oluşturucu için yeterli bilgi içermelidir ' dir. Özel kanal yazarı olarak, bu tür özel durumların zaten yoksa, farklı hata koşulları için karşılık gelen bir özel durum türlerini tanımlayabilir. Kanal katmanlarının geçiş özel durumları donuk arıza verilerini yerine hata koşulu iletişim unutmayın.  
  
### <a name="fault-categories"></a>Hata kategorisi  
 Genellikle hatalarının üç kategoriye ayrılır:  
  
1. Tüm yığını yaygın hataları. Bu hatalar, kanal yığınında, örneğin InvalidCardinalityAddressingException herhangi bir katmanında karşılaştı.  
  
2. Olabilecek hataları herhangi bir yere yığınında belirli bir katmanının akışlı bir işlem veya güvenlik rolleri ilgili örneğin bazı hatalarla karşılaştı.  
  
3. Tek bir katmanda yığınında yönlendirilmiş hataları, hataları WS-RM sıra numarası hataları örneğin gibi.  
  
 Kategori 1. Genellikle WS-Addressing ve SOAP hataları hatalarıdır. Temel `FaultConverter` dönüştürme bu özel durumları işlemek zorunda kalmazsınız WCF tarafından dönüştürür hataları için hata iletileri karşılık gelen WS-Addressing ve SOAP tarafından kendiniz belirtilen sağlanan sınıfı.  
  
 2. kategori. Bir katman, tamamen katmana ilgilidir ileti bilgileri tüketmez iletiye bir özellik ekler. hataları ortaya çıkar. Hataları, daha sonra daha fazla bilgi iletisini işlemek için ileti özelliğini daha yüksek bir katman sorduğunda algılanabilir. Bu kanallar uygulamalıdır `GetProperty` daha önce geriye doğru hata göndermek daha yüksek bir katman etkinleştirmek için belirtilen. Bu TransactionMessageProperty örneğidir. Bu özellik, tam olarak (yapılması. Dağıtılmış İşlem Düzenleyicisi (DTC) başvurarak gerektirebilir üstbilgisindeki tüm veriler doğrulamadan iletiye eklenir  
  
 3. kategori. Hataları yalnızca oluşturulan ve işlemcide tek bir katman tarafından gönderilir. Bu nedenle tüm özel durumları, katman içinde yer alır. Kanallar ve Bakım kolaylığı tutarlılık geliştirmek için özel kanalınızı bile iç hataları için hata iletileri oluşturmak için daha önce belirtilen desenle kullanmanız gerekir.  
  
### <a name="interpreting-received-faults"></a>Alınan hatalar yorumlama  
 Bu bölümde, bir hata iletisi aldığında uygun özel durum oluşturmak için yönergeler sağlanmaktadır. Yığındaki her bir katmanında bir ileti işleme için karar ağacı aşağıdaki gibidir:  
  
1. Geçersiz ileti katmanı olarak değerlendirir, Katman 'geçersiz ileti' işlemesi yapmanız gerekir. Bu tür işleme katmana özgüdür ancak izleme, iletinin bırakarak içerebilir veya, bir özel durum için bir hata dönüştürülür. Güvenlik düzgün güvenli değil bir mesaj veya hatalı sıra numarasıyla mesajı almak RM örneklerindendir.  
  
2. Aksi takdirde, iletinin özellikle katmana uygulayan bir hata iletisi ve ileti Katman etkileşimi dışında anlamlı değil, katman hata koşulu işlemesi gerekir. Bu katmanlara RM kanal yukarıda anlamsız ve RM kanal hatalı ve gelen bekleyen işlemler atma gelir bir RM dizisi reddedildi hatası örneğidir.  
  
3. Aksi takdirde Request() veya Receive() ileti döndürülmelidir. Bu, burada katmanı hatası tanır, ancak hata yalnızca bir istek başarısız oldu ve hatalı kanal ve gelen bekleyen işlemler atma gelmez gösterir servis taleplerini içerir. Böyle bir durumda kullanılabilirliği iyileştirmek için katman uygulamalıdır `GetProperty<FaultConverter>` ve dönüş bir `FaultConverter` hataya bir özel durum için geçersiz kılarak dönüştürebilirsiniz türetilmiş `OnTryCreateException`.  
  
 Aşağıdaki nesne modeli, özel durumları dönüştürme iletileri destekler:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 Kanal katmanını uygulayabilirsiniz `GetProperty<FaultConverter>` özel durumlara dönüştürülürken hata iletileri desteklemek için. Bunu yapmak için geçersiz kılma `OnTryCreateException` ve hata iletisini inceleyin. Tanınırsa, dönüştürme yapmak için Aksi takdirde dönüştürülebilmesi için iç kanal isteyin. Taşıma kanalları temsilci seçmek `FaultConverter.GetDefaultFaultConverter` SOAP/WS-Addressing FaultConverter varsayılan alınamıyor.  
  
 Tipik bir uygulaması şöyle görünür:  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Farklı kurtarma senaryoları sahip belirli hata koşulları için türetilmiş bir sınıf tanımlayarak göz önünde bulundurun `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>MustUnderstand işleme  
 SOAP gereken bir üstbilgi alıcısı tarafından anlaşılmadı sinyal genel bir hata tanımlar. Bu hata olarak da bilinen `mustUnderstand` hata. WCF'de, hiçbir zaman özel kanallar oluşturmak `mustUnderstand` hataları. Bunun yerine, WCF iletişim yığını üst kısmında bulunur, WCF dağıtıcısı, bakar MustUndestand işaretlenmiş tüm üstbilgileri = true temel alınan yığını tarafından anlaşılan. Tüm anlaşılmayan, bir `mustUnderstand` hata bu noktada oluşturulur. (Kullanıcı bunu kapatmak seçebilir `mustUnderstand` işleme ve uygulamanın tüm ileti üstbilgilerini alır. Uygulamanın in that Case yapmaktan sorumlu olduğu `mustUnderstand` işleniyor.) Oluşturulan hata MustUnderstand tüm başlıkları adlarını içeren bir NotUnderstood üst bilgisi içeren = değil anladım true.  
  
 Protokol kanalınızı MustUnderstand ile özel bir üst bilgi gönderirse = true ve alan bir `mustUnderstand` hata, gerekir, şekil bu hata başlığına gönderilen son olup. Üzerinde iki üye yok `MessageFault` , bunun için yararlı olan sınıfı:  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault` döndürür `true` hata olması durumunda bir `mustUnderstand` hata. `WasHeaderNotUnderstood` döndürür `true` üstbilgisi belirtilen ad ve ad alanı ile hata NotUnderstood üst bilgi olarak dahil edilmeyeceğini.  Aksi halde `false`.  
  
 MustUnderstand işaretlenmiş bir üst bilgisi bir kanal yayar, katman ayrıca özel durum oluşturma API'si desenini uygular ve dönüştürmelisiniz = true `mustUnderstand` daha önce açıklandığı gibi daha kullanışlı bir özel durum söz konusu üst kaynaklanan hatalar.  
  
## <a name="tracing"></a>İzleme  
 Aralıklı Sorunlar burada yalnızca mümkün değildir, hata ayıklayıcı ve kodu adımlayın ekleme ya da .NET Framework tanılama üretim uygulamaları yardımcı olmak için bir yol olarak izleme program yürütme için bir mekanizma sağlar. Bu mekanizma temel bileşenleri bulunan <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı ve oluşur:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, yazılması için izleme bilgilerini kaynağı olan <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, gelen izlenecek bilgi alması somut dinleyiciler için Özet temel sınıf olan <xref:System.Diagnostics.TraceSource> ve bir dinleyici özgü hedefe çıktı. Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> çıkışları izleme bilgileri için bir XML dosyası. Son olarak, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, izleme ayrıntı denetim uygulama izin verir ve genellikle yapılandırmada belirtilir.  
  
- Temel bileşenlerine ek olarak, kullandığınız [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) WCF aramak ve görüntülemek için izler. Araç kullanılarak yazılan ve WCF tarafından oluşturulan özel izleme dosyaları için tasarlanan <xref:System.Diagnostics.XmlWriterTraceListener>. Aşağıdaki şekilde, izleme katılan çeşitli bileşenleri gösterir.  
  
 ![Özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Özel bir kanaldan izleme  
 Özel Kanallar, çalışan bir uygulamaya bir hata ayıklayıcının mümkün değilse, sorunların tanılanmasına yardımcı olmak için izleme iletilerini çıkış yazmanız gerekir. Bu iki üst düzey görevleri içerir: Örnekleme bir <xref:System.Diagnostics.TraceSource> ve izlemelerini yazmak için onun yöntemlerini çağırır.  
  
 Örneği oluşturulurken bir <xref:System.Diagnostics.TraceSource>, bu kaynak adı, belirttiğiniz bir dize haline gelir. Bu ad, izleme kaynağı (etkinleştir/devre dışı bırak/set izleme düzeyini) yapılandırmak için kullanılır. Ayrıca, kendi çıktı izlemede görünür. İzleme çıktısına okuyucuları izleme bilgilerini nereden geldiğini anlamak amacıyla özel kanallar benzersiz kaynak adı kullanmanız gerekir. İzleme kaynağı adı olarak bilgilerini yazma derlemenin adını kullanarak yaygın bir uygulamadır. Örneğin, WCF System.ServiceModel derlemeden yazılan bilgi izleme kaynağı System.ServiceModel kullanır.  
  
 Bir izleme kaynağı oluşturduktan sonra arama, <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, veya <xref:System.Diagnostics.TraceSource.TraceInformation%2A> izleme dinleyicilerine izleme girişler yazmak için yöntemleri. Her bir izleme girişi için yazma, olay türü olay türleri içinde tanımlanan biri olarak sınıflandırmak için gereksinim duyduğunuz <xref:System.Diagnostics.TraceEventType>. Bu sınıflandırma ve yapılandırma izleme düzeyi ayarında izleme girişi dinleyicisi çıkış olup olmadığını belirler. Örneğin, izleme düzeyi için yapılandırma ayarını `Warning` sağlayan `Warning`, `Error` ve `Critical` yazılacak girişleri ancak blokları bilgileri ve ayrıntılı girişleri izleme. Bir izleme kaynağı örnekleme ve bilgi düzeyinde bir giriş çıkış yazma örneği aşağıda verilmiştir:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  Belirttiğiniz çıkış nereden geldiğini izleme çıkış kavramasına yardımcı olmak için özel kanal için benzersiz olan bir izleme kaynağı adı önemle tavsiye edilir.  
  
#### <a name="integrating-with-the-trace-viewer"></a>İzleme Görüntüleyici ile tümleştirme  
 İzlemeler, kanal tarafından oluşturulan çıkış tarafından okunabilir bir biçimde olabilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> İzleme dinleyicisi olarak. Bu sorun değil, kanal geliştirici olarak, yapmanız gerekiyor. Bunun yerine, uygulama kullanıcısı (veya uygulama sorunlarını giderme kişi) olduğundan, uygulamanın yapılandırma dosyasında bu İzleme dinleyicisi yapılandırma gerekiyor. Örneğin, aşağıdaki yapılandırma her iki izleme bilgilerini çıkarır <xref:System.ServiceModel?displayProperty=nameWithType> ve `Microsoft.Samples.Udp` adlı dosyaya `TraceEventsFile.e2e`:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a>Yapılandırılmış izleme verileri  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> sahip bir <xref:System.Diagnostics.TraceSource.TraceData%2A> veya daha fazla nesne alan yöntemi olan izleme girişi dahil edilecek. Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> her bir nesneye yöntemi çağrılır ve ortaya çıkan dize bir izleme girişi bir parçası olarak yazılır. Kullanırken <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> izlemeleri çıktısını almak için geçirebilirsiniz bir <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> veri nesnesine olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>. Sonuçta elde edilen izleme girişi tarafından sağlanan XML içerir <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Bir örnek girdi XML uygulama verileriyle şu şekildedir:  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 WCF izleme görüntüleyicisini şemasını anlar `TraceRecord` daha önce gösterilen öğenin alt öğelerine verileri ayıklayan ve tablo biçiminde görüntüler. Kanalınızı bu şema yapılandırılmış uygulama verilerini izlerken veri okuma Svctraceviewer.exe kullanıcılara yardımcı olmak için kullanmanız gerekir.
