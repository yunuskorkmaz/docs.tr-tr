---
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 98fe4977f270b008c51039af19261ca86b8d6642
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601133"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma
Bu konuda, <xref:System.ServiceModel.Description.MetadataResolver> sınıfının bağlama meta verilerini dinamik olarak almak için nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Bağlama meta verilerini dinamik olarak almak için  
  
1. <xref:System.ServiceModel.EndpointAddress>Meta veri uç noktası adresiyle bir nesne oluşturun.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>Hizmet türü ve meta veri uç noktası adresinde geçen çağrı. Bu, belirtilen sözleşmeyi uygulayan bitiş noktaları koleksiyonunu döndürür. Meta verilerden yalnızca bağlama bilgileri içeri aktarılır; sözleşme bilgileri içeri aktarılmaz. Bunun yerine sağlanan sözleşme kullanılır.  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Daha sonra, ihtiyacınız olan bağlama bilgilerini ayıklamak için hizmet uç noktaları koleksiyonunu yineleyebilirsiniz. Aşağıdaki kod uç noktalar üzerinden yinelenir, geçerli uç noktayla ilişkili bağlama ve adreste geçen bir hizmet istemci nesnesi oluşturur ve sonra hizmette bir yöntemi çağırır.  
  
    ```csharp  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](metadata.md)
