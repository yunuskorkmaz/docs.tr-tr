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
ms.openlocfilehash: e088383adf2345f9a2698d0f8794765461cdbaad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975020"
---
# <a name="working-with-binary-data-wcf-data-services"></a>Ikili verilerle çalışma (WCF Veri Hizmetleri)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, aşağıdaki yollarla bir açık veri Protokolü (OData) akışından ikili verileri almanızı ve güncelleştirmenizi sağlar:

- Bir varlığın ilkel tür özelliği olarak. Bu, belleğe kolayca yüklenebilen küçük ikili veri nesneleriyle çalışma için önerilen yöntemdir. Bu durumda, ikili özelliği, veri modeli tarafından kullanıma sunulan bir varlık özelliğidir ve veri hizmeti yanıt iletisinde temel 64 ikili kodlanmış XML olarak seri hale getirir.

- Ayrı bir ikili kaynak akışı olarak. Bu, bir fotoğrafı, videoyu veya herhangi bir tür ikili kodlu veriyi temsil eden ikili büyük nesne (BLOB) verilerine erişmek ve bunları değiştirmek için önerilen yöntemdir.

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], OData 'de tanımlanan HTTP kullanarak ikili verilerin akışını uygular. Bu mekanizmaya, ikili veriler, ancak medya bağlantı girişi olarak adlandırılan bir varlıkla ilişkili olan bir medya kaynağı olarak değerlendirilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).

> [!TIP]
> Fotoğrafları depolayan bir OData hizmetinden ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı serisi-2. Bölüm: Istemciden medya kaynak akışına erişme](https://go.microsoft.com/fwlink/?LinkId=201637). Blog postasında sunulan Stream Photo Data Service için örnek kodu indirmek için MSDN kod galerisinde [akış fotoğrafı veri hizmeti örneğine](https://go.microsoft.com/fwlink/?LinkId=198988) bakın.

## <a name="entity-metadata"></a>Varlık meta verileri

İlişkili bir medya kaynağı akışına sahip bir varlık, veri hizmeti meta verilerinde, medya bağlantısı girişi olan bir varlık türüne uygulanan `HasStream` özniteliği tarafından gösterilir. Aşağıdaki örnekte `PhotoInfo` varlığı, ilişkili bir medya kaynağına sahip olan ve `HasStream` özniteliğiyle belirtilen bir medya bağlantı girişi olur.

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Bu konudaki geri kalan örneklerde, medya kaynağı akışına nasıl erişebileceğiniz ve değiştirileceği gösterilmektedir. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı 'nı kullanarak bir .NET Framework istemci uygulamasında medya kaynak akışının nasıl kullanılacağına ilişkin tüm bir örnek için, [Istemciden medya kaynak akışına erişme](https://go.microsoft.com/fwlink/?LinkID=201637)gönderisini inceleyin.

## <a name="accessing-the-binary-resource-stream"></a>Ikili kaynak akışına erişme

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, OData tabanlı bir veri hizmetinden ikili kaynak akışlarına erişmek için yöntemler sağlar. Bir medya kaynağı indirilirken, Medya kaynağının URI 'sini kullanabilir veya medya kaynağı verilerinin kendisini içeren bir ikili akış alabilirsiniz. Ayrıca, medya kaynağı verilerini ikili akış olarak karşıya yükleyebilirsiniz.

> [!TIP]
> Fotoğrafları depolayan bir OData hizmetinden ikili görüntü dosyalarını yükleyen Windows Presentation Foundation (WPF) istemci uygulamasının nasıl oluşturulacağı hakkında adım adım bir örnek için bkz. Post [Data Services akış sağlayıcısı serisi-2. Bölüm: Istemciden medya kaynak akışına erişme](https://go.microsoft.com/fwlink/?LinkId=201637). Blog postasında sunulan Stream Photo Data Service için örnek kodu indirmek için MSDN kod galerisinde [akış fotoğrafı veri hizmeti örneğine](https://go.microsoft.com/fwlink/?LinkId=198988) bakın.

### <a name="getting-the-uri-of-the-binary-stream"></a>Ikili akışın URI 'sini alma

Görüntüler ve diğer medya dosyaları gibi belirli medya kaynağı türlerini alırken, uygulamanızda, ikili veri akışının kendisini işlemeye kıyasla Medya kaynağının URI 'sini kullanmak genellikle daha kolay olur. Medya verme bağlantı girdisiyle ilişkili bir kaynak akışının URI 'sini almak için, varlığı izleyen <xref:System.Data.Services.Client.DataServiceContext> örneğinde <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> yöntemini çağırmanız gerekir. Aşağıdaki örnek, istemcisinde yeni bir görüntü oluşturmak için kullanılan bir medya kaynak akışının URI 'sini almak üzere <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>Ikili kaynak akışı indiriliyor

Bir ikili kaynak akışı alınırken, medya bağlantı girişini izleyen <xref:System.Data.Services.Client.DataServiceContext> örneğinde <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemini çağırmanız gerekir. Bu yöntem, kaynağı içeren akışa yönelik bir başvuru içeren <xref:System.Data.Services.Client.DataServiceStreamResponse> nesnesini döndüren veri hizmetine bir istek gönderir. Uygulamanız bir <xref:System.IO.Stream>olarak ikili kaynağı gerektirdiğinde bu yöntemi kullanın. Aşağıdaki örnek, istemcisinde yeni bir görüntü oluşturmak için kullanılan bir akışı almak üzere <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> Yanıt iletisindeki Içerik uzunluğu üst bilgisi, buhar ikilisini içeren veri hizmeti tarafından ayarlanmadı. Bu değer, ikili veri akışının gerçek uzunluğunu yansıtmayabilir.

### <a name="uploading-a-media-resource-as-a-stream"></a>Medya kaynağını akış olarak karşıya yükleme

Bir medya kaynağı eklemek veya güncelleştirmek için, varlığı izleyen <xref:System.Data.Services.Client.DataServiceContext> örneğinde <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemini çağırın. Bu yöntem, sağlanan akıştan okunan medya kaynağını içeren veri hizmetine bir istek gönderir. Aşağıdaki örnek, veri hizmetine görüntü göndermek için <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yönteminin nasıl çağrılacağını göstermektedir:

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

Bu örnekte, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi `closeStream` parametresi için bir `true` değeri sağlayarak çağrılır. Bu, ikili veriler veri hizmetine yüklendikten sonra <xref:System.Data.Services.Client.DataServiceContext> akışı kapatılmasını güvence altına alır.

> [!NOTE]
> <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>çağırdığınızda, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> çağrılana kadar akış veri hizmetine gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Veriyi Denetimlere Bağlama](binding-data-to-controls-wcf-data-services.md)
