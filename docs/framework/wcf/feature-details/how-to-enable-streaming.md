---
title: "Nasıl yapılır: Akışı Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8436ceefea936ddbf708aa3f79c5f7bd8153ac66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-streaming"></a>Nasıl yapılır: Akışı Etkinleştirme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]arabelleğe alınan veya akış aktarımları kullanarak iletiler gönderebilir. Bir alıcı okumadan önce varsayılan arabelleğe aktarım modunda bir ileti tamamen teslim edilmelidir. Aktarım modunu akışında alıcı tamamen teslim edilmeden önce iletiyi işlemek başlayabilirsiniz. Geçirilen bilgi uzun olduğunda ve seri olarak işlenebilen akış modu yararlıdır. Akış modu de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.  
  
 Akışını etkinleştirmek için tanımlamak `OperationContract` uygun şekilde ve aktarım düzeyinde akış etkinleştirin.  
  
### <a name="to-stream-data"></a>Veri akışı  
  
1.  Veri akışı için `OperationContract` için hizmet iki gereksinimleri karşılaması gerekir:  
  
    1.  Veri akışı tutar parametresi yöntemi yalnızca parametresinde olmalıdır. Örneğin, giriş ileti akışını ise, işlemi tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıktı ileti akışı, işlemi tam olarak bir çıkış parametresi veya dönüş değeri olmalıdır.  
  
    2.  En az bir parametre ve dönüş değer türlerini olmalıdır ya da <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, veya <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Bir sözleşme akış verileri için bir örnek verilmiştir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` İşlemi bazı arabelleğe alınan girdi verisi olarak aldığı bir `string`, hangi arabelleğe alınıp ve döndürür bir `Stream`, akışı. Buna karşılık `UploadStream` alır bir `Stream` (akışı) ve döndüren bir `bool` (arabelleğe). `EchoStream`alan ve döndüren `Stream` ve bir işlemin girişi örneğidir ve çıktı iletileri her ikisi de akışı. Son olarak, `GetReversedStream` hiç giriş alıp döndüren bir `Stream` (akış).  
  
2.  Akış bağlamada etkinleştirilmesi gerekir. Belirlediğiniz bir `TransferMode` aşağıdaki değerlerden birini alabilir özelliği:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, her iki yönde akış iletişimi sağlar.  
  
    3.  `StreamedRequest`, istek yalnızca akış sağlar.  
  
    4.  `StreamedResponse`, yalnızca yanıtı akış sağlar.  
  
     `BasicHttpBinding` Sunan `TransferMode` yaptığı gibi bağlama özellikte `NetTcpBinding` ve `NetNamedPipeBinding`. `TransferMode` Özelliği de ayarlanabilir aktarım bağlama öğesi üzerindeki ve özel bir bağlama kullanılır.  
  
     Aşağıdaki örnekler nasıl ayarlanacağını göstermektedir `TransferMode` kod hem yapılandırma dosyasını değiştirerek. Her ikisi de ayarlayın örnekleri `maxReceivedMessageSize` cap iletilerin en fazla izin verilen boyutu yerleştirir 64 MB özelliğine alırsınız. Varsayılan `maxReceivedMessageSize` genellikle senaryoları akış için çok düşük 64 KB ' tır. Bu kota ayarı iletileri almak için uygulamanızı bekliyor en büyük boyutuna bağlı olarak uygun şekilde ayarlayın. Ayrıca `maxBufferSize` arabelleğe ve uygun şekilde ayarlanmış maksimum boyutu denetler.  
  
    1.  Aşağıdaki yapılandırma parçacığını örnekten ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  Aşağıdaki kod parçacığını ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  Aşağıdaki kod parçacığını ayarını gösterir `TransferMode` özel TCP bağlamada akış özelliği.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  İşlemleri `GetStream`, `UploadStream`, ve `EchoStream` tüm işlem doğrudan bir dosyadan veri gönderme veya bir dosyaya doğrudan alınan veri kaydetme. Aşağıdaki kod içindir `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Özel akış yazma  
  
1.  Gönderilen gibi bir veri akışı, her bir öbeğin üzerindeki özel işleme yapın veya alınan özel akış sınıfından türetilen <xref:System.IO.Stream>. Özel akış örnek olarak, aşağıdaki kodu içeren bir `GetReversedStream` yöntemi ve `ReverseStream` sınıfı-.  
  
     `GetReversedStream`oluşturur ve yeni bir örneğini döndürür `ReverseStream`. Sistem okur gibi gerçek işleme olur `ReverseStream` nesnesi. `ReverseStream.Read` Yöntemi bayt bir öbek temel alınan dosyayı okur, bunları geri alır, ardından ters bayt döndürür. Bu yöntem, tüm dosya içeriği ters değil; bir kerede bir öbek bayt tersine çevirir. Bu örnek nasıl içerik olarak akış işleme gerçekleştirebilirsiniz gösterir için okuma veya akıştan yazılır.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Büyük veri ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [Akış](../../../../docs/framework/wcf/samples/stream.md)
