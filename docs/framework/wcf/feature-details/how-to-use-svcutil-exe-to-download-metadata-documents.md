---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991608"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Çalışan hizmetlerden meta verileri indirmek ve meta verileri yerel dosyalara kaydetmek için Svcutil. exe ' yi kullanabilirsiniz. HTTP ve HTTPS URL şemaları için, Svcutil. exe, WS-MetadataExchange ve [XML Web hizmeti bulma](https://go.microsoft.com/fwlink/?LinkId=94950)kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için, Svcutil. exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak, Svcutil. exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfında tanımlanan bağlamaları kullanır. WS-MetadataExchange için kullanılan bağlamayı yapılandırmak için, `IMetadataExchange` sözleşmeyi kullanan ve Tekdüzen Kaynak tanımlayıcısı (URI) ile aynı ada sahip olan Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasında bir istemci uç noktası tanımlamanız gerekir meta veri uç noktası adresinin şeması.  
  
> [!CAUTION]
> Her biri aynı adda bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmetin meta verilerini almak üzere Svcutil. exe dosyasını çalıştırırken, Svcutil. exe bir hata görüntüler, "meta veriler alınamıyor...." `ICarService` Örneğin, bir işlemi `Get(Car c)` olan adlı bir hizmet sözleşmesini sunan bir hizmetiniz varsa ve aynı hizmet, bir işlemi `Get(Book b)`olan adlı `IBookService` bir hizmet sözleşmesini kullanıma sunar. Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:
>
> - İşlemlerden birini yeniden adlandırın.
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> Öğesini farklı bir ada ayarlayın.
> - Operations ' ad alanlarından birini <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği kullanarak farklı bir ad alanına ayarlayın.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil. exe kullanarak meta verileri indirmek için  
  
1. Aşağıdaki konumda Svcutil. exe aracını bulun:  
  
     C:\Program Files\Microsoft Sdks\windows\v1.0/\Bin  
  
2. Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Meta verileri indirme `/t:metadata` seçeneğini belirtmeniz gerekir. Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.  
  
3. <`url`> Bağımsız değişkeni, çevrimiçi olarak barındırılan meta verileri veya bir meta veri belgesini sağlayan bir hizmet uç noktasının URL 'sini belirtir. <`epr`> Bağımsız değişkeni, WS-MetadataExchange ' i destekleyen bir hizmet uç noktası için WS `EndpointAddress` -Addressing içeren bir XML dosyasının yolunu belirtir.  
  
 Bu aracı meta verilerin indirilmesi için kullanma hakkında daha fazla seçenek için bkz. [ServiceModel Metadata Utility aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, çalışan bir hizmetten meta veri belgelerini indirir.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
