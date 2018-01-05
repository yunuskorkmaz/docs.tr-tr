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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 571465ab483aef3e3e663b9f82974f35e100c73e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="6e77f-102">Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="6e77f-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="6e77f-103">Meta Veri Hizmetleri çalıştıran indirmek ve meta veriler için yerel dosyaları kaydetmek için Svcutil.exe kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e77f-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="6e77f-104">WS-MetadataExchange kullanarak meta verilerini almak HTTP ve HTTPS URL'si şemaları için Svcutil.exe çalışır ve [XML Web hizmeti bulma](http://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="6e77f-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="6e77f-105">Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-MetadataExchange kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e77f-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="6e77f-106">Varsayılan olarak tanımlanan bağlamaları Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6e77f-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="6e77f-107">WS-MetadataExchange için kullanılan bağlama yapılandırmak için istemci uç nokta yapılandırma dosyasında kullanan Svcutil.exe için (svcutil.exe.config) tanımlamanız gerekir `IMetadataExchange` sözleşme ve, Tekdüzen Kaynak Tanımlayıcısı (URI) olarak aynı ada sahip meta veri uç noktası adresi düzeni.</span><span class="sxs-lookup"><span data-stu-id="6e77f-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6e77f-108">İki farklı hizmet sunan bir hizmet için meta verilerini almak için Svcutil.exe çalıştıran her içeren, aynı ada sahip bir işlem sözleşmeler, Svcutil.exe "Meta verileri elde edemiyor..." belirten, bir hata görüntüler Örneğin, adlı bir hizmet sözleşmesini kullanıma sunan bir hizmetiniz varsa bir işlem var ICarService alın (Car c) ve bir işlemin Get (defteri b) olan IBookService adlı bir hizmet sözleşmesini aynı hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="6e77f-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="6e77f-109">Bu sorunu çözmek için şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="6e77f-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="6e77f-110">İşlemlerden birini yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="6e77f-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="6e77f-111">Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.</span><span class="sxs-lookup"><span data-stu-id="6e77f-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="6e77f-112">İşlemler ad alanlarından birini kullanılarak farklı bir ad alanı olarak ayarlanan <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6e77f-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="6e77f-113">Meta veri svcutil.exe kullanarak yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6e77f-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="6e77f-114">Svcutil.exe aracı şu konumda bulun:</span><span class="sxs-lookup"><span data-stu-id="6e77f-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="6e77f-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="6e77f-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="6e77f-116">Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.</span><span class="sxs-lookup"><span data-stu-id="6e77f-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="6e77f-117">Belirtmeniz gerekir `/t:metadata` seçeneği meta verilerini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e77f-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="6e77f-118">Aksi durumda, istemci kodu ve yapılandırma oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6e77f-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="6e77f-119"><`url`> Bağımsız değişkeni meta verisi sağlayan bir hizmet uç noktası veya çevrimiçi barındırılan bir meta veri belgesi için URL'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e77f-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="6e77f-120"><`epr`> Bağımsız değişkeni bir WS-adresleme içeren bir XML dosyası yolunu belirtir `EndpointAddress` WS-MetadataExchange destekleyen bir hizmet uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="6e77f-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="6e77f-121">Bu aracı için meta veriler indirme kullanma hakkında daha fazla seçenek için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6e77f-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e77f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e77f-122">Example</span></span>  
 <span data-ttu-id="6e77f-123">Aşağıdaki komut çalışan bir hizmetten meta veri belgelerini indirir.</span><span class="sxs-lookup"><span data-stu-id="6e77f-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e77f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e77f-124">See Also</span></span>  
 [<span data-ttu-id="6e77f-125">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6e77f-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
