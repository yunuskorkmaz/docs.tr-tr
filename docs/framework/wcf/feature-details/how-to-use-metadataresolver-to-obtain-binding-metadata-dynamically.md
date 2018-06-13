---
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: cffe47f301c1943a0d97e3a95a5b7c24979b4f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490685"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="4d184-102">Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma</span><span class="sxs-lookup"><span data-stu-id="4d184-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="4d184-103">Bu konuda nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.MetadataResolver> dinamik olarak bağlama meta verilerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4d184-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="4d184-104">Dinamik olarak bağlama meta verilerini almak için</span><span class="sxs-lookup"><span data-stu-id="4d184-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="4d184-105">Oluşturma bir <xref:System.ServiceModel.EndpointAddress> meta veri uç noktasının adresine sahip nesne.</span><span class="sxs-lookup"><span data-stu-id="4d184-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="4d184-106">Çağrı <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, hizmet türü ve meta veri uç noktası adresi geçirir.</span><span class="sxs-lookup"><span data-stu-id="4d184-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="4d184-107">Belirtilen sözleşmesini uygulama uç noktaları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d184-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="4d184-108">Yalnızca bağlama bilgileri meta verileri içe aktarılır; Sözleşme bilgilerini içe aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="4d184-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="4d184-109">Sağlanan sözleşme yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d184-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="4d184-110">Gereksinim duyduğunuz bağlama bilgileri ayıklamak için hizmet uç noktaları toplulukta sonra yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d184-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="4d184-111">Aşağıdaki kod uç noktaları yoluyla tekrarlanan, bağlama ve geçerli uç noktasıyla ilişkili adresi aktardığı hizmeti istemci nesnesi oluşturur ve ardından hizmette bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4d184-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d184-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d184-112">See Also</span></span>  
 [<span data-ttu-id="4d184-113">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="4d184-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
