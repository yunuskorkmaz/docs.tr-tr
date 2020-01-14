---
title: Özel Durum ve Hataları İşleme
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 2886463510a2237834529e1ec61c73ec7251e621
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937714"
---
# <a name="handling-exceptions-and-faults"></a>Özel Durum ve Hataları İşleme
Özel durumlar, hizmette veya istemci uygulamasında yerel olarak hatalara iletişim kurmak için kullanılır. Diğer yandan hatalar, sunucudan istemciye gibi veya tam tersi gibi hizmet sınırları genelinde hataları iletmek için kullanılır. Hatalara ek olarak, aktarım kanalları genellikle aktarım düzeyi hataları iletmek için aktarıma özgü mekanizmalar kullanır. Örneğin, HTTP taşıması mevcut olmayan bir uç nokta URL 'SI ile iletişim kurmak için 404 gibi durum kodlarını kullanır (bir hata geri gönderilmesi için uç nokta yoktur). Bu belge, özel kanal yazarlarına rehberlik sağlayan üç bölümden oluşur. İlk bölüm, özel durumların ne zaman ve nasıl tanımlanacağını ve throw hakkında rehberlik sağlar. İkinci bölüm, hataları oluşturma ve kullanma konusunda rehberlik sağlar. Üçüncü bölümde, çalışan uygulamalarda sorun gidermek için özel kanalınızın kullanıcısına yardımcı olmak üzere izleme bilgilerinin nasıl sağlanacağını açıklanmaktadır.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Özel durum oluştururken göz önünde bulundurmanız gereken iki şey vardır: Ilk olarak, kullanıcıların özel duruma uygun şekilde tepki veren doğru kodu yazmasına izin veren bir tür olması gerekir. İkincisi, kullanıcının neyin yanlış gittiğini, hatanın etkisini ve nasıl düzeltileceğini anlayabilmesi için yeterli bilgi sağlaması gerekir. Aşağıdaki bölümler, Windows Communication Foundation (WCF) kanalları için özel durum türleri ve iletileri hakkında rehberlik sağlar. Özel durumlar için tasarım yönergelerinden .NET 'teki özel durumların etrafında de genel rehberlik vardır.  
  
### <a name="exception-types"></a>Özel Durum Türleri  
 Kanallar tarafından oluşturulan tüm özel durumlar <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>veya <xref:System.ServiceModel.CommunicationException>türetilmiş bir tür olmalıdır. (<xref:System.ObjectDisposedException> gibi özel durumlar da oluşturulabilir, ancak yalnızca çağıran kodun kanalda kötüye kullanılması gerektiğini gösterir. Bir kanal doğru şekilde kullanılırsa yalnızca verilen özel durumları oluşturması gerekir.) WCF, <xref:System.ServiceModel.CommunicationException> türetilen ve kanallar tarafından kullanılmak üzere tasarlanan yedi özel durum türü sağlar. Sistemin diğer bölümleri tarafından kullanılmak üzere tasarlanan diğer <xref:System.ServiceModel.CommunicationException>türetilmiş özel durumlar vardır. Bu özel durum türleri şunlardır:  
  
|Özel Durum Türü|Açıklama|İç özel durum Içeriği|Kurtarma Stratejisi|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Dinleme için belirtilen uç nokta adresi zaten kullanılıyor.|Varsa, bu özel duruma neden olan taşıma hatası hakkında daha fazla ayrıntı sağlar. Örneğin. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>veya <xref:System.Net.Sockets.SocketException>.|Farklı bir adres deneyin.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|İşlem, dinleme için belirtilen uç nokta adresine erişime izin verilmiyor.|Varsa, bu özel duruma neden olan taşıma hatası hakkında daha fazla ayrıntı sağlar. Örneğin, <xref:System.IO.PipeException>veya <xref:System.Net.HttpListenerException>.|Farklı kimlik bilgileriyle deneyin.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|Kullanılan <xref:System.ServiceModel.ICommunicationObject> hatalı durumda (daha fazla bilgi için bkz. [durum değişikliklerini anlama](understanding-state-changes.md)). Birden çok bekleyen çağrıya sahip bir nesne hatalı duruma geçiş yaptığında, yalnızca bir çağrı hatayla ilgili bir özel durum oluşturduğunda ve çağrıların geri kalanı <xref:System.ServiceModel.CommunicationObjectFaultedException>oluşturur. Bu özel durum tipik olarak oluşur çünkü bir uygulama bazı özel durumları daha fazla inceler ve muhtemelen hatalı bir nesneyi kullanmaya çalışır, büyük olasılıkla özgün özel durumu yakaladı dışında bir iş parçacığında.|Varsa, iç özel durumla ilgili ayrıntıları sağlar.|Yeni bir nesne oluşturun. <xref:System.ServiceModel.ICommunicationObject> ilk yerde hatalara neden olduğuna bağlı olarak, kurtarmak için gereken başka bir iş olabilir.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|Kullanılan <xref:System.ServiceModel.ICommunicationObject> durduruldu (daha fazla bilgi için bkz. [durum değişikliklerini anlama](understanding-state-changes.md)). <xref:System.ServiceModel.CommunicationObjectFaultedException>benzer şekilde, özel durumu uygulamanın nesne üzerinde <xref:System.ServiceModel.ICommunicationObject.Abort%2A> çağırdığını, belki de başka bir iş parçacığından olduğunu ve nesnenin artık bu nedenle kullanılamaz olduğunu gösterir.|Varsa, iç özel durumla ilgili ayrıntıları sağlar.|Yeni bir nesne oluşturun. <xref:System.ServiceModel.ICommunicationObject> ilk yerde ne olduğuna bağlı olarak, kurtarmak için gereken başka bir iş olabilir.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Hedef uzak uç nokta dinlemiyor. Bu, uç nokta adresinin herhangi bir kısmının yanlış, irçözümlenebilen veya bitiş noktasının çalışmıyor olmasından kaynaklanabilir. DNS hatası, kuyruk yöneticisi kullanılamıyor ve hizmet çalışmıyor örneklerde yer verilmiştir.|İç özel durum, genellikle temel aktarımdan ayrıntılar sağlar.|Farklı bir adres deneyin. Alternatif olarak, gönderici bir süre bekleyebilir ve hizmetin kapatılmış olması durumunda tekrar deneyebilir|  
|<xref:System.ServiceModel.ProtocolException>|Uç noktanın ilkesinde açıklanan iletişim protokolleri, uç noktalar arasında eşleşmiyor. Örneğin, çerçeveleme içerik türü uyumsuzluğu veya en fazla ileti boyutu aşıldı.|Varsa, belirli protokol hatası hakkında daha fazla bilgi sağlar. Örneğin, hata nedeni MaxReceivedMessageSize değerini aşarak <xref:System.ServiceModel.QuotaExceededException> iç özel durumdur.|Kurtarma: gönderici ve alınan protokol ayarlarının eşleştiğinden emin olun. Bunu yapmanın bir yolu, hizmet uç noktasının meta verilerini (ilke) yeniden içeri aktarmanız ve oluşturulan bağlamayı kullanarak kanalı yeniden oluşturur.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Uzak uç nokta dinliyor ancak iletileri işlemeye hazır değil.|Varsa, iç özel durum SOAP hata veya aktarım düzeyi hata ayrıntılarını sağlar.|Kurtarma: bekleyip işlemi daha sonra yeniden deneyin.|  
|<xref:System.TimeoutException>|İşlem, zaman aşımı süresi içinde tamamlanamadı.|Zaman aşımı hakkındaki ayrıntıları verebilir.|Bekleyip işlemi daha sonra yeniden deneyin.|  
  
 Yalnızca bu tür, mevcut özel durum türlerinden farklı olan belirli bir kurtarma stratejisine karşılık geliyorsa yeni bir özel durum türü tanımlayın. Yeni bir özel durum türü tanımlarsanız, <xref:System.ServiceModel.CommunicationException> veya türetilmiş sınıflarından türetmelidir.  
  
### <a name="exception-messages"></a>Özel durum Iletileri  
 Özel durum iletileri, kullanıcının sorunu anlamalarına ve çözmesine yardımcı olmak için yeterli bilgi sağlamaları için programı değil kullanıcıya hedeflenirler. İyi bir özel durum iletisinin üç temel bölümü şunlardır:  
  
 Olan şeyleri ifade eder. Kullanıcının deneyimiyle ilgili terimleri kullanarak sorun hakkında net bir açıklama sağlayın. Örneğin, hatalı bir özel durum iletisi "geçersiz yapılandırma bölümü" olacaktır. Bu, kullanıcının hangi yapılandırma bölümünün yanlış olduğunu ve neden yanlış olduğunu merak eden kullanıcı olarak bırakır. İyileştirilmiş bir ileti "geçersiz yapılandırma bölümü \<customBinding >" olacaktır. Daha da iyi bir ileti "myTransport adlı bağlamaya myBinding adlı bağlamaya eklenemiyor, çünkü bağlama zaten myTransport adlı bir aktarıma sahip" olur. Bu, kullanıcının uygulama yapılandırma dosyasında kolayca tanımlayabilmesi için hüküm ve adları kullanan çok özel bir iletidir. Ancak, hala birkaç anahtar bileşen eksik.  
  
 Hatanın önemi. İleti, hatanın ne anlama geldiğini açıkça belirtmedikçe, Kullanıcı önemli bir hata olup olmadığını veya yoksayılıp yoksayılmadığını merak ediyor olabilir. Genel olarak, iletiler hatanın anlamı veya önemi ile sonuçlanmalıdır. Önceki örneği geliştirmek için, bir yapılandırma hatası nedeniyle ileti "ServiceHost açılamadı: bağlama zaten myTransport adlı bir aktarıma sahip olduğu için myTransport adlı bağlamaya eklenemedi.  
  
 Kullanıcının sorunu nasıl düzeltebilmelidir. İletinin en önemli bölümü, kullanıcının sorunu gidermesine yardımcı olur. İleti, sorunu gidermek için nelerin denetlenmesi veya düzeltilmesi hakkında bazı kılavuz veya ipuçları içermelidir. Örneğin, "bir yapılandırma hatası nedeniyle ServiceHost açılamadı: bağlama zaten myTransport adlı bir aktarıma sahip olduğu için myTransport adlı bağlamaya myBinding adlı bir aktarıma eklenemiyor. Lütfen bağlamada yalnızca bir aktarım olduğundan emin olun.  
  
## <a name="communicating-faults"></a>Hataları iletişim kurma  
 SOAP 1,1 ve SOAP 1,2 hatalar için belirli bir yapı tanımlar. İki belirtim arasında bazı farklılıklar vardır ancak genel olarak, hata oluşturmak ve kullanmak için Ileti ve MessageFault türleri kullanılır.  
  
 ![Özel durumları ve hataları işleme](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1,2 hatası (sol) ve SOAP 1,1 hatası (sağ). SOAP 1,1 ' de yalnızca hata öğesinin ad alanı nitelikli olduğunu unutmayın.  
  
 SOAP bir hata iletisini, yalnızca bir hata öğesi (adı `<env:Fault>`) içeren bir ileti olarak bir `<env:Body>`alt öğesi olarak tanımlar. Hata öğesinin içeriği, Şekil 1 ' de gösterildiği gibi SOAP 1,1 ve SOAP 1,2 arasında biraz farklılık gösterir. Ancak, <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> sınıfı bu farklılıkları bir nesne modeliyle normalleştirir:  
  
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
  
 `Code` özelliği, `env:Code` (veya SOAP 1,1 ' deki `faultCode`) karşılık gelir ve hatanın türünü tanımlar. SOAP 1,2 `faultCode` için izin verilen beş değeri tanımlar (örneğin, gönderen ve alıcı) ve herhangi bir alt kod değeri içerebilen bir `Subcode` öğesi tanımlar. (İzin verilen hata kodlarının listesi ve anlamları için [SOAP 1,2 belirtimine](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) bakın.) SOAP 1,1 biraz farklı bir mekanizmaya sahiptir: tamamen yeni olanlar tanımlayarak veya nokta gösterimini kullanarak, örneğin Client. Authentication gibi daha belirli `faultCodes`oluşturmak için Genişletilebilir olabilecek dört `faultCode` değeri (örneğin, Istemci ve sunucu) tanımlar.  
  
 Program hatalarına MessageFault kullandığınızda, FaultCode.Name ve FaultCode. Namespace, SOAP 1,2 `env:Code` veya SOAP 1,1 `faultCode`ad ve ad uzayına eşlenir. FaultCode. alt kod SOAP 1,2 için `env:Subcode` eşlenir ve SOAP 1,1 için null.  
  
 Bir hatayı programlama yoluyla ayırt etmek için ilginç olması halinde yeni hata alt kodları (veya SOAP 1,1 kullanıyorsanız yeni hata kodları) oluşturmanız gerekir. Bu, yeni bir özel durum türü oluşturulmasına benzer. SOAP 1,1 hata kodlarıyla nokta gösterimini kullanmaktan kaçının. ( [WS-ı temel profili](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) Ayrıca hata kodu nokta gösteriminin kullanımını etkilenmeden.)  
  
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
  
 `Reason` özelliği, bir özel durumun iletisine benzer şekilde hata koşulunun okunabilir bir açıklamasını (veya SOAP 1,1 ' deki `faultString`) karşılık `env:Reason` gelir. `FaultReason` sınıfı (ve SOAP `env:Reason/faultString`), Genelleştirme açısından birden çok çevirisi olması için yerleşik desteğe sahiptir.  
  
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
  
 Hata ayrıntısı içerikleri, `GetDetail`\<T > ve `GetReaderAtDetailContents`() gibi çeşitli yöntemler kullanılarak MessageFault üzerinde kullanıma sunulur. Hata ayrıntısı, hata hakkında ek ayrıntı taşıyan donuk bir öğedir. Bu, hata ile taşımak istediğiniz rastgele yapılandırılmış bazı ayrıntılar varsa yararlıdır.  
  
### <a name="generating-faults"></a>Hatalar üretiliyor  
 Bu bölümde, bir kanalda veya kanal tarafından oluşturulan bir ileti özelliğinde algılanan bir hata koşuluna yanıt olarak hata oluşturma işlemi açıklanmaktadır. Tipik bir örnek, geçersiz veri içeren bir istek iletisine yanıt olarak hata geri gönderiyor.  
  
 Bir hata oluştururken, özel kanal hatayı doğrudan göndermemelidir, bunun yerine bir özel durum oluşturması ve katmanın bu özel durumu bir hataya dönüştürüp dönüştürmeyeceğine karar vermesini ve bunun nasıl gönderileceğini belirtmenizi sağlar. Bu dönüştürmeye yardımcı olması için kanal, özel kanal tarafından oluşturulan özel durumu uygun hataya dönüştürebileceğiniz bir `FaultConverter` uygulama sağlamalıdır. `FaultConverter` şöyle tanımlanır:  
  
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
  
 Özel hatalar üreten her bir kanalın `FaultConverter` uygulaması ve `GetProperty<FaultConverter>`bir çağrıdan döndürmesi gerekir. Özel `OnTryCreateFaultMessage` uygulama, özel durumu iç kanalın `FaultConverter`bir hataya veya temsilciye dönüştürmelidir. Kanal bir aktarımalıyorsa, özel durumu veya temsilciyi WCF 'de belirtilen varsayılan `FaultConverter` veya `FaultConverter` dönüştürmeniz gerekir. Varsayılan `FaultConverter`, WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür. Örnek `OnTryCreateFaultMessage` bir uygulama aşağıda verilmiştir.  
  
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
  
 Bu düzenin bir aksaklığındaki hata koşulları için katmanlar arasında oluşturulan özel durumların, ilgili hata oluşturucusunun doğru hatayı oluşturması için yeterli bilgi içermesi gerekir. Özel bir kanal yazarı olarak, bu özel durumlar zaten mevcut değilse farklı hata koşullarına karşılık gelen özel durum türleri tanımlayabilirsiniz. Kanal katmanlarındaki özel durumların, donuk hata verileri yerine hata koşulunu iletmeli olduğunu unutmayın.  
  
### <a name="fault-categories"></a>Hata kategorileri  
 Genellikle üç hata kategorisi vardır:  
  
1. Tüm yığının tamamında kapsamlı olan hatalar. Bu hatalara kanal yığınındaki herhangi bir katmanda rastlandı, örneğin ınvalidcardınalityaddressingexception.  
  
2. Yığındaki belirli bir katmanın üzerinde herhangi bir yerde, örneğin, bir akışlı işleme veya güvenlik rollerine ilişkin bazı hatalar ile karşılaşabileceği hatalar.  
  
3. Yığındaki tek bir katmana yönlendirilmiş hatalar, örneğin WS-RM sıra numarası hataları gibi hatalar.  
  
 Kategori 1. Hatalar genellikle WS-Addressing ve SOAP hatalarıdır. WCF tarafından sunulan temel `FaultConverter` sınıfı, WS-Addressing ve SOAP tarafından belirtilen hata iletilerine karşılık gelen hataları dönüştürür, bu nedenle bu özel durumların dönüştürülmesini kendiniz de işlemek zorunda değilsiniz.  
  
 Kategori 2. Bir katman, iletiye o katmana ait ileti bilgisini tamamen tüketmeyen bir özellik eklediğinde hata oluşur. Daha sonra, daha yüksek bir katman ileti özelliğinin ileti bilgisini daha fazla işlemesini istediğinde hatalar algılanabilir. Bu tür kanallar daha önce belirtilen `GetProperty` uygulamalıdır ve daha yüksek katmanın doğru hatayı geri göndermesini sağlar. Bu, TransactionMessageProperty örneğidir. Bu özellik, üstbilgideki tüm verilerin tam olarak doğrulanması gerekmeden iletiye eklenir (Bunun yapılması dağıtılmış işlem Düzenleyicisi 'ne (DTC) başvurmayı gerektirebilir.  
  
 Kategori 3. Hatalar yalnızca işlemcideki tek bir katman tarafından oluşturulup gönderilir. Bu nedenle, tüm özel durumlar katmanın içinde yer alır. Kanallar arasındaki tutarlılığı artırmak ve bakım kolaylığı sağlamak için, özel kanalınız iç hatalar için bile hata iletileri oluşturmak üzere önceden belirtilen kalıbı kullanmalıdır.  
  
### <a name="interpreting-received-faults"></a>Alınan hataları yorumlama  
 Bu bölüm, bir hata iletisi alırken uygun özel durumu oluşturmaya yönelik rehberlik sağlar. Yığındaki her katmanda bir iletiyi işlemeye yönelik karar ağacı aşağıdaki gibidir:  
  
1. Katman iletinin geçersiz olduğunu düşünür, katmanın ' geçersiz ileti ' işlemesini yapması gerekir. Bu tür bir işlem katmana özeldir, ancak iletiyi bırakmayı, izlemeyi veya bir hataya dönüştürülecek bir özel durum üretilmesini içerebilir. Örnek olarak güvenli bir şekilde güvenliği sağlanmış olmayan bir iletiyi alma, veya RM 'nin hatalı sıra numarası içeren bir ileti almasına yönelik güvenlik örnekleri bulunur.  
  
2. Aksi takdirde, ileti özellikle katmana uygulanan bir hata iletiyorsa ve ileti katmanın etkileşimi dışında anlamlı değilse, katmanın hata koşulunu işlemesi gerekir. Bunun bir örneği, RM kanalının üzerindeki katmanlara anlamlı olan ve RM kanalının hata veren ve bekleyen işlemlerden oluşturulamaması gereken bir RM sırası reddedildi hatasıdır.  
  
3. Aksi takdirde, ileti Istekten () veya Receive () döndürülmelidir. Bu, katmanın hatayı tanıdığı durumları içerir, ancak hata yalnızca bir isteğin başarısız olduğunu gösterir ve kanalın hatalı olduğunu göstermez ve bekleyen işlemlerden hata vermez. Böyle bir durumda kullanılabilirliği artırmak için, katman `GetProperty<FaultConverter>` uygulamalıdır ve `OnTryCreateException`geçersiz kılarak hatayı bir özel duruma dönüştürebilen bir `FaultConverter` türetilmiş sınıf döndürmelidir.  
  
 Aşağıdaki nesne modeli, iletilerin özel durumlara dönüştürülmesini destekler:  
  
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
  
 Bir kanal katmanı, hata iletilerinin özel durumlara dönüştürülmesini desteklemek için `GetProperty<FaultConverter>` uygulayabilir. Bunu yapmak için `OnTryCreateException` geçersiz kılın ve hata iletisini inceleyin. Tanınırsa, dönüştürmeyi yapın, aksi takdirde iç kanaldan dönüştürmeyi isteyin. Taşıma kanalları varsayılan SOAP/WS-Addressing FaultConverter 'ı almak için `FaultConverter.GetDefaultFaultConverter` temsilcisine atanmalıdır.  
  
 Tipik bir uygulama şöyle görünür:  
  
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
  
 Ayrı kurtarma senaryolarına sahip belirli hata koşulları için `ProtocolException`türetilmiş bir sınıf tanımlamayı düşünün.  
  
### <a name="mustunderstand-processing"></a>MustUnderstand Işleme  
 SOAP, gerekli bir üstbilginin alıcı tarafından anlaşılmadığından, sinyal için genel bir hata tanımlar. Bu hata `mustUnderstand` hatası olarak bilinir. WCF 'de, özel kanallar hiçbir şekilde `mustUnderstand` hata oluşturmaz. Bunun yerine, WCF iletişim yığınının en üstünde bulunan WCF dağıtıcısı, MustUnderstand = true olarak işaretlenen tüm üstbilgilerin temeldeki yığın tarafından anlaşılmadığını denetler. Herhangi bir anlaşıldığında, bu noktada bir `mustUnderstand` hatası oluşturulur. (Kullanıcı bu `mustUnderstand` işlemeyi kapatmayı seçebilir ve uygulamanın tüm ileti üstbilgilerini almasını sağlayabilir. Bu durumda, uygulama `mustUnderstand` işleme gerçekleştirmekten sorumludur.) Oluşturulan hata, MustUnderstand = true olan tüm üst bilgilerin adlarını içeren bir NotUnderstood üst bilgisi içerir.  
  
 Protokol kanalınızın MustUnderstand = true ile özel bir üst bilgi göndermesi ve bir `mustUnderstand` hatası alması durumunda, bu hatanın gönderdiği üstbilgi olup olmadığını anlamak gerekir. `MessageFault` sınıfında bu için yararlı olan iki üye vardır:  
  
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
  
 hata bir `mustUnderstand` hatası ise `IsMustUnderstandFault` `true` döndürür. `WasHeaderNotUnderstood`, belirtilen ad ve ad alanına sahip üstbilgi hataya NotUnderstood üstbilgisi olarak dahil edilse `true` döndürür.  Aksi takdirde, `false`döndürür.  
  
 Bir kanal MustUnderstand = true olarak işaretlenmiş bir üst bilgi yayıyorsa, bu katman özel durum oluşturma API 'SI modelini de uygulamalıdır ve bu üstbilginin neden olduğu `mustUnderstand` hataları daha önce açıklandığı gibi daha kullanışlı bir özel duruma dönüştürmelidir.  
  
## <a name="tracing"></a>İzleme  
 .NET Framework, program yürütmesini izlemeye yardımcı olmak için bir mekanizma sağlar ve yalnızca bir hata ayıklayıcı iliştirmek ve kodda adım adım ilerlemek mümkün olmadığı durumlarda, üretim uygulamalarını tanılamaya veya aralıklı sorunları ortaya çıkarmanın bir yoludur. Bu mekanizmanın temel bileşenleri <xref:System.Diagnostics?displayProperty=nameWithType> ad alanıdır ve şunlardan oluşur:  
  
- yazılacak izleme bilgilerinin kaynağı olan <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, bu, <xref:System.Diagnostics.TraceSource> izlenecek bilgileri alan somut dinleyiciler için soyut bir temel sınıf olan <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>ve dinleyiciye özgü hedefe çıktı. Örneğin, <xref:System.Diagnostics.XmlWriterTraceListener> izleme bilgilerini bir XML dosyasına verir. Son olarak, uygulama kullanıcısının izleme ayrıntı düzeyini denetlemesini ve genellikle yapılandırmada belirtilmesini sağlayan <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>.  
  
- Çekirdek bileşenlerine ek olarak, WCF izlemelerini görüntülemek ve aramak için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanabilirsiniz. Araç, WCF tarafından oluşturulan ve <xref:System.Diagnostics.XmlWriterTraceListener>kullanılarak yazılan izleme dosyaları için özel olarak tasarlanmıştır. Aşağıdaki şekilde, izlemeyle ilgili çeşitli bileşenler gösterilmektedir.  
  
 ![Özel durumları ve hataları işleme](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Özel bir kanaldan izleme  
 Özel kanallar, çalışan uygulamaya bir hata ayıklayıcı eklemek mümkün olmadığında sorunları tanılamaya yardımcı olmak için izleme iletilerini yazmalıdır. Bu iki üst düzey görevi içerir: bir <xref:System.Diagnostics.TraceSource> örnekleme ve izleme yazmak için yöntemlerini çağırma.  
  
 Bir <xref:System.Diagnostics.TraceSource>örnekledikten sonra belirttiğiniz dize, kaynağın adı olur. Bu ad, izleme kaynağını yapılandırmak için kullanılır (etkinleştirme/devre dışı bırakma/ayarlama izleme düzeyi). Ayrıca, izleme çıktısı içinde de görüntülenir. Özel kanallar, izleme çıktısının okuyucuların izleme bilgilerinin nereden geldiğini anlamasına yardımcı olmak için benzersiz bir kaynak adı kullanmalıdır. İzleme kaynağının adı olarak bilgileri yazan derlemenin adının kullanılması yaygın bir uygulamadır. Örneğin, WCF System. ServiceModel derlemesinden yazılan bilgiler için izleme kaynağı olarak System. ServiceModel kullanır.  
  
 İzleme kaynağına sahip olduktan sonra izleme dinleyicilerine izleme girdileri yazmak için <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>veya <xref:System.Diagnostics.TraceSource.TraceInformation%2A> yöntemlerini çağırabilirsiniz. Yazdığınız her izleme girişi için, olay türünü <xref:System.Diagnostics.TraceEventType>tanımlı olay türlerinden biri olarak sınıflandırmanız gerekir. Yapılandırma içindeki bu sınıflandırma ve izleme düzeyi ayarı, izleme girişinin dinleyiciye çıkış olup olmadığını belirtir. Örneğin, yapılandırmada izleme düzeyinin `Warning` olarak ayarlanması `Warning`, `Error` ve `Critical` izleme girişlerinin yazılmasına izin verir, ancak bilgileri ve ayrıntılı girdileri engeller. Aşağıda, bir izleme kaynağı örneğini oluşturma ve bilgi düzeyinde bir girişi yazma örneği verilmiştir:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> İzleme çıkış okuyucularınızın çıktının nereden geldiğini anlamalarına yardımcı olmak için özel kanalınıza özgü bir izleme kaynağı adı belirtmeniz kesinlikle önerilir.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Izleme görüntüleyiciyle tümleştirme  
 Kanalınıza göre oluşturulan izlemeler, izleme dinleyicisi olarak <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> kullanarak [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tarafından okunabilen bir biçimde çıktı olabilir. Bu, kanal geliştiricisi olarak yapmanız gereken bir şey değildir. Bunun yerine, uygulamanın yapılandırma dosyasında bu izleme dinleyicisini yapılandırması gereken uygulama kullanıcısı (veya uygulamanın sorun giderme ile ilgili kişi). Örneğin, aşağıdaki yapılandırma hem <xref:System.ServiceModel?displayProperty=nameWithType> hem de `TraceEventsFile.e2e`adlı dosyaya `Microsoft.Samples.Udp` izleme bilgilerini çıktı:  
  
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
  
#### <a name="tracing-structured-data"></a>Yapılandırılmış verileri izleme  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, izleme girişine dahil edilecek bir veya daha fazla nesne alan <xref:System.Diagnostics.TraceSource.TraceData%2A> yöntemine sahiptir. Genel olarak, <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi her bir nesnede çağrılır ve elde edilen dize, izleme girişinin bir parçası olarak yazılır. İzleme çıktısını almak için <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> kullanırken, bir <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> veri nesnesi olarak <xref:System.Diagnostics.TraceSource.TraceData%2A>geçirebilirsiniz. Elde edilen izleme girişi, <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>tarafından sağlanan XML 'yi içerir. XML uygulama verileri içeren örnek bir giriş aşağıda verilmiştir:  
  
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
  
 WCF izleme Görüntüleyicisi, daha önce gösterilen `TraceRecord` öğesinin şemasını anlamıştır ve verileri alt öğelerinden ayıklar ve tablosal biçiminde görüntüler. Kanalınızın, SvcTraceViewer. exe kullanıcılarına verileri okumasına yardımcı olmak için yapılandırılmış uygulama verilerini izlerken bu şemayı kullanması gerekir.
