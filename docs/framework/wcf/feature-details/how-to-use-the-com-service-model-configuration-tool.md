---
title: 'Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 528e46a47daa6df865308592eb41658369a74b6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736253"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="f086e-102">Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın</span><span class="sxs-lookup"><span data-stu-id="f086e-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="f086e-103">Uygun bir barındırma modu seçtikten sonra COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) Web Hizmetleri olarak kullanıma sunulacak bir uygulama arabirimleri yapılandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f086e-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f086e-104">Aşağıdaki görevleri gerçekleştirmek için makinede bir yönetici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f086e-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="f086e-105">En son hizmet modeli sürümü (şu anda v4.5) kullanmak için bir web hizmeti yapılandırmak için bir Windows 7 makinesinde ComSvcConfig.exe kullanırken aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="f086e-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1.  <span data-ttu-id="f086e-106">Kayıt defteri anahtarını ayarlayın `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 DWORD değerini</span><span class="sxs-lookup"><span data-stu-id="f086e-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2.  <span data-ttu-id="f086e-107">ComSvcConfig.exe çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f086e-107">Run comsvcconfig.exe</span></span>  
  
3.  <span data-ttu-id="f086e-108">Özgün değeri geri dön 1. adımda eklenen kayıt defteri anahtarı geri veya varsa silin yoktu.</span><span class="sxs-lookup"><span data-stu-id="f086e-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f086e-109">Bu kayıt defteri anahtarı dönüştürme önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f086e-109">Reverting this registry key is important.</span></span> <span data-ttu-id="f086e-110">Bu uyumluluk anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="f086e-110">This is a compatibility key.</span></span> <span data-ttu-id="f086e-111">Bu değişikliği geri döndürülürken değil sorunları makine üzerinde çalışan diğer .NET uygulamaları neden olabilir).</span><span class="sxs-lookup"><span data-stu-id="f086e-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f086e-112">ComSvcConfig.exe kullanırken Windows 8 makinesinde bir iletişim kutusu/Install belirten görüntülenen "bilgisayarınızda bir uygulama aşağıdaki Windows özellik gerekiyor: .NET Framework 3.5 (.NET 2.0 ve 3.0 içerir".NET Framework 3.5 yüklü değilse.</span><span class="sxs-lookup"><span data-stu-id="f086e-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="f086e-113">Bu iletişim kutusunu yok sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="f086e-113">This dialog may be ignored.</span></span> <span data-ttu-id="f086e-114">Alternatif olarak sed OnlyUseLatestCLR kayıt defteri anahtarı DWORD değerini 0x00000001 yapabilecekleriniz</span><span class="sxs-lookup"><span data-stu-id="f086e-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="f086e-115">Bir arabirim kullanarak COM + modu barındırma Web Hizmetleri olarak açığa olan arabirimler kümesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="f086e-115">To add an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="f086e-116">ComSvcConfig / kullanarak çalıştırma `/install` ve `/hosting:complus` , aşağıdaki örnekte gösterildiği gibi seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="f086e-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="f086e-117">Komut ekler `IFinances` arabiriminin `ItemOrders.IFinancial` Web Hizmetleri olarak kullanıma sunulacak arabirimleri kümesine (OnlineStore COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f086e-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="f086e-118">Hizmet, COM + modu barındırma kullanır ve bu nedenle açık uygulama etkinleştirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f086e-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="f086e-119">Yıldız işareti (\*) joker karakterini bileşeni ve arabirimi için kullanılabilse de, yalnızca seçilen işlevleri bir Web hizmeti olarak kullanıma sunmak isteyebilirsiniz, çünkü kullanmaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="f086e-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="f086e-120">Bu bileşen gelecek bir sürümünde çalıştırırsanız, joker karakter kullanılması yanlışlıkla yapılandırma sözdizimi belirlendi olduğunda mevcut olmuş olabilir arabirimler sunabilir.</span><span class="sxs-lookup"><span data-stu-id="f086e-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="f086e-121">/ Verbose seçeneği hataları ek olarak uyarıları görüntülemek için araç bildirir.</span><span class="sxs-lookup"><span data-stu-id="f086e-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="f086e-122">Kullanıma sunulan hizmet sözleşmesini tüm yöntemleri içerecek `IFinances` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f086e-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="f086e-123">Yalnızca belirli yöntemleri kullanarak COM + modu barındırma Web Hizmetleri olarak açığa olan arabirimler kümesi bir arabirimden eklemek için</span><span class="sxs-lookup"><span data-stu-id="f086e-123">To add only specific methods from an interface to the set of interfaces that are to be exposed as Web services, using the COM+ hosting mode</span></span>  
  
-   <span data-ttu-id="f086e-124">ComSvcConfig / kullanarak çalıştırma `/install` ve `/hosting:complus` ile aşağıdaki örnekte gösterildiği gibi gerekli yöntemlerden açık adlandırma seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="f086e-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="f086e-125">Komutu yalnızca ekler `Credit` ve `Debit` yöntemlerinden `IFinances` arabirimi olarak kullanıma sunulan hizmet sözleşmesi işlemleri.</span><span class="sxs-lookup"><span data-stu-id="f086e-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="f086e-126">Tüm diğer yöntemler arabirimde sözleşmeden atlanacak ve Web hizmeti istemcilerden çağrılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f086e-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="f086e-127">Web barındırma modunu kullanarak Web Hizmetleri olarak açığa olan arabirimler kümesi için bir arabirim eklemek için</span><span class="sxs-lookup"><span data-stu-id="f086e-127">To add an interface to the set of interfaces that are to be exposed as Web services, using the Web hosting mode</span></span>  
  
-   <span data-ttu-id="f086e-128">ComSvcConfig / kullanarak çalıştırma `/install` seçeneği ve `/hosting:was` seçeneği, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f086e-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="f086e-129">Komut ekler `IStockLevels` üzerinde arabirim `ItemInventory.Warehouse` Web Hizmetleri olarak kullanıma sunulacak arabirimleri kümesine (OnlineWarehouse COM + uygulaması) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f086e-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="f086e-130">IIS sanal dizini OnlineWarehouse yerine COM +'da barındırılan Web hizmeti ve böylece uygulama otomatik olarak etkinleştirilir gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="f086e-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="f086e-131">Web barındırılan işlem içi yapılandırmayı kullanmak için COM + uygulaması Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalıştırmak için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f086e-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="f086e-132">Sunucu uygulamaları yapılandırılan uygulamalar standart Web barındırılan modunu kullanın ve her isteği işlemek için bir işlem atlama doğurur.</span><span class="sxs-lookup"><span data-stu-id="f086e-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="f086e-133">`/mex` Seçeneği, aynı taşıma, hizmetten bir sözleşme tanımı almak istediğiniz istemcileri desteklemek için uygulamanın hizmet uç noktası olarak kullanan bir ek meta veri değişimi (MEX) hizmet uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="f086e-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="f086e-134">Belirtilen bir arabirim için bir Web hizmeti kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="f086e-134">To remove a Web service for a specified interface</span></span>  
  
-   <span data-ttu-id="f086e-135">ComSvcConfig / kullanarak çalıştırma `/uninstall` seçeneği, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f086e-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="f086e-136">Komut kaldırır `IFinances` üzerinde arabirim `ItemOrders.Financial` (OnlineStore COM + uygulaması) bileşenini.</span><span class="sxs-lookup"><span data-stu-id="f086e-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
### <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="f086e-137">Şu anda arabirimleri listelemek için</span><span class="sxs-lookup"><span data-stu-id="f086e-137">To list currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="f086e-138">ComSvcConfig / kullanarak çalıştırma `/list` seçeneği, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f086e-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="f086e-139">Komut şu anda arabirimleri, bağlama ayrıntıları, yerel makineye kapsamlı ve karşılık gelen adresi birlikte listeler.</span><span class="sxs-lookup"><span data-stu-id="f086e-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="f086e-140">Şu anda belirli listelemek için arabirimleri kullanıma sunulan</span><span class="sxs-lookup"><span data-stu-id="f086e-140">To list specific currently exposed interfaces</span></span>  
  
-   <span data-ttu-id="f086e-141">ComSvcConfig / kullanarak çalıştırma `/list` seçeneği, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f086e-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="f086e-142">Komut listeleri şu anda COM + kullanıma sunulan-arabirimi, yerel makinede OnlineStore COM + uygulaması bağlama ayrıntıları ve karşılık gelen adresi ile barındırılan.</span><span class="sxs-lookup"><span data-stu-id="f086e-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="f086e-143">Yardımcı programı ile kullanılabilecek Seçenekleri Yardımı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="f086e-143">To display help on the options that can be used with the utility</span></span>  
  
-   <span data-ttu-id="f086e-144">Kullanarak ComSvcConfig / çalışan /?</span><span class="sxs-lookup"><span data-stu-id="f086e-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="f086e-145">seçeneği, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f086e-145">option, as shown in the following example.</span></span>  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f086e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f086e-146">See also</span></span>
- [<span data-ttu-id="f086e-147">COM+ Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f086e-147">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
