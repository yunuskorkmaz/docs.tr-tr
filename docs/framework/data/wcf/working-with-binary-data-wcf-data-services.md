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
ms.openlocfilehash: 3c391e641df52d9143630406a40e17c6bc853865
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551757"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Ikili verilerle çalışma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri istemci kitaplığı, aşağıdaki yollarla bir açık veri Protokolü (OData) akışından ikili verileri almanızı ve güncelleştirmenizi sağlar:

- Bir varlığın ilkel tür özelliği olarak. Bu, belleğe kolayca yüklenebilen küçük ikili veri nesneleriyle çalışma için önerilen yöntemdir. Bu durumda, ikili özelliği, veri modeli tarafından kullanıma sunulan bir varlık özelliğidir ve veri hizmeti yanıt iletisinde temel 64 ikili kodlanmış XML olarak seri hale getirir.

- Ayrı bir ikili kaynak akışı olarak. Bu, bir fotoğrafı, videoyu veya herhangi bir tür ikili kodlu veriyi temsil eden ikili büyük nesne (BLOB) verilerine erişmek ve bunları değiştirmek için önerilen yöntemdir.

WCF Veri Hizmetleri, OData 'de tanımlanan HTTP kullanarak ikili verilerin akışını uygular. Bu mekanizmaya, ikili veriler, ancak medya bağlantı girişi olarak adlandırılan bir varlıkla ilişkili olan bir medya kaynağı olarak değerlendirilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).

> [!TIP]
> Fotoğrafları depolayan bir OData hizmetinden ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı serisi-2. Bölüm: Istemciden medya kaynak akışına erişme](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Blog gönderisine özel akış fotoğrafı veri hizmeti için örnek kodu indirmek için bkz. GitHub 'da [akış fotoğrafı veri hizmeti örneği](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) .

## <a name="entity-metadata"></a>Varlık meta verileri

İlişkili bir medya kaynağı akışına sahip bir varlık, veri hizmeti meta verilerinde `HasStream` medya bağlantısı girişi olan bir varlık türüne uygulanan özniteliğe göre belirtilir. Aşağıdaki örnekte, `PhotoInfo` varlık, ilişkili bir medya kaynağına sahip olan ve özniteliğiyle belirtilen bir medya bağlantı girişi `HasStream` .

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Bu konudaki geri kalan örneklerde, medya kaynağı akışına nasıl erişebileceğiniz ve değiştirileceği gösterilmektedir. WCF Veri Hizmetleri istemci kitaplığı 'nı kullanarak bir .NET Framework istemci uygulamasında medya kaynak akışının nasıl kullanılacağına ilişkin tüm bir örnek için, [Istemciden medya kaynak akışına erişme](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client)gönderisini inceleyin.

## <a name="accessing-the-binary-resource-stream"></a>Ikili kaynak akışına erişme

WCF Veri Hizmetleri istemci kitaplığı, OData tabanlı bir veri hizmetinden ikili kaynak akışlarına erişmek için yöntemler sağlar. Bir medya kaynağı indirilirken, Medya kaynağının URI 'sini kullanabilir veya medya kaynağı verilerinin kendisini içeren bir ikili akış alabilirsiniz. Ayrıca, medya kaynağı verilerini ikili akış olarak karşıya yükleyebilirsiniz.

> [!TIP]
> Fotoğrafları depolayan bir OData hizmetinden ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı serisi-2. Bölüm: Istemciden medya kaynak akışına erişme](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client). Blog gönderisine özel akış fotoğrafı veri hizmeti için örnek kodu indirmek için bkz. GitHub 'da [akış fotoğrafı veri hizmeti örneği](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) .

### <a name="getting-the-uri-of-the-binary-stream"></a>Ikili akışın URI 'sini alma

Görüntüler ve diğer medya dosyaları gibi belirli medya kaynağı türlerini alırken, uygulamanızda, ikili veri akışının kendisini işlemeye kıyasla Medya kaynağının URI 'sini kullanmak genellikle daha kolay olur. Medya verme bağlantı girdisiyle ilişkili bir kaynak akışının URI 'sini almak için, <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> <xref:System.Data.Services.Client.DataServiceContext> varlığı izleyen örnekte yöntemini çağırmanız gerekir. Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> istemcisinde yeni bir görüntü oluşturmak için kullanılan bir medya kaynak AKıŞıNıN URI 'sini almak için yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Ikili kaynak akışı indiriliyor

Bir ikili kaynak akışı alınırken, <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> <xref:System.Data.Services.Client.DataServiceContext> Medya bağlantı girişini izleyen örnekte yöntemini çağırmanız gerekir. Bu yöntem <xref:System.Data.Services.Client.DataServiceStreamResponse> , kaynağı içeren akışa bir başvuru içeren bir nesne döndüren veri hizmetine bir istek gönderir. Uygulamanız ikili kaynağı bir olarak gerektirdiğinde bu yöntemi kullanın <xref:System.IO.Stream> . Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> istemcisinde yeni bir görüntü oluşturmak için kullanılan bir akışı almak için yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Yanıt iletisindeki Içerik uzunluğu üst bilgisi, buhar ikilisini içeren veri hizmeti tarafından ayarlanmadı. Bu değer, ikili veri akışının gerçek uzunluğunu yansıtmayabilir.

### <a name="uploading-a-media-resource-as-a-stream"></a>Medya kaynağını akış olarak karşıya yükleme

Bir medya kaynağı eklemek veya güncelleştirmek için, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> <xref:System.Data.Services.Client.DataServiceContext> varlığı izleyen örnekte yöntemi çağırın. Bu yöntem, sağlanan akıştan okunan medya kaynağını içeren veri hizmetine bir istek gönderir. Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> veri hizmetine görüntü göndermek için yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

Bu örnekte, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi parametresi için bir değer sağlayarak çağrılır `true` `closeStream` . Bu, <xref:System.Data.Services.Client.DataServiceContext> ikili veriler veri hizmetine yüklendikten sonra akışın kapandığına güvence sağlar.

> [!NOTE]
> <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>' İ çağırdığınızda, bu akış veri hizmetine <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> çağrılana kadar gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veriyi Denetimlere Bağlama](binding-data-to-controls-wcf-data-services.md)
