---
title: Mesajlaşma Etkinlikleri
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 839e9225db7b5d76cf05f148811634389e81502a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617635"
---
# <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri
Mesajlaşma etkinlikleri, WCF iletileri almak ve göndermek için iş akışları sağlar. Mesajlaşma etkinlikleri iş akışı ekleyerek herhangi bir rasgele karmaşık ileti exchange Düzen (MEP) modelleyebilirsiniz.

## <a name="message-exchange-patterns"></a>İleti Exchange desenleri
 Üç temel ileti exchange desenleri vardır:

-   **Veri birimi** : veri birimi MEP kullanırken istemci hizmete bir ileti gönderir, ancak hizmeti yanıt vermiyor. Bu bazen "Başlat ve unut" olarak adlandırılır. Bir Başlat ve unut değişimi, başarılı bir teslimat bant dışı onay gerektiren bir. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmet ulaşın. İstemci başarıyla bir ileti gönderir, bu hizmet iletisi aldı garanti etmez. Veri birimi Mesajlaşma için temel yapı taşı aynıdır, bunun üstünde kendi MEPs oluşturabilirsiniz.

-   **İstek-yanıt** - istek-yanıt MEP istemci kullanarak service hizmeti için bir ileti gerekli işlemeyi gerçekleştirir ve ardından gönderen bir yanıt istemciye geri gönderir. Desen, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekleri: uzaktan yordam çağrısı (RPC) ve tarayıcı GET istekleri. Bu düzen, yarı çift yönlü da bilinir.

-   **Çift yönlü** - çift yönlü MEP istemciyi ve hizmeti kullanarak iletileri diğer için herhangi bir sırada gönderebilir. Çift yönlü MEP bir telefon konuşması gibi burada konuşulan her bir sözcüğün bir ileti numarasıdır.

 Mesajlaşma etkinlikleri, bu temel MEPs hiçbirini yanı sıra herhangi bir rasgele karmaşık MEP uygulamak olanak tanır.

## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Aşağıdaki ileti etkinlikleri tanımlar:

-   <xref:System.ServiceModel.Activities.Send>-Kullanma <xref:System.ServiceModel.Activities.Send> ileti göndermek için etkinlik.

-   <xref:System.ServiceModel.Activities.SendReply> -Kullanma <xref:System.ServiceModel.Activities.SendReply> bir yanıta bir alınan ileti göndermek için etkinlik. Bu etkinlik bir istek/yanıt MEP uygulama iş akışı hizmetler tarafından kullanılır.

-   <xref:System.ServiceModel.Activities.Receive>-Kullanma <xref:System.ServiceModel.Activities.Receive> bir ileti almak için etkinlik.

-   <xref:System.ServiceModel.Activities.ReceiveReply> -Kullanma <xref:System.ServiceModel.Activities.ReceiveReply> bir yanıt iletisi almak için etkinlik. Bu etkinlik bir istek/yanıt MEP uygulama iş akışı hizmeti istemciler tarafından kullanılır.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Mesajlaşma etkinlikleri ve ileti Exchange desenleri
 Bir veri birimi MEP bir ileti ve iletiyi almak için bir hizmet gönderme bir istemcinin içerir. İstemci bir iş akışı kullanımı ise bir <xref:System.ServiceModel.Activities.Send> ileti göndermek için etkinlik. Bir iş akışında ileti almak için kullandığınız bir <xref:System.ServiceModel.Activities.Receive> etkinlik. <xref:System.ServiceModel.Activities.Send> Ve <xref:System.ServiceModel.Activities.Receive> etkinlikleri her adında bir özelliğe sahip `Content`. Bu özellik, gönderilen veya alınan verileri içerir. İstek-yanıt MEP uygularken hem istemci hem de hizmet etkinlikleri çiftlerini kullanın. İstemcinin kullandığı bir <xref:System.ServiceModel.Activities.Send> ileti göndermek için etkinlik ve <xref:System.ServiceModel.Activities.ReceiveReply> hizmetten yanıt almak için etkinlik. Bu iki etkinliği ile ilişkili olduğunu <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliği. Bu özellik kümesine <xref:System.ServiceModel.Activities.Send> özgün ileti gönderen bir etkinlik. Hizmet bir çift ilgili etkinlikleri de kullanır: <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>. Bu iki etkinliği tarafından ilişkili <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği. Bu özellik kümesine <xref:System.ServiceModel.Activities.Receive> özgün iletisi aldı etkinlik. <xref:System.ServiceModel.Activities.ReceiveReply> Ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler, ister <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> göndermenize izin bir <xref:System.ServiceModel.Channels.Message> örneği veya sözleşme türü bir ileti.

 Uzun süre çalışan iş akışlarının yapısı nedeniyle, çift yönlü ayrıca uzun süre çalışan konuşmaları desteklemek için iletişim deseni için önemlidir. Uzun süre çalışan konuşmaları desteklemek için konuşma başlatmak istemcilere hizmet veriler kullanılabilir olduğunda, daha sonraki bir zamanda geri arama olanağı sağlamalısınız. Örneğin, bir satın alma siparişi isteği için yönetici onayı gönderilir, ancak bu günde bir, bir hafta veya hatta bir yıl için işlenmeyebilir değil; Satınalma Siparişi Onayı yöneten bir iş akışı, onay verildiğinde sonra devam etmek için bilmeniz gerekir. Bu düzen çift yönlü iletişim, bağıntı kullanarak iş akışlarında desteklenir. Çift yönlü bir desen uygulamak için kullanma <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinlikler. Üzerinde <xref:System.ServiceModel.Activities.Receive> etkinlik, bir özel anahtar değerini kullanarak bağıntı başlatma <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Üzerinde <xref:System.ServiceModel.Activities.Send> bu bağıntı işleyici olarak bir etkinlik kümesini <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> özellik değeri. Daha fazla bilgi için [dayanıklı çift yönlü](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).

> [!NOTE]
>  Çift yönlü bir geri çağırma bağıntı ("dayanıklı çift yönlü") kullanarak iş akışının uygulaması, uzun süre çalışan konuşmaları yöneliktir. Bu geri çağırma sözleşmeleri ile çift yönlü WCF ile aynı olduğu konuşma kısa-(kanal ömrünü) olan çalışmıyor.

## <a name="message-formatting-and-messaging-activities"></a>İleti biçimlendirme ve mesajlaşma etkinlikleri
 <xref:System.ServiceModel.Activities.Receive> Ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri adında bir özelliğe sahip `Content`. Bu özellik türünde <xref:System.ServiceModel.Activities.ReceiveContent> ve verileri temsil eden <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği alır. .NET Framework adlı iki ilişkili sınıfları tanımlar <xref:System.ServiceModel.Activities.ReceiveMessageContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> ikisi için de türetilmiş <xref:System.ServiceModel.Activities.ReceiveContent>. Ayarlama <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğin `Content` özelliğini bir iş akışı hizmeti içinde veri almak için bu tür bir örneği. Kullanılacak türünü etkinlik aldığı veri türüne bağlıdır. Etkinlik alırsa bir `Message` nesne veya sözleşme türü, kullanan bir ileti <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Etkinlik bir veri anlaşması veya seri hale getirilebilir XML türleri kümesi alırsa, kullanın <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> birden çok parametre göndermenize olanak sağlarken <xref:System.ServiceModel.Activities.ReceiveMessageContent> yalnızca bir nesne Gönder, ileti (veya ileti anlaşması türü) sağlar.

> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> Ayrıca bir tek veri anlaşması veya seri hale getirilebilir bir XML türü ile kullanılabilir. ' In kullanımı arasındaki fark <xref:System.ServiceModel.Activities.ReceiveParametersContent> tek bir parametre ve doğrudan geçirilen nesne <xref:System.ServiceModel.Activities.ReceiveMessageContent> kablo biçimi. Parametrenin içerik işlem adına karşılık gelen bir XML öğesi içine sarmalanır ve parametre adını kullanarak bir XML öğesi serileştirilmiş nesne sarmalandıktan (örneğin, `<Echo><msg>Hello, World</msg></Echo>`). İleti içeriğini işlem adına göre sarmalanmamış. Bunun yerine, serileştirilmiş nesne XML nitelikli tür adı'nı kullanarak bir XML öğesi içinde yer alır (örneğin, `<string>Hello, World</string>`).

 <xref:System.ServiceModel.Activities.Send> Ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri adlı bir özellik de `Content`. Bu özellik türünde <xref:System.ServiceModel.Activities.SendContent> ve verileri temsil eden <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinlik gönderir. .NET Framework adlı iki ilgili türleri tanımlar <xref:System.ServiceModel.Activities.SendMessageContent> ve <xref:System.ServiceModel.Activities.SendParametersContent> ikisi için de türetilmiş <xref:System.ServiceModel.Activities.SendContent>. Ayarlama <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğin `Content` özelliğini bir iş akışı hizmetinden veri göndermek için bu tür bir örneği. Kullanılacak türünü etkinlik gönderdiği veri türüne bağlıdır. Etkinlik gönderirse bir `Message` nesne veya sözleşme türü, kullanan bir ileti <xref:System.ServiceModel.Activities.SendMessageContent>. Etkinlik bir veri anlaşması türü kullanımı gönderirse <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> birden çok parametre göndermenize olanak sağlarken <xref:System.ServiceModel.Activities.SendMessageContent> yalnızca bir nesne, ileti (veya ileti anlaşması türü) göndermenize olanak sağlar.

 Mesajlaşma etkinlikleri ile kesin programlama genel kullanarak <xref:System.Activities.InArgument%601> ve <xref:System.Activities.OutArgument%601> ileti veya parametre özelliklerine atadığınız nesneleri sarmalamak için <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.ReceiveReply>etkinlikler. Kullanım <xref:System.Activities.InArgument%601> için <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri ve <xref:System.Activities.OutArgument%601> için <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler. `In` Veri etkinliklerine geçtiğinden bağımsız değişkenleri ile gönderme etkinlikler için kullanılır. `Out` Veri dışı etkinlikleri, aşağıdaki örnekte gösterildiği gibi geçirilmiş çünkü bağımsız değişkenleri ile alma etkinlikler için kullanılır.

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

 İstek/yanıt işlemi tanımlayan bir iş akışı hizmeti uygularken, void döndüren, örneği oluşturmanız gerekir bir <xref:System.ServiceModel.Activities.SendReply> etkinliği ve kümesi <xref:System.ServiceModel.Activities.SendReply.Content%2A> içerik türlerden birinde boş bir örnek özelliğini (<xref:System.ServiceModel.Activities.SendMessageContent> veya <xref:System.ServiceModel.Activities.SendParametersContent>) aşağıdaki örnekte gösterildiği gibi.

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
 Bir iş akışı uygulamasından bir iş akışı hizmeti çağrılırken, Visual Studio 2012 normal kapsülleyen Mesajlaşma özel etkinlikler oluşturur <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri bir istek/yanıt MEP kullanılır. Bu özelliği kullanmak için Visual Studio'da istemci projesini sağ tıklatın ve seçin **Ekle** > **hizmet başvurusu**. Hizmetin taban adresi adres kutusuna yazın ve Git'e tıklayın. Kullanılabilir hizmetlerin görüntülenen **Hizmetleri:** kutusu. Desteklenen sözleşmeleri görüntülemek için hizmet düğümünü genişletin. Kullanılabilir işlemler listesi görüntülenir ve çağırmak istediğiniz sözleşmesini seçin **işlemleri** kutusu. Oluşturulan etkinliği için bir ad alanını belirtin ve tıklayın **Tamam**. Ardından ve sonra projeyi yeniden oluşturduysanız, oluşturulan özel etkinlikler araç kutusundan işleminin başarıyla tamamlandığını bildiren bir iletişim kutusu görürsünüz. Hizmet sözleşmesini tanımlanan her işlem için bir etkinlik yok. Projeyi yeniden oluşturulduktan sonra sürükleyin ve özel etkinlikleri, iş akışınızı bırakabilir ve Özellikler penceresinde tüm gerekli özellikleri ayarlayın.

<!--## Messaging Activity Templates
 To make setting up a request/response MEP on the client and service easier, Visual Studio 2012 provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.
-->
## <a name="messaging-activities-and-transactions"></a>Mesajlaşma etkinlikleri ve işlemler
 Bir iş akışı hizmetine çağrı yapıldığında, bir işlem hizmet işlemi için akış isteyebilirsiniz. Burası yapmak için <xref:System.ServiceModel.Activities.Receive> etkinlik içinde bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinliği içeren bir `Receive` etkinliği ve bir gövdesi. Hizmet kalır gövdesinin yürütülmesini ortam için işlem akışı yapılan işlemler <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Gövdenin yürütülmesi tamamlandığında işlem tamamlandı. İş akışları ve işlemler hakkında daha fazla bilgi için bkz. [iş akışı işlemleri](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İş akışı hizmetleri hataları alıp göndermek nasıl](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
