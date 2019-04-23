---
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 3fe09699304de42ed00312f50f3b9e0edb20615d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298935"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma
Bu konu nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.MetadataResolver> dinamik olarak bağlama meta verilerini almak için sınıf.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Dinamik olarak bağlama meta verilerini almak için  
  
1. Oluşturma bir <xref:System.ServiceModel.EndpointAddress> meta veri uç noktasının adresini içeren nesne.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Çağrı <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, hizmet türü ve meta veri uç noktası adresi geçirir. Bu, belirtilen sözleşmesini uygulama uç noktaları koleksiyonunu döndürür. Bağlama bilgileri meta verilerinden alınır; Sözleşme bilgi aktarılmaz. Sağlanan sözleşmeyi yerine kullanılır.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Ardından, ihtiyacınız olan bağlama bilgileri ayıklamak için hizmet uç noktaları koleksiyonu yineleyebilirsiniz. Aşağıdaki kod, uç noktalar üzerinden yinelenir, bağlama ve geçerli uç nokta ile ilişkili adres geçen hizmet istemci nesnesi oluşturur ve ardından hizmet üzerinde bir yöntemi çağırır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
