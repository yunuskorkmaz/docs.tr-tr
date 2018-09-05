---
title: Başlarken Öğreticisi Sorun Giderme
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 43128743ba16aefc8669ace85070a16d80145a71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519427"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a><span data-ttu-id="43e75-102">Başlarken Öğreticisi Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="43e75-102">Troubleshooting the Getting Started Tutorial</span></span>
<span data-ttu-id="43e75-103">Bu konuda bunların nasıl çözüleceğine ile çalışmaya başlama Öğreticisi ile çalışırken en sık karşılaşılan sorunlar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="43e75-103">This topic lists the most common problems encountered when working through the Getting Started Tutorial and how to resolve them.</span></span>  
  
<span data-ttu-id="43e75-104">**Sabit Sürücümün proje dosyalarını bulmak oluşturamıyorum.**</span><span class="sxs-lookup"><span data-stu-id="43e75-104">**I am unable to find the project files on my hard drive.**</span></span>

 <span data-ttu-id="43e75-105">Visual Studio, proje dosyaları içinde c:\users kaydeder\\<user name>\Documents\\< Visual Studio sürümü\>\Projects.</span><span class="sxs-lookup"><span data-stu-id="43e75-105">Visual Studio saves project files in c:\users\\<user name>\Documents\\<Visual Studio version\>\Projects.</span></span>  
  
<span data-ttu-id="43e75-106">**Hizmet uygulaması çalıştırma denemesi: HTTP URL'si kaydedemedi `http://+:8000/ServiceModelSamples/Service/`.** 
 **İşleminizi bu ad alanı için erişim haklarına sahip değil.**</span><span class="sxs-lookup"><span data-stu-id="43e75-106">**Attempting to run the service application: HTTP could not register URL `http://+:8000/ServiceModelSamples/Service/`.**
**Your process does not have access rights to this namespace.**</span></span> 

 <span data-ttu-id="43e75-107">Bir WCF hizmetini barındıran işlemi yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43e75-107">The process that hosts a WCF service must be run with Administrative privileges.</span></span> <span data-ttu-id="43e75-108">Hizmet çalışıyorsa, gelen Visual Studio içinde Visual Studio'yu yönetici olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43e75-108">If you are running the service from inside Visual Studio, you must run Visual Studio as an Administrator.</span></span> <span data-ttu-id="43e75-109">Bunu yapmak için **Başlat**, sağ **Visual Studio \< *sürüm* >**  seçip **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="43e75-109">To do so click **Start**, right-click **Visual Studio \<*version*>** and select **Run As Administrator**.</span></span> <span data-ttu-id="43e75-110">Konsol penceresinde komut satırı isteminden hizmeti çalıştırıyorsanız, konsol penceresinde benzer şekilde bir yönetici olarak başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43e75-110">If you are running the service from a command-line prompt in a console window, you must start the console window as an Administrator in a similar way.</span></span> <span data-ttu-id="43e75-111">Tıklayın **Başlat**, sağ **komut istemi** seçip **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="43e75-111">Click **Start**, right-click **Command Prompt** and select **Run As Administrator**.</span></span>  
  
<span data-ttu-id="43e75-112">**Svcutil.exe aracını çalışılıyor: 'svcutil' iç ya da dış komut, çalıştırılabilir program ya da toplu iş dosyası tanınmıyor.**</span><span class="sxs-lookup"><span data-stu-id="43e75-112">**Attempting to use the Svcutil.exe tool: 'svcutil' is not recognized as an internal or external command, operable program or batch file.**</span></span>

 <span data-ttu-id="43e75-113">Svcutil.exe sistem yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43e75-113">Svcutil.exe must be in the system path.</span></span> <span data-ttu-id="43e75-114">Kolay çözümü, komut istemini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="43e75-114">The easiest solution is to use the Command Prompt.</span></span> <span data-ttu-id="43e75-115">Tıklayın **Başlat**seçin **tüm programlar**, **Visual Studio \< *sürüm*>**,  **Visual Studio Araçları**, ve **Visual Studio için geliştirici komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="43e75-115">Click **Start**, select **All Programs**, **Visual Studio \<*version*>**, **Visual Studio Tools**, and **Developer Command Prompt for Visual Studio**.</span></span> <span data-ttu-id="43e75-116">Bu komut istemi, Visual Studio'nun bir parçası olarak gönderildiğini tüm araçları için doğru konuma sistem yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="43e75-116">This command prompt sets the system path to the correct locations for all tools shipped as part of Visual Studio.</span></span>  

<span data-ttu-id="43e75-117">**Svcutil.exe'yi oluşturulan App.config dosyasını bulmak yüklenemiyor.**</span><span class="sxs-lookup"><span data-stu-id="43e75-117">**Unable to find the App.config file generated by Svcutil.exe.**</span></span>

 <span data-ttu-id="43e75-118">**Varolan öğeyi Ekle** iletişim varsayılan olarak yalnızca şu uzantılara sahip dosyaları görüntüler: .cs, .resx, .settings, .xsd, .wsdl.</span><span class="sxs-lookup"><span data-stu-id="43e75-118">The **Add Existing Item** dialog only displays files with the following extensions by default: .cs, .resx, .settings, .xsd, .wsdl.</span></span> <span data-ttu-id="43e75-119">Tüm dosya türlerini seçerek görmek istediğinizi belirtebilirsiniz **tüm dosyalar (\*.\*)**  alt sağ köşesinde aşağı açılan liste kutusunda **varolan öğeyi Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="43e75-119">You can specify that you want to see all file types by selecting **All Files (\*.\*)** in the drop-down list box in the lower right corner of the **Add Existing Item** dialog box.</span></span>  


<span data-ttu-id="43e75-120">**İstemci uygulaması derleme: 'CalculatorClient' için bir tanım içermiyor '\<yöntem adı >' ve hiçbir genişletme yönteminin '\<yöntem adı >' 'CalculatorClient' türünde bir ilk bağımsız değişken kabul eden bulunamadı (olduğunuz eksik bir kullanma yönergeniz veya derleme başvurunuz?)**</span><span class="sxs-lookup"><span data-stu-id="43e75-120">**Compiling the client application: 'CalculatorClient' does not contain a definition for '\<method name>' and no extension method '\<method name>' accepting a first argument of type 'CalculatorClient' could be found (are you missing a using directive or an assembly reference?)**</span></span>  

<span data-ttu-id="43e75-121">İle işaretlenmiş yöntemler `ServiceOperationAttribute` dışında tüm dünyada kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="43e75-121">Only those methods that are marked with the `ServiceOperationAttribute` are exposed to the outside world.</span></span> <span data-ttu-id="43e75-122">Kaçırdıysanız `ServiceOperationAttribute` metotlarından birini özniteliğinden `ICalculator` arabirimi, bu hata iletisini özniteliği eksik işlemi çağrıda bir istemci uygulaması derlerken alın.</span><span class="sxs-lookup"><span data-stu-id="43e75-122">If you omitted the `ServiceOperationAttribute` attribute from one of the methods in the `ICalculator` interface, you get this error message when compiling a client application that makes a call to the operation missing the attribute.</span></span>  

<span data-ttu-id="43e75-123">**İstemci uygulaması derleme: 'CalculatorClient' bulunamadı tür veya ad alanı adı (bir using eksik yönergeniz veya derleme başvurunuz?)**</span><span class="sxs-lookup"><span data-stu-id="43e75-123">**Compiling the client application: The type or namespace name 'CalculatorClient' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

 <span data-ttu-id="43e75-124">İstemci projenize Proxy.cs veya Proxy.vb dosya eklemezseniz bu hatayı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="43e75-124">You get this error if you do not add the Proxy.cs or Proxy.vb file to your client project.</span></span>  

<span data-ttu-id="43e75-125">**İstemcisi çalıştıran: işlenmeyen özel durum: System.ServiceModel.EndpointNotFoundException: bağlanamadı `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP hata kodu 10061: hedef makine etkin olarak reddettiğinden hiçbir bağlantı kurulamadı.**</span><span class="sxs-lookup"><span data-stu-id="43e75-125">**Running the client: Unhandled Exception: System.ServiceModel.EndpointNotFoundException: Could not connect to `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP error code 10061: No connection could be made because the target machine actively refused it.**</span></span>

<span data-ttu-id="43e75-126">Hizmet çalıştırmadan istemci uygulaması, bu hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="43e75-126">This error occurs if you run the client application without running the service.</span></span>  
  
<span data-ttu-id="43e75-127">**İşlenmeyen özel durum: System.ServiceModel.Security.SecurityNegotiationException: SOAP güvenlik anlaşması `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` hedefi için `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` başarısız oldu**</span><span class="sxs-lookup"><span data-stu-id="43e75-127">**Unhandled Exception: System.ServiceModel.Security.SecurityNegotiationException: SOAP security negotiation with `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` for target `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` failed**</span></span>  

<span data-ttu-id="43e75-128">Ağ bağlantısı yok. etki alanına katılmış bir bilgisayarda bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="43e75-128">This error occurs on a domain-joined computer that does not have network connectivity.</span></span> <span data-ttu-id="43e75-129">Bilgisayarınız ağa bağlanmak veya hem istemci hem de hizmet için güvenliği devre dışı.</span><span class="sxs-lookup"><span data-stu-id="43e75-129">Either connect your computer to the network or turn off security for both the client and the service.</span></span> <span data-ttu-id="43e75-130">Hizmet için şu WSHttpBinding oluşturan kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43e75-130">For the service, modify the code that creates the WSHttpBinding to the following.</span></span>  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

<span data-ttu-id="43e75-131">İstemci için değiştirme  **\<Güvenlik >** öğesi altında  **\<bağlama >** aşağıdaki öğe:</span><span class="sxs-lookup"><span data-stu-id="43e75-131">For the client, change the **\<security>** element under the **\<binding>** element to the following:</span></span>  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a><span data-ttu-id="43e75-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43e75-132">See Also</span></span>  
 [<span data-ttu-id="43e75-133">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="43e75-133">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="43e75-134">WCF Sorun Giderme Hızlı Başlangıcı</span><span class="sxs-lookup"><span data-stu-id="43e75-134">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [<span data-ttu-id="43e75-135">Kurulum Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="43e75-135">Troubleshooting Setup Issues</span></span>](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
