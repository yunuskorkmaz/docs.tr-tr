---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 359cdb58ef65c9fb69c0ecfc759f70164a369cce
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212108"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Çalışan hizmetlerden meta verileri indirmek ve meta verileri yerel dosyalara kaydetmek için Svcutil. exe ' yi kullanabilirsiniz. HTTP ve HTTPS URL şemaları için, Svcutil. exe, WS-MetadataExchange ve [XML Web hizmeti bulma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için, Svcutil. exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak, Svcutil. exe <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfında tanımlanan bağlamaları kullanır. WS-MetadataExchange için kullanılan bağlamayı yapılandırmak için, `IMetadataExchange` sözleşmesini kullanan ve meta veri uç noktası adresinin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle aynı ada sahip olan Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasında bir istemci uç noktası tanımlamanız gerekir.  
  
> [!CAUTION]
> Her biri aynı adda bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmetin meta verilerini almak üzere Svcutil. exe dosyasını çalıştırırken, Svcutil. exe bir hata görüntüler, "meta veriler alınamıyor...." Örneğin, bir işlem `Get(Car c)` olan `ICarService` adlı bir hizmet sözleşmesini kullanıma sunan bir hizmetiniz varsa ve aynı hizmet bir işlem `Get(Book b)``IBookService` adlı bir hizmet sözleşmesini kullanıma sunar. Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:
>
> - İşlemlerden birini yeniden adlandırın.
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> farklı bir ada ayarlayın.
> - Operations ' ad alanlarından birini <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliğini kullanarak farklı bir ad alanına ayarlayın.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil. exe kullanarak meta verileri indirmek için  
  
1. Aşağıdaki konumda Svcutil. exe aracını bulun:  
  
     C:\Program Files\Microsoft Sdks\windows\v1.0/\Bin  
  
2. Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Meta verileri indirmek için `/t:metadata` seçeneğini belirtmeniz gerekir. Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.  
  
3. <`url`> bağımsız değişkeni, çevrimiçi olarak barındırılan meta verileri veya bir meta veri belgesini sağlayan bir hizmet uç noktasının URL 'sini belirtir. `epr`> bağımsız değişkeni, WS-MetadataExchange ' i destekleyen bir hizmet uç noktası için WS-Addressing `EndpointAddress` içeren bir XML dosyasının yolunu belirtir.  
  
 Bu aracı meta verilerin indirilmesi için kullanma hakkında daha fazla seçenek için bkz. [ServiceModel Metadata Utility aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, çalışan bir hizmetten meta veri belgelerini indirir.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
