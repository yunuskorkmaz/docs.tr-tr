---
title: 'Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 91712963908ecc56ff17fbac028389207544b82f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600263"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="abf92-102">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="abf92-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="abf92-103"><xref:System.Xml.Serialization.XmlSerializer>Çalışma zamanında bu veri türleri için Oluştur ve derle serileştirme kodu kullanılarak seri hale getirilebilir veri türlerini kullanan hizmet ve istemci uygulamaları, yavaş başlangıç performansına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="abf92-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abf92-104">Önceden oluşturulmuş serileştirme kodu, hizmetlerde değil yalnızca istemci uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abf92-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="abf92-105">[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , uygulama için derlenmiş derlemelerden gerekli serileştirme kodunu oluşturarak bu uygulamalar için başlangıç performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="abf92-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="abf92-106">Svcutil. exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="abf92-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="abf92-107">Kullanan hizmet ve işlem sözleşmeleri <xref:System.Xml.Serialization.XmlSerializer> ile işaretlenir <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="abf92-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="abf92-108">XmlSerializer Serileştirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="abf92-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="abf92-109">Hizmetinizi veya istemci kodunuzu bir veya daha fazla derlemede derleyin.</span><span class="sxs-lookup"><span data-stu-id="abf92-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="abf92-110">SDK komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="abf92-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="abf92-111">Komut isteminde, aşağıdaki biçimi kullanarak Svcutil. exe aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="abf92-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="abf92-112">`assemblyPath`Bağımsız değişkeni, hizmet sözleşmesi türlerini içeren bir derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abf92-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="abf92-113">Svcutil. exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="abf92-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="abf92-114">Svcutil. exe yalnızca C# serileştirme kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="abf92-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="abf92-115">Her giriş derlemesi için bir kaynak kodu dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="abf92-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="abf92-116">Oluşturulan kodun dilini değiştirmek için **/Language** anahtarını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="abf92-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="abf92-117">Bağımlı derlemelerin yolunu belirtmek için **/Reference** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="abf92-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="abf92-118">Aşağıdaki seçeneklerden birini kullanarak, üretilen serileştirme kodunu uygulamanız için kullanılabilir hale getirin:</span><span class="sxs-lookup"><span data-stu-id="abf92-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="abf92-119">Oluşturulan serileştirme kodunu, adı [*özgün derleme*] olan ayrı bir derlemede derleyin. Xmlserileştiriciler. dll (örneğin, MyApp. Xmlserileştiriciler. dll).</span><span class="sxs-lookup"><span data-stu-id="abf92-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="abf92-120">Uygulamanız, özgün derlemeyle aynı anahtarla imzalanması gereken derlemeyi yükleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="abf92-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="abf92-121">Özgün derlemeyi yeniden derlemenizin serileştirme derlemesini yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="abf92-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="abf92-122">Oluşturulan serileştirme kodunu ayrı bir derlemede derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesinde kullanın <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="abf92-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="abf92-123"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini derlenen serileştirme derlemesini işaret etmek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="abf92-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="abf92-124">Oluşturulan serileştirme kodunu uygulama derlemenizde derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesine ekleyin <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="abf92-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="abf92-125"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="abf92-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="abf92-126">Varsayılan serileştirme derlemesinin geçerli derleme olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="abf92-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="abf92-127">Visual Studio 'da XmlSerializer Serileştirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="abf92-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="abf92-128">Visual Studio 'da WCF hizmetini ve istemci projelerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abf92-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="abf92-129">Ardından, istemci projesine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf92-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="abf92-130"><xref:System.ServiceModel.XmlSerializerFormatAttribute> *reference.cs* **ServiceReference**  ->  **Reference. svcmap**altındaki istemci uygulaması projesindeki Reference.cs dosyasına hizmet sözleşmesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf92-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="abf92-131">Bu dosyaları görmek için **Çözüm Gezgini** tüm dosyaları göstermesinin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="abf92-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="abf92-132">İstemci uygulamasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abf92-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="abf92-133">Şu komutu kullanarak önceden oluşturulmuş bir seri hale getirici *. cs* dosyası oluşturmak Için [ServiceModel meta veri yardımcı programı aracı 'Nı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="abf92-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="abf92-134">AssemblyPath bağımsız değişkeni, WCF istemci derlemesinin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abf92-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="abf92-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="abf92-135">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="abf92-136">*WCFClient.XmlSerializers.dll.cs* dosyası oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="abf92-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="abf92-137">Önceden oluşturulmuş serileştirme derlemesini derleyin.</span><span class="sxs-lookup"><span data-stu-id="abf92-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="abf92-138">Önceki adımdaki örneğe bağlı olarak, derleme komutu aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="abf92-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="abf92-139">Oluşturulan *Wcfclient. Xmlserileştiriciler. dll dosyasının* bu durumda *wcfclient. exe* olan istemci uygulamasıyla aynı dizinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="abf92-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="abf92-140">İstemci uygulamasını her zamanki gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abf92-140">Run the client app as usual.</span></span> <span data-ttu-id="abf92-141">Önceden oluşturulmuş serileştirme derlemesi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="abf92-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf92-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf92-142">Example</span></span>  
 <span data-ttu-id="abf92-143">Aşağıdaki komut, `XmlSerializer` derlemedeki herhangi bir hizmet sözleşmesi tarafından kullanılan türler için serileştirme türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf92-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf92-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf92-144">See also</span></span>

- [<span data-ttu-id="abf92-145">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="abf92-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
