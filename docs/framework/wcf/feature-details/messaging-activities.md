---
title: Mesajlaşma etkinlikleri
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 1e65a3ead9df4103fb270911e3bbb2cc03fcfcba
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347572"
---
# <a name="messaging-activities"></a>Mesajlaşma etkinlikleri

Mesajlaşma etkinlikleri, iş akışlarının WCF iletileri gönderip almasına izin verir. Bir iş akışına mesajlaşma etkinlikleri ekleyerek, rastgele karmaşık ileti değişimi düzenlerini (MEP) modelleyebilirsiniz.

## <a name="message-exchange-patterns"></a>İleti değişimi desenleri

Üç temel ileti değişim deseni vardır:

- **Veri birimi** -istemci, MEP 'yi kullanırken hizmete bir ileti gönderir, ancak hizmet yanıt vermez. Bu bazen "yangın ve unut" olarak adlandırılır. Bir ateş ve unutur, başarılı teslimin bant dışı onayını gerektiren bir adım. İleti iletimde kaybolmuş olabilir ve hizmete hiçbir şekilde ulaşamamalıdır. İstemci başarıyla bir ileti gönderirse hizmetin iletiyi aldığını garanti etmez. Veri birimi, en üstünde kendi büyük PS 'nizi oluşturabileceğiniz gibi, mesajlaşma için temel bir yapı taşıdır.

- **İstek-yanıt** -istek-yanıt MEP 'si kullanılırken, istemci hizmete bir ileti gönderdiğinde, hizmet gerekli işlemeyi yapar ve istemciye bir yanıt gönderir. Bu model, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrılarına örnek olarak uzak yordam çağrıları (RPC) ve tarayıcı GET istekleri verilebilir. Bu model, yarı çift yönlü olarak da bilinir.

- **Çift yönlü** -çift yönlü MEP 'yi kullanırken, istemci ve hizmet herhangi bir sırada birbirlerine ileti gönderebilir. Çift yönlü MEP, konuşulan her sözcüğün bir ileti olduğu bir telefon konuşması gibidir.

Mesajlaşma etkinlikleri, bu temel MEPs 'nin yanı sıra rastgele karmaşık MEP 'lerin herhangi birini uygulamanıza olanak tanır.

## <a name="messaging-activities"></a>Mesajlaşma etkinlikleri

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] aşağıdaki mesajlaşma etkinliklerini tanımlar:

- <xref:System.ServiceModel.Activities.Send>-bir ileti göndermek için <xref:System.ServiceModel.Activities.Send> etkinliğini kullanın.

- <xref:System.ServiceModel.Activities.SendReply>-alınan bir iletiye yanıt göndermek için <xref:System.ServiceModel.Activities.SendReply> etkinliğini kullanın. Bu etkinlik, bir istek/yanıt MEP 'si uygularken iş akışı hizmetleri tarafından kullanılır.

- <xref:System.ServiceModel.Activities.Receive>-bir ileti almak için <xref:System.ServiceModel.Activities.Receive> etkinliğini kullanın.

- <xref:System.ServiceModel.Activities.ReceiveReply>-yanıt iletisi almak için <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini kullanın. Bu etkinlik, bir istek/yanıt MEP 'si uygularken iş akışı hizmeti istemcileri tarafından kullanılır.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Mesajlaşma etkinlikleri ve ileti değişimi desenleri

Veri birimi MEP, ileti gönderen bir istemciyi ve iletiyi alan bir hizmeti içerir. İstemci bir iş akışıdır iletiyi göndermek için <xref:System.ServiceModel.Activities.Send> etkinliğini kullanın. Bu iletiyi bir iş akışında almak için <xref:System.ServiceModel.Activities.Receive> etkinliğini kullanın. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinliklerinin her biri `Content`adında bir özelliğe sahiptir. Bu özellik gönderilmekte veya alınmakta olan verileri içerir. İstek sırasında-Response MEP her ikisi de istemci ve hizmet etkinlik çiftlerini kullanır. İstemci iletiyi göndermek için bir <xref:System.ServiceModel.Activities.Send> etkinliği ve hizmetten gelen yanıtı almak için bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği kullanır. Bu iki etkinlik, <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliğine göre birbirleriyle ilişkilendirilir. Bu özellik özgün iletiyi gönderen <xref:System.ServiceModel.Activities.Send> etkinliğe ayarlanır. Hizmet ayrıca bir çift ilişkili etkinlik kullanır: <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>. Bu iki etkinlik <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği tarafından ilişkilendirilir. Bu özellik özgün iletiyi alan <xref:System.ServiceModel.Activities.Receive> etkinliğe ayarlanır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> gibi <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri bir <xref:System.ServiceModel.Channels.Message> örneği veya bir ileti sözleşmesi türü göndermenizi sağlar.

İş akışlarının uzun süre çalışan doğası nedeniyle, iletişim çift yönlü iletişim modelinin uzun süreli konuşmaları desteklemesi önemlidir. Uzun süreli konuşmaları desteklemek için konuşmayı Başlatan istemciler, verileri daha sonra kullanılabilir hale geldiğinde daha sonra geri çağırma olanağı sağlamalıdır. Örneğin, bir satın alma siparişi isteği, yönetici onayı için gönderilir, ancak bir gün, bir hafta ya da bir yıl boyunca işlenmeyebilir; onay verdikten sonra, satın alma siparişi onayını yöneten iş akışının sürdürülmesi gerekir. Bu çift yönlü iletişim stili bağıntı kullanan iş akışlarında desteklenir. Çift yönlü bir model uygulamak için <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinliklerini kullanın. <xref:System.ServiceModel.Activities.Receive> etkinliğinde, <xref:System.ServiceModel.Activities.CorrelationHandle>kullanarak bir bağıntı başlatın. <xref:System.ServiceModel.Activities.Send> etkinliği, bağıntı işleyicisini <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> Özellik değeri olarak ayarlayın. Daha fazla bilgi için bkz. [dayanıklı çift yönlü](durable-duplex-correlation.md).

> [!NOTE]
> İş akışının, bir geri çağırma bağıntısı ("dayanıklı çift yönlü") kullanılarak çift yönlü uygulanması, uzun süredir çalışan konuşmalar için tasarlanmıştır. Bu, görüşmenin kısa süreli olarak çalıştığı (kanalın ömrü) geri çağırma sözleşmeleri ile WCF çift yönlü olarak aynı değildir.

## <a name="message-formatting-and-messaging-activities"></a>İleti biçimlendirme ve mesajlaşma etkinlikleri

<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerinin `Content`adında bir özelliği vardır. Bu özellik <xref:System.ServiceModel.Activities.ReceiveContent> türündedir ve <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğinin aldığı verileri temsil eder. .NET Framework, <xref:System.ServiceModel.Activities.ReceiveMessageContent> adlı iki ilişkili sınıfı tanımlar ve bunların her ikisi de <xref:System.ServiceModel.Activities.ReceiveContent>türetilir <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Bir iş akışı hizmetine veri almak için <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğinin `Content` özelliğini bu türlerden birinin bir örneğine ayarlayın. Kullanılacak tür, etkinliğin aldığı veri türüne bağlıdır. Etkinlik bir `Message` nesnesi veya bir ileti sözleşmesi türü alırsa, <xref:System.ServiceModel.Activities.ReceiveMessageContent>kullanın. Etkinlik seri hale getirilebilen bir veri anlaşması veya XML türleri kümesi alırsa <xref:System.ServiceModel.Activities.ReceiveParametersContent>kullanın. <xref:System.ServiceModel.Activities.ReceiveParametersContent> birden çok parametre göndermenizi sağlar, ancak <xref:System.ServiceModel.Activities.ReceiveMessageContent> yalnızca bir nesne, ileti (veya ileti sözleşmesi türü) göndermenize izin verir.

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent>, seri hale getirilebilen tek bir veri sözleşmesi veya XML türü ile de kullanılabilir. Tek bir parametre ile <xref:System.ServiceModel.Activities.ReceiveParametersContent> kullanma arasındaki fark ve doğrudan <xref:System.ServiceModel.Activities.ReceiveMessageContent> geçirilecek nesne, Tel biçimidir. Parametrenin içeriği, işlem adına karşılık gelen bir XML öğesinde sarmalanmış ve serileştirilmiş nesne, parametre adı kullanılarak bir XML öğesinde sarmalandı (örneğin, `<Echo><msg>Hello, World</msg></Echo>`). İleti içeriği, işlem adı tarafından sarmalanmamış. Bunun yerine, serileştirilmiş nesne XML-nitelenmiş tür adı kullanılarak bir XML öğesi içine yerleştirilir (örneğin, `<string>Hello, World</string>`).

<xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerinin `Content`adında bir özelliği de vardır. Bu özellik <xref:System.ServiceModel.Activities.SendContent> türündedir ve <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğinin gönderdiği verileri temsil eder. .NET Framework, <xref:System.ServiceModel.Activities.SendMessageContent> adlı iki ilişkili türü tanımlar ve bunların her ikisi de <xref:System.ServiceModel.Activities.SendContent>türetilir <xref:System.ServiceModel.Activities.SendParametersContent>. Bir iş akışı hizmetinden veri göndermek için <xref:System.ServiceModel.Activities.Send> veya <xref:System.ServiceModel.Activities.SendReply> etkinliğinin `Content` özelliğini bu türlerden birinin bir örneğine ayarlayın. Kullanılacak tür, etkinliğin gönderdiği veri türüne bağlıdır. Etkinlik bir `Message` nesnesi veya bir ileti sözleşmesi türü gönderiyorsa <xref:System.ServiceModel.Activities.SendMessageContent>kullanın. Etkinlik bir veri anlaşması türü gönderirse <xref:System.ServiceModel.Activities.SendParametersContent>kullanın. <xref:System.ServiceModel.Activities.SendParametersContent> birden çok parametre göndermenizi sağlar, ancak <xref:System.ServiceModel.Activities.SendMessageContent> yalnızca bir nesne, ileti (veya ileti sözleşmesi türü) göndermenize izin verir.

İmperatively 'i mesajlaşma etkinlikleriyle programlarken, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerinin ileti veya parametreler özelliklerine atadığınız nesneleri kaydırmak için genel <xref:System.Activities.InArgument%601> ve <xref:System.Activities.OutArgument%601> kullanırsınız. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri için <xref:System.Activities.InArgument%601>, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri için <xref:System.Activities.OutArgument%601> kullanın. `In` bağımsız değişkenler, veriler etkinliklere geçirildiğinden gönderme etkinlikleriyle birlikte kullanılır. `Out` bağımsız değişkenler, aşağıdaki örnekte gösterildiği gibi, veriler etkinliklerden geçirilmediğinden alma etkinlikleriyle birlikte kullanılır.

```csharp
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

Void döndüren bir istek/yanıt işlemini tanımlayan bir iş akışı hizmeti uygularken, aşağıdaki örnekte gösterildiği gibi bir <xref:System.ServiceModel.Activities.SendReply> etkinlik örneği oluşturmanız ve <xref:System.ServiceModel.Activities.SendReply.Content%2A> özelliğini içerik türlerinden birinin boş bir örneğine ayarlamanız gerekir (<xref:System.ServiceModel.Activities.SendMessageContent> veya <xref:System.ServiceModel.Activities.SendParametersContent>).

```csharp
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

## <a name="add-service-reference"></a>Hizmet başvurusu Ekle

Bir iş akışı hizmetini bir iş akışı uygulamasından çağırırken, Visual Studio 2012, bir istek/yanıt durumunda kullanılan olağan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinliklerini kapsülleyen özel mesajlaşma etkinlikleri oluşturur. Bu özelliği kullanmak için, Visual Studio 'da istemci projesine sağ tıklayın ve > **hizmet başvurusu** **Ekle** ' yi seçin. Adres kutusuna hizmetin temel adresini yazın ve git ' e tıklayın. Kullanılabilir Hizmetler **Hizmetler:** kutusunda görüntülenir. Desteklenen sözleşmeleri göstermek için hizmet düğümünü genişletin. Çağırmak istediğiniz sözleşmeyi seçin ve kullanılabilir işlemler listesi **işlemler** kutusunda görüntülenir. Ardından, oluşturulan etkinliğin ad alanını belirtebilir ve **Tamam**' a tıklayabilirsiniz. Ardından, işlemin başarıyla tamamlandığını belirten bir iletişim kutusu ve projeyi yeniden oluşturduktan sonra oluşturulan özel etkinliklerin araç kutusunda olduğunu belirten bir iletişim kutusu görürsünüz. Hizmet sözleşmesinde tanımlanan her işlem için bir etkinlik vardır. Projeyi yeniden oluşturduktan sonra özel etkinlikleri iş akışınıza sürükleyip bırakabilir ve Özellikler penceresinde gerekli özellikleri ayarlayabilirsiniz.

## <a name="messaging-activity-templates"></a>Mesajlaşma etkinlik şablonları

İstemci ve hizmet üzerinde bir istek/yanıt ayarlamayı daha kolay hale getirmek için, Visual Studio 2012 iki mesajlaşma etkinlik şablonu sağlar. `System.ServiceModel.Activities.Design.ReceiveAndSendReply`, hizmette kullanılır ve `System.ServiceModel.Activities.Design.SendAndReceiveReply` istemcisinde kullanılır. Her iki durumda da şablonlar, uygun mesajlaşma etkinliklerini iş akışınıza ekler. Hizmette, `System.ServiceModel.Activities.Design.ReceiveAndSendReply` bir <xref:System.ServiceModel.Activities.Receive> etkinliği ve ardından bir <xref:System.ServiceModel.Activities.SendReply> etkinliği ekler. <xref:System.ServiceModel.Activities.SendReply.Request> özelliği otomatik olarak <xref:System.ServiceModel.Activities.Receive> etkinliğine ayarlanır. İstemcisinde `System.ServiceModel.Activities.Design.SendAndReceiveReply`, ardından bir <xref:System.ServiceModel.Activities.ReceiveReply><xref:System.ServiceModel.Activities.Send> etkinlik ekler. <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliği otomatik olarak <xref:System.ServiceModel.Activities.Send> etkinliğine ayarlanır. Bu şablonları kullanmak için, uygun şablonu yalnızca iş akışınıza sürükleyip bırakın.

## <a name="messaging-activities-and-transactions"></a>Mesajlaşma etkinlikleri ve işlemler

Bir iş akışı hizmetine bir çağrı yapıldığında, hizmet işlemine bir işlem akışını isteyebilirsiniz. Bunu yapmak için <xref:System.ServiceModel.Activities.Receive> etkinliğini bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği içine yerleştirin. <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği bir `Receive` etkinliği ve bir gövdesi içerir. Hizmete aktarılan işlem, <xref:System.ServiceModel.Activities.TransactedReceiveScope>gövdesinin yürütülmesi boyunca çevresel olarak kalır. Gövde yürütmeyi bitirdiğinde işlem tamamlanır. İş akışları ve işlemler hakkında daha fazla bilgi için bkz. [Iş akışı işlemleri](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Iş akışı hizmetlerinde hata gönderme ve alma](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](creating-a-long-running-workflow-service.md)
