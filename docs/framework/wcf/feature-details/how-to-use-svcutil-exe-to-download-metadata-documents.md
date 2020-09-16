---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
description: Çalışan hizmetlerden meta verileri indirmek için Svcutil.exe kullanmayı ve meta verileri yerel dosyalara kaydetmeyi öğrenin.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 6877d860a4465947268d6535b9edeb9856d4d689
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554312"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Svcutil.exe kullanarak, çalışan hizmetlerden meta verileri indirebilir ve meta verileri yerel dosyalara kaydedebilirsiniz. HTTP ve HTTPS URL şemaları için, Svcutil.exe WS-MetadataExchange ve [XML Web hizmeti bulma](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))kullanarak meta verileri almaya çalışır. Diğer tüm URL şemaları için Svcutil.exe yalnızca WS-MetadataExchange kullanır.  
  
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
