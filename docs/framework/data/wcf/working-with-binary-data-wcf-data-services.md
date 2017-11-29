---
title: "İkili veriler (WCF Veri Hizmetleri) ile çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ed6e20e899ce151f91c370bdf9553a7ace23c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-binary-data-wcf-data-services"></a>İkili veriler (WCF Veri Hizmetleri) ile çalışma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı almak ve ikili verileri güncelleştirmek sağlayan bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] aşağıdaki yollardan biriyle akış:  
  
-   Bir varlık bir ilkel tür özelliği. Bu, kolayca belleğe yüklenen nesneler küçük ikili verilerle çalışmak için önerilen yöntemdir. Bu durumda, ikili özelliği veri modeli tarafından kullanıma sunulan bir varlık özelliğidir ve veri hizmeti ikili kodlanmış XML yanıt iletisi base-64 olarak ikili verileri serileştirir.  
  
-   Ayrı ikili kaynak akış olarak. Bu, erişmek ve fotoğraf, video veya başka türde bir ikili kodlanmış verileri gösterebilir ikili büyük nesne (BLOB) verileri değiştirme önerilen yöntemdir.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]' da tanımlandığı gibi HTTP kullanarak ikili veri akışı uygulayan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Bu mekanizma, ikili veri ayrıdır bir medya kaynağı olarak kabul ancak ilgili medya bağlantısı girişi olarak adlandırılan bir varlık için. Daha fazla bilgi için bkz: [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Nasıl oluşturulacağı hakkında adım adım bir örneği için bir [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ikili resim dosyalarını indirir istemci uygulaması bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fotoğrafları, depolayan hizmeti Bkz post [Veri Hizmetleri Akış sağlayıcısı serisi bölüm 2: bir ortama erişme Kaynak akışı istemciden](http://go.microsoft.com/fwlink/?LinkId=201637). Blog postasına öne çıkan akış fotoğraf veri hizmeti için örnek kod indirmek için bkz: [akış fotoğraf veri hizmeti örnek](http://go.microsoft.com/fwlink/?LinkId=198988) MSDN kod Galerisi'nden içinde.  
  
## <a name="entity-metadata"></a>Varlık meta verileri  
 İlgili medya kaynak akışı sahip bir varlık veri hizmeti meta verilerini tarafından belirtilen `HasStream` medya bağlantısı girişinin bir varlık türü için uygulanan öznitelik. Aşağıdaki örnekte, `PhotoInfo` varlıktır belirttiği bir ilgili medya kaynağı olan medya bağlantı girdisini `HasStream` özniteliği.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Bu konudaki kalan örnekler erişmek ve medya kaynak akışı değiştirmek nasıl gösterir. Bir .NET Framework istemci uygulamasındaki bir ortam kaynak akışı kullanmalarını nasıl tam bir örnek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, post bkz [bir medya kaynak akışı istemciden erişme](http://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>İkili kaynak akışı erişme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı ikili kaynak akışlardan erişmek için yöntemler sağlayan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-tabanlı veri hizmeti. Ne zaman bir medya kaynağı indirme, medya kaynağı URI'sini ya da kullanabilir veya, bir ikili akış elde edebilirsiniz medya kaynak verilerini kendisini içerir. Ayrıca, ikili akış olarak medya kaynak verilerini karşıya yükleyebilir.  
  
> [!TIP]
>  Nasıl oluşturulacağı hakkında adım adım bir örneği için bir [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] ikili resim dosyalarını indirir istemci uygulaması bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fotoğrafları, depolayan hizmeti Bkz post [Veri Hizmetleri Akış sağlayıcısı serisi bölüm 2: bir ortama erişme Kaynak akışı istemciden](http://go.microsoft.com/fwlink/?LinkId=201637). Blog postasına öne çıkan akış fotoğraf veri hizmeti için örnek kod indirmek için bkz: [akış fotoğraf veri hizmeti örnek](http://go.microsoft.com/fwlink/?LinkId=198988) MSDN kod Galerisi'nden içinde.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>İkili akışın URI'sini alma  
 Belirli türde bir ortam kaynakları, resimleri ve diğer medya dosyaları gibi alınırken çoğu medya kaynağı URI'sini ikili veri akışı işleme daha, uygulamanızda kullanmak kolaydır. Bir medya bağlantısı girişle ile ilişkili bir kaynak akışı URI'sini almak için çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> varlık izleme örneği. Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> istemci üzerinde yeni bir görüntü oluşturmak için kullanılan bir medya kaynak akışı URI'sini almak için yöntemi:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>İkili kaynak akışı indirme  
 Bir ikili kaynak akışı alınırken çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> media link entry izleme örneği. Bu yöntem, döndüren veri hizmetine bir istek gönderir bir <xref:System.Data.Services.Client.DataServiceStreamResponse> kaynak içeren akışı başvuruyor nesnesi. Uygulamanız ikili kaynak olarak gerektirdiğinde bu yöntemi kullanın. bir <xref:System.IO.Stream>. Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yöntemi, istemci üzerinde yeni bir görüntü oluşturmak için kullanılan bir akış almak için:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Content-Length üstbilgisi ikili akış içeren yanıt iletisi veri hizmeti tarafından ayarlanmadı. Bu değer, ikili veri akışını gerçek uzunluğuyla yansıtmayabilir.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Bir akış olarak bir medya kaynağı karşıya  
 Eklemek veya bir medya kaynağı güncelleştirmek için arama <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> varlık izleme örneği. Bu yöntem, sağlanan akıştan okunan medya kaynağı içeren veri hizmeti için bir istek gönderir. Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi bir görüntü veri hizmetine göndermek için:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> değerini sağlayarak yöntemi çağrıldığında `true` için `closeStream` parametresi. Bu sayede <xref:System.Data.Services.Client.DataServiceContext> ikili veriler için veri hizmeti yüklendikten sonra akışı kapatır.  
  
> [!NOTE]
>  Çağırdığınızda <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, akış kadar veri hizmetine gönderilmez <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
