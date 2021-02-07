---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation örnekleri oluşturma'
title: Windows Communication Foundation Örnekleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: a53073ac92369574b204dbce998bebb8844fce8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704192"
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="32ea2-103">Windows Communication Foundation Örnekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="32ea2-103">Building the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="32ea2-104">Windows Communication Foundation (WCF) örnekleri, Visual Studio IDE kullanılarak veya komut satırından **MSBuild** komutu kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-104">The Windows Communication Foundation (WCF) samples can be built using the Visual Studio IDE or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="32ea2-105">Her iki yordam de bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-105">Both procedures are described in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="32ea2-106">WCF örneklerinden herhangi birini oluşturmadan veya çalıştırmadan önce, [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="32ea2-106">Before building or running any of the WCF samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

## <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="32ea2-107">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32ea2-107">To build the sample using a command prompt</span></span>

1. <span data-ttu-id="32ea2-108">Visual Studio için Geliştirici Komut İstemi açın ve örneği yüklediğiniz dizin konumunun altındaki dile özgü alt dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-108">Open Developer Command Prompt for Visual Studio and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="32ea2-109">`msbuild`Komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-109">Type `msbuild` at the command line.</span></span> <span data-ttu-id="32ea2-110">İstemci program dosyaları *client\bin* 'e kurulmuştur ve hizmet programı dosyaları *service\bin*'e yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-110">The client program files are built to *client\bin* and the service program files are built to *service\bin*.</span></span> <span data-ttu-id="32ea2-111">Hizmet Internet Information Services (IIS) tarafından barındırılıyorsa, hizmet programı dosyaları da *servicemodelsamples* dizinine ve *\Bin* alt dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-111">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="32ea2-112">Üzerinde çalışan hesap için değiştirme izinleri vermek üzere *%systemdrive%\ınetpub\wwwroot* üzerinde ACL 'ler ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-112">You must set the ACLs on *%systemdrive%\inetpub\wwwroot* to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="32ea2-113">Aksi takdirde, bazı derleme sonrası olaylar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="32ea2-113">Otherwise some post build events fail.</span></span> <span data-ttu-id="32ea2-114">Alternatif olarak, ACL 'Leri olduğu gibi bırakabilir ve yönetici olarak SDK komut istemi 'ni çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32ea2-114">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>

## <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="32ea2-115">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32ea2-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="32ea2-116">Visual Studio 'daki **Dosya** menüsünde   >  **Proje/çözüm** aç ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-116">From the **File** menu in Visual Studio, select **Open** > **Project/Solution**.</span></span> <span data-ttu-id="32ea2-117">Örneği yüklediğiniz dizinin altındaki dile özgü alt dizine gidin ve Visual Studio 'da çözümü açmak için. sln dosya simgesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-117">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>

1. <span data-ttu-id="32ea2-118">**Derle** menüsünde **çözümü yeniden derle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-118">From the **Build** menu, select **Rebuild Solution**.</span></span>

   <span data-ttu-id="32ea2-119">İstemci program dosyaları, client\bin 'e kurulmuştur ve hizmet programı dosyaları service\bin. için oluşturulmuştur</span><span class="sxs-lookup"><span data-stu-id="32ea2-119">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="32ea2-120">Hizmet IIS 'de barındırılıyorsa, hizmet programı dosyaları da *servicemodelsamples* dizinine ve *\Bin* alt dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-120">If the service is hosted in IIS, the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="32ea2-121">Üzerinde çalışan hesap için değiştirme izinleri vermek üzere%systemdrive%\ınetpub\wwwroot üzerinde ACL 'Ler ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-121">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="32ea2-122">Aksi takdirde, bazı derleme sonrası olaylar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="32ea2-122">Otherwise some post build events fail.</span></span> <span data-ttu-id="32ea2-123">Alternatif olarak, ACL 'Leri olduğu gibi bırakabilir ve SDK komut istemi 'ni veya Visual Studio 'Yu yönetici olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32ea2-123">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="32ea2-124">Bazı Visual Studio eylemleri (örneğin, ASP.NET Worker işlemine bir hata ayıklayıcı eklemek) ayrıca yönetim ayrıcalıkları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-124">Some Visual Studio actions (such as attaching a debugger to the ASP.NET worker process) also require administrative privileges.</span></span>

## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="32ea2-125">Toplu Iş dosyalarını ve betikleri ayarla</span><span class="sxs-lookup"><span data-stu-id="32ea2-125">Setup Batch Files and Scripts</span></span>

 <span data-ttu-id="32ea2-126">Setup.exe ve Cleanup.exe Batch dosyaları ve betikleri Visual Studio için Geliştirici Komut İstemi çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-126">Setup.exe and Cleanup.exe batch files and scripts should be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="32ea2-127">Çeşitli dosyaları ayarlama ve Temizleme, yönetici ayrıcalıkları gerektiren görevleri gerçekleştirir ve yönetici ayrıcalıklarıyla başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-127">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>

## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="32ea2-128">Meta veri uç noktaları hakkında önemli güvenlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="32ea2-128">Important Security Information about Metadata Endpoints</span></span>

 <span data-ttu-id="32ea2-129">Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="32ea2-129">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="32ea2-130">Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil.exe gibi) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="32ea2-130">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="32ea2-131">Örnekleri daha kolay hale getirmek için neredeyse tüm örnekler güvenli olmayan bir meta veri yayımlama uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="32ea2-131">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="32ea2-132">Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-132">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="32ea2-133">Hizmet meta verilerini yayımlama hakkında daha fazla bilgi için bkz. [meta veri yayımlama davranışı](metadata-publishing-behavior.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="32ea2-133">For more information about publishing service metadata, see the [Metadata Publishing Behavior](metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="32ea2-134">Meta veri uç noktasının güvenliğini sağlamaya yönelik bir örnek için [özel güvenli meta veri uç noktası](custom-secure-metadata-endpoint.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-134">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>

## <a name="exception-handling"></a><span data-ttu-id="32ea2-135">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="32ea2-135">Exception Handling</span></span>

 <span data-ttu-id="32ea2-136">Genellikle bu örneklere konuşarak, kodu örnek konusuna odaklanmış tutmak için özel durum işleme dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-136">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> <span data-ttu-id="32ea2-137">Özel durum işleme hakkında daha fazla bilgi için [Beklenen özel durumlar](expected-exceptions.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-137">For more information about exception handling, see the [Expected Exceptions](expected-exceptions.md) sample.</span></span>

## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="32ea2-138">Svcutil ile Istemcileri ve yapılandırmayı yeniden oluşturma</span><span class="sxs-lookup"><span data-stu-id="32ea2-138">Regenerating Clients and Configuration with Svcutil</span></span>

 <span data-ttu-id="32ea2-139">Örnek çoğu için istemci kodu ve yapılandırmasını yeniden oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32ea2-139">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="32ea2-140">Bazı örneklerin el ile düzenlenmiş yapılandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-140">Some samples require manually edited configuration.</span></span> <span data-ttu-id="32ea2-141">Örneğin, istemci sertifikası kimlik bilgilerini kullanan bir örnek için yapılandırmayı yeniden oluşturmak üzere Svcutil.exe kullanırsanız, önceden yapılandırılmış kimlik bilgilerini el ile belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-141">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="32ea2-142">Bazı örnekler, oluşturulan kodu etkilemek için belirli Svcutil.exe seçeneklerini kullanır, bu seçenekler belirli örnek konularda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32ea2-142">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>

### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="32ea2-143">İstemci ve yapılandırma dosyalarını yeniden oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32ea2-143">To regenerate the client and configuration files</span></span>

1. <span data-ttu-id="32ea2-144">Bir SDK komut istemi açın ve örneği yüklediğiniz dizin konumunun altındaki dile özgü alt dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-144">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="32ea2-145">Hizmet Web 'de barındırılan bir tür ise aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-145">If the service is a Web-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="32ea2-146">Hizmet şirket içinde barındırılan bir tür ise aşağıdaki komutu yazın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-146">If the service is a self-hosted type the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="32ea2-147">`http://localhost:8000/ServiceModelSamples/service.svc/mex`Şirket içinde barındırılan Hizmetin MEX uç noktasının adresiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-147">Replace `http://localhost:8000/ServiceModelSamples/service.svc/mex` with the address of the self-hosted service's mex endpoint.</span></span>

     <span data-ttu-id="32ea2-148">İstemciyi Visual Basic bir türde oluşturmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-148">To generate the client in a Visual Basic type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     <span data-ttu-id="32ea2-149">Hizmet kendi kendine barındırılan bir tür ise aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="32ea2-149">If the service is a self-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > <span data-ttu-id="32ea2-150">İstemci yapılandırması oluşturulmasını atlamak için **/noconfig** seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32ea2-150">To skip the generation of client configuration add the **/noConfig** option.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ea2-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32ea2-151">See also</span></span>

- [<span data-ttu-id="32ea2-152">Windows Communication Foundation Örneklerini Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="32ea2-152">Running the Windows Communication Foundation Samples</span></span>](running-the-samples.md)
- [<span data-ttu-id="32ea2-153">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="32ea2-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
