---
title: 'Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 61f5f0f3ec9a4386fa12e7511b4a518f2b56a21c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123661"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="1bf22-102">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1bf22-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="1bf22-103">.NET Framework tabanlı bileşenlere yönelik kayıt için ücretsiz etkinleştirme, COM bileşenleri için olduğundan biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="1bf22-104">Kurulum için iki bildirim gerekir:</span><span class="sxs-lookup"><span data-stu-id="1bf22-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="1bf22-105">COM uygulamalarının, yönetilen bileşeni tanımlamak için bir Win32 stili uygulama bildirimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="1bf22-106">.NET Framework tabanlı bileşenlerin, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen bildirimine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="1bf22-107">Bu konu, uygulama bildiriminin bir uygulamayla nasıl ilişkilendirileceğini açıklar; bileşen bildirimini bir bileşeniyle ilişkilendirin; ve bir derlemeye bileşen bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bf22-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="1bf22-108">Uygulama bildirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1bf22-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="1bf22-109">Bir XML Düzenleyicisi kullanarak, bir veya daha fazla yönetilen bileşenle birlikte bulunan COM uygulamasına ait uygulama bildirimini oluşturun (veya değiştirin).</span><span class="sxs-lookup"><span data-stu-id="1bf22-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="1bf22-110">Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bf22-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="1bf22-111">Bildirim öğeleri ve öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="1bf22-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="1bf22-112">Bildirimin sahibini belirler.</span><span class="sxs-lookup"><span data-stu-id="1bf22-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="1bf22-113">Aşağıdaki örnekte, `myComApp` sürüm 1 ' ın bildirim dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. <span data-ttu-id="1bf22-114">Bağımlı derlemeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="1bf22-114">Identify dependent assemblies.</span></span> <span data-ttu-id="1bf22-115">Aşağıdaki örnekte, `myComApp` `myManagedComp`bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="1bf22-116">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1bf22-116">Save and name the manifest file.</span></span> <span data-ttu-id="1bf22-117">Uygulama bildiriminin adı, derleme yürütülebilir dosyasının ve ardından. manifest uzantısının adıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="1bf22-118">Örneğin, myComApp. exe için uygulama bildirimi dosya adı myComApp. exe. manifest ' dir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="1bf22-119">Uygulama bildirimini COM uygulamasıyla aynı dizine yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf22-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="1bf22-120">Alternatif olarak, uygulamayı uygulamanın. exe dosyasına bir kaynak olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf22-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="1bf22-121">Daha fazla bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="1bf22-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="1bf22-122">Bileşen bildirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1bf22-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="1bf22-123">XML Düzenleyicisi kullanarak, yönetilen derlemeyi betimleyen bir bileşen bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bf22-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="1bf22-124">Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bf22-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="1bf22-125">Dosyanın sahibini belirler.</span><span class="sxs-lookup"><span data-stu-id="1bf22-125">Identify the owner of the file.</span></span> <span data-ttu-id="1bf22-126">Uygulama bildirimi dosyasındaki `<dependentAssembly>` öğesinin `<assemblyIdentity>` öğesi, bileşen bildiriminde bulunan ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="1bf22-127">Aşağıdaki örnekte, `myManagedComp` sürümü, bildirim dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. <span data-ttu-id="1bf22-128">Derlemedeki her bir sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="1bf22-128">Identify each class in the assembly.</span></span> <span data-ttu-id="1bf22-129">Yönetilen derlemedeki her bir sınıfı benzersiz şekilde tanımlamak için `<clrClass>` öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bf22-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="1bf22-130">`<assembly>` öğesinin bir alt öğesi olan öğesi, aşağıdaki tabloda açıklanan özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="1bf22-131">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1bf22-131">Attribute</span></span>|<span data-ttu-id="1bf22-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf22-132">Description</span></span>|<span data-ttu-id="1bf22-133">Gerekli</span><span class="sxs-lookup"><span data-stu-id="1bf22-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="1bf22-134">Etkinleştirilecek sınıfı belirten tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="1bf22-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="1bf22-135">Evet</span><span class="sxs-lookup"><span data-stu-id="1bf22-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="1bf22-136">Kullanıcıya bileşen hakkında bilgilendiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="1bf22-136">A string that informs the user about the component.</span></span> <span data-ttu-id="1bf22-137">Boş bir dize varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-137">An empty string is the default.</span></span>|<span data-ttu-id="1bf22-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="1bf22-138">No</span></span>|  
    |`name`|<span data-ttu-id="1bf22-139">Yönetilen sınıfı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="1bf22-139">A string that represents the managed class.</span></span>|<span data-ttu-id="1bf22-140">Evet</span><span class="sxs-lookup"><span data-stu-id="1bf22-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="1bf22-141">Geç bağlantılı etkinleştirme için kullanılacak tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="1bf22-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="1bf22-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="1bf22-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="1bf22-143">COM iş parçacığı modeli.</span><span class="sxs-lookup"><span data-stu-id="1bf22-143">The COM threading model.</span></span> <span data-ttu-id="1bf22-144">"Her ikisi de varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-144">"Both" is the default value.</span></span>|<span data-ttu-id="1bf22-145">Hayır</span><span class="sxs-lookup"><span data-stu-id="1bf22-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="1bf22-146">Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="1bf22-147">Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 ' ten önceki en son yüklenen CLR ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="1bf22-148">V 1.0.3705, v 1.1.4322 veya v 2.0.50727 belirtirseniz, sürüm CLR sürüm 4 ' ten (genellikle v 2.0.50727) önce yüklenen en son CLR sürümüne otomatik olarak kaydolur.</span><span class="sxs-lookup"><span data-stu-id="1bf22-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="1bf22-149">CLR 'nin başka bir sürümü zaten yüklüyse ve belirtilen sürüm, işlem içi yan yana yüklenebiliyorsanız, belirtilen sürüm yüklenir; Aksi takdirde, yüklenen CLR kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="1bf22-150">Bu bir yükleme hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-150">This might cause a load failure.</span></span>|<span data-ttu-id="1bf22-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="1bf22-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="1bf22-152">Sınıf hakkında tür bilgilerini içeren tür kitaplığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1bf22-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="1bf22-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="1bf22-153">No</span></span>|  
  
     <span data-ttu-id="1bf22-154">Tüm öznitelik etiketleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="1bf22-155">OLE/COM ObjectViewer (Oleview. exe) ile derleme için aktarılmış tür kitaplığını görüntüleyerek CLSID, ProgID 'ler, iş parçacığı modelleri ve çalışma zamanı sürümünü edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf22-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="1bf22-156">Aşağıdaki bileşen bildirimi, `testClass1` ve `testClass2`iki sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bf22-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="1bf22-157">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1bf22-157">Save and name the manifest file.</span></span> <span data-ttu-id="1bf22-158">Bir bileşen bildiriminin adı, derleme kitaplığının adı ve ardından. manifest uzantısını izler.</span><span class="sxs-lookup"><span data-stu-id="1bf22-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="1bf22-159">Örneğin, myManagedComp. dll myManagedComp. manifest ' dir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="1bf22-160">Bileşen bildirimini derlemede bir kaynak olarak katıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="1bf22-161">Yönetilen bir derlemede bir bileşen bildirimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="1bf22-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="1bf22-162">Aşağıdaki ifadeyi içeren bir kaynak betiği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1bf22-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="1bf22-163">Bu bildirimde `myManagedComp.manifest`, eklenen bileşen bildiriminin adıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="1bf22-164">Bu örnekte, betik dosyası adı `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="1bf22-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="1bf22-165">Microsoft Windows Kaynak derleyicisi (RC. exe) kullanarak betiği derleyin.</span><span class="sxs-lookup"><span data-stu-id="1bf22-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="1bf22-166">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="1bf22-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="1bf22-167">RC. exe `myresource.res` kaynak dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="1bf22-168">Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:</span><span class="sxs-lookup"><span data-stu-id="1bf22-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="1bf22-169">Yeniden `myresource.res`, katıştırılmış kaynakları içeren kaynak dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="1bf22-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf22-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf22-170">See also</span></span>

- [<span data-ttu-id="1bf22-171">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="1bf22-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="1bf22-172">[Kayıtsız COM birlikte çalışma gereksinimleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1bf22-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="1bf22-173">[Kayıt-ücretsiz etkinleştirme için COM bileşenlerini yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1bf22-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="1bf22-174">[Kayıt-ücretsiz etkinleştirmesi. NET tabanlı bileşenler: Izlenecek yol](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="1bf22-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
