---
title: "Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8f3d8245b9d5bf05297b4d1edfba1926d2104ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma
Bu konuda nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.MetadataResolver> dinamik olarak bağlama meta verilerini almak için sınıf.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Dinamik olarak bağlama meta verilerini almak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.EndpointAddress> meta veri uç noktasının adresine sahip nesne.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Çağrı <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, hizmet türü ve meta veri uç noktası adresi geçirir. Belirtilen sözleşmesini uygulama uç noktaları koleksiyonunu döndürür. Yalnızca bağlama bilgileri meta verileri içe aktarılır; Sözleşme bilgilerini içe aktarılmaz. Sağlanan sözleşme yerine kullanılır.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Gereksinim duyduğunuz bağlama bilgileri ayıklamak için hizmet uç noktaları toplulukta sonra yineleyebilirsiniz. Aşağıdaki kod uç noktaları yoluyla tekrarlanan, bağlama ve geçerli uç noktasıyla ilişkili adresi aktardığı hizmeti istemci nesnesi oluşturur ve ardından hizmette bir yöntemi çağırır.  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
