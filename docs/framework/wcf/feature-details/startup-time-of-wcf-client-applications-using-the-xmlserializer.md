---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: XmlSerializer kullanarak WCF Istemci uygulamalarının başlangıç zamanını geliştirme'
title: 'Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 8cf46cc35753934e8f4cb3abadc20c912e9efca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793408"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="54982-103">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="54982-103">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>

<span data-ttu-id="54982-104"><xref:System.Xml.Serialization.XmlSerializer>Çalışma zamanında bu veri türleri için Oluştur ve derle serileştirme kodu kullanılarak seri hale getirilebilir veri türlerini kullanan hizmet ve istemci uygulamaları, yavaş başlangıç performansına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="54982-104">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54982-105">Önceden oluşturulmuş serileştirme kodu, hizmetlerde değil yalnızca istemci uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54982-105">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="54982-106">[ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , uygulama için derlenmiş derlemelerden gerekli serileştirme kodu oluşturarak bu uygulamalar için başlangıç performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="54982-106">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="54982-107">Svcutil.exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="54982-107">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="54982-108">Kullanan hizmet ve işlem sözleşmeleri <xref:System.Xml.Serialization.XmlSerializer> ile işaretlenir <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="54982-108">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="54982-109">XmlSerializer Serileştirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54982-109">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="54982-110">Hizmetinizi veya istemci kodunuzu bir veya daha fazla derlemede derleyin.</span><span class="sxs-lookup"><span data-stu-id="54982-110">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="54982-111">SDK komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="54982-111">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="54982-112">Komut isteminde aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="54982-112">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="54982-113">`assemblyPath`Bağımsız değişkeni, hizmet sözleşmesi türlerini içeren bir derlemenin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="54982-113">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="54982-114">Svcutil.exe, kullanılarak seri hale getirilenebilecek derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="54982-114">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="54982-115">Svcutil.exe yalnızca C# serileştirme kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="54982-115">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="54982-116">Her giriş derlemesi için bir kaynak kodu dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54982-116">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="54982-117">Oluşturulan kodun dilini değiştirmek için **/Language** anahtarını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="54982-117">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="54982-118">Bağımlı derlemelerin yolunu belirtmek için **/Reference** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54982-118">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="54982-119">Aşağıdaki seçeneklerden birini kullanarak, üretilen serileştirme kodunu uygulamanız için kullanılabilir hale getirin:</span><span class="sxs-lookup"><span data-stu-id="54982-119">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="54982-120">Oluşturulan serileştirme kodunu, adı [*özgün derleme*] .XmlSerializers.dll (örneğin, MyApp.XmlSerializers.dll) ayrı bir derlemede derleyin.</span><span class="sxs-lookup"><span data-stu-id="54982-120">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="54982-121">Uygulamanız, özgün derlemeyle aynı anahtarla imzalanması gereken derlemeyi yükleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="54982-121">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="54982-122">Özgün derlemeyi yeniden derlemenizin serileştirme derlemesini yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="54982-122">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="54982-123">Oluşturulan serileştirme kodunu ayrı bir derlemede derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesinde kullanın <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="54982-123">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="54982-124"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini derlenen serileştirme derlemesini işaret etmek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54982-124">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="54982-125">Oluşturulan serileştirme kodunu uygulama derlemenizde derleyin ve öğesini <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesine ekleyin <xref:System.ServiceModel.XmlSerializerFormatAttribute> .</span><span class="sxs-lookup"><span data-stu-id="54982-125">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="54982-126"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>Veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özelliklerini ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="54982-126">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="54982-127">Varsayılan serileştirme derlemesinin geçerli derleme olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="54982-127">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="54982-128">Visual Studio 'da XmlSerializer Serileştirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="54982-128">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="54982-129">Visual Studio 'da WCF hizmetini ve istemci projelerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54982-129">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="54982-130">Ardından, istemci projesine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54982-130">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="54982-131"><xref:System.ServiceModel.XmlSerializerFormatAttribute>  **ServiceReference**  ->  **Reference. svcmap** altındaki istemci uygulaması projesindeki Reference.cs dosyasına hizmet sözleşmesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54982-131">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="54982-132">Bu dosyaları görmek için **Çözüm Gezgini** tüm dosyaları göstermesinin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="54982-132">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="54982-133">İstemci uygulamasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54982-133">Build the client app.</span></span>  
  
4. <span data-ttu-id="54982-134">Şu komutu kullanarak önceden oluşturulmuş bir seri hale getirici *. cs* dosyası oluşturmak Için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="54982-134">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="54982-135">AssemblyPath bağımsız değişkeni, WCF istemci derlemesinin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="54982-135">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="54982-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="54982-136">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="54982-137">*WCFClient.XmlSerializers.dll. cs* dosyası oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="54982-137">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="54982-138">Önceden oluşturulmuş serileştirme derlemesini derleyin.</span><span class="sxs-lookup"><span data-stu-id="54982-138">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="54982-139">Önceki adımdaki örneğe bağlı olarak, derleme komutu aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="54982-139">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="54982-140">Oluşturulan *WCFClient.XmlSerializers.dll* , bu durumda *WCFClient.exe* istemci uygulamasıyla aynı dizinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54982-140">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="54982-141">İstemci uygulamasını her zamanki gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="54982-141">Run the client app as usual.</span></span> <span data-ttu-id="54982-142">Önceden oluşturulmuş serileştirme derlemesi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="54982-142">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54982-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="54982-143">Example</span></span>  

 <span data-ttu-id="54982-144">Aşağıdaki komut, `XmlSerializer` derlemedeki herhangi bir hizmet sözleşmesi tarafından kullanılan türler için serileştirme türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54982-144">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="54982-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54982-145">See also</span></span>

- [<span data-ttu-id="54982-146">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="54982-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
