---
title: 'Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma'
description: Çalışan hizmetlerden meta verileri indirmek için Svcutil.exe kullanmayı ve meta verileri yerel dosyalara kaydetmeyi öğrenin.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246772"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="40944-103">Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="40944-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="40944-104">Svcutil.exe kullanarak, çalışan hizmetlerden meta verileri indirebilir ve meta verileri yerel dosyalara kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40944-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="40944-105">HTTP ve HTTPS URL şemaları için, Svcutil.exe WS-MetadataExchange ve [XML Web hizmeti bulma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))kullanarak meta verileri almaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="40944-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="40944-106">Diğer tüm URL şemaları için Svcutil.exe yalnızca WS-MetadataExchange kullanır.</span><span class="sxs-lookup"><span data-stu-id="40944-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="40944-107">Varsayılan olarak, Svcutil.exe sınıfında tanımlanan bağlamaları kullanır <xref:System.ServiceModel.Description.MetadataExchangeBindings> .</span><span class="sxs-lookup"><span data-stu-id="40944-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="40944-108">WS-MetadataExchange için kullanılan bağlamayı yapılandırmak için, `IMetadataExchange` sözleşmeyi kullanan ve meta veri uç noktası adresinin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle aynı ada sahip Svcutil.exe (svcutil.exe.config) için yapılandırma dosyasında bir istemci uç noktası tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40944-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="40944-109">Her birinde aynı ada sahip bir işlem içeren iki farklı hizmet sözleşmesi sunan bir hizmetin meta verilerini almak üzere Svcutil.exe çalıştırılırken Svcutil.exe, "meta veriler alınamıyor...." ifadesini bildiren bir hata görüntüler. Örneğin, bir işlemi olan adlı bir hizmet sözleşmesini sunan bir hizmetiniz varsa `ICarService` `Get(Car c)` ve aynı hizmet, bir işlemi olan adlı bir hizmet sözleşmesini kullanıma sunar `IBookService` `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="40944-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="40944-110">Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="40944-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="40944-111">İşlemlerden birini yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="40944-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="40944-112">Öğesini <xref:System.ServiceModel.OperationContractAttribute.Name%2A> farklı bir ada ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40944-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="40944-113">Operations ' ad alanlarından birini özelliği kullanarak farklı bir ad alanına ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="40944-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="40944-114">Svcutil.exe kullanarak meta verileri indirmek için</span><span class="sxs-lookup"><span data-stu-id="40944-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="40944-115">Svcutil.exe aracını aşağıdaki konumda bulun:</span><span class="sxs-lookup"><span data-stu-id="40944-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="40944-116">C:\Program Files\Microsoft Sdks\windows\v1.0/\Bin</span><span class="sxs-lookup"><span data-stu-id="40944-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="40944-117">Komut isteminde, aşağıdaki biçimi kullanarak aracı başlatın.</span><span class="sxs-lookup"><span data-stu-id="40944-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="40944-118">`/t:metadata`Meta verileri indirme seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="40944-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="40944-119">Aksi takdirde, istemci kodu ve yapılandırma oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="40944-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="40944-120"><`url`>bağımsız değişkeni, çevrimiçi olarak barındırılan meta verileri veya bir meta veri belgesini sağlayan bir hizmet uç noktasının URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40944-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="40944-121"><`epr`> bağımsız değişkeni, `EndpointAddress` WS-MetadataExchange ' i destekleyen bir hizmet uç noktası için ws-Addressing IÇEREN bir XML dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="40944-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="40944-122">Bu aracı meta verilerin indirilmesi için kullanma hakkında daha fazla seçenek için bkz. [ServiceModel Metadata Utility aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="40944-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40944-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="40944-123">Example</span></span>  
 <span data-ttu-id="40944-124">Aşağıdaki komut, çalışan bir hizmetten meta veri belgelerini indirir.</span><span class="sxs-lookup"><span data-stu-id="40944-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="40944-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40944-125">See also</span></span>

- [<span data-ttu-id="40944-126">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="40944-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
