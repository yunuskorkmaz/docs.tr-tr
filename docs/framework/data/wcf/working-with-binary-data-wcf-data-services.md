---
title: İkili verileri (WCF Veri Hizmetleri) ile çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 82a773623c1941320aa155dd5bd937d318c1238a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170332"
---
# <a name="working-with-binary-data-wcf-data-services"></a>İkili verileri (WCF Veri Hizmetleri) ile çalışma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı sağlar, almak ve ikili verileri güncelleştirmek bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] aşağıdaki yollardan biriyle akış:  
  
-   Varlık bir basit tür özelliği. Kolayca belleğe yüklenebilen nesneleri küçük ikili verilerle çalışma için önerilen yöntem budur. Bu durumda, veri modeli tarafından ortaya konan bir varlık özelliği ikili özelliğidir ve veri hizmeti yanıt iletisinde base-64 ikili kodlanan XML olarak ikili verileri serileştirir.  
  
-   Ayrı ikili kaynak akışı. Erişme ve fotoğraf, video veya başka türde bir kodlanmış ikili verileri temsil edebilir ikili büyük nesne (BLOB) verilerin değiştirilmesi için önerilen yöntem budur.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sınıfında tanımlandığı gibi HTTP kullanarak ikili verilerin akış uygulayan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Bu mekanizma ikili veri hesaplarından ayrı bir medya kaynağı olarak işlem görür ancak medya bağlantısı girişinin çağrılan bir varlıkla ilgili. Daha fazla bilgi için [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  İkili resim dosyaları indirir bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturmak adım adım bir örnek bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fotoğraf depolayan hizmet gönderisine bakın [Veri Hizmetleri Akış sağlayıcısı serisi-bölüm 2: İstemciden bir medya kaynağı Stream erişme](https://go.microsoft.com/fwlink/?LinkId=201637). Öne çıkan blog gönderisinde stream fotoğraf veri hizmeti için örnek kodu indirmek için bkz [akış fotoğraf veri hizmeti örneği](https://go.microsoft.com/fwlink/?LinkId=198988) MSDN kod Galerisi'ndeki.  
  
## <a name="entity-metadata"></a>Varlık meta verileri  
 İlgili medya kaynak akışı olan bir varlık veri hizmeti meta verileri tarafından belirtilen `HasStream` özniteliği uygulandı, medya bağlantısı girişinin bir varlık türü. Aşağıdaki örnekte, `PhotoInfo` varlıktır tarafından belirtilen ilgili medya kaynağına sahip bir medya bağlantısı girişinin `HasStream` özniteliği.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Kalan örnekler bölümüne erişme ve medya kaynak akışı değiştirme işlemini göstermektedir. Tam bir örnek bir .NET Framework istemci uygulamasındaki bir ortam kaynak akışı yardımıyla nasıl [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı gönderiye bakın [istemciden bir medya kaynağı Stream erişme](https://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>İkili kaynak Stream erişme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı ikili kaynak akışlardan erişmek için yöntemler sağlar bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-temel veri hizmeti. Ne zaman bir medya kaynağı indirirken, medya kaynağın URI'sini ya da kullanabilirsiniz veya ikili akışa alabilirsiniz, medya kaynak verileri kendisini içerir. Bir ikili akış olarak da medya kaynak verileri karşıya yükleyebilirsiniz.  
  
> [!TIP]
>  İkili resim dosyaları indirir bir Windows Presentation Foundation (WPF) istemci uygulaması oluşturmak adım adım bir örnek bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fotoğraf depolayan hizmet gönderisine bakın [Veri Hizmetleri Akış sağlayıcısı serisi-bölüm 2: İstemciden bir medya kaynağı Stream erişme](https://go.microsoft.com/fwlink/?LinkId=201637). Öne çıkan blog gönderisinde stream fotoğraf veri hizmeti için örnek kodu indirmek için bkz [akış fotoğraf veri hizmeti örneği](https://go.microsoft.com/fwlink/?LinkId=198988) MSDN kod Galerisi'ndeki.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>İkili Stream URI'sini alma  
 Belirli türdeki resimler ve diğer medya dosyaları gibi medya kaynağı alınırken genellikle ikili veri akışı işleme daha uygulamanızdaki medya kaynağın URI'sini kullanımı daha kolay olur. Bir medya bağlantısı girişle ile ilişkili bir kaynak akışı URI'sini almak için çağırmalıdır <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> varlık izleme örneği. Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> istemcide yeni bir görüntü oluşturmak için kullanılan bir medya kaynak akışı URI'sini almak için yöntemi:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>İkili kaynak Stream indiriliyor  
 Bir ikili kaynak akışı alınırken çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> media link entry izleme örneği. Bu yöntem, döndüren veri hizmetine bir istek gönderir. bir <xref:System.Data.Services.Client.DataServiceStreamResponse> başvuru kaynağı içeren akış olan nesne. Uygulamanız ikili bir kaynak olarak gerektirdiğinde bu yöntemi kullanın. bir <xref:System.IO.Stream>. Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> yönteminin istemci üzerinde yeni bir görüntü oluşturmak için kullanılan bir akışa almak için:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  Content-Length üst bilgisinde ikili akış içeren yanıt iletisi, veri hizmeti tarafından ayarlanmadı. Bu değer, ikili veri akışını gerçek uzunluğunu yansıtmayabilir.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Bir medya kaynağı bir Stream karşıya yükleme  
 Ekleme veya bir medya kaynağı güncelleştirmek için çağrı <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> varlık izleme örneği. Bu yöntem, sağlanan akıştan okunan medya kaynağı içeren veri hizmetine bir istek gönderir. Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> yöntemi bir görüntü veri hizmetine göndermek için:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> değeri sağlanarak yöntemi çağrıldığında `true` için `closeStream` parametresi. Bu garanti <xref:System.Data.Services.Client.DataServiceContext> ikili veri verileri hizmete yüklendikten sonra akışı kapatır.  
  
> [!NOTE]
>  Çağırdığınızda <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, akış kadar veri hizmetine gönderilmez <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Veriyi Denetimlere Bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
