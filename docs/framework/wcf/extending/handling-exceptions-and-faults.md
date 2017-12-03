---
title: "Özel Durum ve Hataları İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a69acb9b640c17e6641efc6c30798e3856ef6e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="handling-exceptions-and-faults"></a>Özel Durum ve Hataları İşleme
Özel durumlar, yerel hizmet veya istemci uygulaması içindeki hataları iletişim kurmak için kullanılır. Hataları, diğer yandan hataları hizmet sınırları boyunca gibi istemci (veya tersi) sunucusundan iletişim kurmak için kullanılır. Hataları yanı sıra, taşıma kanalları çoğunlukla aktarım özgü mekanizmaları aktarım düzeyi hataları iletişim kurmak için kullanır. Örneğin, HTTP taşıma (bir arıza geri gönderilecek bitiş noktası yoktur) bir var olmayan uç nokta URL'si iletişim kurmak için durum kodları 404 gibi kullanır. Özel kanal yazarları için kılavuzluk üç bölüm, bu belgede oluşur. İlk bölümde, ne zaman ve nasıl tanımlamak ve özel durumlar oluşturma yönergeler sağlanmaktadır. İkinci bölümde oluşturma ve hatalarını tüketen etrafında yönergeler sağlanmaktadır. Üçüncü bölüm özel kanal kullanıcı çalışan uygulamalarda sorun gidermede yardımcı olmak için izleme bilgilerini sağlamayı açıklar.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir özel durum atma zaman göz önünde bulundurmanız gereken iki nokta vardır: önce kullanıcıların özel durumu uygun şekilde tepki gösterebilmesi doğru kod yazmanıza olanak veren bir türde olması gerekir. İkinci olarak, nelerin yanlış gittiğini anlamak için kullanıcıyı, hata etkisi ve nasıl düzeltileceği için yeterli bilgi sağlamak vardır. Aşağıdaki bölümlerde özel durum türleri ve iletiler için yönergeler vermek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanalları. Özel durumlar belge için tasarım yönergeleri .NET özel durumları genel yönergeler bulunmaktadır.  
  
### <a name="exception-types"></a>Özel Durum Türleri  
 Kanalları tarafından oluşturulan tüm özel durumları ya da olmalıdır bir <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, veya türetilmiş bir tür <xref:System.ServiceModel.CommunicationException>. (Özel durumlar gibi <xref:System.ObjectDisposedException> de, ancak yalnızca çağıran kodu kanal kötüye kullanımını göstermek için durum oluşturulabilir. Bir kanal doğru kullandıysanız, yalnızca belirli özel durumlar oluşturma gerekir.) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öğesinden türetilen yedi özel durum türleri sağlar <xref:System.ServiceModel.CommunicationException> ve kanalları tarafından kullanılmak üzere tasarlanmıştır. Diğer vardır <xref:System.ServiceModel.CommunicationException>-sisteminin diğer bölümleriyle tarafından kullanılmak üzere tasarlanmış özel durumlar türetilmiş. Bu özel durum türleri şunlardır:  
  
|Özel durum türü|Açıklama|İç özel duruma içeriği|Kurtarma stratejisi|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Dinlemek için belirtilen uç nokta adresi zaten kullanılıyor.|Varsa, bu özel durumun nedeni aktarım hatası hakkında daha fazla ayrıntı sağlar. Örneğin. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, veya <xref:System.Net.Sockets.SocketException>.|Farklı bir adres deneyin.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|İşlem dinlemek için belirtilen uç nokta adresi erişmesine izin verilmiyor.|Varsa, bu özel durumun nedeni aktarım hatası hakkında daha fazla ayrıntı sağlar. Örneğin, <xref:System.IO.PipeException>, veya <xref:System.Net.HttpListenerException>.|Farklı kimlik bilgileriyle deneyin.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılmakta olan Faulted durumunda (daha fazla bilgi için bkz: [anlama durum değişiklikleri](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Bir nesne, birden çok Faulted durumunda çağrıları geçişleri bekleyen yalnızca bir çağrı hatası ve çağrıları throw geri kalanı ile ilgili bir özel durum atar Not bir <xref:System.ServiceModel.CommunicationObjectFaultedException>. Çünkü uygulamanın bazı özel durum gözden ve zaten hatalı bir nesne, büyük olasılıkla orijinal özel durumu yakalandı farklı bir iş parçacığında kullanmayı dener ve bu durum genellikle atılır.|Varsa, iç özel duruma hakkında ayrıntılar sağlar.|Yeni nesne oluşturma. Neyin neden bağlı olarak unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta arıza için kurtarmak için gereken diğer iş olabilir.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılan durduruldu (daha fazla bilgi için bkz: [anlama durum değişiklikleri](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Benzer şekilde <xref:System.ServiceModel.CommunicationObjectFaultedException>, kendi özel durumu uygulama olarak adlandırılan gösterir <xref:System.ServiceModel.ICommunicationObject.Abort%2A> nesnesi, büyük olasılıkla başka bir iş parçacığı üzerinde ve nesne artık bu nedenle kullanılamaz.|Varsa, iç özel duruma hakkında ayrıntılar sağlar.|Yeni nesne oluşturma. Neyin neden bağlı olarak unutmayın <xref:System.ServiceModel.ICommunicationObject> ilk başta iptal etmek için diğer iş kurtarmak için gerekli olabilir.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Hedef uzak uç noktada dinleme değil. Bu herhangi bir parçası olan yanlış, irresolvable uç noktası adresi ya da aşağı olan uç nokta neden olabilir. Örnekler DNS hatası, sıra Yöneticisi kullanılabilir değil ve hizmet çalışmıyor.|İç özel duruma ayrıntılarının, genellikle temel aktarımı sağlar.|Farklı bir adres deneyin. Alternatif olarak, gönderici bir süre bekleyin ve durumda aşağı hizmeti, yeniden deneyin|  
|<xref:System.ServiceModel.ProtocolException>|İletişim protokolleri uç noktanın İlkesi tarafından açıklanan uç noktaları arasında eşleşmiyor. Örneğin, içerik türü uyuşmazlığı veya maksimum ileti boyutu aşıldı çerçeveleme.|Varsa, belirli bir protokol hata hakkında daha fazla bilgi sağlar. Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedenini MaxReceivedMessageSize aşıldığında iç istisnadır.|Kurtarma: gönderen ve alınan Protokolü ayarlarla eşleştiğinden emin olun. Bunu yapmanın bir yolu, hizmet uç noktanın meta veriler (ilke) yeniden içeri aktarın ve kanal yeniden oluşturmak için oluşturulan bağlama kullanmaktır.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Uzak uç noktada dinleme ancak iletileri işlemek hazır değil.|Varsa, iç özel duruma bir SOAP hatası veya aktarım düzeyinde hata ayrıntıları sağlar.|Kurtarma: Bekleyin ve daha sonra işlemi yeniden deneyin.|  
|<xref:System.TimeoutException>|İşlem zaman aşımı süresi içinde tamamlayamadı.|Zaman aşımı ayrıntılarını sağlayabilir.|Bekleyin ve daha sonra işlemi yeniden deneyin.|  
  
 Yalnızca bu belirli bir kurtarma stratejisi tüm var olan özel durum türleri farklı karşılık gelen türü varsa yeni bir özel durum türü tanımlar. Yeni bir özel durum türü tanımlarsanız öğesinden türetilmelidir <xref:System.ServiceModel.CommunicationException> veya türetilmiş sınıflarından biri.  
  
### <a name="exception-messages"></a>Özel durum iletileri  
 Özel durum iletilerini kullanıcının hedeflenen kullanıcı anlamanıza ve sorunu çözmenize yardımcı olması için yeterli bilgi vermelidir böylece programın değil. İyi özel durum iletisi üç temel bölümleri şunlardır:  
  
 Ne oldu. Kullanıcı deneyimi ile ilgili koşulları'nı kullanarak sorunun anlaşılır bir açıklama sağlayın. Örneğin, hatalı özel durum iletisi "Geçersiz yapılandırma bölümünde" olur. Bu, kullanıcının hangi yapılandırma bölümü hatalı ve neden yanlış olduğunu merak ediyor bırakır. Geliştirilmiş iletisine olacaktır "Geçersiz yapılandırma bölümü \<customBinding >". Daha iyi bir ileti olacaktır "myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten". Bu, uygulamanın yapılandırma dosyasında hüküm ve kullanıcı kolayca tanıyacak adlarını kullanarak, belirli bir iletidir. Ancak, eksik hala birkaç anahtar bileşenleri vardır.  
  
 Hata önemi. İleti açıkça hata anlamı belirtilmedikçe, kullanıcı önemli bir hata olup olmadığını veya yoksayılabilir varsa merak ediyor olasıdır. Genel olarak, iletileri anlamı ya da hata önemini neden. Önceki örnekte geliştirmek için ileti olabilir "ServiceHost açık bir yapılandırma hatası nedeniyle başarısız oldu: myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten".  
  
 Nasıl kullanıcı sorunu düzeltmeniz gerekir. İleti en önemli bir parçası kullanıcı düzeltme sorun yardımcı oluyor. İletinin bazı yönergeler veya denetleyin veya sorunu çözmek düzeltme gerekenler hakkında ipuçları içermesi gerekir. Örneğin, "ServiceHost açık bir yapılandırma hatası nedeniyle başarısız oldu: myBinding çünkü adlı bağlama myTransport adlı aktarım ekleyemezsiniz bağlama myTransport adlı bir aktarım zaten. Lütfen yalnızca bir aktarım bağlama sağlayın".  
  
## <a name="communicating-faults"></a>İletişim hataları  
 SOAP 1.1 ve SOAP 1.2 hataları için belirli bir yapı tanımlayın. İki özellikleri arasında bazı farklar vardır, ancak genel olarak, ileti ve MessageFault türleri oluşturmak ve hataları kullanmak için kullanılır.  
  
 ![Özel durumlar ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1 1AndSOAP1 2FaultComparisonc")  
SOAP 1.2 arıza (sol) ve (sağdaki) bir SOAP 1.1 hatası. SOAP 1.1 tam ad alanı yalnızca hataya öğesi olduğuna dikkat edin.  
  
 SOAP yalnızca bir hata öğesi içeren bir ileti bir hata iletisi tanımlar (adı olan bir öğeyi `<env:Fault>`) bir alt öğesi olarak `<env:Body>`. Hataya öğenin içeriğini, biraz Şekil 1 ' gösterildiği gibi SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir. Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıfı normalleştirir bir nesne modeline Bu farklılıklar:  
  
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
  
 `Code` Özelliğine karşılık gelen `env:Code` (veya `faultCode` SOAP 1.1 içinde) ve hataya türünü tanımlar. SOAP 1.2 tanımlar için beş izin verilen değerler `faultCode` (örneğin, gönderici ve alıcı) ve tanımlayan bir `Subcode` herhangi bir alt değer içeren öğe. (Bkz [SOAP 1.2 belirtimi](http://go.microsoft.com/fwlink/?LinkId=95176) izin verilen hata kodları ve anlamları listesi için.) SOAP 1.1 biraz farklı mekanizması vardır: dört tanımlar `faultCode` tamamen yenilerini tanımlayarak ya da daha fazla belirli oluşturulacağı noktalı gösterim kullanılarak genişletilmiş değerleri (örneğin, istemci ve sunucu) `faultCodes`, örneğin, Client.Authentication.  
  
 Ne zaman FaultCode.Name program hataları MessageFault kullanın ve FaultCode.Namespace eşler adı ve SOAP 1.2 ad alanı `env:Code` veya SOAP 1.1 `faultCode`. FaultCode.SubCode eşlendiği `env:Subcode` SOAP 1.2 ve SOAP 1.1 için null.  
  
 Yeni hata kodlarını (veya SOAP 1.1 kullanıyorsanız yeni hata kodları) oluşturmalısınız program aracılığıyla bir arıza ayırt etmek ilginç ise. Bu, yeni bir özel durum türü oluşturmak için benzerdir. SOAP 1.1 hata kodlarıyla noktalı gösterim kullanılarak kaçınmalısınız. ( [WS-ı temel profil](http://go.microsoft.com/fwlink/?LinkId=95177) hata kodu noktalı gösterim kullanımını da zorlaştırır.)  
  
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
  
 `Reason` Özelliğine karşılık gelen `env:Reason` (veya `faultString` SOAP 1.1 içinde) özel durum iletisi benzer hata koşulu okunabilir açıklaması. `FaultReason` Sınıfı (ve SOAP `env:Reason/faultString`) birden çok çevirisinde Genelleştirme gerçekleştirebiliriz sahip olmak için yerleşik desteğe sahiptir.  
  
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
  
 Hata ayrıntı içeriği de dahil olmak üzere çeşitli yöntemlerle MessageFault üzerinde gösterilen `GetDetail` \<T > ve `GetReaderAtDetailContents`(). Hata ayrıntı, hata hakkında ek ayrıntılar taşınma donuk bir öğedir. Bu hata ile gerçekleştirmek istediğiniz bazı rastgele yapılandırılmış ayrıntı ise yararlı olur.  
  
### <a name="generating-faults"></a>Oluşturma hataları  
 Bu bölümde bir kanal veya kanal tarafından oluşturulan bir ileti özelliği algılanan bir hata koşulu yanıtta bir arıza oluşturma işlemi açıklanmaktadır. Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak bir hata geri gönderiyor.  
  
 Bir arıza oluşturulurken özel kanal hataya doğrudan göndermemelisiniz, bunun yerine, bir özel durum ve üzerindeki başka bir özel durum bir hata dönüştürülüp dönüştürülmeyeceğini ve göndermek nasıl karar katmanı sağlar. Bu dönüştürme yardımcı olmak için kanal sağlamalıdır bir `FaultConverter` uygulamasında, uygun hataya özel kanal tarafından oluşturulan özel durum dönüştürebilirsiniz. `FaultConverter`olarak tanımlanır:  
  
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
  
 Özel hatalar oluşturan her bir kanala uygulamalıdır `FaultConverter` ve çağrısından döndürün `GetProperty<FaultConverter>`. Özel `OnTryCreateFaultMessage` uygulama için bir hata özel durum Dönüştür veya temsilci iç kanalın için `FaultConverter`. Kanal aktarım ise özel durum Dönüştür veya temsilci kodlayıcıya 's `FaultConverter` veya varsayılan `FaultConverter` sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] . Varsayılan `FaultConverter` WS adresleme ve SOAP tarafından belirtilen hata iletileri için karşılık gelen hataları dönüştürür. İşte bir örnek `OnTryCreateFaultMessage` uygulaması.  
  
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
  
 Hataları gerektiren hata koşulları için Katmanlar arasında oluşturulan özel durumları doğru hataya oluşturmak karşılık gelen arıza Oluşturucu için yeterli bilgi içermelidir olduğu bu desenin bir çıkarımında bulunulur. Özel kanal yazar olarak, bu tür özel durumlar zaten yoksa, farklı hata koşulları için karşılık gelen özel durum türleri tanımlayabilir. Kanal katmanlarının çapraz geçiş yapan özel durumlar donuk arıza verilerini yerine hata koşulu iletişim unutmayın.  
  
### <a name="fault-categories"></a>Hata kategorisi  
 Genellikle hatalarının üç kategoriye ayrılır:  
  
1.  Tüm yığın yaygın hataları. Bu hataları kanal yığınında, örneğin InvalidCardinalityAddressingException herhangi katmanında karşılaştı.  
  
2.  Olabilecek hataları herhangi bir yere yığınında belirli bir katmanının akışlı bir işlem veya güvenlik rollerini ait örneğin bazı hatalarla karşılaştı.  
  
3.  Yığındaki tek bir katmanında yönlendirilmiş hataları, örneğin hataları WS-RM sıra numarası hataları gibi çalışır.  
  
 Kategori 1. Genellikle WS adresleme ve SOAP hataları hatalarıdır. Temel `FaultConverter` sınıfı tarafından sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hata iletileri için karşılık gelen dönüştürür hataları belirtilen WS adresleme ve SOAP tarafından bu özel durumlar dönüştürmeyi gerekmez şekilde kendiniz.  
  
 Kategori 2. Bir katman tamamen katmana ilgilidir ileti bilgilerini tüketen değil ileti bir özellik ekler hataları oluşur. Daha yüksek bir katman daha fazla bilgi iletisi işleyemedi ileti özelliği sorduğunda hataları daha sonra algılanabilir. Bu tür kanalları uygulamalıdır `GetProperty` daha önce doğru hataya geri göndermek daha yüksek katman etkinleştirmek için belirtilen. Bu TransactionMessageProperty örneğidir. Bu özellik tamamen (Dağıtılmış İşlem Düzenleyicisi (DTC) başvurarak gerektirebilir Bunun yapılması. üstbilgisindeki tüm verilere doğrulamadan iletiye eklenir  
  
 Kategori 3. Hataları yalnızca oluşturulur ve tek bir işlemcinin katmanda tarafından gönderilir. Bu nedenle tüm özel durumları katman içinde yer alır. Kanallar ve kolaylığı bakım arasında tutarlılığı artırmak için özel kanal bile iç hataları için hata iletileri oluşturmak için daha önce belirtilen desenle kullanmanız gerekir.  
  
### <a name="interpreting-received-faults"></a>Alınan hataları yorumlama  
 Bu bölümde, bir hata iletisi alırken uygun özel durum oluşturmak için yönergeler sağlanmaktadır. Yığındaki her katmanında bir ileti işleme için karar ağacı aşağıdaki gibidir:  
  
1.  Geçersiz olduğu için ileti katmanı göz önünde bulundurur varsa Katman 'geçersiz bir ileti' işlemesi yapmanız gerekir. Bu tür işleme katmana özgü ancak izleme, iletinin bırakarak dahil olabilir veya bir özel durum atma bir hataya dönüştürülür. Güvenlik düzgün korunmuyorsa bir mesaj alarak veya hatalı sıra numarasına sahip bir ileti alma RM örnek olarak verilebilir.  
  
2.  Aksi takdirde, ileti özellikle katmana uygulanır bir hata iletisi ve ileti katman etkileşim dışında anlamlı değil, katman hata koşulu işlemesi gerekir. Bu RM kanal yukarıda katmanlara anlamsız ve RM kanal hatalı ve gelen bekleyen işlemler atma gelir bir RM sırası reddedildi hatası örneğidir.  
  
3.  Aksi takdirde, ileti Request() veya Receive() döndürülmelidir. Bu, burada hataya katman tanır, ancak hata yalnızca bir istek başarısız oldu ve kanal hatalı ve gelen bekleyen işlemler atma göstermez gösterir durumları içerir. Böyle bir durumda kullanılabilirliğini artırmak için katman uygulamalıdır `GetProperty<FaultConverter>` ve dönüş bir `FaultConverter` türetilen hataya bir özel durum için geçersiz kılarak dönüştürebilirsiniz sınıfı `OnTryCreateException`.  
  
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
  
 Kanal katmanını uygulayabilirsiniz `GetProperty<FaultConverter>` özel durumları dönüştürme hata iletileri desteklemek için. Bunu yapmak için geçersiz kılma `OnTryCreateException` ve hata iletisini inceleyin. Kabul dönüştürme yapılamıyor, aksi takdirde dönüştürülebilmesi için iç kanal isteyin. Taşıma kanalları için temsilci seçme `FaultConverter.GetDefaultFaultConverter` SOAP/WS-adresleme FaultConverter varsayılan alınamıyor.  
  
 Tipik bir uygulama şöyle görünür:  
  
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
  
 Farklı kurtarma senaryoları gereken belirli hata koşulları için türetilmiş bir sınıf tanımlama göz önünde bulundurun `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>MustUnderstand işleme  
 SOAP gereken bir üstbilgi alıcı tarafından anlaşılmadı sinyal genel bir hata tanımlar. Bu hata olarak bilinen `mustUnderstand` hata. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hiçbir zaman özel kanallar oluşturmak `mustUnderstand` hataları. Bunun yerine, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en üstünde bulunan dağıtıcısı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletişim yığını kontrol eder, MustUndestand işaretlenen tüm üstbilgileri = true temel yığını tarafından anlaşılan. Herhangi bir anlaşılmayan, bir `mustUnderstand` arıza bu noktada oluşturulur. (Kullanıcı bunu kapatmak seçebilir `mustUnderstand` işleme ve tüm ileti üstbilgilerini almak uygulamaya sahip. Uygulama in that Case gerçekleştirmek için sorumlu olduğu `mustUnderstand` işleme.) Oluşturulan hata MustUnderstand ile tüm üstbilgileri adlarını içeren bir NotUnderstood üstbilgisi içerir = değil anladım true.  
  
 Protokol kanal MustUnderstand sahip özel bir üstbilgi gönderirse = true ve alan bir `mustUnderstand` arıza, gerekir, şekil bu hataya, gönderilen üstbilgisi son olup. İki üye vardır `MessageFault` bunun için yararlı sınıfı:  
  
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
  
 `IsMustUnderstandFault`döndürür `true` arıza olması durumunda bir `mustUnderstand` hatası. `WasHeaderNotUnderstood`döndürür `true` üstbilgisi belirtilen ad ve ad alanı ile NotUnderstood üstbilgisi olarak hataya dahil değilse.  Aksi takdirde, döndürür `false`.  
  
 Bir kanal MustUnderstand olarak işaretlenmiş bir üstbilgi yayar katman özel durum oluşturma API'si düzeni de uygulamanız gerekir ve dönüştürmeniz gerekir. ardından, = true `mustUnderstand` bu başlığı için daha önce açıklandığı gibi daha kullanışlı bir özel nedeni hataları.  
  
## <a name="tracing"></a>İzleme  
 .NET Framework tanılama üretim uygulamaları yardımcı olmak için bir yol olarak izleme program yürütme için bir mekanizma sağlar veya bir hata ayıklayıcı ve kod aracılığıyla adım burada yalnızca mümkün değildir zaman zaman ortaya çıkan sorunları iliştirin. Bu mekanizma çekirdek bileşenlerini bulunan <xref:System.Diagnostics?displayProperty=nameWithType> ad alanı ve oluşur:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, yazılması için izleme bilgilerin kaynağına ait olduğu <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, gelen izlenecek bilgileri almanızı somut dinleyiciler için Özet temel sınıf olan <xref:System.Diagnostics.TraceSource> ve bir dinleyici özgü hedefine çıktı. Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> çıkışları izleme bilgileri bir XML dosyası. Son olarak, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, izleme ayrıntı denetim uygulama kullanıcının izin verir ve genellikle yapılandırmasında belirtilen.  
  
-   Temel bileşenlerine ek olarak, kullandığınız [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) görüntülemek ve arama için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izlemeleri. Araç özellikle tarafından oluşturulan izleme dosyaları için tasarlanmış [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve kullanılarak yazılan <xref:System.Diagnostics.XmlWriterTraceListener>. Aşağıdaki şekilde çeşitli bileşenler izleme katılan gösterilmektedir.  
  
 ![Özel durumlar ve hataları işleme](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Bir özel kanaldan izleme  
 Özel kanal çalışan uygulama bir hata ayıklayıcısı eklemeniz mümkün değilse, sorunları tanılamalarına yardımcı olmak için izleme iletilerini çıkışı yazmanız gerekir. Bu iki üst düzey görevler içerir: örnekleme bir <xref:System.Diagnostics.TraceSource> ve izlemelerini yazmak için kendi yöntemleri çağırma.  
  
 Başlatılırken bir <xref:System.Diagnostics.TraceSource>, belirttiğiniz dize kaynak adı haline gelir. Bu ad, izleme kaynağı (etkinleştir/devre dışı bırak/kümesi izleme düzeyini) yapılandırmak için kullanılır. Ayrıca, kendi çıktı izlemede görünür. Özel kanal izleme bilgilerini nereden geldiğini anlamak okuyucular izleme çıktısını yardımcı olmak için bir benzersiz kaynak adı kullanmanız gerekir. İzleme kaynağı adı olarak bilgilerinin yazma derlemenin adını kullanarak yaygın bir uygulamadır. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.ServiceModel System.ServiceModel derlemesinden yazılan bilgi izleme kaynak olarak kullanır.  
  
 İzleme kaynağı oluşturduktan sonra arama kendi <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, veya <xref:System.Diagnostics.TraceSource.TraceInformation%2A> izleme dinleyicileri izleme girişler yazmak için yöntemleri. Her izleme giriş için yazma, tanımlanan olay türleri biri olarak olay türünü sınıflandırmak için ihtiyacınız <xref:System.Diagnostics.TraceEventType>. Bu sınıflandırma ve izleme düzeyi ayarı yapılandırmasında izleme girişi dinleyicisi çıkış olup olmadığını belirler. Örneğin, yapılandırma için izleme düzeyi ayarını `Warning` sağlayan `Warning`, `Error` ve `Critical` yazılacak girişleri ancak blokları bilgiler ve ayrıntılı girişleri izleme. İzleme kaynağı başlatmasını ve bilgi düzeyindeki bir giriş çıkışı yazma örnek aşağıda verilmiştir:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  İzleme çıktısı okuyucular çıkış nereden geldiğini anlamak amacıyla, özel kanal için benzersiz olan bir izleme kaynak adı belirtmeniz önerilir.  
  
#### <a name="integrating-with-the-trace-viewer"></a>İzleme Görüntüleyicisi ile tümleştirme  
 Kanal tarafından oluşturulan izlemeleri, çıktı tarafından okunabilir bir biçimde olabilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> İzleme dinleyicisi olarak. Bu zorunlu değildir, kanal geliştiricisi olarak, yapmanız gereken. Bunun yerine, uygulama kullanıcısı (veya uygulama sorunlarını giderme kişi) olduğundan, bu İzleme dinleyicisi uygulamanın yapılandırma dosyasındaki yapılandırma gerekiyor. Örneğin, aşağıdaki yapılandırma hem izleme bilgilerini çıkarır <xref:System.ServiceModel?displayProperty=nameWithType> ve `Microsoft.Samples.Udp` adlı dosyaya `TraceEventsFile.e2e`:  
  
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
  
#### <a name="tracing-structured-data"></a>İzleme yapılandırılmış verileri  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>sahip bir <xref:System.Diagnostics.TraceSource.TraceData%2A> bir veya daha fazla nesne alan yöntemi olan izleme girişi dahil edilecek. Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi, her nesne üzerinde çağrılır ve sonuç dizesini izleme girişi bir parçası olarak yazılır. Kullanırken <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> izlemeleri çıktısını almak için geçirebilirsiniz bir <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> veri nesnesi olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>. Sonuçta elde edilen izleme girişi tarafından sağlanan XML içeren <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Bir örnek girdi XML uygulama verilerle şöyledir:  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] İzleme görüntüleyicisini anlar şeması `TraceRecord` daha önce gösterilen öğesi ve kendi alt öğelerini verileri ayıklar ve tablo biçiminde görüntüler. Kanalınızı Bu şemayı yapılandırılmış uygulama verilerini izlerken veri okuma Svctraceviewer.exe kullanıcıların yardımcı olmak için kullanmanız gerekir.
