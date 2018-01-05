---
title: "Mesajlaşma Etkinlikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ba5d49f357fe1cf56a45f733e91c1dbc2208736
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri
Mesajlaşma etkinlikleri WCF ileti gönderme ve alma için iş akışlarını izin verir. Bir iş akışına Mesajlaşma etkinlikleri ekleyerek tüm rasgele karmaşık ileti exchange desenleri (MEP) model oluşturabilirsiniz.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 Üç temel ileti exchange desenleri vardır:  
  
-   **Veri birimi** - MEP datagram kullanırken istemci hizmete ileti gönderir, ancak hizmeti yanıt vermiyor. Buna bazen "yangın ve unut" adı verilir. A yangın ve exchange başarılı teslimat bant dışı onay gerektiren bir tane olduğunu unutmayın. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmete erişmek. İstemci başarıyla bir ileti gönderir, bu hizmet ileti aldı garanti etmez. Veri birimi Mesajlaşma için temel yapı bloğu aynıdır, üzerinde kendi MEPs oluşturabilirsiniz.  
  
-   **İstek-yanıt** - istek-yanıt MEP istemci kullanarak hizmet, hizmet için bir ileti gereken işlem yapar ve sonra gönderir bir yanıt istemciye geri gönderir. Desen istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekler uzaktan yordam çağrısı (RPC) ve tarayıcı GET istekleri. Bu desen yarı çift yönlü da bilinir.  
  
-   **Çift yönlü** - çift yönlü MEP istemci ve hizmet kullanarak iletileri göndermek için herhangi bir sırada gönderebilirsiniz. Çift yönlü MEP bir telefon konuşması gibi konuşulan her sözcüğün bir ileti olduğu.  
  
 Mesajlaşma etkinlikleri, bu temel MEPs hiçbirini yanı sıra rasgele karmaşık herhangi MEP uygulamanızı sağlar.  
  
## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Aşağıdaki Mesajlaşma etkinlikleri tanımlar:  
  
-   <xref:System.ServiceModel.Activities.Send>-Kullanın <xref:System.ServiceModel.Activities.Send> bir ileti göndermek için etkinlik.  
  
-   <xref:System.ServiceModel.Activities.SendReply>-Kullanın <xref:System.ServiceModel.Activities.SendReply> yanıt alınan ileti gönder etkinliği. Bu etkinlik bir istek/yanıt MEP uygulama iş akışı hizmetleri tarafından kullanılır.  
  
-   <xref:System.ServiceModel.Activities.Receive>-Kullanın <xref:System.ServiceModel.Activities.Receive> etkinliği bir ileti alırsınız.  
  
-   <xref:System.ServiceModel.Activities.ReceiveReply>-Kullanın <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği bir yanıt iletisi alırsınız. Bu etkinlik bir istek/yanıt MEP uygularken iş akışı hizmeti istemciler tarafından kullanılır.  
  
## <a name="messaging-activities-and-message-exchange-patterns"></a>Mesajlaşma etkinlikleri ve ileti Exchange desenleri  
 Veri birimi MEP bir ileti ve iletiyi alan bir hizmet gönderme bir istemcinin içerir. İstemci bir iş akışı kullanımı ise bir <xref:System.ServiceModel.Activities.Send> ileti göndermek için etkinlik. Bu ileti bir iş akışında almak için kullandığınız bir <xref:System.ServiceModel.Activities.Receive> etkinlik. <xref:System.ServiceModel.Activities.Send> Ve <xref:System.ServiceModel.Activities.Receive> etkinlikleri her adlı bir özellik olması `Content`. Bu özellik gönderilen veya alınan verileri içerir. İstek-yanıt MEP uygularken hem istemci hem de hizmet etkinliklerin çiftlerini kullanır. İstemcinin kullandığı bir <xref:System.ServiceModel.Activities.Send> ileti göndermek için etkinliği ve bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik Hizmeti'nden yanıtı alırsınız. Bu iki etkinlikleri birbirine göre ilişkili <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliği. Bu özelliği ayarlamak <xref:System.ServiceModel.Activities.Send> özgün ileti gönderilen etkinlik. Hizmet Ayrıca ilişkili etkinlikleri çifti kullanır: <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>. Bu iki etkinlik tarafından ilişkili <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği. Bu özelliği ayarlamak <xref:System.ServiceModel.Activities.Receive> özgün iletisi aldı etkinlik. <xref:System.ServiceModel.Activities.ReceiveReply> Ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, ister <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> göndermenize izin bir <xref:System.ServiceModel.Channels.Message> örneği veya sözleşme türü bir ileti.  
  
 İş akışı uzun süre çalışan yapısı nedeniyle, uzun süre çalışan görüşmeleri de desteklemek için iletişim çift yönlü düzeni için önemlidir. Uzun süre çalışan görüşmeleri desteklemek için konuşma başlatmak istemciler hizmet veriler kullanılabilir duruma geldiğinde, daha sonraki bir zamanda geri arama fırsatına sahip sağlamanız gerekir. Örneğin, bir satın alma siparişi isteği için yönetici onayı gönderildi ancak, bir gün, haftada bir ya da bile bir yıl için işlenmedi; satın alma siparişi onayı yönetir iş akışı onayı verilen sonra devam etmek için bilmeniz gerekir. Bu deseni çift yönlü iletişim bağıntı kullanarak iş akışlarında desteklenir. Çift yönlü bir desen uygulamak için kullandığınız <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinlikler. Üzerinde <xref:System.ServiceModel.Activities.Receive> etkinlik, bir özel anahtar değeri kullanılarak bağıntı Initialize <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Üzerinde <xref:System.ServiceModel.Activities.Send> etkinliği o bağıntı tanıtıcının olarak ayarlandı <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> özellik değeri. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Dayanıklı çift yönlü](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).  
  
> [!NOTE]
>  Çift yönlü bir geri çağırma bağıntı ("dayanıklı çift yönlü") kullanarak iş akışının uyarlamasını uzun süre çalışan görüşmeleri için tasarlanmıştır. Bu geri çağırma Sözleşmelerle çift yönlü WCF ile aynı olduğu konuşma kısa (kanal ömrü) çalışan olduğu değildir.  
  
## <a name="message-formatting-and-messaging-activities"></a>İleti biçimlendirme ve mesajlaşma etkinlikleri  
 <xref:System.ServiceModel.Activities.Receive> Ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri adlı bir özellik olması `Content`. Bu özellik türünde <xref:System.ServiceModel.Activities.ReceiveContent> ve verileri temsil <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik alır. .NET Framework adlı iki ilişkili sınıfları tanımlar <xref:System.ServiceModel.Activities.ReceiveMessageContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> her ikisi de türetilmiş <xref:System.ServiceModel.Activities.ReceiveContent>. Ayarlama <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğin `Content` özelliği bir iş akışı hizmetinde veri almak için şu türlerden birine örneği. Kullanılacak türü etkinlik aldığı veri türüne bağlıdır. Etkinlik alırsa bir `Message` nesne veya sözleşme türü, kullanan bir ileti <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Etkinlik veri sözleşmesi ya da serileştirilebilir XML türleri alırsa, kullanmak <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent>birden çok parametre göndermenize olanak sağlarken <xref:System.ServiceModel.Activities.ReceiveMessageContent> yalnızca gönderme bir nesne, ileti (veya ileti sözleşme türü) sağlar.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent>Ayrıca bir tek veri sözleşmesi veya seri hale getirilebilir XML türü ile kullanılabilir. Kullanarak arasındaki farkı <xref:System.ServiceModel.Activities.ReceiveParametersContent> tek bir parametre ve doğrudan geçirilen nesnesi ile <xref:System.ServiceModel.Activities.ReceiveMessageContent> kablo biçimi. Parametrenin içeriği işlemi adına karşılık gelen bir XML öğesi paketlenir ve serileştirilmiş nesne bir XML öğesi parametre adı ile sarılır (örneğin, `<Echo><msg>Hello, World</msg></Echo>`). İleti içeriği, işlem adı tarafından sarmalanmamış. Bunun yerine, serileştirilmiş nesne XML nitelenmiş tür adını kullanarak bir XML öğesi içinde yerleştirilir (örneğin, `<string>Hello, World</string>`).  
  
 <xref:System.ServiceModel.Activities.Send> Ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri adlı bir özellik de `Content`. Bu özellik türünde <xref:System.ServiceModel.Activities.SendContent> ve verileri temsil <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinlik gönderir. .NET Framework adlı iki ilgili türlerini tanımlar <xref:System.ServiceModel.Activities.SendMessageContent> ve <xref:System.ServiceModel.Activities.SendParametersContent> her ikisi de türetilmiş <xref:System.ServiceModel.Activities.SendContent>. Ayarlama <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğin `Content` özelliği bir iş akışı hizmetinden veri göndermek için şu türlerden birine örneği. Kullanılacak türü etkinlik gönderdiği veri türüne bağlıdır. Etkinlik gönderirse bir `Message` nesne veya sözleşme türü, kullanan bir ileti <xref:System.ServiceModel.Activities.SendMessageContent>. Etkinlik bir veri sözleşmesi türü kullanım gönderirse <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent>birden çok parametre göndermenize olanak sağlarken <xref:System.ServiceModel.Activities.SendMessageContent> yalnızca bir nesne, ileti (veya ileti sözleşme türü) göndermenize izin verir.  
  
 Mesajlaşma etkinlikleriyle imperatively programlama, genel kullanın <xref:System.Activities.InArgument%601> ve <xref:System.Activities.OutArgument%601> ileti veya parametre özellikleri atadığınız nesneleri sarmalamak için <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.ReceiveReply>etkinlikler. Kullanım <xref:System.Activities.InArgument%601> için <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri ve <xref:System.Activities.OutArgument%601> için <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler. `In`Veri etkinliklerine geçtiğinden bağımsız değişkenleri gönderme etkinlikleri ile kullanılır. `Out`bağımsız değişkenler veri dışında etkinlikleri, aşağıdaki örnekte gösterildiği gibi geçirilmiş alma etkinlikleri ile kullanılır.  
  
```  
Receive reserveSeat = new Receive  
{   
    ...   
    Content = new ReceiveParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }  
        }  
    }  
};  
SendReply reserveSeat = new SendReply  
{   
    ...   
    Request = reserveSeat,  
    Content = new SendParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationId", new InArgument<string>(reservationId) }  
        }  
    },  
};  
```  
  
 Bir istek/yanıt işlemi tanımlayan bir iş akışı hizmeti uygularken void döndüren, örneği gerekir bir <xref:System.ServiceModel.Activities.SendReply> etkinliği ve kümesi <xref:System.ServiceModel.Activities.SendReply.Content%2A> içerik türlerden birinde boş bir örnek özelliğine (<xref:System.ServiceModel.Activities.SendMessageContent> veya <xref:System.ServiceModel.Activities.SendParametersContent>) aşağıdaki örnekte gösterildiği gibi.  
  
```  
Receive rcv = new Receive()  
{  
ServiceContractName = "IService",  
OperationName = "NullReturningContract",  
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )  
};  
SendReply sr = new SendReply()  
{  
Request = rcv  
   Content = new SendParametersContent();  
};  
```  
  
## <a name="add-service-reference"></a>Hizmet Başvurusu Ekle  
 Bir iş akışı hizmeti bir iş akışı uygulamasından çağrılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] normal kapsülleyen özel Mesajlaşma etkinlikleri oluşturur <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bir istek/yanıt MEP kullanılan etkinliklerin. Bu özelliği kullanmak için istemci projeye sağ tıklayın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] seçip **hizmet Başvurusu Ekle**. Hizmetin taban adresi adres kutusuna yazın ve Git'i tıklatın. Kullanılabilir hizmetler görüntülenir **Hizmetleri:** kutusu. Desteklenen sözleşmeleri görüntülemek için hizmet düğümünü genişletin. Çağrı istediğiniz sözleşmeyi seçin ve kullanılabilir işlemleri listesi görüntülenir **Operations** kutusu. Oluşturulan etkinlik için ad alanını belirtin ve tıklatın **Tamam**. Ardından işlemi başarıyla tamamlandı bildiren ve projeyi yeniden sonra oluşturulan özel etkinlikler Araç Kutusu'nda olan bir iletişim kutusu görürsünüz. Hizmet sözleşmesini tanımlanan her işlem için bir etkinlik yok. Projeyi yeniden derlemeyi sonra sürükleyin ve özel etkinlikler, iş akışınızı bırakabilir ve Özellikler penceresinde tüm gerekli özellikleri ayarlayın.  
  
<!--## Messaging Activity Templates  
 To make setting up a request/response MEP on the client and service easier, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.  
-->
## <a name="messaging-activities-and-transactions"></a>Mesajlaşma etkinlikleri ve işlemler  
 Bir iş akışı hizmetine çağrı yapıldığında hizmet işlemi için işlem akış isteyebilirsiniz. Burası yapmak için <xref:System.ServiceModel.Activities.Receive> içinde etkinlik bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik içeren bir `Receive` etkinliği ve gövde. Hizmet kalır gövdesini yürütme ortam için işlem akışı yapılan işlem <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Gövde yürütme tamamlandığında işlem tamamlandı. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İş akışları ve işlem görür [iş akışı işlemleri](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışı hizmetleri hataları alıp göndermek nasıl](http://go.microsoft.com/fwlink/?LinkId=189151)  
 [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
