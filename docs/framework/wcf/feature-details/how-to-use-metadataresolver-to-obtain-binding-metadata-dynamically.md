---
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: dfa36c81bbeb70c1dd981ff91b4efb6d7c423a5c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991617"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma
Bu konuda, <xref:System.ServiceModel.Description.MetadataResolver> sınıfının bağlama meta verilerini dinamik olarak almak için nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Bağlama meta verilerini dinamik olarak almak için  
  
1. Meta veri <xref:System.ServiceModel.EndpointAddress> uç noktası adresiyle bir nesne oluşturun.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Hizmet <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>türü ve meta veri uç noktası adresinde geçen çağrı. Bu, belirtilen sözleşmeyi uygulayan bitiş noktaları koleksiyonunu döndürür. Meta verilerden yalnızca bağlama bilgileri içeri aktarılır; sözleşme bilgileri içeri aktarılmaz. Bunun yerine sağlanan sözleşme kullanılır.  
  
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

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
