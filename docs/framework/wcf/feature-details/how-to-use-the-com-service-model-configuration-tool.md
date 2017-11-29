---
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 71d4a08f46578e185e7e6cde9e6c77a6313638a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="c7e9a-102">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7e9a-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="c7e9a-103">Uygun bir barındırma modu seçtikten sonra Web Hizmetleri olarak ifşa edilip uygulama arabirimleri yapılandırmak için COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7e9a-104">Aşağıdaki görevleri gerçekleştirmek için makinede yönetici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="c7e9a-105">ComSvcConfig.exe en son hizmet modeli sürümü (şu anda v4.5) kullanmak için bir web hizmeti yapılandırmak için bir Windows 7 makinede kullanırken, aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="c7e9a-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="c7e9a-106">Kayıt defteri anahtarını ayarlayın `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 bir DWORD değeri için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="c7e9a-107">ComSvcConfig.exe Çalıştır</span><span class="sxs-lookup"><span data-stu-id="c7e9a-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="c7e9a-108">Özgün değeri dön 1. adımda eklenen kayıt defteri anahtarını geri veya varsa silme yoktu.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7e9a-109">Bu kayıt defteri anahtarı geri döndürmeyi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-109">Reverting this registry key is important.</span></span> <span data-ttu-id="c7e9a-110">Bu uyumluluk anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-110">This is a compatibility key.</span></span> <span data-ttu-id="c7e9a-111">Bu değişikliği geri döndürmeyi olmayan sorunlar makinede çalışan diğer .NET uygulamaları neden olabilir).</span><span class="sxs-lookup"><span data-stu-id="c7e9a-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c7e9a-112">ComSvcConfig.exe kullanırken bir Windows 8 makinede bir iletişim kutusu/install belirten görüntülenir "aşağıdaki Windows özelliği, bilgisayarınızdaki bir uygulama gerekiyor: .NET Framework 3.5 (.NET 2.0 ve 3.0 içerir".NET Framework 3.5 yüklü değilse.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="c7e9a-113">Bu iletişim kutusunu yok sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-113">This dialog may be ignored.</span></span> <span data-ttu-id="c7e9a-114">Alternatif olarak azaltılabilir 0x00000001 DWORD değerini OnlyUseLatestCLR kayıt defteri anahtarına olabilir</span><span class="sxs-lookup"><span data-stu-id="c7e9a-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="c7e9a-115">COM + modu barındırma kullanarak Web Hizmetleri açığa çıkarılması olan arabirimler kümesi için bir arabirim eklemek için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="c7e9a-116">ComSvcConfig / kullanarak çalışan `/install` ve `/hosting:complus` , aşağıdaki örnekte gösterildiği gibi seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="c7e9a-117">Komut ekler `IFinances` arabiriminin `ItemOrders.IFinancial` bileşeninden (OnlineStore COM + uygulaması) için Web Hizmetleri olarak sunulan arabirimleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="c7e9a-118">Hizmet COM + modu barındırma kullanır ve bu nedenle açık uygulama etkinleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="c7e9a-119">Yıldız işareti (*) joker karakterini bileşeni ve arabirim için kullanılabilir, ancak yalnızca seçilen işlevleri bir Web hizmeti olarak kullanıma sunmak istediğiniz çünkü bunu kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-119">While the wildcard asterisk (*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="c7e9a-120">Bu bileşen gelecek bir sürümünde çalıştırırsanız, joker karakter kullanılması yapılandırma sözdizimi belirlendi olduğunda mevcut olmayabilen arabirimler kasıtsız olarak sunabilir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="c7e9a-121">/ Verbose seçeneği hataları ek olarak uyarıları görüntülemek için aracı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="c7e9a-122">Sunulan hizmet sözleşmesini yöntemlerden tümünde içerecek `IFinances` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="c7e9a-123">Yalnızca belirli yöntemler kullanarak COM + modu barındırma Web Hizmetleri açığa çıkarılması olan arabirimler kümesi arabirimden eklemek için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="c7e9a-124">ComSvcConfig / kullanarak çalışan `/install` ve `/hosting:complus` aşağıdaki örnekte gösterildiği gibi gerekli yöntemleri açık adlandırma ile seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="c7e9a-125">Komut yalnızca ekler `Credit` ve `Debit` yöntemleri `IFinances` arabirimi olarak sunulan hizmet sözleşmesi işlemleri.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="c7e9a-126">Diğer tüm yöntemleri arabirimde sözleşmeden atlanacak ve Web hizmeti istemcilerden aranabilir olmaz.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="c7e9a-127">Web barındırma modunu kullanan Web Hizmetleri açığa çıkarılması olan arabirimler kümesi için bir arabirim eklemek için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="c7e9a-128">ComSvcConfig / kullanarak çalışan `/install` seçeneği ve `/hosting:was` , aşağıdaki örnekte gösterildiği gibi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="c7e9a-129">Komut ekler `IStockLevels` üzerinde arabirim `ItemInventory.Warehouse` bileşeninden (OnlineWarehouse COM + uygulaması) için Web Hizmetleri olarak sunulan arabirimleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="c7e9a-130">Böylece uygulama otomatik olarak etkinleştirilir ve IIS OnlineWarehouse sanal dizinin yerine COM +'da barındırılan Web hizmetidir gerektiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="c7e9a-131">Web barındırılan işlem dışı yapılandırmayı kullanmak için COM + uygulaması Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalıştırmak için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="c7e9a-132">Sunucu uygulamaları yapılandırılan uygulamalar standart Web barındırılan modunu kullanın ve her isteği işlemek için bir işlem atlama doğurur.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="c7e9a-133">`/mex` Seçeneği, aynı aktarım hizmetinden bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için uygulamanın hizmet uç noktası olarak kullanan bir ek meta veri değişimi (MEX) Hizmeti uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="c7e9a-134">Belirtilen bir arabirim için bir Web hizmetini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="c7e9a-135">ComSvcConfig / kullanarak çalıştırmanız `/uninstall` , aşağıdaki örnekte gösterildiği gibi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="c7e9a-136">Komut kaldırır `IFinances` üzerinde arabirim `ItemOrders.Financial` bileşen (uygulamadan OnlineStore COM +).</span><span class="sxs-lookup"><span data-stu-id="c7e9a-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="c7e9a-137">Şu anda arabirimleri listelemek için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="c7e9a-138">ComSvcConfig / kullanarak çalıştırmanız `/list` , aşağıdaki örnekte gösterildiği gibi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="c7e9a-139">Komut şu anda arabirimleri, ilgili adres ve yerel makineye kapsamlı bağlama ayrıntıları ile birlikte listeler.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="c7e9a-140">Şu anda belirli listelemek için sergilenen arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7e9a-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="c7e9a-141">ComSvcConfig / kullanarak çalıştırmanız `/list` , aşağıdaki örnekte gösterildiği gibi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="c7e9a-142">Komut listeleri şu anda COM + kullanıma sunulan-arabirimi, yerel makinede OnlineStore COM + uygulaması için bağlama ayrıntıları ve karşılık gelen adresi ile barındırılan.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="c7e9a-143">Yardımcı programı ile kullanılabilir seçenekler hakkında Yardım görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c7e9a-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="c7e9a-144">ComSvcConfig / kullanarak Çalıştır /?</span><span class="sxs-lookup"><span data-stu-id="c7e9a-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="c7e9a-145">Aşağıdaki örnekte gösterildiği gibi seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c7e9a-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7e9a-146">See Also</span></span>  
 [<span data-ttu-id="c7e9a-147">COM + uygulamaları ile tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="c7e9a-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
