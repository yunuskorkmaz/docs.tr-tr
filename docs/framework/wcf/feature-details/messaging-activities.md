---
title: Mesajlaşma etkinlikleri
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 69a0e9a415b10d9c58d04eac27e48b1ed6a78064
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576401"
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

, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Aşağıdaki mesajlaşma etkinliklerini tanımlar:

- <xref:System.ServiceModel.Activities.Send>- <xref:System.ServiceModel.Activities.Send> Bir ileti göndermek için etkinliğini kullanın.

- <xref:System.ServiceModel.Activities.SendReply>-Alınan bir <xref:System.ServiceModel.Activities.SendReply> iletiye yanıt göndermek için etkinliğini kullanın. Bu etkinlik, bir istek/yanıt MEP 'si uygularken iş akışı hizmetleri tarafından kullanılır.

- <xref:System.ServiceModel.Activities.Receive>- <xref:System.ServiceModel.Activities.Receive> Bir ileti almak için etkinliğini kullanın.

- <xref:System.ServiceModel.Activities.ReceiveReply>- <xref:System.ServiceModel.Activities.ReceiveReply> Bir yanıt iletisi almak için etkinliğini kullanın. Bu etkinlik, bir istek/yanıt MEP 'si uygularken iş akışı hizmeti istemcileri tarafından kullanılır.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Mesajlaşma etkinlikleri ve ileti değişimi desenleri

Veri birimi MEP, ileti gönderen bir istemciyi ve iletiyi alan bir hizmeti içerir. İstemci bir iş akışıdır <xref:System.ServiceModel.Activities.Send> iletiyi göndermek için bir etkinlik kullanın. Bu iletiyi bir iş akışında almak için bir etkinlik kullanın <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Send>Ve <xref:System.ServiceModel.Activities.Receive> etkinliklerinin her biri adlı bir özelliğe sahiptir `Content` . Bu özellik gönderilmekte veya alınmakta olan verileri içerir. İstek sırasında-Response MEP her ikisi de istemci ve hizmet etkinlik çiftlerini kullanır. İstemci, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> hizmetten yanıtı alacak şekilde iletiyi ve etkinliği göndermek için bir etkinlik kullanır. Bu iki etkinlik, özelliği tarafından birbirleriyle ilişkilidir <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> . Bu özellik <xref:System.ServiceModel.Activities.Send> özgün iletiyi gönderen etkinliğe ayarlanır. Hizmet ayrıca bir çift ilişkili etkinlik kullanır: <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> . Bu iki etkinlik, özelliği tarafından ilişkilendirilir <xref:System.ServiceModel.Activities.SendReply.Request%2A> . Bu özellik <xref:System.ServiceModel.Activities.Receive> özgün iletiyi almış olan etkinliğe ayarlanır. Ve <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> gibi etkinlikler, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Channels.Message> örnek veya ileti sözleşme türü göndermenizi sağlar.

İş akışlarının uzun süre çalışan doğası nedeniyle, iletişim çift yönlü iletişim modelinin uzun süreli konuşmaları desteklemesi önemlidir. Uzun süreli konuşmaları desteklemek için konuşmayı Başlatan istemciler, verileri daha sonra kullanılabilir hale geldiğinde daha sonra geri çağırma olanağı sağlamalıdır. Örneğin, bir satın alma siparişi isteği, yönetici onayı için gönderilir, ancak bir gün, bir hafta ya da bir yıl boyunca işlenmeyebilir; onay verdikten sonra, satın alma siparişi onayını yöneten iş akışının sürdürülmesi gerekir. Bu çift yönlü iletişim stili bağıntı kullanan iş akışlarında desteklenir. Çift yönlü bir model uygulamak için <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> etkinliklerini kullanın. <xref:System.ServiceModel.Activities.Receive>Etkinlikte, kullanarak bir bağıntı başlatın <xref:System.ServiceModel.Activities.CorrelationHandle> . <xref:System.ServiceModel.Activities.Send>Özellik değeri olarak bağıntı tanıtıcısı olan etkinlik kümesi <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> . Daha fazla bilgi için bkz. [dayanıklı çift yönlü](durable-duplex-correlation.md).

> [!NOTE]
> İş akışının, bir geri çağırma bağıntısı ("dayanıklı çift yönlü") kullanılarak çift yönlü uygulanması, uzun süredir çalışan konuşmalar için tasarlanmıştır. Bu, görüşmenin kısa süreli olarak çalıştığı (kanalın ömrü) geri çağırma sözleşmeleri ile WCF çift yönlü olarak aynı değildir.

## <a name="message-formatting-and-messaging-activities"></a>İleti biçimlendirme ve mesajlaşma etkinlikleri

<xref:System.ServiceModel.Activities.Receive>Ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri adlı bir özelliğe sahiptir `Content` . Bu özellik türündedir <xref:System.ServiceModel.Activities.ReceiveContent> ve <xref:System.ServiceModel.Activities.Receive> veya etkinliğinin aldığı verileri temsil eder <xref:System.ServiceModel.Activities.ReceiveReply> . .NET Framework, <xref:System.ServiceModel.Activities.ReceiveMessageContent> ve <xref:System.ServiceModel.Activities.ReceiveParametersContent> her ikisi de öğesinden türetilmiş iki ilişkili sınıfı tanımlar <xref:System.ServiceModel.Activities.ReceiveContent> . <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> `Content` Bir iş akışı hizmetine veri almak için, veya etkinliğinin özelliğini bu türlerden birinin bir örneğine ayarlayın. Kullanılacak tür, etkinliğin aldığı veri türüne bağlıdır. Etkinlik bir `Message` nesne veya bir ileti sözleşme türü alırsa, kullanın <xref:System.ServiceModel.Activities.ReceiveMessageContent> . Etkinlik seri hale getirilebilen bir veri anlaşması veya XML türleri kümesi alırsa, kullanın <xref:System.ServiceModel.Activities.ReceiveParametersContent> . <xref:System.ServiceModel.Activities.ReceiveParametersContent>birden çok parametre göndermenizi sağlar, ancak <xref:System.ServiceModel.Activities.ReceiveMessageContent> yalnızca bir nesne, ileti (veya ileti sözleşmesi türü) göndermenize olanak tanır.

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent>Ayrıca, seri hale getirilebilen tek bir veri sözleşmesi veya XML türü ile de kullanılabilir. <xref:System.ServiceModel.Activities.ReceiveParametersContent>Tek bir parametre ve doğrudan öğesine geçirilen nesne ile kullanma arasındaki fark, <xref:System.ServiceModel.Activities.ReceiveMessageContent> tel biçimidir. Parametrenin içeriği, işlem adına karşılık gelen bir XML öğesinde sarmalanmış ve serileştirilmiş nesne, parametre adı kullanılarak bir XML öğesinde sarmalandı (örneğin, `<Echo><msg>Hello, World</msg></Echo>` ). İleti içeriği, işlem adı tarafından sarmalanmamış. Bunun yerine, serileştirilmiş nesne XML-nitelenmiş tür adı kullanılarak bir XML öğesi içine yerleştirilir (örneğin, `<string>Hello, World</string>` ).

<xref:System.ServiceModel.Activities.Send>Ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri adlı özelliği de vardır `Content` . Bu özellik türündedir <xref:System.ServiceModel.Activities.SendContent> ve <xref:System.ServiceModel.Activities.Send> veya etkinliğinin gönderdiği verileri temsil eder <xref:System.ServiceModel.Activities.SendReply> . .NET Framework, <xref:System.ServiceModel.Activities.SendMessageContent> <xref:System.ServiceModel.Activities.SendParametersContent> her ikisi de öğesinden türetilen iki ilişkili türü tanımlar <xref:System.ServiceModel.Activities.SendContent> . <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> `Content` Bir iş akışı hizmetinden veri göndermek için, veya etkinliğinin özelliğini bu türlerden birinin bir örneğine ayarlayın. Kullanılacak tür, etkinliğin gönderdiği veri türüne bağlıdır. Etkinlik bir `Message` nesne veya ileti anlaşması türü gönderiyorsa, kullanın <xref:System.ServiceModel.Activities.SendMessageContent> . Etkinlik bir veri anlaşması türü kullanımını gönderirse <xref:System.ServiceModel.Activities.SendParametersContent> . <xref:System.ServiceModel.Activities.SendParametersContent>birden çok parametre göndermenize izin verir, ancak <xref:System.ServiceModel.Activities.SendMessageContent> yalnızca bir nesne, ileti (veya ileti sözleşmesi türü) göndermenize olanak tanır.

İmperatively 'i mesajlaşma etkinlikleriyle programlarken,,, <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> ve etkinliklerinin ileti ya da parametre özelliklerine atadığınız nesneleri kaydırmak için genel ' i kullanırsınız <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> . <xref:System.Activities.InArgument%601>Ve etkinlikleri ve etkinlikleri için kullanın <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.OutArgument%601> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> . `In`bağımsız değişkenler gönderme etkinlikleriyle birlikte kullanılır çünkü veriler etkinliklere geçirilir. `Out`bağımsız değişkenler, aşağıdaki örnekte gösterildiği gibi, veriler etkinliklerden geçirildiğinden, alma etkinlikleriyle birlikte kullanılır.

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

Void döndüren bir istek/yanıt işlemini tanımlayan bir iş akışı hizmeti uygularken, bir <xref:System.ServiceModel.Activities.SendReply> etkinlik örneği oluşturup <xref:System.ServiceModel.Activities.SendReply.Content%2A> özelliği, <xref:System.ServiceModel.Activities.SendMessageContent> <xref:System.ServiceModel.Activities.SendParametersContent> Aşağıdaki örnekte gösterildiği gibi içerik türlerinden birinin boş bir örneğine ayarlamanız gerekir.

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

İş akışı hizmetini bir iş akışı uygulamasından çağırırken, Visual Studio 2012, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> bir istek/yanıt verme sırasında kullanılan olağan ve etkinlikleri kapsülleyen özel mesajlaşma etkinlikleri oluşturur. Bu özelliği kullanmak için, Visual Studio 'da istemci projesine sağ tıklayın ve **Add**  >  **hizmet başvurusu**Ekle ' yi seçin. Adres kutusuna hizmetin temel adresini yazın ve git ' e tıklayın. Kullanılabilir Hizmetler **Hizmetler:** kutusunda görüntülenir. Desteklenen sözleşmeleri göstermek için hizmet düğümünü genişletin. Çağırmak istediğiniz sözleşmeyi seçin ve kullanılabilir işlemler listesi **işlemler** kutusunda görüntülenir. Ardından, oluşturulan etkinliğin ad alanını belirtebilir ve **Tamam**' a tıklayabilirsiniz. Ardından, işlemin başarıyla tamamlandığını belirten bir iletişim kutusu ve projeyi yeniden oluşturduktan sonra oluşturulan özel etkinliklerin araç kutusunda olduğunu belirten bir iletişim kutusu görürsünüz. Hizmet sözleşmesinde tanımlanan her işlem için bir etkinlik vardır. Projeyi yeniden oluşturduktan sonra özel etkinlikleri iş akışınıza sürükleyip bırakabilir ve Özellikler penceresinde gerekli özellikleri ayarlayabilirsiniz.

## <a name="messaging-activity-templates"></a>Mesajlaşma etkinlik şablonları

İstemci ve hizmet üzerinde bir istek/yanıt ayarlamayı daha kolay hale getirmek için, Visual Studio 2012 iki mesajlaşma etkinlik şablonu sağlar. `System.ServiceModel.Activities.Design.ReceiveAndSendReply`, hizmette kullanılır ve `System.ServiceModel.Activities.Design.SendAndReceiveReply` istemcide kullanılır. Her iki durumda da şablonlar, uygun mesajlaşma etkinliklerini iş akışınıza ekler. Hizmette, etkinlik `System.ServiceModel.Activities.Design.ReceiveAndSendReply` <xref:System.ServiceModel.Activities.Receive> tarafından izlenen bir etkinlik ekler <xref:System.ServiceModel.Activities.SendReply> . <xref:System.ServiceModel.Activities.SendReply.Request>Özelliği otomatik olarak <xref:System.ServiceModel.Activities.Receive> etkinliğe ayarlanır. İstemcisinde, `System.ServiceModel.Activities.Design.SendAndReceiveReply` <xref:System.ServiceModel.Activities.Send> sonrasında bir etkinlik ekler <xref:System.ServiceModel.Activities.ReceiveReply> . <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>Özelliği otomatik olarak <xref:System.ServiceModel.Activities.Send> etkinliğe ayarlanır. Bu şablonları kullanmak için, uygun şablonu yalnızca iş akışınıza sürükleyip bırakın.

## <a name="messaging-activities-and-transactions"></a>Mesajlaşma etkinlikleri ve işlemler

Bir iş akışı hizmetine bir çağrı yapıldığında, hizmet işlemine bir işlem akışını isteyebilirsiniz. Bunu yapmak için <xref:System.ServiceModel.Activities.Receive> etkinliği bir etkinliğin içine yerleştirin <xref:System.ServiceModel.Activities.TransactedReceiveScope> . <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik bir `Receive` etkinlik ve bir gövde içeriyor. Hizmete akan işlem, gövdesinin yürütülmesi boyunca çevresel olarak kalır <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Gövde yürütmeyi bitirdiğinde işlem tamamlanır. İş akışları ve işlemler hakkında daha fazla bilgi için bkz. [Iş akışı işlemleri](../../windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Iş akışı hizmetlerinde hata gönderme ve alma](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Uzun Süre Çalışan Bir İş Akışı Hizmeti Oluşturma](creating-a-long-running-workflow-service.md)
