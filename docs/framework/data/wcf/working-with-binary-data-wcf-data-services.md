---
title: Ikili verilerle çalışma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: fa64308593656ccd6e89684a18de13e7c64343fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930017"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Ikili verilerle çalışma (WCF Veri Hizmetleri)
İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplığı, aşağıdaki yollarla bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akıştan ikili verileri almanızı ve güncelleştirmenizi sağlar:  
  
- Bir varlığın ilkel tür özelliği olarak. Bu, belleğe kolayca yüklenebilen küçük ikili veri nesneleriyle çalışma için önerilen yöntemdir. Bu durumda, ikili özelliği, veri modeli tarafından kullanıma sunulan bir varlık özelliğidir ve veri hizmeti yanıt iletisinde temel 64 ikili kodlanmış XML olarak seri hale getirir.  
  
- Ayrı bir ikili kaynak akışı olarak. Bu, bir fotoğrafı, videoyu veya herhangi bir tür ikili kodlu veriyi temsil eden ikili büyük nesne (BLOB) verilerine erişmek ve bunları değiştirmek için önerilen yöntemdir.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]içinde tanımlanan http kullanarak ikili verilerin akışını uygular. Bu mekanizmaya, ikili veriler, ancak medya bağlantı girişi olarak adlandırılan bir varlıkla ilişkili olan bir medya kaynağı olarak değerlendirilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Fotoğrafları depolayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmetten ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı Serisi-Bölüm 2: Istemciden](https://go.microsoft.com/fwlink/?LinkId=201637)bir medya kaynak akışına erişme. Blog postasında sunulan Stream Photo Data Service için örnek kodu indirmek için MSDN kod galerisinde [akış fotoğrafı veri hizmeti örneğine](https://go.microsoft.com/fwlink/?LinkId=198988) bakın.  
  
## <a name="entity-metadata"></a>Varlık meta verileri  
 İlişkili bir medya kaynağı akışına sahip bir varlık, veri hizmeti meta verilerinde medya bağlantısı girişi olan bir `HasStream` varlık türüne uygulanan özniteliğe göre belirtilir. Aşağıdaki örnekte, `PhotoInfo` varlık, ilişkili bir medya kaynağına sahip olan ve `HasStream` özniteliğiyle belirtilen bir medya bağlantı girişi.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]  
  
 Bu konudaki geri kalan örneklerde, medya kaynağı akışına nasıl erişebileceğiniz ve değiştirileceği gösterilmektedir. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığını kullanarak bir .NET Framework istemci uygulamasında bir medya kaynak akışının nasıl kullanılacağına ilişkin tüm bir örnek için, [istemciden medya kaynak akışına erişme](https://go.microsoft.com/fwlink/?LinkID=201637)gönderisini inceleyin.  
  
## <a name="accessing-the-binary-resource-stream"></a>Ikili kaynak akışına erişme  
 İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplığı, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]tabanlı veri hizmetinden ikili kaynak akışlarına erişmek için yöntemler sağlar. Bir medya kaynağı indirilirken, Medya kaynağının URI 'sini kullanabilir veya medya kaynağı verilerinin kendisini içeren bir ikili akış alabilirsiniz. Ayrıca, medya kaynağı verilerini ikili akış olarak karşıya yükleyebilirsiniz.  
  
> [!TIP]
>  Fotoğrafları depolayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmetten ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı Serisi-Bölüm 2: Istemciden](https://go.microsoft.com/fwlink/?LinkId=201637)bir medya kaynak akışına erişme. Blog postasında sunulan Stream Photo Data Service için örnek kodu indirmek için MSDN kod galerisinde [akış fotoğrafı veri hizmeti örneğine](https://go.microsoft.com/fwlink/?LinkId=198988) bakın.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Ikili akışın URI 'sini alma  
 Görüntüler ve diğer medya dosyaları gibi belirli medya kaynağı türlerini alırken, uygulamanızda, ikili veri akışının kendisini işlemeye kıyasla Medya kaynağının URI 'sini kullanmak genellikle daha kolay olur. Medya verme bağlantı girdisiyle ilişkili bir kaynak akışının URI 'sini almak için, varlığı izleyen <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> <xref:System.Data.Services.Client.DataServiceContext> örnekte yöntemini çağırmanız gerekir. Aşağıdaki örnek, istemcisinde yeni bir görüntü oluşturmak <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> için kullanılan bir medya kaynak akışının URI 'sini almak için yönteminin nasıl çağrılacağını göstermektedir:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Ikili kaynak akışı indiriliyor  
 Bir ikili kaynak akışı alınırken, medya bağlantı girişini izleyen <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> <xref:System.Data.Services.Client.DataServiceContext> örnekte yöntemini çağırmanız gerekir. Bu yöntem, kaynağı içeren akışa bir başvuru içeren bir <xref:System.Data.Services.Client.DataServiceStreamResponse> nesne döndüren veri hizmetine bir istek gönderir. Uygulamanız ikili kaynağı bir <xref:System.IO.Stream>olarak gerektirdiğinde bu yöntemi kullanın. Aşağıdaki örnek, istemcisinde yeni bir görüntü oluşturmak <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> için kullanılan bir akışı almak için yönteminin nasıl çağrılacağını göstermektedir:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
> Yanıt iletisindeki Içerik uzunluğu üst bilgisi, buhar ikilisini içeren veri hizmeti tarafından ayarlanmadı. Bu değer, ikili veri akışının gerçek uzunluğunu yansıtmayabilir.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Medya kaynağını akış olarak karşıya yükleme  
 Bir medya kaynağı eklemek veya güncelleştirmek için, varlığı izleyen <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> <xref:System.Data.Services.Client.DataServiceContext> örnekte yöntemi çağırın. Bu yöntem, sağlanan akıştan okunan medya kaynağını içeren veri hizmetine bir istek gönderir. Aşağıdaki örnek, veri hizmetine görüntü göndermek için <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yönteminin nasıl çağrılacağını göstermektedir:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi `closeStream` parametresi `true` için bir değer sağlayarak çağrılır. Bu, <xref:System.Data.Services.Client.DataServiceContext> ikili veriler veri hizmetine yüklendikten sonra akışın kapandığına güvence sağlar.  
  
> [!NOTE]
> ' İ çağırdığınızda <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, bu akış veri hizmetine çağrılana kadar <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> gönderilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Veriyi Denetimlere Bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
