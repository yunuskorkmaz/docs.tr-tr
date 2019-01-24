---
title: 'Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: dc3a1d402a9f6ffb69c1f692800698609f9fa84b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603280"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="26b7d-102">Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="26b7d-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="26b7d-103">Svcutil.exe Hizmetleri çalışmasını meta verileri indirmek ve yerel dosyalar için meta verileri kaydetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b7d-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="26b7d-104">HTTP ve HTTPS URL'si düzenleri için Svcutil.exe WS-MetadataExchange kullanarak meta verilerini almayı dener ve [XML Web hizmeti bulma](https://go.microsoft.com/fwlink/?LinkId=94950).</span><span class="sxs-lookup"><span data-stu-id="26b7d-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="26b7d-105">Diğer tüm URL şemalarını için Svcutil.exe yalnızca WS-MetadataExchange kullanır.</span><span class="sxs-lookup"><span data-stu-id="26b7d-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="26b7d-106">Varsayılan olarak, içinde tanımlanan bağlamalardan Svcutil.exe kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="26b7d-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="26b7d-107">WS-MetadataExchange için kullanılan bağlama yapılandırmak için istemci uç nokta yapılandırma dosyasında kullanan Svcutil.exe için (svcutil.exe.config) tanımlamalısınız `IMetadataExchange` sözleşme ve, Tekdüzen Kaynak Tanımlayıcısı (URI) olarak aynı ada sahip meta veri uç noktası adresi düzeni.</span><span class="sxs-lookup"><span data-stu-id="26b7d-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="26b7d-108">İki farklı hizmet sunan bir hizmet için meta verileri almak için Svcutil.exe çalıştıran her içerir, aynı ada sahip bir işlem sözleşmeleri, Svcutil.exe "Meta verileri alınamıyor..." ifadesini içeren bir hata görüntüler. Örneğin, adında bir hizmet sözleşmesini gösteren bir hizmetiniz varsa `ICarService` bir işlem olan `Get(Car c)` aynı hizmet olarak adlandırılan bir hizmet sözleşmesini gösteren `IBookService` bir işlem olan `Get(Book b)`.</span><span class="sxs-lookup"><span data-stu-id="26b7d-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="26b7d-109">Bu sorunu geçici olarak çözmek için şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="26b7d-109">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="26b7d-110">İşlemlerden birini yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="26b7d-110">Rename one of the operations.</span></span>
> - <span data-ttu-id="26b7d-111">Ayarlama <xref:System.ServiceModel.OperationContractAttribute.Name%2A> için farklı bir ad.</span><span class="sxs-lookup"><span data-stu-id="26b7d-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="26b7d-112">İşlemleri ad alanlarından birini kullanarak farklı bir ad alanı için ayarlanmış <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="26b7d-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="26b7d-113">Svcutil.exe kullanarak meta verileri indirilemedi</span><span class="sxs-lookup"><span data-stu-id="26b7d-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="26b7d-114">Şu konumda Svcutil.exe aracını bulun:</span><span class="sxs-lookup"><span data-stu-id="26b7d-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="26b7d-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="26b7d-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="26b7d-116">Komut isteminde, aşağıdaki biçimi kullanarak aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="26b7d-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="26b7d-117">Belirtmelisiniz `/t:metadata` seçeneği meta verileri indirilemedi.</span><span class="sxs-lookup"><span data-stu-id="26b7d-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="26b7d-118">Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="26b7d-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="26b7d-119"><`url`> Bağımsız değişkeni, meta veri sağlayan bir hizmet uç noktası ya da çevrimiçi barındırılan bir meta veri belgesinin URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26b7d-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="26b7d-120"><`epr`> Bağımsız değişkeni, WS-Addressing içeren bir XML dosyasının yolunu belirtir `EndpointAddress` WS-MetadataExchange destekleyen bir hizmet uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="26b7d-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="26b7d-121">Meta verileri indirme için bu aracı kullanma hakkında daha fazla seçenek için bkz: [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="26b7d-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26b7d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="26b7d-122">Example</span></span>  
 <span data-ttu-id="26b7d-123">Aşağıdaki komut, meta veri belgelerini çalışan bir hizmetten indirir.</span><span class="sxs-lookup"><span data-stu-id="26b7d-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="26b7d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26b7d-124">See also</span></span>
- [<span data-ttu-id="26b7d-125">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="26b7d-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
