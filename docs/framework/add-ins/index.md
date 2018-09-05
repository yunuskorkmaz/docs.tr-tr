---
title: Eklentiler ve Genişletilebilirlik
ms.date: 03/30/2017
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510060"
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="b7325-102">Eklentiler ve Genişletilebilirlik</span><span class="sxs-lookup"><span data-stu-id="b7325-102">Add-ins and Extensibility</span></span>
<a name="top"></a> <span data-ttu-id="b7325-103">Genişletilmiş özellikler veya hizmetler bir Windows uygulaması için eklentiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="b7325-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Geliştiriciler eklentileri geliştirmek ve bunları ana bilgisayar uygulamalarını etkinleştirmek için kullanabileceğiniz bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="b7325-105">Model bir ana bilgisayar ile eklenti arasındaki iletişim hattının oluşturularak elde eder.</span><span class="sxs-lookup"><span data-stu-id="b7325-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="b7325-106">Model türleri kullanarak uygulanan <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, ve <xref:System.AddIn.Contract> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="b7325-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="b7325-107">Bu genel bakış aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b7325-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="b7325-108">Eklenti modeli</span><span class="sxs-lookup"><span data-stu-id="b7325-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="b7325-109">Eklentiler ve konaklar arasında ayrım</span><span class="sxs-lookup"><span data-stu-id="b7325-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="b7325-110">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="b7325-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="b7325-111">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b7325-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="b7325-112">Yapı ardışık'ın eklenti ek örnek kodlar ve müşteri teknolojisi önizlemeler araçların bulabilirsiniz [CodePlex üzerinde Yönetilen Genişletilebilirlik ve eklenti Framework site](https://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="b7325-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="b7325-113">Eklenti modeli</span><span class="sxs-lookup"><span data-stu-id="b7325-113">Add-in Model</span></span>  
 <span data-ttu-id="b7325-114">Bir dizi eklenti ile ana bilgisayar arasındaki tüm iletişim için sorumlu eklenti işlem hattı (iletişim kanalı olarak da bilinir) oluşturan parçaların eklenti modeli oluşur.</span><span class="sxs-lookup"><span data-stu-id="b7325-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="b7325-115">İşlem hattı, bir eklenti ile bunun konağı arasında veri değişimi segmentleri simetrik iletişim modelidir.</span><span class="sxs-lookup"><span data-stu-id="b7325-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="b7325-116">Konak ve eklenti arasındaki bu parçaları geliştirme, sürüm oluşturma desteği gerekli Soyutlama Katmanı ve eklentinin yalıtım sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="b7325-117">Aşağıdaki resimde, işlem hattı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7325-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="b7325-118">![Ekleme&#45;işlem hattı modelinde. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="b7325-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="b7325-119">Eklenti ardışık düzeni</span><span class="sxs-lookup"><span data-stu-id="b7325-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="b7325-120">Bu kesimler için derlemeleri, aynı uygulama etki alanında olması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7325-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="b7325-121">Bir eklenti kendi yeni bir uygulama etki alanına, var olan bir uygulama etki alanına veya ana bilgisayarın uygulama etki alanına da yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7325-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="b7325-122">Kaynaklar ve güvenlik kapsamlarını paylaşmak add-INS sağlayan aynı uygulama etki alanına, birden çok eklentileri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b7325-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="b7325-123">Eklenti modeli destekler ve önerir, konak ve yalıtım sınırı (uzaktan iletişim sınırı olarak da bilinir) olarak adlandırılan eklentiyi arasında isteğe bağlı bir sınır.</span><span class="sxs-lookup"><span data-stu-id="b7325-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="b7325-124">Bu sınır bir uygulama etki alanı ya da işlem sınırı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7325-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="b7325-125">İşlem hattı ortasında sözleşme kesim ana bilgisayarın uygulama etki alanı ve eklentinin uygulama etki alanı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b7325-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="b7325-126">Sözleşme sanal yöntemleri tanımlar, konak ve türleri birbirleriyle exchange için eklenti kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7325-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="b7325-127">Yalıtım sınırı geçmek için türler sözleşmeleri veya serializable türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7325-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="b7325-128">Sözleşmeleri olmayan türler veya serializable türler işlem hattındaki bağdaştırıcısı parçaları tarafından sözleşmelerine dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7325-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="b7325-129">Görünüm işlem hattının soyut taban sınıfları veya konak ve eklenti anlaşma tarafından tanımlandığı şekilde paylaşırlar, yöntem bir görünümünü sağlamak arabirimleri segmentler.</span><span class="sxs-lookup"><span data-stu-id="b7325-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="b7325-130">Geliştirme hakkında daha fazla bilgi için ardışık düzen segmentleri, bkz: [ardışık düzen geliştirme](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="b7325-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="b7325-131">Aşağıdaki bölümlerde, eklenti modeli özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7325-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="b7325-132">Bağımsız bir sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7325-132">Independent Versioning</span></span>  
 <span data-ttu-id="b7325-133">Eklenti modeli ana bilgisayarlar ve eklentiler sürüme bağımsız olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="b7325-134">Sonuç olarak, aşağıdaki senaryolarda eklenti modeli sağlar:</span><span class="sxs-lookup"><span data-stu-id="b7325-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="b7325-135">Bir bağdaştırıcı oluşturma, bir konağın konak önceki bir sürümü için yerleşik bir eklenti kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="b7325-136">Bir bağdaştırıcı oluşturma, bir konağın konak daha sonraki bir sürümüyle oluşturulmuş bir eklenti kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7325-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="b7325-137">Add-INS kullanmak bir konak sağlayan bir bağdaştırıcı oluşturma için farklı bir konak üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b7325-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="b7325-138">Bulma ve etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b7325-138">Discovery and Activation</span></span>  
 <span data-ttu-id="b7325-139">Bir eklenti, bir bilgi deposundan bulunan eklentileri temsil eden bir koleksiyondan bir belirteç kullanarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7325-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="b7325-140">Eklentileri eklenti konağın görünümü tanımlayan türü için arama yaparak bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="b7325-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="b7325-141">Bir özel eklenti tarafından eklentiyi tanımlayan tür bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7325-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="b7325-142">Bilgi deposunu iki önbellek dosyalardan oluşur: işlem hattı mağazaya ve eklenti.</span><span class="sxs-lookup"><span data-stu-id="b7325-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="b7325-143">Güncelleştirme ve bilgi deposunu yeniden oluşturma hakkında daha fazla bilgi için bkz: [eklenti bulma](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="b7325-143">For information about updating and rebuilding the information store, see [Add-in Discovery](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="b7325-144">Eklentileri etkinleştirme hakkında daha fazla bilgi için bkz: [eklenti etkinleştirme](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) ve [nasıl yapılır: eklentileri farklı yalıtım ve güvenlik ile etkinleştirme](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="b7325-144">For information about activating add-ins, see [Add-in Activation](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="b7325-145">Yalıtım düzeyleri ve dış işlemleri</span><span class="sxs-lookup"><span data-stu-id="b7325-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="b7325-146">Eklenti modeli birkaç eklentileri veya bir eklenti ile bunun konağı arasında yalıtım düzeyini destekler. Az yalıtılmış başlayarak, bu düzeyler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7325-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="b7325-147">Eklenti aynı uygulama etki alanı konağı olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b7325-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="b7325-148">Yalıtım ve farklı uygulama etki alanları kullandığınızda aldığınız kaldırma özellikleri kaybetmek nedeniyle bu önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b7325-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="b7325-149">Birden çok eklentileri, ana bilgisayar tarafından kullanılan uygulama etki alanından farklı aynı uygulama etki alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b7325-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="b7325-150">Her eklenti yalnızca kendi uygulama etki alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b7325-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="b7325-151">Bu yalıtım en genel düzeydir.</span><span class="sxs-lookup"><span data-stu-id="b7325-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="b7325-152">Birden çok eklentileri, bir dış işlem aynı uygulama etki alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b7325-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="b7325-153">Her eklenti yalnızca bir dış işlem kendi uygulama etki alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b7325-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="b7325-154">Bu en yalıtılmış bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="b7325-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="b7325-155">Dış işlemlere kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: eklentileri farklı yalıtım ve güvenlik ile etkinleştirme](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="b7325-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="b7325-156">Ömür Yönetimi</span><span class="sxs-lookup"><span data-stu-id="b7325-156">Lifetime Management</span></span>  
 <span data-ttu-id="b7325-157">Uygulama etki alanı ve işlem sınırları eklenti modeli yayılan olduğundan, çöp toplamanın kendisini bırakın ve nesneleri geri kazanmak için yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="b7325-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="b7325-158">Eklenti modeli belirteçleri ve başvuru sayımı kullanan bir ömrü Yönetimi mekanizması sağlar ve ek programlama genellikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7325-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="b7325-159">Daha fazla bilgi için [ömür Yönetimi](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="b7325-159">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="b7325-160">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b7325-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="b7325-161">Eklentiler ve konaklar arasında ayrım</span><span class="sxs-lookup"><span data-stu-id="b7325-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="b7325-162">Bir eklenti ile ana bilgisayar arasındaki fark yalnızca konak eklentiyi etkinleştirir bir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b7325-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="b7325-163">Konak bir sözcük işleme uygulama ve onun yazım denetleyicileri gibi iki büyük olabilir. veya konağın bir medya yürütücüsü katıştıran anlık ileti istemcisi gibi iki daha küçük olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7325-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="b7325-164">Eklenti modeli, hem istemci hem de sunucu senaryolarda eklentileri destekler.</span><span class="sxs-lookup"><span data-stu-id="b7325-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="b7325-165">Posta sunucuları virüs taraması, istenmeyen posta filtreleri ve IP koruma sağlayan eklentileri sunucu eklentileri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="b7325-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="b7325-166">İstemci eklentisi için sözcük işlemci, grafik programı, oyunlar ve virüs taraması için yerel e-posta istemcileri için özelleştirilmiş bir Özellik Başvurusu eklentileri örneklerindendir.</span><span class="sxs-lookup"><span data-stu-id="b7325-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local email clients.</span></span>  
  
 [<span data-ttu-id="b7325-167">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b7325-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="b7325-168">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="b7325-168">Related Topics</span></span>  
  
|<span data-ttu-id="b7325-169">Başlık</span><span class="sxs-lookup"><span data-stu-id="b7325-169">Title</span></span>|<span data-ttu-id="b7325-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7325-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b7325-171">İşlem Hattı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b7325-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="b7325-172">Eklentinin ana bilgisayar uygulamasına kesimlerinden iletişim hattının açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7325-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="b7325-173">İşlem hattı oluşturmak ve parçaları Visual Studio'da işlem hattını dağıtmak anlatan izlenecek yol konuları kod örnekleri sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7325-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in Visual Studio.</span></span>|  
|[<span data-ttu-id="b7325-174">Uygulama Etki Alanları ve Derlemeler</span><span class="sxs-lookup"><span data-stu-id="b7325-174">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="b7325-175">Güvenlik, güvenilirlik ve sürüm oluşturma için bir yalıtım sınırı sağlar uygulama etki alanları ve derlemeler arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7325-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="b7325-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b7325-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="b7325-177">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b7325-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="b7325-178">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b7325-178">Back to top</span></span>](#top)