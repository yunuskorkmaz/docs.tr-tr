---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: cc9fc4acaeafe4583b1e85a24cab97af1689c638
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328354"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Svcutil.exe Hizmetleri çalışmasını meta verileri indirmek ve yerel dosyalar için meta verileri kaydetmek için kullanabilirsiniz. HTTP ve HTTPS URL'si düzenleri için Svcutil.exe WS-MetadataExchange kullanarak meta verilerini almayı dener ve [XML Web hizmeti bulma](https://go.microsoft.com/fwlink/?LinkId=94950). Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak, içinde tanımlanan bağlamalardan Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı. WS-MetadataExchange için kullanılan bağlama yapılandırmak için istemci uç nokta yapılandırma dosyasında kullanan Svcutil.exe için (svcutil.exe.config) tanımlamalısınız `IMetadataExchange` sözleşme ve, Tekdüzen Kaynak Tanımlayıcısı (URI) olarak aynı ada sahip meta veri uç noktası adresi düzeni.  
  
> [!CAUTION]
> İki farklı hizmet sunan bir hizmet için meta verileri almak için Svcutil.exe çalıştıran her içerir, aynı ada sahip bir işlem sözleşmeleri, Svcutil.exe "Meta verileri alınamıyor..." ifadesini içeren bir hata görüntüler. Örneğin, adında bir hizmet sözleşmesini gösteren bir hizmetiniz varsa `ICarService` bir işlem olan `Get(Car c)` aynı hizmet olarak adlandırılan bir hizmet sözleşmesini gösteren `IBookService` bir işlem olan `Get(Book b)`. Bu sorunu geçici olarak çözmek için şunlardan birini yapın:
>
> - İşlemlerden birini yeniden adlandırın.
> - Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.
> - İşlemleri ad alanlarından birini kullanarak farklı bir ad alanı için ayarlanmış <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe kullanarak meta verileri indirilemedi  
  
1. Şu konumda Svcutil.exe aracını bulun:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. Komut isteminde, aşağıdaki biçimi kullanarak aracını başlatın.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Belirtmelisiniz `/t:metadata` seçeneği meta verileri indirilemedi. Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.  
  
3. <`url`> Bağımsız değişkeni, meta veri sağlayan bir hizmet uç noktası ya da çevrimiçi barındırılan bir meta veri belgesinin URL'sini belirtir. <`epr`> Bağımsız değişkeni, WS-Addressing içeren bir XML dosyasının yolunu belirtir `EndpointAddress` WS-MetadataExchange destekleyen bir hizmet uç noktası için.  
  
 Meta verileri indirme için bu aracı kullanma hakkında daha fazla seçenek için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, meta veri belgelerini çalışan bir hizmetten indirir.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
