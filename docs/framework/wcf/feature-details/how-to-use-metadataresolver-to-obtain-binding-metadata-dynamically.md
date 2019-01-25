---
title: 'Nasıl yapılır: Dinamik olarak meta verilerini almak için MetadataResolver kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 9887f74902a1f324f57e39a61a48b5826127cba9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735980"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="f7582-102">Nasıl yapılır: Dinamik olarak meta verilerini almak için MetadataResolver kullanma</span><span class="sxs-lookup"><span data-stu-id="f7582-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="f7582-103">Bu konu nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.MetadataResolver> dinamik olarak bağlama meta verilerini almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f7582-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="f7582-104">Dinamik olarak bağlama meta verilerini almak için</span><span class="sxs-lookup"><span data-stu-id="f7582-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="f7582-105">Oluşturma bir <xref:System.ServiceModel.EndpointAddress> meta veri uç noktasının adresini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="f7582-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="f7582-106">Çağrı <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, hizmet türü ve meta veri uç noktası adresi geçirir.</span><span class="sxs-lookup"><span data-stu-id="f7582-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="f7582-107">Bu, belirtilen sözleşmesini uygulama uç noktaları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7582-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="f7582-108">Bağlama bilgileri meta verilerinden alınır; Sözleşme bilgi aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="f7582-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="f7582-109">Sağlanan sözleşmeyi yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7582-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="f7582-110">Ardından, ihtiyacınız olan bağlama bilgileri ayıklamak için hizmet uç noktaları koleksiyonu yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7582-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="f7582-111">Aşağıdaki kod, uç noktalar üzerinden yinelenir, bağlama ve geçerli uç nokta ile ilişkili adres geçen hizmet istemci nesnesi oluşturur ve ardından hizmet üzerinde bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f7582-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7582-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7582-112">See also</span></span>
- [<span data-ttu-id="f7582-113">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="f7582-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
