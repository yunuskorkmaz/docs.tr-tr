---
title: "Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 102b605b0b985d433092482cf55b0994c33d58ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma
Meta Veri Hizmetleri çalıştıran indirmek ve meta veriler için yerel dosyaları kaydetmek için Svcutil.exe kullanabilirsiniz. WS-MetadataExchange kullanarak meta verilerini almak HTTP ve HTTPS URL'si şemaları için Svcutil.exe çalışır ve [XML Web hizmeti bulma](http://go.microsoft.com/fwlink/?LinkId=94950). Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-MetadataExchange kullanır.  
  
 Varsayılan olarak tanımlanan bağlamaları Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı. WS-MetadataExchange için kullanılan bağlama yapılandırmak için istemci uç nokta yapılandırma dosyasında kullanan Svcutil.exe için (svcutil.exe.config) tanımlamanız gerekir `IMetadataExchange` sözleşme ve, Tekdüzen Kaynak Tanımlayıcısı (URI) olarak aynı ada sahip meta veri uç noktası adresi düzeni.  
  
> [!CAUTION]
>  İki farklı hizmet sunan bir hizmet için meta verilerini almak için Svcutil.exe çalıştıran her içeren, aynı ada sahip bir işlem sözleşmeler, Svcutil.exe "Meta verileri elde edemiyor..." belirten, bir hata görüntüler Örneğin, adlı bir hizmet sözleşmesini kullanıma sunan bir hizmetiniz varsa bir işlem var ICarService alın (Car c) ve bir işlemin Get (defteri b) olan IBookService adlı bir hizmet sözleşmesini aynı hizmeti sunar. Bu sorunu çözmek için şunlardan birini yapın:  
>   
>  -   İşlemlerden birini yeniden adlandırın  
> -   Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.  
> -   İşlemler ad alanlarından birini kullanılarak farklı bir ad alanı olarak ayarlanan <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Meta veri svcutil.exe kullanarak yüklemek için  
  
1.  Svcutil.exe aracı şu konumda bulun:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Belirtmeniz gerekir `/t:metadata` seçeneği meta verilerini indirebilirsiniz. Aksi durumda, istemci kodu ve yapılandırma oluşturulur.  
  
3.  <`url`> Bağımsız değişkeni meta verisi sağlayan bir hizmet uç noktası veya çevrimiçi barındırılan bir meta veri belgesi için URL'yi belirtir. <`epr`> Bağımsız değişkeni bir WS-adresleme içeren bir XML dosyası yolunu belirtir `EndpointAddress` WS-MetadataExchange destekleyen bir hizmet uç noktası için.  
  
 Bu aracı için meta veriler indirme kullanma hakkında daha fazla seçenek için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut çalışan bir hizmetten meta veri belgelerini indirir.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
