---
title: 'Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b6f010cb5edc3111f05c78f5d27cf178bd501ef9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326430"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="47052-102">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="47052-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="47052-103">Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamalar <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve yavaş başlatma performansı düşürebilir çalışma zamanında bu veri türleri için serileştirme kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="47052-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47052-104">Önceden oluşturulan serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47052-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="47052-105">[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) derlenmiş bütünleştirilmiş uygulama için gerekli serileştirme kod oluşturarak bu uygulamaları için başlatma performansını geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="47052-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="47052-106">Svcutil.exe kullanarak seri hale getirilebilir derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kod oluşturur <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="47052-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="47052-107">Kullandığınız hizmet ve işlem sözleşmeler <xref:System.Xml.Serialization.XmlSerializer> ile işaretlenmiş <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="47052-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="47052-108">XmlSerializer serileştirme kod oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47052-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="47052-109">Hizmet veya istemci kodunuz, bir veya daha fazla derlemeye derlemesi.</span><span class="sxs-lookup"><span data-stu-id="47052-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="47052-110">Bir SDK komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="47052-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="47052-111">Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe aracını başlatın.</span><span class="sxs-lookup"><span data-stu-id="47052-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="47052-112">`assemblyPath` Bağımsız değişkeni, hizmet sözleşmesi türleri içeren bir bütünleştirilmiş kod yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47052-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="47052-113">Svcutil.exe kullanarak seri hale getirilebilir derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için serileştirme kod oluşturur <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="47052-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="47052-114">Svcutil.exe yalnızca oluşturabileceği C# serileştirme kodu.</span><span class="sxs-lookup"><span data-stu-id="47052-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="47052-115">Giriş her derleme için bir kaynak kodu dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47052-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="47052-116">Kullanamazsınız **/language** oluşturulan kod dilini değiştirmek için anahtar.</span><span class="sxs-lookup"><span data-stu-id="47052-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="47052-117">Bağımlı derlemelerin yolu belirtmek için kullanın **/reference** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="47052-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="47052-118">Aşağıdaki seçeneklerden birini kullanarak oluşturulan serileştirme kodu, uygulamanızın kullanılabilir hale getirmek:</span><span class="sxs-lookup"><span data-stu-id="47052-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="47052-119">Ada sahip ayrı bir derleme halinde oluşturulan serileştirme kodu derleme [*orijinal derleme*]. XmlSerializers.dll (örneğin, MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="47052-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="47052-120">Uygulamanızı orijinal derleme olarak aynı anahtarla imzalanmalıdır derlemeyi yüklemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47052-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="47052-121">Orijinal derlemeyi yeniden derlerseniz, serileştirme bütünleştirilmiş kodu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47052-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="47052-122">Oluşturulan serileştirme kodu ayrı bir derlemeye derlemek ve kullanmak <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanır hizmet sözleşmesindeki <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="47052-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="47052-123">Ayarlama <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> derlenmiş serileştirme derlemeye işaret edecek şekilde özellikleri.</span><span class="sxs-lookup"><span data-stu-id="47052-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="47052-124">Oluşturulan serileştirme kodu, uygulama derlemeye derlemek ve ekleme <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesi <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="47052-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="47052-125">Ayarlı değil <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="47052-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="47052-126">Varsayılan serileştirme bütünleştirilmiş kodu geçerli derleme varsayılır.</span><span class="sxs-lookup"><span data-stu-id="47052-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="47052-127">Visual Studio'da XmlSerializer serileştirme kod oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47052-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="47052-128">WCF hizmeti ve istemcisine Visual Studio'da projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47052-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="47052-129">Ardından, istemci projesinin bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47052-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="47052-130">Ekleme bir <xref:System.ServiceModel.XmlSerializerFormatAttribute> için hizmet sözleşmesi içerisinde *reference.cs* altında istemci uygulaması projenizi dosyasında **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="47052-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="47052-131">Tüm dosyaları göster gerektiğini unutmayın **Çözüm Gezgini** bu dosyaları görmek için.</span><span class="sxs-lookup"><span data-stu-id="47052-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="47052-132">İstemci uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47052-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="47052-133">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) önceden oluşturulmuş bir seri hale getirici oluşturulacak *.cs* komutu kullanarak dosya:</span><span class="sxs-lookup"><span data-stu-id="47052-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="47052-134">WCF istemci derleme yolu assemblyPath bağımsız değişken belirtir.</span><span class="sxs-lookup"><span data-stu-id="47052-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="47052-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="47052-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="47052-136">*WCFClient.XmlSerializers.dll.cs* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47052-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="47052-137">Önceden oluşturulan serileştirme bütünleştirilmiş kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="47052-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="47052-138">Örnek önceki adımda bağlı olarak, derleme komut şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="47052-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="47052-139">Oluşturulan emin *WCFClient.XmlSerializers.dll* olan istemci uygulaması ile aynı dizinde olduğu *WCFClient.exe* böyle bir durumda.</span><span class="sxs-lookup"><span data-stu-id="47052-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="47052-140">İstemci uygulaması her zaman olduğu gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47052-140">Run the client app as usual.</span></span> <span data-ttu-id="47052-141">Önceden oluşturulan serileştirme bütünleştirilmiş kodu kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="47052-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47052-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="47052-142">Example</span></span>  
 <span data-ttu-id="47052-143">Aşağıdaki komutu için seri hale getirme türlerinde oluşturur `XmlSerializer` derleme kullanımda herhangi bir hizmet sözleşmeleri türleri.</span><span class="sxs-lookup"><span data-stu-id="47052-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="47052-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47052-144">See also</span></span>

- [<span data-ttu-id="47052-145">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="47052-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
