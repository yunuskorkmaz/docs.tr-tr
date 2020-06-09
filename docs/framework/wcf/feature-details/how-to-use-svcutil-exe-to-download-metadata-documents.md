---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: c04b63fa4963a5df0f910da8702643a6484a4edd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596935"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Çalışan hizmetlerden meta verileri indirmek ve meta verileri yerel dosyalara kaydetmek için Svcutil. exe ' yi kullanabilirsiniz. HTTP ve HTTPS URL şemaları için, Svcutil. exe, WS-MetadataExchange ve [XML Web hizmeti bulma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için, Svcutil. exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak, Svcutil. exe sınıfında tanımlanan bağlamaları kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> . WS-MetadataExchange için kullanılan bağlamayı yapılandırmak için, sözleşmeyi kullanan Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasında, `IMetadataExchange` meta veri uç noktası adresinin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle aynı ada sahip bir istemci uç noktası tanımlamanız gerekir.  
  
> [!CAUTION]
> Her biri aynı adda bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmetin meta verilerini almak üzere Svcutil. exe dosyasını çalıştırırken, Svcutil. exe bir hata görüntüler, "meta veriler alınamıyor...." Örneğin, bir işlemi olan adlı bir hizmet sözleşmesini sunan bir hizmetiniz varsa `ICarService` `Get(Car c)` ve aynı hizmet, bir işlemi olan adlı bir hizmet sözleşmesini kullanıma sunar `IBookService` `Get(Book b)` . Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:
>
> - İşlemlerden birini yeniden adlandırın.
> - Öğesini <xref:System.ServiceModel.OperationContractAttribute.Name%2A> farklı bir ada ayarlayın.
> - Operations ' ad alanlarından birini özelliği kullanarak farklı bir ad alanına ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil. exe kullanarak meta verileri indirmek için  
  
1. Aşağıdaki konumda Svcutil. exe aracını bulun:  
  
     C:\Program Files\Microsoft Sdks\windows\v1.0/\Bin  
  
2. Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     `/t:metadata`Meta verileri indirme seçeneğini belirtmeniz gerekir. Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.  
  
3. <`url`>bağımsız değişkeni, çevrimiçi olarak barındırılan meta verileri veya bir meta veri belgesini sağlayan bir hizmet uç noktasının URL 'sini belirtir. <`epr`> bağımsız değişkeni, `EndpointAddress` WS-MetadataExchange ' i destekleyen bir hizmet uç noktası için ws-Addressing IÇEREN bir XML dosyasının yolunu belirtir.  
  
 Bu aracı meta verilerin indirilmesi için kullanma hakkında daha fazla seçenek için bkz. [ServiceModel Metadata Utility aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, çalışan bir hizmetten meta veri belgelerini indirir.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
