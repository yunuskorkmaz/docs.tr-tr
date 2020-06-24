---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
description: İşlem yapılmadan önce tamamen alınması gereken varsayılan arabelleğe alınmış aktarımlar yerine WCF 'de akış iletileri etkinleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 538fd8634094aa6fbf097ddb94469d7bca749a63
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247032"
---
# <a name="how-to-enable-streaming"></a>Nasıl yapılır: Akışı Etkinleştirme
Windows Communication Foundation (WCF), arabelleğe alınmış veya akış aktarımları kullanarak ileti gönderebilir. Varsayılan arabelleğe alınmış Aktarım modunda, bir alıcının okuyabilmesi için bir iletinin tamamen teslim edilmesi gerekir. Akış Aktarım modunda, alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilir. Aktarım modu, iletilen bilgiler uzun olduğunda ve hizmet dışı olarak işlenebilmesi durumunda faydalıdır. İleti tamamen arabelleğe alınamayacak kadar büyük olduğunda akış modu da yararlıdır.  
  
 Akışı etkinleştirmek için, `OperationContract` Aktarım düzeyinde uygun bir şekilde tanımlayın ve akışı etkinleştirin.  
  
### <a name="to-stream-data"></a>Veri akışı için  
  
1. Veri akışı için, `OperationContract` hizmetin iki gereksinimi karşılaması gerekir:  
  
    1. Akışa eklenecek verileri tutan parametrenin yöntemdeki tek parametre olması gerekir. Örneğin, giriş iletisi akışla bir giriş ise, işlemin tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıkış iletisi akışı ise, işlemin tam olarak bir çıkış parametresi veya dönüş değeri olması gerekir.  
  
    2. Parametre ve dönüş değerinin en az biri, ya da olmalıdır <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message> <xref:System.Xml.Serialization.IXmlSerializable> .  
  
     Aşağıda akış verileri için bir sözleşme örneği verilmiştir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     İşlem, ara belleğe `GetStream` alınmış bir olarak bazı arabellekli giriş verileri alır `string` ve akış olan bir döndürür `Stream` . Bunun tersine `UploadStream` bir `Stream` (akışlı) alır ve `bool` (ara belleğe alınmış) döndürür. `EchoStream`, `Stream` giriş ve çıkış iletilerinin her ikisi de akışındaki bir işlemin örneğini alır ve döndürür. Son olarak, `GetReversedStream` giriş yapılmaz ve `Stream` (akış) döndürür.  
  
2. Bağlamada akış etkinleştirilmelidir. `TransferMode`Aşağıdaki değerlerden birini içerebilen bir özellik ayarlarsınız:  
  
    1. `Buffered`,  
  
    2. `Streamed`Her iki yönde de akış iletişimi sağlayan.  
  
    3. `StreamedRequest`, yalnızca isteği akışa izin veren.  
  
    4. `StreamedResponse`yalnızca yanıtı akışa izin veren.  
  
     ,, `BasicHttpBinding` `TransferMode` Ve gibi bağlama üzerinde özelliğini kullanıma sunar `NetTcpBinding` `NetNamedPipeBinding` . `TransferMode`Özelliği, aktarım bağlama öğesinde de ayarlanabilir ve özel bir bağlamada kullanılabilir.  
  
     Aşağıdaki örnekler, `TransferMode` kod ile ve yapılandırma dosyasını değiştirerek nasıl ayarlanacağını göstermektedir. Ayrıca örneklerin her ikisi de `maxReceivedMessageSize` , alma sırasında izin verilen en fazla ileti boyutuna bir sınır yerleştiren, özelliği 64 MB olarak ayarlar. Varsayılan değer, `maxReceivedMessageSize` genellikle akış senaryolarında çok düşük olan 64 KB 'tır. Uygulamanızın almasını beklediği en fazla ileti boyutuna bağlı olarak bu kota ayarını uygun şekilde ayarlayın. Ayrıca `maxBufferSize` , arabelleğe alınan en büyük boyutu denetler ve uygun şekilde ayarlayın.  
  
    1. Örnekteki aşağıdaki yapılandırma kod parçacığı, `TransferMode` özelliğinin `basicHttpBinding` ve özel bir http bağlamasındaki akış için ayarlanmasını gösterir.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Aşağıdaki kod parçacığı, `TransferMode` `basicHttpBinding` ve özel bir http bağlamasındaki özelliği akışa alma özelliğini gösterir.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Aşağıdaki kod parçacığı, `TransferMode` özelliği özel bır TCP bağlamasındaki akışa ayarlamayı gösterir.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. İşlemler `GetStream` , `UploadStream` ve `EchoStream` hepsi doğrudan bir dosyadan veri göndermeye veya alınan verileri doğrudan bir dosyaya kaydetmeye yöneliktir. Aşağıdaki kod içindir `GetStream` .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Özel akış yazma  
  
1. Gönderilen veya alınan bir veri akışının her öbeğiyle özel işlem yapmak için, öğesinden özel bir akış sınıfı türetirsiniz <xref:System.IO.Stream> . Özel bir akışa örnek olarak aşağıdaki kod bir `GetReversedStream` yöntemi ve bir `ReverseStream` sınıfı içerir.  
  
     `GetReversedStream`Yeni bir örneğini oluşturur ve döndürür `ReverseStream` . Gerçek işlem, nesneden sistem okuduğunda oluşur `ReverseStream` . `ReverseStream.Read`Yöntemi, temel alınan dosyadaki bir bayt öbeğini okur, bunları tersine çevirir ve ters bayt döndürür. Bu yöntem, tüm dosya içeriğini tersine almaz; tek seferde bir bayt öbeğini tersine çevirir. Bu örnek, içerik okuma veya akışa yazma sırasında akış işlemeyi nasıl gerçekleştirebileceğini gösterir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Büyük Veriler ve Akış Yapma](large-data-and-streaming.md)
- [Akış](../samples/stream.md)
