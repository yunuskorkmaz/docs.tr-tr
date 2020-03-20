---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 1d1eaa1ebf41ef86478dda795b3b199239cd37b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184940"
---
# <a name="how-to-enable-streaming"></a>Nasıl yapılır: Akışı Etkinleştirme
Windows Communication Foundation (WCF), arabelleğe alınan veya akışlı aktarımları kullanarak ileti gönderebilir. Varsayılan arabelleğe alınan aktarım modunda, bir iletinin bir alıcının okuyabilmesi için tamamen teslim edilmesi gerekir. Akış aktarım modunda, alıcı iletiyi tamamen teslim edilmeden önce işlemeye başlayabilir. Akış modu, geçirilen bilgiler uzun olduğunda ve seri olarak işlenebilirse yararlıdır. Akış modu, ileti tamamen arabelleğe alınamayacak kadar büyükolduğunda da kullanışlıdır.  
  
 Akışı etkinleştirmek için, uygun şekilde tanımlayın `OperationContract` ve aktarım düzeyinde akışı etkinleştirin.  
  
### <a name="to-stream-data"></a>Veri akışı için  
  
1. Veri akışı için, hizmet `OperationContract` için iki gereksinimi karşılamalıdır:  
  
    1. Akışlanacak verileri tutan parametre yöntemdeki tek parametre olmalıdır. Örneğin, giriş iletisi akış için bir işlem varsa, işlem tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıktı iletisi akış olacaksa, işlemin tam olarak bir çıkış parametresi veya bir iade değeri olmalıdır.  
  
    2. Parametre ve iade değeri türlerinden en az <xref:System.IO.Stream>biri <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.Serialization.IXmlSerializable>, veya .  
  
     Aşağıda, akışlı veriler için bir sözleşme örneği verilmiştir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     İşlem, `GetStream` arabelleğe alınan bazı arabelleğe alınan giriş verilerini `string`, `Stream`arabelleğe alınan bir , olarak alır ve akışlı bir , döndürür. Tersine `UploadStream` bir `Stream` (akış) alır ve `bool` bir (arabelleğe alındı) döndürür. `EchoStream`alır ve `Stream` döndürür ve giriş ve çıktı iletileri hem akış lı bir işlem örneğidir. Son `GetReversedStream` olarak, hiçbir giriş `Stream` alır ve bir (akış) döndürür.  
  
2. Bağlamada akış etkinleştirilmelidir. Aşağıdaki değerlerden birini alabilecek bir `TransferMode` özellik ayarlarsınız:  
  
    1. `Buffered`,  
  
    2. `Streamed`, her iki yönde de iletişim akışı sağlar.  
  
    3. `StreamedRequest`, yalnızca isteği akışı sağlar.  
  
    4. `StreamedResponse`, yalnızca yanıtAkışını sağlar.  
  
     Bağlama `BasicHttpBinding` özelliğini `TransferMode` ortaya çıkarır, yaptığı `NetTcpBinding` `NetNamedPipeBinding`gibi ve . Özellik, `TransferMode` aktarım bağlama öğesi üzerinde de ayarlanabilir ve özel bir bağlama da kullanılabilir.  
  
     Aşağıdaki örnekler, koda `TransferMode` göre ve yapılandırma dosyasını değiştirerek nasıl ayarlanır gösterin. Örneklerin her ikisi `maxReceivedMessageSize` de özelliği 64 MB olarak ayarlar ve bu da alınan iletilerin izin verilen maksimum boyutuna bir kapak yerleştirir. Varsayılan `maxReceivedMessageSize` 64 KB, genellikle çok düşük akış senaryoları için. Bu kota ayarını, uygulamanızın almayı beklediği maksimum ileti boyutuna bağlı olarak uygun şekilde ayarlayın. Arabelleğe `maxBufferSize` alınan maksimum boyutu denetler ve uygun şekilde ayarlayın.  
  
    1. Örnekten aşağıdaki yapılandırma parçacığı, `TransferMode` özelliği akışa `basicHttpBinding` ve özel bir HTTP bağlamaya ayarlayışgösterir.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Aşağıdaki kod snippet `TransferMode` `basicHttpBinding` ve özel bir HTTP bağlama üzerinde akış özelliği ayarı gösterir.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Aşağıdaki kod snippet özel `TransferMode` bir TCP bağlama üzerinde akış özelliği ayarı gösterir.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. İşlemler `GetStream` `UploadStream`ve `EchoStream` tüm işlemler, doğrudan bir dosyadan veri gönderme veya alınan verileri doğrudan bir dosyaya kaydetme ile ilgilenir. Aşağıdaki kod `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Özel akış yazma  
  
1. Bir veri akışının gönderildiği veya alındığı her yığın da özel işleme yapmak için, 'den <xref:System.IO.Stream>özel bir akış sınıfı türetmek. Özel bir akış örneği olarak, aşağıdaki `GetReversedStream` kod bir `ReverseStream` yöntem ve bir sınıf içerir.  
  
     `GetReversedStream`yeni bir örnek oluşturur `ReverseStream`ve döndürür. Gerçek işleme, sistem `ReverseStream` nesneden okurken gerçekleşir. Yöntem, `ReverseStream.Read` alttaki dosyadan bayt bir yığın okur, bunları tersine çevirir ve ters bayt döndürür. Bu yöntem, dosya içeriğinin tamamını tersine çevirmez; bir seferde bir bayt parçasını tersine çevirir. Bu örnek, içerik akışa okunurken veya akıştan yazılırken akış işlemeyi nasıl gerçekleştirebileceğinizi gösterir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Büyük Veriler ve Akış Yapma](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Akış](../../../../docs/framework/wcf/samples/stream.md)
