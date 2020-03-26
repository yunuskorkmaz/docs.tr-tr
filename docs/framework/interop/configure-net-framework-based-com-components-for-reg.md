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
ms.openlocfilehash: 9e273bd3e4bf2bb6945fe48c850783a54fa9a869
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291750"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="52c23-102">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="52c23-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="52c23-103">.NET Framework tabanlı bileşenler için kayıt gerektirmeden etkinleştirme, COM bileşenlerine göre yalnızca biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="52c23-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="52c23-104">Kurulum iki bildirim gerektirir:</span><span class="sxs-lookup"><span data-stu-id="52c23-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="52c23-105">COM uygulamaları, yönetilen bileşeni tanımlamak için Win32 tarzı bir uygulama bildirimine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="52c23-106">.NET Framework tabanlı bileşenler, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen manifestosuna sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="52c23-107">Bu konu, bir uygulama bildiriminin bir uygulamayla nasıl ilişkilendirilen; bileşen bildirimini bir bileşenle ilişkilendirin; ve bir bileşen bildirimini bir derlemeye katıştırın.</span><span class="sxs-lookup"><span data-stu-id="52c23-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="52c23-108">Uygulama bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="52c23-108">Create an application manifest</span></span>  
  
1. <span data-ttu-id="52c23-109">Bir XML düzenleyicisi kullanarak, com uygulamasının sahip olduğu ve bir veya daha fazla yönetilen bileşenle birlikte çalışan uygulama bildirimini oluşturun (veya değiştirin).</span><span class="sxs-lookup"><span data-stu-id="52c23-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="52c23-110">Dosyanın başına aşağıdaki standart üstbilgi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52c23-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="52c23-111">Bildirim öğeleri ve öznitelikleri hakkında bilgi için [Uygulama Bildirimleri'ne](/windows/desktop/SbsCs/application-manifests)bakın.</span><span class="sxs-lookup"><span data-stu-id="52c23-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="52c23-112">Bildirimin sahibini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52c23-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="52c23-113">Aşağıdaki örnekte, `myComApp` sürüm 1 manifesto dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="52c23-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="52c23-114">Bağımlı derlemeleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52c23-114">Identify dependent assemblies.</span></span> <span data-ttu-id="52c23-115">Aşağıdaki örnekte, `myComApp` `myManagedComp`bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="52c23-116">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="52c23-116">Save and name the manifest file.</span></span> <span data-ttu-id="52c23-117">Bir uygulama bildiriminin adı, .manifest uzantısı tarafından izlenen yürütülebilir derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="52c23-118">Örneğin, myComApp.exe için uygulama bildirimi dosya adı myComApp.exe.manifest olduğunu.</span><span class="sxs-lookup"><span data-stu-id="52c23-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="52c23-119">Com uygulamasıyla aynı dizinde bir uygulama bildirimi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52c23-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="52c23-120">Alternatif olarak, uygulamanın .exe dosyasına kaynak olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52c23-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="52c23-121">Daha fazla bilgi için Yan [Yana Montajlar Hakkında'ya](/windows/desktop/SbsCs/about-side-by-side-assemblies-)bakın.</span><span class="sxs-lookup"><span data-stu-id="52c23-121">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="52c23-122">Bileşen bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="52c23-122">Create a component manifest</span></span>  
  
1. <span data-ttu-id="52c23-123">Bir XML düzenleyicisi kullanarak, yönetilen derlemeyi açıklamak için bir bileşen bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="52c23-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="52c23-124">Dosyanın başına aşağıdaki standart üstbilgi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52c23-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="52c23-125">Dosyanın sahibini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52c23-125">Identify the owner of the file.</span></span> <span data-ttu-id="52c23-126">Uygulama `<assemblyIdentity>` bildirimi `<dependentAssembly>` dosyasındaki öğe öğesi, bileşen bildirimindeki öğeyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="52c23-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="52c23-127">Aşağıdaki örnekte, `myManagedComp` sürüm 1.2.3.4 bildirim dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="52c23-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="52c23-128">Derlemedeki her sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="52c23-128">Identify each class in the assembly.</span></span> <span data-ttu-id="52c23-129">Yönetilen `<clrClass>` derlemedeki her sınıfı benzersiz olarak tanımlamak için öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="52c23-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="52c23-130">Öğenin `<assembly>` bir alt öğesi olan öğe, aşağıdaki tabloda açıklanan özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="52c23-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="52c23-131">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52c23-131">Attribute</span></span>|<span data-ttu-id="52c23-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52c23-132">Description</span></span>|<span data-ttu-id="52c23-133">Gerekli</span><span class="sxs-lookup"><span data-stu-id="52c23-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="52c23-134">Sınıfın etkinleştirilecek lerini belirten tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="52c23-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="52c23-135">Evet</span><span class="sxs-lookup"><span data-stu-id="52c23-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="52c23-136">Kullanıcıyı bileşen hakkında bilgilendiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="52c23-136">A string that informs the user about the component.</span></span> <span data-ttu-id="52c23-137">Boş bir dize varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="52c23-137">An empty string is the default.</span></span>|<span data-ttu-id="52c23-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="52c23-138">No</span></span>|  
    |`name`|<span data-ttu-id="52c23-139">Yönetilen sınıfı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="52c23-139">A string that represents the managed class.</span></span>|<span data-ttu-id="52c23-140">Evet</span><span class="sxs-lookup"><span data-stu-id="52c23-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="52c23-141">Geç bağlanan etkinleştirme için kullanılacak tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="52c23-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="52c23-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="52c23-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="52c23-143">COM iş parçacığı modeli.</span><span class="sxs-lookup"><span data-stu-id="52c23-143">The COM threading model.</span></span> <span data-ttu-id="52c23-144">"Her ikisi de" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="52c23-144">"Both" is the default value.</span></span>|<span data-ttu-id="52c23-145">Hayır</span><span class="sxs-lookup"><span data-stu-id="52c23-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="52c23-146">Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="52c23-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="52c23-147">Bu özniteliği belirtmezseniz ve CLR zaten yüklenmemişse, bileşen CLR sürüm 4'ten önce en son yüklenen CLR ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="52c23-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="52c23-148">V1.0.3705, v1.1.4322 veya v2.0.50727 belirtirseniz, sürüm otomatik olarak CLR sürüm 4 'den önce (genellikle v2.0.50727) en son yüklenen CLR sürümüne geçilir.</span><span class="sxs-lookup"><span data-stu-id="52c23-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="52c23-149">CLR'nin başka bir sürümü zaten yüklenmişse ve belirtilen sürüm işlem içinde yan yana yüklenebilirse, belirtilen sürüm yüklenir; aksi takdirde, yüklenen CLR kullanılır.</span><span class="sxs-lookup"><span data-stu-id="52c23-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="52c23-150">Bu bir yük hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="52c23-150">This might cause a load failure.</span></span>|<span data-ttu-id="52c23-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="52c23-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="52c23-152">Sınıf hakkında tür bilgileri içeren tür kitaplığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="52c23-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="52c23-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="52c23-153">No</span></span>|  
  
     <span data-ttu-id="52c23-154">Tüm öznitelik etiketleri büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="52c23-155">OLE/COM ObjectViewer (Oleview.exe) ile derleme için dışa aktarılan tür kitaplığını görüntüleyerek CLSID'leri, ProgID'leri, iş parçacığı modellerini ve çalışma zamanı sürümünü edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52c23-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="52c23-156">Aşağıdaki bileşen bildirimi iki `testClass1` sınıf `testClass2`tanımlar ve .</span><span class="sxs-lookup"><span data-stu-id="52c23-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="52c23-157">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="52c23-157">Save and name the manifest file.</span></span> <span data-ttu-id="52c23-158">Bileşen bildiriminin adı, .manifest uzantısı tarafından izlenen derleme kitaplığı adıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="52c23-159">Örneğin, myManagedComp.dll myManagedComp.manifest olduğunu.</span><span class="sxs-lookup"><span data-stu-id="52c23-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="52c23-160">Bileşen bildirimini derlemeye kaynak olarak gömmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52c23-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="52c23-161">Yönetilen bir derlemeye bileşen bildirimini gömmek için</span><span class="sxs-lookup"><span data-stu-id="52c23-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="52c23-162">Aşağıdaki deyimi içeren bir kaynak komut dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="52c23-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="52c23-163">Bu ifadede, `myManagedComp.manifest` gömülü olan bileşen bildiriminin adıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="52c23-164">Bu örnekte, komut dosyası `myresource.rc`dosya adı.</span><span class="sxs-lookup"><span data-stu-id="52c23-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="52c23-165">Microsoft Windows Kaynak Derleyicisini (Rc.exe) kullanarak komut dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="52c23-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="52c23-166">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="52c23-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="52c23-167">Rc.exe kaynak `myresource.res` dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="52c23-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="52c23-168">Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:</span><span class="sxs-lookup"><span data-stu-id="52c23-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="52c23-169">Yine, `myresource.res` katıştırılmış kaynakları içeren kaynak dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="52c23-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c23-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c23-170">See also</span></span>

- [<span data-ttu-id="52c23-171">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="52c23-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="52c23-172">[Kayıt-Free COM Interop için Gereksinimleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="52c23-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="52c23-173">[Kayıt-Free Aktivasyon için COM Bileşenlerinin Yapılandırılması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="52c23-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="52c23-174">[Kayıt-Free Aktivasyonu . NET Tabanlı Bileşenler: Bir Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="52c23-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
