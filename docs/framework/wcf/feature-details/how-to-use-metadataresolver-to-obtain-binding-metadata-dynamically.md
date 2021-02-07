---
description: 'Daha fazla bilgi edinin: nasıl yapılır: bağlama meta verilerini dinamik olarak almak için MetadataResolver kullanma'
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 00f33b31504ede6868113040ba83b6f9462ee808
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734288"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="72cd9-103">Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma</span><span class="sxs-lookup"><span data-stu-id="72cd9-103">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>

<span data-ttu-id="72cd9-104">Bu konuda, <xref:System.ServiceModel.Description.MetadataResolver> sınıfının bağlama meta verilerini dinamik olarak almak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72cd9-104">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="72cd9-105">Bağlama meta verilerini dinamik olarak almak için</span><span class="sxs-lookup"><span data-stu-id="72cd9-105">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="72cd9-106"><xref:System.ServiceModel.EndpointAddress>Meta veri uç noktası adresiyle bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="72cd9-106">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="72cd9-107"><xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>Hizmet türü ve meta veri uç noktası adresinde geçen çağrı.</span><span class="sxs-lookup"><span data-stu-id="72cd9-107">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="72cd9-108">Bu, belirtilen sözleşmeyi uygulayan bitiş noktaları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="72cd9-108">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="72cd9-109">Meta verilerden yalnızca bağlama bilgileri içeri aktarılır; sözleşme bilgileri içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="72cd9-109">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="72cd9-110">Bunun yerine sağlanan sözleşme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72cd9-110">The supplied contract is used instead.</span></span>  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="72cd9-111">Daha sonra, ihtiyacınız olan bağlama bilgilerini ayıklamak için hizmet uç noktaları koleksiyonunu yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72cd9-111">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="72cd9-112">Aşağıdaki kod uç noktalar üzerinden yinelenir, geçerli uç noktayla ilişkili bağlama ve adreste geçen bir hizmet istemci nesnesi oluşturur ve sonra hizmette bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="72cd9-112">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72cd9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72cd9-113">See also</span></span>

- [<span data-ttu-id="72cd9-114">Meta veri</span><span class="sxs-lookup"><span data-stu-id="72cd9-114">Metadata</span></span>](metadata.md)
