---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
description: Çalışan hizmetlerden meta verileri indirmek için Svcutil.exe kullanmayı ve meta verileri yerel dosyalara kaydetmeyi öğrenin.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246772"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Svcutil.exe kullanarak, çalışan hizmetlerden meta verileri indirebilir ve meta verileri yerel dosyalara kaydedebilirsiniz. HTTP ve HTTPS URL şemaları için, Svcutil.exe WS-MetadataExchange ve [XML Web hizmeti bulma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için Svcutil.exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak, Svcutil.exe sınıfında tanımlanan bağlamaları kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> . WS-MetadataExchange için kullanılan bağlamayı yapılandırmak için, `IMetadataExchange` sözleşmeyi kullanan ve meta veri uç noktası adresinin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle aynı ada sahip Svcutil.exe (svcutil.exe.config) için yapılandırma dosyasında bir istemci uç noktası tanımlamanız gerekir.  
  
> [!CAUTION]
> Her birinde aynı ada sahip bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmetin meta verilerini almak üzere Svcutil.exe çalıştırılırken Svcutil.exe, "meta veriler alınamıyor...." ifadesini bildiren bir hata görüntüler. Örneğin, bir işlemi olan adlı bir hizmet sözleşmesini sunan bir hizmetiniz varsa `ICarService` `Get(Car c)` ve aynı hizmet, bir işlemi olan adlı bir hizmet sözleşmesini kullanıma sunar `IBookService` `Get(Book b)` . Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:
>
> - İşlemlerden birini yeniden adlandırın.
> - Öğesini <xref:System.ServiceModel.OperationContractAttribute.Name%2A> farklı bir ada ayarlayın.
> - Operations ' ad alanlarından birini özelliği kullanarak farklı bir ad alanına ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe kullanarak meta verileri indirmek için  
  
1. Svcutil.exe aracını aşağıdaki konumda bulun:  
  
     C:\Program Files\Microsoft Sdks\windows\v1.0/\Bin  
  
2. Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     `/t:metadata`Meta verileri indirme seçeneğini belirtmeniz gerekir. Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.  
  
3. <`url`>bağımsız değişkeni, çevrimiçi olarak barındırılan meta verileri veya bir meta veri belgesini sağlayan bir hizmet uç noktasının URL 'sini belirtir. <`epr`> bağımsız değişkeni, `EndpointAddress` WS-MetadataExchange ' i destekleyen bir hizmet uç noktası için ws-Addressing IÇEREN bir XML dosyasının yolunu belirtir.  
  
 Bu aracı meta verilerin indirilmesi için kullanma hakkında daha fazla seçenek için bkz. [ServiceModel Metadata Utility aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, çalışan bir hizmetten meta veri belgelerini indirir.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
