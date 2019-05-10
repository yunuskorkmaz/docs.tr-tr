---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: bd1a52f1ce0f656af79928a20e3badc73661e89a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635299"
---
# <a name="how-to-enable-streaming"></a>Nasıl yapılır: Akışı Etkinleştirme
Windows Communication Foundation (WCF) iletilerini arabelleğe alınan ya da akış aktarımları kullanarak gönderebilirsiniz. Bir alıcı okumadan önce varsayılan arabelleğe alınan aktarım modunda bir ileti tamamen teslim edilmelidir. Aktarım modunu akışında alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilirsiniz. Akış modunda iletilen bilgiler uzun ve seri olarak işlenebilecek yararlı olur. Akış modunda de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.  
  
 Akışını etkinleştirmek için tanımladığınız `OperationContract` uygun şekilde ve akış taşıma düzeyinde etkinleştirin.  
  
### <a name="to-stream-data"></a>Akış verileri  
  
1. Veri akışı `OperationContract` için hizmeti iki gereksinimleri karşılaması gerekir:  
  
    1. Akışla verileri tutan parametresi, yöntemin tek parametre olmalıdır. Örneğin, giriş iletisine akışla birine ise, işlemi tam olarak bir girdi parametreniz olmalıdır. Benzer şekilde, çıktı iletisi akışını ise işlemi tam olarak bir çıkış parametresi ya da dönüş değeri olması gerekir.  
  
    2. En az bir parametre ve dönüş değeri türlerini olmalıdır ya da <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, veya <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Akış veri sözleşme örneği verilmiştir.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` İşlemi arabelleğe alınan bazı girdi verisi olarak aldığı bir `string`, arabelleğe alınıp ve döndürür bir `Stream`, hangi akış. Buna karşılık `UploadStream` alır bir `Stream` (akış) ve döndüren bir `bool` (arabelleğe). `EchoStream` alan ve döndüren `Stream` işlem girişi örneğidir ve çıkış iletileri hem de akış. Son olarak, `GetReversedStream` giriş alan ve döndüren bir `Stream` (akış).  
  
2. Akış bağlamadaki etkinleştirilmesi gerekir. Ayarladığınız bir `TransferMode` özelliği şu değerlerden birini alabilir:  
  
    1. `Buffered`,  
  
    2. `Streamed`, her iki yönde de akış iletişimi sağlar.  
  
    3. `StreamedRequest`, yalnızca istek akışı etkinleştirir.  
  
    4. `StreamedResponse`, yalnızca yanıt akışı etkinleştirir.  
  
     `BasicHttpBinding` Sunan `TransferMode` aynı bağlama özelliğinin `NetTcpBinding` ve `NetNamedPipeBinding`. `TransferMode` Özelliği ayrıca aktarım bağlama öğede ayarlama ve kullanılan özel bir bağlama.  
  
     Aşağıdaki örnekler nasıl belirleyeceğinizi `TransferMode` kod ve yapılandırma dosyasını değiştirerek. Her ikisi de ayarlanmış örnekleri `maxReceivedMessageSize` yerleştirir iletileri izin verilen en büyük boyutu için üst sınır 64 MB özelliğini alır. Varsayılan `maxReceivedMessageSize` genellikle akış senaryoları için düşükse, 64 KB ' tır. Bu kota ayarı iletileri almak için uygulamanızı bekliyor en büyük boyutuna bağlı olarak uygun şekilde ayarlayın. Ayrıca `maxBufferSize` arabelleğe alınır ve uygun şekilde ayarlanmış maksimum boyutu denetler.  
  
    1. Ayar örneği aşağıdaki yapılandırma parçacığından gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel bir HTTP bağlaması.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2. Aşağıdaki kod parçacığı ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel bir HTTP bağlaması.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Aşağıdaki kod parçacığı ayarını gösterir `TransferMode` özel TCP bağlamada akış özelliği.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. İşlemleri `GetStream`, `UploadStream`, ve `EchoStream` tüm baş doğrudan bir dosyadan veri gönderen veya alınan verileri bir dosyaya kaydetme. Aşağıdaki kod içindir `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Özel bir akış yazma  
  
1. Bunu gönderildiği sırada bir veri akışı, her bir öbeği özel işleme yapmak veya alınan özel akış sınıfından türetilen <xref:System.IO.Stream>. Özel bir akışa ilişkin bir örnek olarak, aşağıdaki kodu içeren bir `GetReversedStream` yöntemi ve bir `ReverseStream` sınıfı-.  
  
     `GetReversedStream` oluşturur ve yeni bir örneğini döndürür `ReverseStream`. Sistem okur gibi gerçek işleme olur `ReverseStream` nesne. `ReverseStream.Read` Yöntemi bayt öbeğini temel alınan dosyadan okur, bunları tersine çevirir ve sonra ters bayt sayısını döndürür. Bu yöntem, tüm dosya içeriğini ters değil; bir kerede bir bayt bir öbek tersine çevirir. Bu örnek, içeriği olarak akış işlemede nasıl gerçekleştirebileceğiniz gösterir akıştan yazılamaz veya okunamaz için okuyun.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Büyük Veriler ve Akış Yapma](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Akış](../../../../docs/framework/wcf/samples/stream.md)
