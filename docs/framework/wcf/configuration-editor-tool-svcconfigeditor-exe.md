---
title: Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)
description: WCF bağlamaları, davranışları, hizmetleri ve tanılama ayarlarını WCF hizmeti yapılandırma düzenleyicisini kullanarak yönetmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247655"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="d0c21-103">Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="d0c21-103">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="d0c21-104">Windows Communication Foundation (WCF) hizmet yapılandırma Düzenleyicisi (SvcConfigEditor.exe), yöneticilerin ve geliştiricilerin bir grafik kullanıcı arabirimi kullanarak WCF Hizmetleri için yapılandırma ayarlarını oluşturmalarına ve değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-104">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="d0c21-105">Bu araçla, XML yapılandırma dosyalarını doğrudan düzenlemeye gerek kalmadan WCF bağlamaları, davranışlar, hizmetler ve Tanılamalar için ayarları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-105">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="d0c21-106">Hizmet yapılandırma Düzenleyicisi, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-106">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="d0c21-107">WCF yapılandırma Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="d0c21-107">The WCF Configuration Editor</span></span>

<span data-ttu-id="d0c21-108">Hizmet yapılandırma Düzenleyicisi, WCF hizmeti veya istemcisini yapılandırma içindeki tüm adımlarda size rehberlik eden bir sihirbaz ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-108">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="d0c21-109">Doğrudan düzenleyici yerine sihirbazı kullanmanız önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-109">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="d0c21-110">Standart System.Configurlama şemasıyla uyumlu bir yapılandırma dosyası zaten varsa, Kullanıcı arabirimiyle bağlamalar, davranış, hizmet ve Tanılamalar için belirli ayarları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-110">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="d0c21-111">Hizmet yapılandırma Düzenleyicisi, mevcut WCF yapılandırma dosyalarının yanı sıra yürütülebilir dosyalar, COM+ Hizmetleri ve Web 'de barındırılan hizmetler için ayarları yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-111">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="d0c21-112">Hizmet yapılandırma Düzenleyicisi ile Web 'de barındırılan bir hizmet açılırken, hem hizmetin kendi Yapılandırması hem de üst düzey düğümlerin devralınan yapılandırmalar bölümleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-112">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="d0c21-113">WCF yapılandırma ayarları `<system.serviceModel>` yapılandırma dosyasının bölümünde bulunduğundan, düzenleyici özel olarak bu öğenin içeriğinde çalışır ve aynı dosyadaki diğer öğelere erişemez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-113">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="d0c21-114">Mevcut yapılandırma dosyalarına doğrudan gidebilir veya hizmet, sanal dizin veya COM+ hizmeti içeren bir derleme seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-114">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="d0c21-115">Düzenleyici, söz konusu hizmet için yapılandırma dosyasını yükler ve kullanıcının yapılandırma dosyasının bölümünde iç içe geçmiş öğeleri eklemesini veya varolan öğeleri düzenlemesini sağlar `<system.serviceModel>` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-115">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="d0c21-116">Düzenleyici IntelliSense 'i destekler ve şema uyumluluğunu zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-116">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="d0c21-117">Elde edilen çıktının yapılandırma dosyasının şemasıyla uyumlu olması ve sözdizimsel olarak doğru veri değerlerinin olması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-117">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="d0c21-118">Ancak, düzenleyici yapılandırma dosyasının anlam olarak geçerli olduğunu garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-118">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="d0c21-119">Diğer bir deyişle, düzenleyici yapılandırma dosyasının yapılandırdığı hizmet ile çalışabileceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-119">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="d0c21-120">Öğe değiştirildikten sonra düzenleyici yapılandırma dosyasından bir yapılandırma öğesini temizlemez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-120">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="d0c21-121">Örneğin, uç nokta adını boş olmayan bir dizeye ayarlamak ve kaydetmek için düzenleyiciyi kullanırsanız, aşağıdaki örnekte gösterildiği gibi yapılandırma dosyası aşağıdaki içeriğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-121">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="d0c21-122">Adı boş bir dizeye ayarlayarak ve dosyayı kaydettikten sonra, `name` Aşağıdaki örnekte gösterildiği gibi yapılandırma dosyası yine de özniteliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-122">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="d0c21-123">Özniteliği temizlemek için, başka bir metin düzenleyicisi kullanarak öğeyi el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-123">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="d0c21-124">`issueToken`Uç nokta davranışının öğesini kullandığınızda bu sorunla özellikle dikkatli olmanız gerekir `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-124">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="d0c21-125">Özellikle, `address` `localIssuer` alt öğesinin özniteliği boş bir dize olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-125">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="d0c21-126">`address`Yapılandırma düzenleyicisini kullanarak özniteliği değiştirdiyseniz ve tamamen kaldırmak istiyorsanız, bunu düzenleyici dışında bir araç kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-126">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="d0c21-127">Aksi takdirde, öznitelik boş bir dize içerir ve uygulamanız bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0c21-127">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="d0c21-128">Yapılandırma düzenleyicisini kullanma</span><span class="sxs-lookup"><span data-stu-id="d0c21-128">Using the Configuration Editor</span></span>

<span data-ttu-id="d0c21-129">Hizmet yapılandırma Düzenleyicisi, aşağıdaki Windows SDK yükleme konumunda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="d0c21-129">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="d0c21-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="d0c21-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="d0c21-131">Hizmet yapılandırma düzenleyicisini başlattıktan sonra, yönetmek istediğiniz hizmet veya derlemeye gitmek için **dosya/açma** menüsünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-131">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="d0c21-132">Yapılandırma dosyalarını doğrudan açabilir, WCF/COM + hizmetlerine gözatabilir ve Web 'de barındırılan hizmetler için yapılandırma dosyalarını açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-132">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="d0c21-133">Hizmet yapılandırma düzenleyicisinin Kullanıcı arabirimi aşağıdaki alanlara ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="d0c21-133">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="d0c21-134">Sol taraftaki bir ağaç yapısında yapılandırma öğelerini görüntüleyen ağaç görünümü bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d0c21-134">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="d0c21-135">Düğümleri sağ tıklayarak ağaçta işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-135">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="d0c21-136">Pencerenin sol alt köşesindeki geçerli öğeler için ortak görevleri görüntüleyen görev bölmesi</span><span class="sxs-lookup"><span data-stu-id="d0c21-136">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="d0c21-137">Sağ taraftaki ağaç görünümünde seçilen yapılandırma düğümünün ayrıntılı ayarlarını görüntüleyen ayrıntı bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d0c21-137">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="d0c21-138">Yapılandırma dosyası açılıyor</span><span class="sxs-lookup"><span data-stu-id="d0c21-138">Opening a Configuration File</span></span>

1. <span data-ttu-id="d0c21-139">WCF yükleme konumunuza gitmek için bir komut penceresi kullanarak hizmet yapılandırma düzenleyicisini başlatın ve ardından yazın `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-139">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="d0c21-140">**Dosya** menüsünde **Aç** ' ı seçin ve yönetmek istediğiniz dosya türüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-140">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="d0c21-141">**Aç** iletişim kutusunda, yönetmek istediğiniz belirli dosyaya gidin ve çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-141">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="d0c21-142">Görüntüleyici otomatik olarak yapılandırma birleştirme yolunu izler ve birleştirilmiş yapılandırmanın bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0c21-142">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="d0c21-143">Örneğin, barındırılmayan bir hizmetin gerçek yapılandırması, Machine.config ve App.config bir birleşimidir. Tüm değişiklikler, SvcConfigEditor 'daki etkin dosyaya uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-143">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="d0c21-144">Yapılandırma birleştirme yolundaki belirli bir dosyayı düzenlemek istiyorsanız, doğrudan açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-144">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="d0c21-145">Yapılandırma Düzenleyicisi, ikinci olarak düzenleyici dışında değiştirildiğinde, açılmış olan yapılandırma dosyasını yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-145">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="d0c21-146">Bu durumda, düzenleyicinin içine durmayan tüm değişiklikler kaybolur.</span><span class="sxs-lookup"><span data-stu-id="d0c21-146">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="d0c21-147">Yeniden yükleme sürekli gerçekleşse, en olası nedeni yapılandırma dosyasına sürekli erişen, örneğin arka planda çalışan bir virüsten koruma yazılımı olan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-147">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="d0c21-148">Bu sorunu çözmek için, yapılandırma Düzenleyicisi 'nin açıldığında dosyaya erişebilen tek işlem olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d0c21-148">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="d0c21-149">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="d0c21-149">Services</span></span>

<span data-ttu-id="d0c21-150">**Hizmetler** düğümü, yapılandırma dosyasında şu anda atanmış olan tüm hizmetleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-150">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="d0c21-151">Ağaçtaki her alt düğüm, yapılandırma dosyasında <> öğesinin bir alt öğesine karşılık gelir `services` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-151">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="d0c21-152">**Hizmetler** düğümüne tıkladığınızda, **Ayrıntılar** bölmesindeki hizmet Özeti sayfasında görevleri görüntüleyebilir veya yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-152">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="d0c21-153">Yeni bir hizmet yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-153">Creating a new Service Configuration</span></span>

<span data-ttu-id="d0c21-154">Aşağıdaki yollarla yeni bir hizmet yapılandırması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-154">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="d0c21-155">Sihirbaz kullanarak: **yeni hizmet oluştur bağlantısına tıklayın...**</span><span class="sxs-lookup"><span data-stu-id="d0c21-155">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="d0c21-156">Sihirbazı başlatmak için görev bölmesinde veya Özet sayfasında.</span><span class="sxs-lookup"><span data-stu-id="d0c21-156">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="d0c21-157">**Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-157">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="d0c21-158">El ile oluştur: **Hizmetler** düğümüne sağ tıklayıp **yeni hizmet**seçeneğini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-158">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="d0c21-159">Yeni bir hizmet uç noktası yapılandırması oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="d0c21-159">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="d0c21-160">Aşağıdaki yollarla yeni bir hizmet uç noktası yapılandırması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-160">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="d0c21-161">Sihirbaz kullanarak oluşturma: **yeni hizmet uç noktası oluştur** bağlantısına tıklayın...</span><span class="sxs-lookup"><span data-stu-id="d0c21-161">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="d0c21-162">Sihirbazı başlatmak için görev bölmesinde veya Özet sayfasında.</span><span class="sxs-lookup"><span data-stu-id="d0c21-162">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="d0c21-163">**Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-163">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="d0c21-164">El ile oluştur: bir hizmet oluşturduktan sonra, **uç noktalar** düğümüne sağ tıklayıp "**yeni hizmet uç noktası**" seçeneğini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-164">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="d0c21-165">Hizmet yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-165">Editing a Service Configuration</span></span>

1. <span data-ttu-id="d0c21-166">Bir **hizmet** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-166">Click a **Service** node.</span></span>

2. <span data-ttu-id="d0c21-167">Özellik kılavuzlarında ayarları düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-167">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="d0c21-168">Hizmet uç noktası yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-168">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="d0c21-169">**Hizmet uç noktası** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-169">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="d0c21-170">Özellik kılavuzlarında ayarları düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-170">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="d0c21-171">Temel adres ekleme</span><span class="sxs-lookup"><span data-stu-id="d0c21-171">Adding a Base Address</span></span>

1. <span data-ttu-id="d0c21-172">**Ana bilgisayar** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-172">Click the **Host** node.</span></span>

2. <span data-ttu-id="d0c21-173">**Yeni...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-173">Click the **New…**</span></span> <span data-ttu-id="d0c21-174">düğmesini **tıklatın** .</span><span class="sxs-lookup"><span data-stu-id="d0c21-174">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="d0c21-175">İletişim kutusuna taban adresi URI 'sini yazın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-175">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="d0c21-176">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-176">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="d0c21-177">[\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md)Bu aracın içindeki değerini düzenleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-177">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="d0c21-178">Bu öğeyi eklemek veya değiştirmek için bir metin Düzenleyicisi veya Visual Studio kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-178">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="d0c21-179">İstemci</span><span class="sxs-lookup"><span data-stu-id="d0c21-179">Client</span></span>

<span data-ttu-id="d0c21-180">**İstemci** düğümü, yapılandırma dosyasındaki tüm istemci uç noktalarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-180">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="d0c21-181">Ağaçtaki her alt düğüm, yapılandırma dosyasında <> öğesinin bir alt öğesine karşılık gelir `client` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-181">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="d0c21-182">**İstemci** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**istemci **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-182">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="d0c21-183">Yeni Istemci uç noktası yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-183">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="d0c21-184">Aşağıdaki yollarla yeni bir istemci uç noktası yapılandırması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-184">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="d0c21-185">Sihirbaza göre oluşturma: **Yeni Istemci oluştur bağlantısına tıklayın...**</span><span class="sxs-lookup"><span data-stu-id="d0c21-185">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="d0c21-186">Sihirbazı başlatmak için pencerenin sol alt kısmındaki **görev bölmesinde** veya **Özet sayfasında** .</span><span class="sxs-lookup"><span data-stu-id="d0c21-186">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="d0c21-187">**Dosya** menüsündeki > **Yeni öğe Ekle**' de de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-187">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="d0c21-188">Sihirbaz, istemci yapılandırmasının oluşturulduğu hizmet yapılandırmasının konumunu işaret etmesini ister.</span><span class="sxs-lookup"><span data-stu-id="d0c21-188">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="d0c21-189">Daha sonra, bağlanılacak hizmet uç noktasını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-189">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="d0c21-190">El ile oluştur: **istemci**altındaki **uç noktalar** düğümüne sağ tıklayın ve **yeni istemci uç noktası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-190">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="d0c21-191">Istemci uç noktası yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-191">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="d0c21-192">**Istemci uç noktası** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-192">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="d0c21-193">Özellik kılavuzlarında ayarları düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-193">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="d0c21-194">Standart uç nokta</span><span class="sxs-lookup"><span data-stu-id="d0c21-194">Standard Endpoint</span></span>

<span data-ttu-id="d0c21-195">Standart uç noktalar, adresin, sözleşmenin ve bağlamanın bir veya daha fazla yönü varsayılan değerlere ayarlanmış olan özel uç noktalardır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-195">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="d0c21-196">Bu tür yapılandırma ayarları **standart uç nokta** düğümünde depolanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-196">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="d0c21-197">**Standart uç nokta** düğümü yapılandırma dosyasındaki tüm standart uç nokta ayarlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-197">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="d0c21-198">Ağaçtaki her alt düğüm, yapılandırma dosyasındaki öğesindeki bir alt öğeye karşılık gelir `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-198">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="d0c21-199">**Standart uç nokta** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**standart uç nokta **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-199">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="d0c21-200">Yeni bir standart uç nokta yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-200">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="d0c21-201">Aşağıdaki yollarla yeni bir standart uç nokta yapılandırması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-201">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="d0c21-202">**Standart uç nokta** düğümüne sağ tıklayın ve **Yeni standart uç nokta yapılandırması ' nı seçin...**</span><span class="sxs-lookup"><span data-stu-id="d0c21-202">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="d0c21-203">İletişim kutusunda bağlama türünü seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-203">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="d0c21-204">**Standart uç nokta** düğümünü seçin ve **Yeni standart uç nokta yapılandırması...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-204">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="d0c21-205">pencerenin sol alt kısmındaki **görev bölmesinde** .</span><span class="sxs-lookup"><span data-stu-id="d0c21-205">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="d0c21-206">**Yeni bir standart uç nokta oluşturma** iletişim kutusu, tüm kayıtlı standart uç nokta türlerini görüntüler ve listeler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-206">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="d0c21-207">Standart uç nokta yapılandırmasını görüntüleme ve düzenlemeyle</span><span class="sxs-lookup"><span data-stu-id="d0c21-207">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="d0c21-208">Aşağıdaki yollarla görüntüleme ve düzenlemeyle ilgili standart bir uç nokta yapılandırması açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-208">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="d0c21-209">**Standart uç nokta** düğümünü genişletmek için tıklayın ve ilgili uç nokta alt düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-209">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="d0c21-210">**Standart uç nokta** düğümüne tıklayın ve Ayrıntılar bölmesinde ilgili uç noktaya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-210">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="d0c21-211">Uç nokta öznitelikleri, düzenlemenin sağ bölmesinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-211">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="d0c21-212">Standart uç nokta yapılandırmasını silme</span><span class="sxs-lookup"><span data-stu-id="d0c21-212">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="d0c21-213">Standart uç nokta yapılandırmasını aşağıdaki yollarla silebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0c21-213">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="d0c21-214">**Standart uç nokta** düğümünü genişletmek için tıklayın ve ilgili uç nokta alt düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-214">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="d0c21-215">Uç noktayı silmek için **standart uç nokta yapılandırmasını silme** bağlam komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-215">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="d0c21-216">**Standart uç nokta** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-216">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="d0c21-217">**Görev** bölmesinde **standart uç nokta yapılandırmasını sil**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-217">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="d0c21-218">Standart uç nokta kullanılıyorsa, onu silmeye çalıştığınızda bir uyarı iletisi görüntülenir: **standart uç nokta kullanımda. Şimdi silerseniz, lütfen yapılandırmanın diğer bölümlerinde (örneğin, hizmet uç noktası veya istemci uç noktasında) tüm başvurularını sildiğinizden emin olun. Aksi takdirde, yapılandırma geçersiz olur ve bir dahaki sefer açılamaz. Standart uç noktayı silmek istediğinizden emin misiniz? "**</span><span class="sxs-lookup"><span data-stu-id="d0c21-218">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="d0c21-219">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d0c21-219">Binding</span></span>

<span data-ttu-id="d0c21-220">Bağlama yapılandırması uç noktalarda bağlamaları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-220">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="d0c21-221">Bu tür yapılandırma ayarları **bağlama** düğümünde depolanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-221">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="d0c21-222">Ada ve birden çok uç noktaya göre bağlantı yapılandırmaları için uç noktalar tek bir bağlama yapılandırmasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-222">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="d0c21-223">**Bağlamalar** düğümü yapılandırma dosyasındaki tüm bağlama ayarlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-223">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="d0c21-224">Ağaçtaki her alt düğüm, yapılandırma dosyasındaki <> öğesinde bir alt öğeye karşılık gelir `bindings` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-224">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="d0c21-225">**Bağlamalar** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**bağlama **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-225">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="d0c21-226">Yeni bir bağlama yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-226">Creating a New Binding Configuration</span></span>

<span data-ttu-id="d0c21-227">Aşağıdaki yollarla yeni bir bağlama yapılandırması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-227">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="d0c21-228">**Bağlamalar** düğümüne sağ tıklayın ve **yeni bağlama yapılandırması**' nı seçin...</span><span class="sxs-lookup"><span data-stu-id="d0c21-228">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="d0c21-229">İletişim kutusunda bağlama türünü seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-229">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="d0c21-230">**Bağlamalar** düğümünü seçin ve **yeni bağlama yapılandırması**... öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-230">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="d0c21-231">pencerenin sol alt kısmındaki **görev bölmesinde** .</span><span class="sxs-lookup"><span data-stu-id="d0c21-231">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="d0c21-232">Hizmet veya istemci Özeti sayfasında, ilgili uç nokta için bir bağlama yapılandırması oluşturmak üzere **bağlama yapılandırması** alanında **oluşturmak için tıklama** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-232">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="d0c21-233">Özel bağlamaya bağlama öğesi uzantıları ekleme</span><span class="sxs-lookup"><span data-stu-id="d0c21-233">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="d0c21-234">Uzantı öğesi eklemek istediğiniz bağlamayı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-234">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="d0c21-235">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-235">Click **Add**.</span></span>

3. <span data-ttu-id="d0c21-236">Kullanılabilir uzantılar listesinden eklemek istediğiniz bağlama öğesi uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-236">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="d0c21-237">Birden çok öğe seçmek için CTRL tuşuna aynı anda basın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-237">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="d0c21-238">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-238">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="d0c21-239">Özel bağlamadaki uzantı konumunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="d0c21-239">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="d0c21-240">Özel bağlama bir yığın oluşturan bağlama öğelerinin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="d0c21-240">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="d0c21-241">Yığındaki her bağlama öğesinin kendi yapılandırma ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-241">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="d0c21-242">Özel bağlamadaki bağlama öğesi uzantılarının sırası, yığındaki konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-242">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="d0c21-243">Yığının en üstünde bulunan öğeler önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-243">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="d0c21-244">Sıralamayı değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="d0c21-244">To change the ordering:</span></span>

1. <span data-ttu-id="d0c21-245">Özel bağlama düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-245">Select the custom binding node.</span></span>

2. <span data-ttu-id="d0c21-246">**Bağlama öğesi uzantı konumu** bölümünde bir bağlama uzantı öğesi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-246">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="d0c21-247">Seçili öğenin konumunu değiştirmek için listenin sol tarafındaki **yukarı** veya **aşağı** düğmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-247">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="d0c21-248">Özel bağlamadaki bağlama öğesi uzantılarının yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-248">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="d0c21-249">Ağaçtaki bağlama düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-249">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="d0c21-250">Düzenlemek istediğiniz öğeyi içeren özel bağlamayı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-250">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="d0c21-251">Düzenlemek istediğiniz bağlama öğesi uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-251">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="d0c21-252">Öğe ayarları sağ bölmede görünür ve burada düzenlenebilirler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-252">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="d0c21-253">Tanılama</span><span class="sxs-lookup"><span data-stu-id="d0c21-253">Diagnostics</span></span>

<span data-ttu-id="d0c21-254">**Tanılama** düğümü yapılandırma dosyasındaki tüm tanılama ayarlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-254">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="d0c21-255">Performans sayaçlarını açıp kapamanızı, Windows Yönetim Araçları (WMI) etkinleştirebilir veya devre dışı bırakmanızı, WCF izlemeyi yapılandırmanızı ve WCF ileti günlüğe kaydetmeyi yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-255">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="d0c21-256">**Tanılama** düğümündeki ayarlar `system.diagnostics` , `<diagnostics>` yapılandırma dosyasında <> bölümüne ve bölümüne karşılık gelir `<system.serviceModel>` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-256">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="d0c21-257">**Tanılama** düğümüne tıkladığınızda, **Ayrıntılar bölmesindeki**tanılama **Özeti sayfasında** görevleri görüntüleyebilir veya yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-257">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="d0c21-258">Performans sayaçlarını ve WMI 'yi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0c21-258">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="d0c21-259">**Tanılama** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-259">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="d0c21-260">**Performans sayaçlarını aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-260">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="d0c21-261">Performans sayacının üç durumu vardır: kapalı (varsayılan), ServiceOnly ve ALL.</span><span class="sxs-lookup"><span data-stu-id="d0c21-261">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="d0c21-262">Bağlantıya tıkladığınızda bu üç durum arasındaki ayar geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-262">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="d0c21-263">WMI sağlayıcısını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0c21-263">Configuring WMI Provider</span></span>

1. <span data-ttu-id="d0c21-264">**Tanılama** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-264">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="d0c21-265">WMI sağlayıcısını etkinleştirmek için **WMI sağlayıcısını etkinleştir** bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-265">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="d0c21-266">WCF Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d0c21-266">Enabling WCF Tracing</span></span>

<span data-ttu-id="d0c21-267">Standart özelliklerle bir WCF izleme dosyası oluşturabilir veya özel bir izleme dosyası ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-267">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="d0c21-268">**Tanılama** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-268">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="d0c21-269">**Izlemeyi etkinleştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-269">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="d0c21-270">İzleme düzeyini ayarlamak için **Izleme düzeyi** bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-270">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="d0c21-271">Altı izleme düzeyi vardır: kapalı, kritik, hata, uyarı, bilgi ve ayrıntılı.</span><span class="sxs-lookup"><span data-stu-id="d0c21-271">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="d0c21-272">**Etkinlik izleme** ve **yayma ETKINLIĞI** seçeneği, WCF etkinlik izleme özelliğini kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-272">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="d0c21-273">İzleme dosyasını ve seçeneklerini belirtmek için izleme dinleyicisi adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-273">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="d0c21-274">WCF günlüğü etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="d0c21-274">Enabling WCF Logging</span></span>

<span data-ttu-id="d0c21-275">Standart özelliklerle bir WCF izleme dosyası oluşturabilir veya özel bir izleme dosyası ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-275">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="d0c21-276">**Tanılama** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-276">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="d0c21-277">**Ileti günlüğe kaydetmeyi etkinleştir**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-277">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="d0c21-278">Günlük düzeyini ayarlamak için **günlük düzeyi** bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-278">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="d0c21-279">Üç günlük düzeyi vardır: Hatalı biçimlendirilmiş, hizmet ve aktarım.</span><span class="sxs-lookup"><span data-stu-id="d0c21-279">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="d0c21-280">Günlük dosyasını ve seçeneklerini belirtmek için dinleyici adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-280">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="d0c21-281">Uygulamanız kapatıldığında izleme ve ileti günlüklerinin otomatik olarak **temizlenmesi Istiyorsanız otomatik temizleme** seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-281">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="d0c21-282">**Tanılama** **Özeti sayfası** , tanılamayı yapılandırırken en sık kullanılan görevleri gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-282">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="d0c21-283">Ancak, dinleyicileri ve kaynak ayarlarını el ile düzenlemek isterseniz, **Tanılama** düğümünü genişletmeli ve **ileti günlüğe kaydetme**, **dinleyiciler** ve **kaynaklar** düğümündeki ayarları düzenlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-283">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="d0c21-284">WCF özel Izleme veya Ileti günlüğe kaydetme etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="d0c21-284">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="d0c21-285">**Tanılama** düğümüne tıklayın ve genişletin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-285">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="d0c21-286">**Dinleyiciler** düğümüne sağ tıklayın ve **Yeni dinleyici**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-286">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="d0c21-287">**InitData** alanına izleme dosyası adını yazın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-287">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="d0c21-288">"..." Düğmesine tıklayabilirsiniz bir yola gözatmaya yönelik düğme.</span><span class="sxs-lookup"><span data-stu-id="d0c21-288">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="d0c21-289">**TypeName** satırına tıkladığınızda bir "..." görüntülenir Bu.</span><span class="sxs-lookup"><span data-stu-id="d0c21-289">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="d0c21-290">Zaten yüklü olan önceden yapılandırılmış izleme dinleyicilerini bulmak için kullanabileceğiniz **Izleme dinleyicisi türü tarayıcısını**açmak için bu düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-290">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="d0c21-291">**Kaynak** bölümüne göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-291">Note the **Source** section.</span></span> <span data-ttu-id="d0c21-292">Kullanılabilir izleme kaynaklarını listeleyen açılan menü içeren bir iletişim kutusu açmak için bu bölümde **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-292">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="d0c21-293">Bir izleme kaynağı seçip **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-293">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="d0c21-294">Ileti günlüğe kaydetme ayarlarını düzenlemek için **Ileti günlüğe kaydetme** düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-294">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="d0c21-295">Özellik kılavuzundaki ayarları düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-295">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="d0c21-296">Gelişmiş</span><span class="sxs-lookup"><span data-stu-id="d0c21-296">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="d0c21-297">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="d0c21-297">Behaviors</span></span>

<span data-ttu-id="d0c21-298">**Davranışlar** düğümü, yapılandırma dosyasında şu anda tanımlanan davranışları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-298">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="d0c21-299">Davranış yapılandırması, uç noktaların ve hizmetlerin davranışlarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-299">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="d0c21-300">Bu tür yapılandırma ayarları, **Gelişmiş** düğümde **hizmet davranışları** ve **uç nokta davranışları**altında depolanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-300">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="d0c21-301">Hizmet davranışları hizmetler tarafından kullanılır; uç nokta davranışları uç noktalara göre.</span><span class="sxs-lookup"><span data-stu-id="d0c21-301">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="d0c21-302">Davranışlar, yığın için bir genişletme öğelerinin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="d0c21-302">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="d0c21-303">Yığının en üstünde bulunan öğe önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-303">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="d0c21-304">Her uzantı öğesi kendi yapılandırmasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-304">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="d0c21-305">Yeni davranış yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-305">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="d0c21-306">İki şekilde yeni bir davranış yapılandırması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-306">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="d0c21-307">Davranış düğümlerinden birine sağ tıklayın ve "**Yeni davranış yapılandırması..** ." seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-307">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="d0c21-308">Davranış düğümlerinden birini seçin ve **Yeni davranış yapılandırmasına**tıklayın...</span><span class="sxs-lookup"><span data-stu-id="d0c21-308">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="d0c21-309">pencerenin sol alt kısmındaki **görev bölmesinde** .</span><span class="sxs-lookup"><span data-stu-id="d0c21-309">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="d0c21-310">Davranışa davranış öğesi uzantıları ekleme</span><span class="sxs-lookup"><span data-stu-id="d0c21-310">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="d0c21-311">Davranış düğümlerinden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-311">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="d0c21-312">Düzenlemek istediğiniz davranışı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-312">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="d0c21-313">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-313">Click **Add**.</span></span>

4. <span data-ttu-id="d0c21-314">Kullanılabilir uzantılar listesinden eklemek istediğiniz davranış öğesi uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-314">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="d0c21-315">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-315">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="d0c21-316">Uzantı konumunu bir davranışta ayarlama</span><span class="sxs-lookup"><span data-stu-id="d0c21-316">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="d0c21-317">Davranışlar, yığın oluşturan öğelerin koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-317">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="d0c21-318">Yığındaki her bir öğenin kendi yapılandırması vardır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-318">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="d0c21-319">Davranış öğesi uzantılarının bir davranıştaki sırası yığındaki konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-319">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="d0c21-320">Yığının en üstünde bulunan öğeler önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-320">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="d0c21-321">Sıralamayı değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="d0c21-321">To change the ordering:</span></span>

1. <span data-ttu-id="d0c21-322">Davranış düğümlerinden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-322">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="d0c21-323">Düzenlemek istediğiniz davranışı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-323">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="d0c21-324">**Davranış öğesi uzantısı konumu** bölümünde bir davranış uzantısı öğesi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-324">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="d0c21-325">Seçili öğenin konumunu değiştirmek için listenin sol tarafındaki **yukarı** veya **aşağı** düğmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-325">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="d0c21-326">Davranış öğesi uzantılarının yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-326">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="d0c21-327">Ağaçtaki davranış düğümlerinden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-327">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="d0c21-328">Düzenlemek istediğiniz öğeyi içeren davranışı seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-328">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="d0c21-329">Düzenlemek istediğiniz davranış öğesi uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-329">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="d0c21-330">Öğenin ayarları, düzenlenebilecekleri sağ bölmede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-330">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="d0c21-331">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="d0c21-331">ProtocolMapping</span></span>

<span data-ttu-id="d0c21-332">Bu bölüm, protokol adres şemaları ve olası bağlamalar arasında tanımlı eşleme aracılığıyla http, TCP, MSMQ veya net. pipe gibi farklı protokoller için varsayılan bağlama türlerini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-332">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="d0c21-333">Ayrıca diğer protokollere yeni eşlemeler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-333">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="d0c21-334">Uzantılar</span><span class="sxs-lookup"><span data-stu-id="d0c21-334">Extensions</span></span>

<span data-ttu-id="d0c21-335">Yeni bağlama uzantıları, bağlama öğesi uzantıları, standart uç nokta uzantıları ve davranış uzantıları, WCF yapılandırmasında kullanılmak üzere kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-335">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="d0c21-336">Uzantılar ad/tür çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-336">Extensions are name/type pairs.</span></span> <span data-ttu-id="d0c21-337">Ad, yapılandırmada uzantının adını tanımlar, ancak tür uzantıyı uygular.</span><span class="sxs-lookup"><span data-stu-id="d0c21-337">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="d0c21-338">Dört tür uzantı vardır:</span><span class="sxs-lookup"><span data-stu-id="d0c21-338">There are four types of extensions:</span></span>

- <span data-ttu-id="d0c21-339">Bağlama uzantıları, tüm bağlama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-339">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="d0c21-340">Örnek: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d0c21-340">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="d0c21-341">Bağlama öğesi uzantıları bağlama bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-341">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="d0c21-342">Örnek: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="d0c21-342">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="d0c21-343">Standart uç nokta uzantıları tüm standart uç noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-343">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="d0c21-344">Örnek: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="d0c21-344">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="d0c21-345">Davranış öğesi uzantıları bir davranışın öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-345">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="d0c21-346">Örnek: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="d0c21-346">Example: `clientVia`.</span></span>

 <span data-ttu-id="d0c21-347">Yapılandırmada kayıtlı olan uzantılar aynı türdeki diğer WCF bileşenleri gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-347">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="d0c21-348">Yeni uzantı ekleme</span><span class="sxs-lookup"><span data-stu-id="d0c21-348">Adding a new extension</span></span>

<span data-ttu-id="d0c21-349">Gelişmiş düğümlerdeki uzantı düğümlerinden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="d0c21-349">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="d0c21-350">**Yeni**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-350">Click **New**.</span></span>

2. <span data-ttu-id="d0c21-351">Bir ad girin ve yazın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-351">Enter a name and type.</span></span>

3. <span data-ttu-id="d0c21-352">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-352">Click **OK**.</span></span>

4. <span data-ttu-id="d0c21-353">Uzantı artık düzenleyicide uygun yerde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-353">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="d0c21-354">Örneğin, bir davranış öğesi uzantısı eklerseniz, kullanılabilir Uzantılar listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="d0c21-354">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="d0c21-355">Barındırma ortamı</span><span class="sxs-lookup"><span data-stu-id="d0c21-355">Hosting Environment</span></span>

<span data-ttu-id="d0c21-356">Bu bölüm, hizmet barındırma ortamı için örnek oluşturma ayarlarını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-356">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="d0c21-357">Sihirbazı kullanarak yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-357">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="d0c21-358">Yeni bir yapılandırma dosyası oluşturmanın bir yolu, yeni hizmet öğesi Sihirbazı 'nı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-358">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="d0c21-359">Sihirbaz, yüklü hizmet türlerini ve bilgisayarda WCF ile uyumlu diğer öğeleri bulur (COM+ ve Web 'de barındırılan sanal dizinler dahil) ve yapılandırmayı çok daha kolay bir şekilde oluşturmak için yükler.</span><span class="sxs-lookup"><span data-stu-id="d0c21-359">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="d0c21-360">Yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-360">Creating a Configuration File</span></span>

1. <span data-ttu-id="d0c21-361">WCF yükleme konumunuza gitmek için bir komut penceresi kullanarak hizmet yapılandırma düzenleyicisini başlatın ve ardından yazın `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="d0c21-361">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="d0c21-362">**Dosya** menüsünde **Aç** ' ı seçin ve ardından, oluşturmak istediğiniz yapılandırma dosyasının türüne bağlı olarak **yürütülebilir**, **com+ hizmeti**veya **webhosted Service**' i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-362">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="d0c21-363">**Aç** iletişim kutusunda, bir yapılandırma dosyası oluşturmak istediğiniz belirli dosyaya gidin ve çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-363">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="d0c21-364">**Dosya** menüsünde, **Yeni öğe Ekle** ' nin üzerine gelin ve **hizmet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-364">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="d0c21-365">Yeni hizmet öğesi Sihirbazı açılır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-365">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="d0c21-366">Yeni hizmeti oluşturmak için sihirbazdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-366">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="d0c21-367">Sihirbaz tarafından oluşturulan yapılandırma dosyasından NetPeerTcpBinding kullanmak istiyorsanız, bir bağlama yapılandırma öğesini el ile eklemeniz ve `mode` `security` öğesinin özniteliğini "none" olarak değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-367">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="d0c21-368">COM+ yapılandırılıyor</span><span class="sxs-lookup"><span data-stu-id="d0c21-368">Configuring COM+</span></span>

<span data-ttu-id="d0c21-369">Hizmet yapılandırma Düzenleyicisi, var olan bir COM+ uygulaması için yeni bir yapılandırma dosyası oluşturmanızı veya mevcut bir COM+ yapılandırmasını düzenlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-369">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="d0c21-370">**Com sözleşmesi** düğümü yalnızca `comContract` yapılandırma dosyasında <> bölümü varsa görünür.</span><span class="sxs-lookup"><span data-stu-id="d0c21-370">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="d0c21-371">Yeni COM+ Yapılandırması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0c21-371">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="d0c21-372">Yeni bir COM+ Yapılandırması oluşturmadan önce, COM+ uygulamanızın Bileşen Hizmetleri 'nde yüklü olduğundan ve genel derleme önbelleği 'ne (GAC) kayıtlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d0c21-372">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="d0c21-373">**Dosya** menüsünü seçin-> **Integrate**  ->  **com+ uygulamasını tümleştirin.**</span><span class="sxs-lookup"><span data-stu-id="d0c21-373">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="d0c21-374">Bu işlem, geçerli açılan dosyayı kapatır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-374">This operation closes the current opened file.</span></span> <span data-ttu-id="d0c21-375">Geçerli dosyada kaydedilmemiş veriler varsa, bir Kaydet iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-375">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="d0c21-376">Ardından **com+ Tümleştirme Sihirbazı** başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-376">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="d0c21-377">İlk sayfada, ağaçtan COM+ uygulamasını seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-377">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="d0c21-378">COM+ uygulamanızı ağaçta bulamıyorsanız bileşen hizmetlerinde yüklü olduğunu ve genel derleme önbelleği 'ne (GAC) kayıtlı olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-378">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="d0c21-379">Sonraki sayfada, WCF Hizmetleri olarak göstermek istediğiniz yöntemi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-379">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="d0c21-380">COM+ uygulamasındaki tüm desteklenen yöntemler varsayılan olarak görüntülenir ve seçilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-380">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="d0c21-381">Bir barındırma yöntemi seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-381">Choose a hosting method.</span></span>

5. <span data-ttu-id="d0c21-382">Sihirbazdaki kılavuzlara göre diğer ayarları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-382">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="d0c21-383">Hizmet yapılandırma Düzenleyicisi, yapılandırma dosyası oluşturmak için arka planda ComSvcConfig.exe kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-383">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="d0c21-384">Bu tamamlandıktan sonra bir özeti görüntüleyebilir ve sihirbazdan çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-384">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="d0c21-385">Oluşturulan yapılandırma dosyası, doğrudan düzenleyebilmeniz için açılır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-385">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="d0c21-386">Var olan bir COM+ yapılandırmasını düzenle</span><span class="sxs-lookup"><span data-stu-id="d0c21-386">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="d0c21-387">**Dosya** menüsünü seçin-> **Open**  ->  **com+ hizmetini**açın...</span><span class="sxs-lookup"><span data-stu-id="d0c21-387">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="d0c21-388">Listeden düzenlemek istediğiniz COM+ hizmetini seçin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-388">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="d0c21-389">**Com sözleşmeleri** düğümündeki yapılandırma ayarlarını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="d0c21-389">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0c21-390">Ayrıca, COM sözleşmeleri içeren bir yapılandırma dosyasını doğrudan açabilir ve düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0c21-390">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="d0c21-391">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="d0c21-391">Security</span></span>

<span data-ttu-id="d0c21-392">Yapılandırma Düzenleyicisi tarafından oluşturulan bir hizmet yapılandırma dosyasının güvenli olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-392">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="d0c21-393">WCF hizmetlerinizi güvenli hale getirme hakkında bilgi edinmek için lütfen [güvenlik](./feature-details/security.md) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="d0c21-393">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="d0c21-394">Ayrıca, yapılandırma Düzenleyicisi yalnızca geçerli WCF yapılandırma öğelerini okumak ve yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c21-394">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="d0c21-395">Araç, şema uyumlu, Kullanıcı tanımlı öğeleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="d0c21-395">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="d0c21-396">Ayrıca, bu öğeleri yapılandırma dosyasından kaldırmayı veya bilinen WCF öğelerinde etkilerini belirlemeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="d0c21-396">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="d0c21-397">Bu öğelerin uygulama veya sistem için tehdit oluşturmadığını belirleme kullanıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="d0c21-397">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
