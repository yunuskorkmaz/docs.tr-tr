---
title: "Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2ac51a99db002633aaf80070d8820ce6e3144a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="63dcc-102">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="63dcc-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="63dcc-103">Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamaları <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında veri türleri için seri hale getirme kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="63dcc-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63dcc-104">Önceden oluşturulmuş serileştirme kod yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="63dcc-105">[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="63dcc-106">Svcutil.exe oluşturur kullanılarak serileştirilmiş derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için seri hale getirme kodu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="63dcc-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="63dcc-107">Kullandığınız hizmet ve işlem sözleşmeler <xref:System.Xml.Serialization.XmlSerializer> işaretlenir <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63dcc-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="63dcc-108">XmlSerializer seri hale getirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="63dcc-108">To generate XmlSerializer serialization code</span></span>  
  
1.  <span data-ttu-id="63dcc-109">Hizmet veya istemci kodunuzun bir veya daha fazla derlemeye derlemesi.</span><span class="sxs-lookup"><span data-stu-id="63dcc-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2.  <span data-ttu-id="63dcc-110">SDK komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="63dcc-110">Open an SDK command prompt.</span></span>  
  
3.  <span data-ttu-id="63dcc-111">Komut isteminde, aşağıdaki biçimi kullanarak Svcutil.exe Aracı'nı başlatın.</span><span class="sxs-lookup"><span data-stu-id="63dcc-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="63dcc-112">`assemblyPath` Bağımsız değişkeni hizmet sözleşmesi türlerini içeren bir derleme yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="63dcc-113">Svcutil.exe oluşturur kullanılarak serileştirilmiş derlenmiş uygulama derlemesindeki hizmet sözleşmelerinde kullanılan tüm veri türleri için seri hale getirme kodu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="63dcc-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="63dcc-114">Svcutil.exe yalnızca C# seri hale getirme kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="63dcc-115">Bir kaynak kodu dosyasının her giriş derlemesi için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63dcc-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="63dcc-116">Kullanamazsınız **/language** oluşturulan kod dilini değiştirmek için anahtar.</span><span class="sxs-lookup"><span data-stu-id="63dcc-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="63dcc-117">Bağımlı derlemeleri yolunu belirtmek için kullanın **/reference** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="63dcc-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4.  <span data-ttu-id="63dcc-118">Aşağıdaki seçeneklerden birini kullanarak oluşturulan seri hale getirme kodu uygulamanız için kullanılabilir hale getirmek:</span><span class="sxs-lookup"><span data-stu-id="63dcc-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="63dcc-119">Adlı ayrı bir derleme halinde üretilen seri hale getirme kodu derleme [*özgün derleme*]. XmlSerializers.dll (örneğin, MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="63dcc-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="63dcc-120">Uygulamanızı özgün derlemesi aynı anahtarla imzalanmalıdır derlemeyi yüklemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="63dcc-121">Özgün derleme yeniden derleyin, seri hale getirme derlemesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="63dcc-122">Ayrı bir derleme üretilen seri hale getirme Kodu derlemek ve kullanmak <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesinde <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63dcc-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="63dcc-123">Ayarlama <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> derlenmiş serileştirme derlemeye işaret edecek şekilde özellikleri.</span><span class="sxs-lookup"><span data-stu-id="63dcc-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="63dcc-124">Uygulama derlemeye üretilen seri hale getirme Kodu derlemek ve ekleme <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kullanan hizmet sözleşmesi <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63dcc-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="63dcc-125">Ayarlamayın <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> veya <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="63dcc-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="63dcc-126">Varsayılan seri hale getirme derlemesi geçerli derleme olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="63dcc-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="63dcc-127">Visual Studio'da XmlSerializer seri hale getirme kodu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="63dcc-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1.  <span data-ttu-id="63dcc-128">WCF hizmeti ve istemci Visual Studio'da projeler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63dcc-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="63dcc-129">Ardından, istemci projesine hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63dcc-129">Then, add a service reference to the client project.</span></span>  
  
2.  <span data-ttu-id="63dcc-130">Ekleme bir <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesi için *reference.cs* altında istemci uygulaması proje dosyasında **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="63dcc-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="63dcc-131">Tüm dosyaları göster gerektiğini unutmayın **Çözüm Gezgini** bu dosyaları görmek için.</span><span class="sxs-lookup"><span data-stu-id="63dcc-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3.  <span data-ttu-id="63dcc-132">İstemci uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="63dcc-132">Build the client app.</span></span>  
  
4.  <span data-ttu-id="63dcc-133">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) önceden oluşturulmuş bir seri hale getirici oluşturmak için *.cs* komutunu kullanarak dosya:</span><span class="sxs-lookup"><span data-stu-id="63dcc-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="63dcc-134">AssemblyPath bağımsız değişkeni WCF istemci derleme yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="63dcc-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="63dcc-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="63dcc-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="63dcc-136">*WCFClient.XmlSerializers.dll.cs* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63dcc-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5.  <span data-ttu-id="63dcc-137">Önceden oluşturulmuş seri hale getirme derlemesi derleyin.</span><span class="sxs-lookup"><span data-stu-id="63dcc-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="63dcc-138">Örnek önceki adımda bağlı olarak, derleme komut aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="63dcc-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="63dcc-139">Oluşturulan emin olun *WCFClient.XmlSerializers.dll* olan istemci uygulaması ile aynı dizinde yer *WCFClient.exe* bu durumda.</span><span class="sxs-lookup"><span data-stu-id="63dcc-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6.  <span data-ttu-id="63dcc-140">İstemci uygulamayı her zamanki gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63dcc-140">Run the client app as usual.</span></span> <span data-ttu-id="63dcc-141">Önceden oluşturulmuş seri hale getirme derlemesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63dcc-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63dcc-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="63dcc-142">Example</span></span>  
 <span data-ttu-id="63dcc-143">Aşağıdaki komut, seri hale getirme türlerinde oluşturur `XmlSerializer` derleme kullanımda herhangi bir hizmet sözleşmeleri türleri.</span><span class="sxs-lookup"><span data-stu-id="63dcc-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="63dcc-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63dcc-144">See Also</span></span>  
 [<span data-ttu-id="63dcc-145">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="63dcc-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
