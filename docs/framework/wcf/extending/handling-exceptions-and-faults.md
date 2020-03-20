---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: bca77b575be65513f9a792352e14e3f9bd7b4904
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185622"
---
# <a name="handling-exceptions-and-faults"></a>Özel Durum ve Hataları İşleme
Özel durumlar, hizmet veya istemci uygulaması içindeki hataları yerel olarak iletmek için kullanılır. Hatalar, diğer taraftan, sunucudan istemciye veya tam tersi gibi hizmet sınırları içinde hataları iletmek için kullanılır. Aktarım kanalları hatalara ek olarak, aktarım düzeyi hatalarını iletmek için genellikle aktarıma özgü mekanizmalar kullanır. Örneğin, HTTP aktarım, varolmayan bir uç nokta URL'sini iletmek için 404 gibi durum kodları kullanır (hata yı geri göndermek için bitiş noktası yoktur). Bu belge, özel kanal yazarlarına rehberlik sağlayan üç bölümden oluşur. İlk bölümde, özel durumların ne zaman ve nasıl tanımlanılı piştileli ve atılaması konusunda rehberlik sağlar. İkinci bölümde, hata oluşturma ve tüketme konusunda kılavuzluk sağlar. Üçüncü bölümde, çalışan uygulamalarda sorun gidermede özel kanalınızın kullanıcısına yardımcı olmak için izleme bilgilerinin nasıl sağlandığı açıklanmaktadır.  
  
## <a name="exceptions"></a>Özel durumlar  
 Bir özel durum atarken akılda tutulması gereken iki şey vardır: Öncelikle kullanıcıların özel duruma uygun şekilde tepki verebilen doğru kod yazmalarına olanak tanıyan bir tür olmalıdır. İkinci olarak, kullanıcının neyin yanlış gittiğini, hata etkisini ve nasıl düzeltilebildiğini anlaması için yeterli bilgi sağlaması yeterlidir. Aşağıdaki bölümler, Windows Communication Foundation (WCF) kanalları için özel durum türleri ve iletileri hakkında rehberlik eder. Özel Durumlar için Tasarım Yönergeleri belgesinde .NET'teki özel durumlar hakkında genel kılavuz da vardır.  
  
### <a name="exception-types"></a>Özel Durum Türleri  
 Kanallar tarafından atılan tüm özel durumlar, bir <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>veya <xref:System.ServiceModel.CommunicationException>türetilen bir tür olmalıdır. (Örneğin, <xref:System.ObjectDisposedException> yalnızca arama kodunun kanalı kötüye verdiğini belirtmek için de verilebilir. Bir kanal doğru kullanılırsa, yalnızca verilen özel durumları atmalıdır.) WCF, kanallardan <xref:System.ServiceModel.CommunicationException> türeyen ve kanallar tarafından kullanılmak üzere tasarlanmış yedi özel durum türü sağlar. Sistemin diğer <xref:System.ServiceModel.CommunicationException>bölümleri tarafından kullanılmak üzere tasarlanmış başka türemiş özel durumlar da vardır. Bu özel durum türleri şunlardır:  
  
|Özel Durum Türü|Anlamı|İç Özel Durum İçeriği|Kurtarma Stratejisi|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Dinleme için belirtilen bitiş noktası adresi zaten kullanımdadır.|Varsa, bu özel durum neden aktarım hatası hakkında daha fazla ayrıntı sağlar. Örneğin. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>veya <xref:System.Net.Sockets.SocketException>.|Farklı bir adres deneyin.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|İşlem, dinleme için belirtilen uç nokta adresine erişim edeğildir.|Varsa, bu özel durum neden aktarım hatası hakkında daha fazla ayrıntı sağlar. Örneğin, <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>veya .|Farklı kimlik bilgileri ile deneyin.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılan hata lı durumdadır (daha fazla bilgi için [bkz.](understanding-state-changes.md) Birden çok bekleyen çağrısı olan bir nesne Hatalı duruma geçtiğinde, yalnızca bir arama hatayla ilgili bir özel durum <xref:System.ServiceModel.CommunicationObjectFaultedException>atar ve geri kalan çağrılar da . Bir uygulama bazı özel durumu gözden kbaktığından ve büyük olasılıkla özgün özel durumu yakalayan iş parçacığı dışında bir iş parçacığı üzerinde zaten hatalı bir nesne kullanmaya çalıştığından, bu özel durum genellikle atılır.|Varsa iç özel durum hakkında ayrıntılı bilgi sağlar.|Yeni bir nesne oluşturun. İlk etapta <xref:System.ServiceModel.ICommunicationObject> hataya neyin neden olduğuna bağlı olarak, kurtarmak için gereken başka işler olabileceğini unutmayın.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Kullanılan iptal edildi (daha fazla bilgi için [bkz.](understanding-state-changes.md) Benzer <xref:System.ServiceModel.CommunicationObjectFaultedException>, onun özel durum <xref:System.ServiceModel.ICommunicationObject.Abort%2A> uygulama nesne, büyük olasılıkla başka bir iş parçacığı çağırdı gösterir ve nesne artık bu nedenle kullanılabilir.|Varsa iç özel durum hakkında ayrıntılı bilgi sağlar.|Yeni bir nesne oluşturun. İlk etapta iptal <xref:System.ServiceModel.ICommunicationObject> in neden ne bağlı olarak, kurtarmak için gerekli başka bir iş olabilir unutmayın.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Hedef uzak bitiş noktası dinlemiyor. Bu, bitiş noktası adresinin herhangi bir bölümünün yanlış, çözülemez veya bitiş noktasının aşağı olmasına neden olabilir. Örnekler arasında DNS hatası, Queue Manager kullanılamıyor ve hizmet inçalışmıyor.|İç özel durum, genellikle temel aktarımdan ayrıntılar sağlar.|Farklı bir adres deneyin. Alternatif olarak, gönderen bir süre bekleyebilir ve hizmetin düşmesi durumunda yeniden deneyebilir|  
|<xref:System.ServiceModel.ProtocolException>|Bitiş noktası ilkesinde açıklandığı gibi iletişim protokolleri uç noktalar arasında eşleşmez. Örneğin, çerçeveleme içerik türü uyuşmazlığı veya maksimum ileti boyutu aşıldı.|Varsa, belirli bir iletişim kuralı hatası hakkında daha fazla bilgi sağlar. Örneğin, <xref:System.ServiceModel.QuotaExceededException> hata nedeni MaxReceivedMessageSize'ı aştığında iç özel durumdur.|Kurtarma: Gönderenin ve alınan protokol ayarlarının eşleştirilmesini sağlayın. Bunu yapmanın bir yolu, hizmet bitiş noktasının meta verilerini (ilkesi) yeniden içe aktarma ve kanalı yeniden oluşturmak için oluşturulan bağlamayı kullanmaktır.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Uzak bitiş noktası dinliyor, ancak iletileri işlemeye hazır değil.|Varsa, iç Özel Durum SOAP hatası veya taşıma düzeyinde hata ayrıntıları sağlar.|Kurtarma: Bekleyin ve daha sonra işlemi yeniden deneyin.|  
|<xref:System.TimeoutException>|İşlem zaman açısından tamamlanmadı.|Zaman açığı hakkında ayrıntılı bilgi verebilir.|Bekleyin ve işlemi daha sonra yeniden deneyin.|  
  
 Yalnızca bu tür varolan özel durum türlerinin tümünden farklı belirli bir kurtarma stratejisine karşılık geliyorsa yeni bir özel durum türü tanımlayın. Yeni bir özel durum türü tanımlarsanız, <xref:System.ServiceModel.CommunicationException> türetilmiş sınıflarından veya bunlardan birini türemesi gerekir.  
  
### <a name="exception-messages"></a>Özel Durum Mesajları  
 Özel durum iletileri, kullanıcının sorunu anlamasına ve çözmesine yardımcı olacak yeterli bilgi sağlaması gerektiğinden, programı değil, kullanıcıyı hedeflenebiliyor. İyi bir özel durum iletisinin üç temel bölümü şunlardır:  
  
 Olan şeyleri ifade eder. Kullanıcının deneyimiyle ilgili terimleri kullanarak sorunun net bir açıklamasını sağlayın. Örneğin, kötü bir özel durum iletisi "Geçersiz yapılandırma bölümü" olacaktır. Bu, kullanıcıyı hangi yapılandırma bölümünün yanlış olduğunu ve neden yanlış olduğunu merak etmeye bırakır. Geliştirilmiş bir ileti "Geçersiz yapılandırma \<bölümü özel> bağlama" olacaktır. Daha da iyi bir mesaj olacaktır "Bağlama zaten myTransport adlı bir taşıma var, çünkü myBinding adlı bağlama myTransport adlı taşıma ekleyemezsiniz". Bu, kullanıcının uygulamanın yapılandırma dosyasında kolayca tanımlayabileceği terimleri ve adları kullanan çok özel bir iletidir. Ancak, hala birkaç önemli bileşenleri eksik.  
  
 Hatanın önemi. İleti hatanın ne anlama geldiğini açıkça belirtmediği sürece, kullanıcı büyük olasılıkla bunun önemli bir hata mı yoksa yoksayoksayılabilir mi diye merak edebilir. Genel olarak, iletiler hatanın anlamı veya önemi ile yol açmalıdır. Önceki örneği iyileştirmek için, ileti "ServiceHost bir yapılandırma hatası nedeniyle Aç'a ulaşamadı: bağlama zaten myTransport adlı bir aktarım olduğundan myBinding adlı bağlama myTransport adlı aktarım ekleyemezsiniz".  
  
 Kullanıcının sorunu nasıl düzeltmesi gerektiği. İletinin en önemli bölümü, kullanıcının sorunu düzeltmesi için yardımcı olmaktır. İleti, sorunu gidermek için neyi denetlemesi veya düzeltilmeye ilişkin bazı kılavuzlar veya ipuçları içermelidir. Örneğin, "ServiceHost bir yapılandırma hatası nedeniyle Aç'a ulaşamadı: Bağlama zaten myTransport adlı bir aktarım olduğundan myBinding adlı bağlama myTransport adlı aktarım ekleyemez. Lütfen bağlamada sadece bir nakil olduğundan emin olun" dedi.  
  
## <a name="communicating-faults"></a>İletişim Hataları  
 SOAP 1.1 ve SOAP 1.2 her ikisi de hatalar için belirli bir yapı tanımlar. İki belirtim arasında bazı farklar vardır, ancak genel olarak, İleti ve MessageFault türleri hata oluşturmak ve tüketmek için kullanılır.  
  
 ![Özel durumları ve hataları işleme](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultKarşılaştırmac")  
SOAP 1.2 Arıza (sol) ve SOAP 1.1 Arıza (sağ). SOAP 1.1'de yalnızca Fay öğesinin ad alanı nın nitelikli olduğunu unutmayın.  
  
 SOAP, hata iletisini yalnızca bir hata öğesi (adı olan `<env:Fault>`bir öğe) `<env:Body>`içeren bir ileti olarak tanımlar. Hata elemanının içeriği şekil 1'de gösterildiği gibi SOAP 1.1 ile SOAP 1.2 arasında biraz farklılık gösterir. Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıf bu farklılıkları tek bir nesne modeline normalleştirir:  
  
```csharp
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
  
 Özellik `Code` `env:Code` (veya `faultCode` SOAP 1.1'de) karşılık gelir ve hatanın türünü tanımlar. SOAP 1.2 için `faultCode` izin verilen beş değer (örneğin, Gönderen ve `Subcode` Alıcı) tanımlar ve herhangi bir alt kod değeri içerebilen bir öğe tanımlar. (İzin verilebilen arıza kodları listesi ve anlamları için [SOAP 1.2 belirtimine](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) bakın.) SOAP 1.1'in biraz farklı bir mekanizması `faultCode` vardır: Tamamen yenilerini tanımlayarak veya nokta notasını kullanarak daha spesifik `faultCodes`, örneğin Client.Authentication' ı kullanarak genişletilebilecek dört değeri (örneğin, İstemci ve Sunucu) tanımlar.  
  
 MessageFault'ı program hataları için kullandığınızda, FaultCode.Name ve FaultCode.Namespace, SOAP 1.2 `env:Code` veya SOAP 1.1'in `faultCode`adı ve ad alanına eşler. Soap 1.2 `env:Subcode` için FaultCode.SubCode haritaları ve SOAP 1.1 için null.  
  
 Bir hatayı programlı bir şekilde ayırt etmek ilginçse, yeni hata alt kodları (veya SOAP 1.1 kullanıyorsanız yeni hata kodları) oluşturmalısınız. Bu, yeni bir özel durum türü oluşturmaya benzer. SOAP 1.1 hata kodları ile nokta gösterimini kullanmaktan kaçınmalısınız. [(WS-I Temel Profili](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) de hata kodu nokta gösterimi kullanımını engeller.)  
  
```csharp
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
  
 Özellik, `Reason` bir özel durum `faultString` iletisine benzer hata durumunun insan tarafından okunabilir bir açıklamasına (veya SOAP 1.1'de) karşılık gelir. `env:Reason` Sınıf `FaultReason` (ve `env:Reason/faultString`SOAP) küreselleşme yararına birden fazla çeviri olması için yerleşik destek vardır.  
  
```csharp
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
  
 Hata detay ı `GetDetail` \<içeriği, T> ve `GetReaderAtDetailContents`() dahil olmak üzere çeşitli yöntemler kullanılarak MessageFault'da açıklanır. Hata ayrıntısı, hata yla ilgili ek ayrıntı taşımak için opak bir öğedir. Bu, hatayla birlikte taşımak istediğiniz bazı rasgele yapılandırılmış ayrıntı varsa yararlıdır.  
  
### <a name="generating-faults"></a>Hata Oluşturma  
 Bu bölümde, bir kanalda veya kanal tarafından oluşturulan bir ileti özelliğinde algılanan bir hata durumuna yanıt olarak hata oluşturma işlemi açıklanır. Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak bir hata geri göndermektir.  
  
 Bir hata oluştururken, özel kanal hatayı doğrudan göndermemeli, bunun yerine, bir özel durum oluşturmalı ve yukarıdaki katmanın bu özel durumu bir hataya dönüştürüp dönüştürmemeye ve nasıl gönderilemeyeceğine karar vermesine izin vermelidir. Bu dönüşüme yardımcı olmak için `FaultConverter` kanal, özel kanal tarafından atılan özel durumu uygun hataya dönüştürebilecek bir uygulama sağlamalıdır. `FaultConverter`olarak tanımlanır:  
  
```csharp
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
  
 Özel hatalar oluşturan her kanal, `FaultConverter` bir çağrıdan ''a' `GetProperty<FaultConverter>`yı uygulamalı ve döndürmelidir. Özel `OnTryCreateFaultMessage` uygulama, özel durumu bir hataya dönüştürmeli veya `FaultConverter`iç kanalın. Kanal bir aktarım ise, özel durumu dönüştürmesi veya kodlayıcının `FaultConverter` `FaultConverter` veya WCF'de sağlanan varsayılan değere dönüştürmesi gerekir. Varsayılan, `FaultConverter` WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür. Burada bir `OnTryCreateFaultMessage` örnek uygulamadır.  
  
```csharp
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
  
 Bu desenin bir sonucu, hata gerektiren hata koşulları için katmanlar arasında atılan özel durumlar doğru hata oluşturmak için ilgili hata oluşturucu için yeterli bilgi içermelidir. Özel bir kanal yazarı olarak, bu tür özel durumlar zaten yoksa, farklı hata koşullarına karşılık gelen özel durum türleri tanımlayabilirsiniz. Kanal katmanlarında geçiş yapan özel durumlar, opak hata verileri yerine hata koşulunu iletmesi gerektiğini unutmayın.  
  
### <a name="fault-categories"></a>Hata Kategorileri  
 Genellikle üç hata kategorisi vardır:  
  
1. Tüm yığın boyunca yaygın olan hatalar. Bu hatalar kanal yığınındaki herhangi bir katmanda karşılaşılan olabilir, örneğin GeçersizKardinalityAddressingException.  
  
2. Yığında belirli bir katmanın üzerinde herhangi bir yerde karşılaşılabilen hatalar, örneğin akışlı bir hareketle veya güvenlik rolleriyle ilgili bazı hatalar.  
  
3. Yığındaki tek bir katmana yönlendirilen hatalar, örneğin WS-RM sıra numarası hataları gibi hatalar.  
  
 Kategori 1. Hatalar genellikle WS-Adresleme ve SOAP hatalarıdır. WCF `FaultConverter` tarafından sağlanan taban sınıf, WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür, böylece bu özel durumların dönüştürülmesini kendiniz yapmak zorunda kalmamanız gerekir.  
  
 Kategori 2. Hatalar, bir katman iletiye bu katmanla ilgili ileti bilgilerini tamamen tüketmeyen bir özellik eklediğinde oluşur. Daha yüksek bir katman ileti özelliğinden ileti bilgilerini daha fazla işlemesini istediğinde hatalar daha sonra algılanabilir. Bu tür kanallar, `GetProperty` daha yüksek katmanın doğru hatayı geri göndermesini sağlamak için daha önce belirtilenleri uygulamalıdır. Bunun bir örneği TransactionMessageProperty'dir. Bu özellik, üstbilgideki tüm verileri tam olarak doğrulamadan iletiye eklenir (bunu yapmak, dağıtılmış işlem koordinatörüyle (DTC) iletişim kurmayı içerebilir.  
  
 Kategori 3. Hatalar yalnızca işlemcide tek bir katman tarafından oluşturulur ve gönderilir. Bu nedenle tüm özel durumlar katman içinde yer almaktadır. Kanallar arasında tutarlılığı artırmak ve bakımı kolaylaştırmak için, özel kanalınız dahili hatalar için bile hata iletileri oluşturmak için önceden belirtilen deseni kullanmalıdır.  
  
### <a name="interpreting-received-faults"></a>Alınan Hataları yorumlama  
 Bu bölümde, bir hata iletisi alırken uygun özel durum oluşturmak için kılavuz sağlar. Yığındaki her katmanda bir iletiyi işlemek için karar ağacı aşağıdaki gibidir:  
  
1. Katman iletiyi geçersiz kabul ederse, katman 'geçersiz ileti' işlemini yapmalıdır. Bu tür işlemler katmana özgüdür, ancak iletiyi bırakmayı, izlemeyi veya hataya dönüştürülen bir özel durum atmayı içerebilir. Örnekler arasında güvenliğin düzgün güvenli olmayan bir ileti alması veya RM'nin hatalı sıra numarası olan bir ileti alması verilebilir.  
  
2. Aksi takdirde, ileti katmana özel olarak uygulanan bir hata iletisiyse ve ileti katmanın etkileşimi dışında anlamlı değilse, katman hata koşulunu işlemelidir. Bunun bir örneği, RM kanalının üzerindeki katmanlar için anlamsız olan ve RM kanalının hatalı olması ve bekleyen işlemlerden atılması anlamına gelen bir RM Dizisi Reddedilen hatadır.  
  
3. Aksi takdirde, ileti İstek() veya Receive() adresinden döndürülmelidir. Bu, katmanın hatayı tanıdığı durumları içerir, ancak hata yalnızca bir isteğin başarısız olduğunu gösterir ve kanalı niçin hatalı olduğu ve bekleyen işlemlerden atıldığı anlamına gelmez. Böyle bir durumda kullanılabilirliği artırmak için, `GetProperty<FaultConverter>` katman `FaultConverter` uygulamalı ve geçersiz kılma tarafından bir `OnTryCreateException`özel duruma hata dönüştürebilir türemiş bir sınıf döndürün.  
  
 Aşağıdaki nesne modeli iletileri özel durumlara dönüştürmeyi destekler:  
  
```csharp
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
  
 Bir kanal katmanı, hata iletilerinin özel durumlara dönüştürülmesini desteklemek için uygulayabilir. `GetProperty<FaultConverter>` Bunu yapmak için `OnTryCreateException` hata iletisini geçersiz kılın ve denetleyin. Tanındıysa, dönüştürmeyi yapın, aksi takdirde iç kanaldan dönüştürmesini isteyin. Aktarım kanalları varsayılan `FaultConverter.GetDefaultFaultConverter` SOAP/WS Adresleme FaultConverter almak için temsilci gerekir.  
  
 Tipik bir uygulama şuna benzer:  
  
```csharp
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
  
 Farklı kurtarma senaryoları olan belirli hata koşulları için, `ProtocolException`türetilmiş bir sınıf tanımlamayı düşünün.  
  
### <a name="mustunderstand-processing"></a>MustUnderstand İşleme  
 SOAP, gerekli bir üstbilginin alıcı tarafından anlaşılmadığını bildirmek için genel bir hata tanımlar. Bu hata `mustUnderstand` hata olarak bilinir. WCF'de özel kanallar `mustUnderstand` hiçbir zaman hata oluşturmaz. Bunun yerine, WCF iletişim yığınının üst kısmında bulunan WCF Dispatcher, MustUnderstand=true olarak işaretlenmiş tüm üstbilginin temel yığın tarafından anlaşıldığını denetler. Herhangi bir anlaşılamadı, `mustUnderstand` bir hata bu noktada oluşturulur. (Kullanıcı bu `mustUnderstand` işlemi kapatmayı seçebilir ve uygulamanın tüm ileti üstbilgilerini almasını sağlayabilir. Bu durumda uygulama işleme nin `mustUnderstand` uygulanmasından sorumludur.) Oluşturulan hata, MustUnderstand=true olan ve anlaşılamayan tüm üstbilginin adlarını içeren bir NotUnderstood üstbilgi içerir.  
  
 Protokol kanalınız MustUnderstand=true ile özel bir üstbilgi gönderir ve bir `mustUnderstand` hata alırsa, bu hatanın gönderdiği üstbilgiden kaynaklanıp kaynaklanmadığını belirlemesi gerekir. `MessageFault` Sınıfta bunun için yararlı olan iki üye vardır:  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault`hata `true` bir `mustUnderstand` hata ise döndürür. `WasHeaderNotUnderstood`belirtilen `true` ad ve ad alanına sahip üstbilgi hataya NotUnderstood üstbilgi olarak dahil edilirse döndürür.  Aksi takdirde, `false`döner.  
  
 Bir kanal MustUnderstand = true olarak işaretlenmiş bir üstbilgi yayarsa, bu katma da `mustUnderstand` Özel Durum Oluşturma API deseni uygulamalı ve bu üstbilginin neden olduğu hataları daha önce açıklandığı gibi daha kullanışlı bir özel durum dönüştürmeli.  
  
## <a name="tracing"></a>İzleme  
 .NET Framework, üretim uygulamalarını veya yalnızca hata ayıklayıcı eklemenin ve kod üzerinden adım atmanın mümkün olmadığı aralıklı sorunların tanılanmasına yardımcı olmak için program yürütmesini izlemek için bir mekanizma sağlar. Bu mekanizmanın temel bileşenleri <xref:System.Diagnostics?displayProperty=nameWithType> ad alanındadır ve aşağıdakilerden oluşur:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, hangi iz bilgi nin kaynağı <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>yazılması, hangi somut dinleyiciler için soyut bir taban sınıf <xref:System.Diagnostics.TraceSource> olan bu bilgi takip almak ve bir dinleyici özgü hedefe çıktı. Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> bir XML dosyasına izleme bilgileri çıktıları. Son <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>olarak, uygulama kullanıcı izleme verbosity kontrol sağlar ve genellikle yapılandırmada belirtilir.  
  
- Temel bileşenlere ek olarak, WCF izlerini görüntülemek ve aramak için [Service Trace Viewer Aracı'nı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanabilirsiniz. Araç, WCF tarafından oluşturulan ve kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener>yazılan izleme dosyaları için özel olarak tasarlanmıştır. Aşağıdaki şekil, izleme ile ilgili çeşitli bileşenleri göstermektedir.  
  
 ![Özel durumları ve hataları işleme](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Özel Kanaldan İzleme  
 Özel kanallar, çalışan uygulamaya hata ayıklama eklemenin mümkün olmadığında sorunları tanılamada yardımcı olmak için izleme iletileri yazmalıdır. Bu iki üst düzey görev içerir: <xref:System.Diagnostics.TraceSource> A'yı anında bulma ve izleme yazmak için yöntemlerini çağırma.  
  
 Bir <xref:System.Diagnostics.TraceSource>, belirttiğiniz dize, o kaynağın adı olur. Bu ad, izleme kaynağını yapılandırmak (etkinleştirme/devre dışı bırakma/ayarlama düzeyi) için kullanılır. Ayrıca izleme çıktısının kendisinde de görünür. Özel kanallar, izleme çıktısını okuyucuların izleme bilgilerinin nereden geldiğini anlamalarına yardımcı olmak için benzersiz bir kaynak adı kullanmalıdır. İzleme kaynağının adı olarak bilgileri yazan derlemenin adını kullanmak yaygın bir uygulamadır. Örneğin, WCF System.ServiceModel assemblyinden yazılan bilgiler için izleme kaynağı olarak System.ServiceModel kullanır.  
  
 Bir izleme kaynağına sahip olduktan <xref:System.Diagnostics.TraceSource.TraceData%2A> <xref:System.Diagnostics.TraceSource.TraceEvent%2A>sonra, <xref:System.Diagnostics.TraceSource.TraceInformation%2A> izleme dinleyicilerine izleme girişleri yazmak için onun , veya yöntemleri çağırırsınız. Yazdığınız her izleme girişi için, olay türünü <xref:System.Diagnostics.TraceEventType>'de tanımlanan olay türlerinden biri olarak sınıflandırmanız gerekir. Bu sınıflandırma ve yapılandırmadaki izleme düzeyi ayarı, izleme girişinin dinleyiciye çıktı olup olmadığını belirler. Örneğin, yapılandırmada izleme düzeyini, `Warning` `Warning`girişlerin yazılmasına `Error` izin verir ve izleme yi engeller, ancak Bilgi ve `Critical` Verbose girişlerini engeller. Aşağıda, izleme kaynağının anlık olarak yazılması ve Bilgi düzeyinde bir girişin yazılmasına bir örnek verilmiştir:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> Çıktı okuyucularının çıktının nereden geldiğini anlamasına yardımcı olmak için özel kanalınıza özgü bir izleme kaynağı adı belirtmeniz önerilir.  
  
#### <a name="integrating-with-the-trace-viewer"></a>İz Görüntüleyici ile Tümleştirme  
 Kanalınız tarafından oluşturulan izleme ler, izleme dinleyicisi olarak kullanılarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Service Trace Viewer Tool [(SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tarafından okunabilir bir biçimde çıkarılabilir. Bu, kanal geliştiricisi olarak yapmanız gereken bir şey değildir. Bunun yerine, bu izleme dinleyicisini uygulamanın yapılandırma dosyasında yapılandırması gereken uygulama kullanıcısı (veya uygulamayı sorun gideren kişidir). Örneğin, aşağıdaki yapılandırma çıktıları hem <xref:System.ServiceModel?displayProperty=nameWithType> de `Microsoft.Samples.Udp` adlı `TraceEventsFile.e2e`dosyaya aşağıdaki bilgileri izleme:  
  
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
  
#### <a name="tracing-structured-data"></a>Yapılandırılmış Verilerin İzlemi  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>izleme <xref:System.Diagnostics.TraceSource.TraceData%2A> girişine dahil edilecek bir veya daha fazla nesneyi alan bir yönteme sahiptir. Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntem her nesneye çağrılır ve elde edilen dize izleme girişinin bir parçası olarak yazılır. Çıktı <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> izlemelerini kullanırken, veri <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> nesnesi olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>bir 'e geçebilirsiniz. Elde edilen izleme girişi, <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>xml tarafından sağlanan içerir. Aşağıda, XML uygulama verilerine sahip bir örnek giriş verilmiştir:  
  
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
  
 WCF iz görüntüleyici, daha önce `TraceRecord` gösterilen öğenin şemasını anlar ve alt öğelerinden verileri ayıklar ve bir tabular biçiminde görüntüler. Kanalınız, Yapılandırılmış uygulama verilerini takip ederken Svctraceviewer.exe kullanıcılarının verileri okumasına yardımcı olmak için bu şemayı kullanmalıdır.
