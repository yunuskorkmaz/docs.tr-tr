---
title: 'Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma'
description: Yapılandırma. Kayıtsız etkinleştirme için NET tabanlı COM bileşenleri. Kurulum bir Win32 stili uygulama bildirimi ve bir .NET bileşen bildirimi gerektirir.
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: ad25a79add84e43ba0a8e71a0f48c5ddf65108bd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554846"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="a4811-104">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a4811-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="a4811-105">.NET Framework tabanlı bileşenlere yönelik kayıt için ücretsiz etkinleştirme, COM bileşenleri için olduğundan biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="a4811-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="a4811-106">Kurulum için iki bildirim gerekir:</span><span class="sxs-lookup"><span data-stu-id="a4811-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="a4811-107">COM uygulamalarının, yönetilen bileşeni tanımlamak için bir Win32 stili uygulama bildirimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4811-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="a4811-108">.NET Framework tabanlı bileşenlerin, çalışma zamanında gerekli etkinleştirme bilgileri için bir bileşen bildirimine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4811-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="a4811-109">Bu konu, uygulama bildiriminin bir uygulamayla nasıl ilişkilendirileceğini açıklar; bileşen bildirimini bir bileşeniyle ilişkilendirin; ve bir derlemeye bileşen bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4811-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="a4811-110">Uygulama bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4811-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="a4811-111">Bir XML Düzenleyicisi kullanarak, bir veya daha fazla yönetilen bileşenle birlikte bulunan COM uygulamasına ait uygulama bildirimini oluşturun (veya değiştirin).</span><span class="sxs-lookup"><span data-stu-id="a4811-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="a4811-112">Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4811-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="a4811-113">Bildirim öğeleri ve öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="a4811-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="a4811-114">Bildirimin sahibini belirler.</span><span class="sxs-lookup"><span data-stu-id="a4811-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="a4811-115">Aşağıdaki örnekte, `myComApp` Sürüm 1 bildirim dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="a4811-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="a4811-116">Bağımlı derlemeleri belirler.</span><span class="sxs-lookup"><span data-stu-id="a4811-116">Identify dependent assemblies.</span></span> <span data-ttu-id="a4811-117">Aşağıdaki örnekte, `myComApp` öğesine bağımlıdır `myManagedComp` .</span><span class="sxs-lookup"><span data-stu-id="a4811-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="a4811-118">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a4811-118">Save and name the manifest file.</span></span> <span data-ttu-id="a4811-119">Uygulama bildiriminin adı, derleme yürütülebilir dosyasının ve ardından. manifest uzantısının adıdır.</span><span class="sxs-lookup"><span data-stu-id="a4811-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="a4811-120">Örneğin, myComApp.exe için uygulama bildirimi dosya adı myComApp.exe. manifest ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4811-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="a4811-121">Uygulama bildirimini COM uygulamasıyla aynı dizine yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4811-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="a4811-122">Alternatif olarak, uygulamayı uygulamanın. exe dosyasına bir kaynak olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4811-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="a4811-123">Daha fazla bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="a4811-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="a4811-124">Bileşen bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4811-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="a4811-125">XML Düzenleyicisi kullanarak, yönetilen derlemeyi betimleyen bir bileşen bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4811-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="a4811-126">Aşağıdaki standart üstbilgiyi dosyanın başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4811-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="a4811-127">Dosyanın sahibini belirler.</span><span class="sxs-lookup"><span data-stu-id="a4811-127">Identify the owner of the file.</span></span> <span data-ttu-id="a4811-128">`<assemblyIdentity>` `<dependentAssembly>` Uygulama bildirimi dosyasındaki öğenin öğesi, bileşen bildiriminde bulunan ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4811-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="a4811-129">Aşağıdaki örnekte, belirtilen `myManagedComp` Sürüm, bildirim dosyasının sahibidir.</span><span class="sxs-lookup"><span data-stu-id="a4811-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="a4811-130">Derlemedeki her bir sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="a4811-130">Identify each class in the assembly.</span></span> <span data-ttu-id="a4811-131">`<clrClass>`Yönetilen derlemedeki her bir sınıfı benzersiz şekilde tanımlamak için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4811-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="a4811-132">Öğesinin bir alt öğesi olan öğesi, `<assembly>` Aşağıdaki tabloda açıklanan özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a4811-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="a4811-133">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4811-133">Attribute</span></span>|<span data-ttu-id="a4811-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4811-134">Description</span></span>|<span data-ttu-id="a4811-135">Gerekli</span><span class="sxs-lookup"><span data-stu-id="a4811-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="a4811-136">Etkinleştirilecek sınıfı belirten tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="a4811-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="a4811-137">Yes</span><span class="sxs-lookup"><span data-stu-id="a4811-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="a4811-138">Kullanıcıya bileşen hakkında bilgilendiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4811-138">A string that informs the user about the component.</span></span> <span data-ttu-id="a4811-139">Boş bir dize varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a4811-139">An empty string is the default.</span></span>|<span data-ttu-id="a4811-140">No</span><span class="sxs-lookup"><span data-stu-id="a4811-140">No</span></span>|  
    |`name`|<span data-ttu-id="a4811-141">Yönetilen sınıfı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4811-141">A string that represents the managed class.</span></span>|<span data-ttu-id="a4811-142">Yes</span><span class="sxs-lookup"><span data-stu-id="a4811-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="a4811-143">Geç bağlantılı etkinleştirme için kullanılacak tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="a4811-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="a4811-144">No</span><span class="sxs-lookup"><span data-stu-id="a4811-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="a4811-145">COM iş parçacığı modeli.</span><span class="sxs-lookup"><span data-stu-id="a4811-145">The COM threading model.</span></span> <span data-ttu-id="a4811-146">"Her ikisi de varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a4811-146">"Both" is the default value.</span></span>|<span data-ttu-id="a4811-147">No</span><span class="sxs-lookup"><span data-stu-id="a4811-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="a4811-148">Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4811-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="a4811-149">Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 ' ten önceki en son yüklenen CLR ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a4811-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="a4811-150">V 1.0.3705, v 1.1.4322 veya v 2.0.50727 belirtirseniz, sürüm CLR sürüm 4 ' ten (genellikle v 2.0.50727) önce yüklenen en son CLR sürümüne otomatik olarak kaydolur.</span><span class="sxs-lookup"><span data-stu-id="a4811-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="a4811-151">CLR 'nin başka bir sürümü zaten yüklüyse ve belirtilen sürüm, işlem içi yan yana yüklenebiliyorsanız, belirtilen sürüm yüklenir; Aksi takdirde, yüklenen CLR kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4811-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="a4811-152">Bu bir yükleme hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4811-152">This might cause a load failure.</span></span>|<span data-ttu-id="a4811-153">No</span><span class="sxs-lookup"><span data-stu-id="a4811-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="a4811-154">Sınıf hakkında tür bilgilerini içeren tür kitaplığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a4811-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="a4811-155">No</span><span class="sxs-lookup"><span data-stu-id="a4811-155">No</span></span>|  
  
     <span data-ttu-id="a4811-156">Tüm öznitelik etiketleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4811-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="a4811-157">OLE/COM ObjectViewer (Oleview.exe) ile derleme için aktarılmış tür kitaplığını görüntüleyerek CLSID, ProgID 'ler, iş parçacığı oluşturma modellerini ve çalışma zamanı sürümünü edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4811-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="a4811-158">Aşağıdaki bileşen bildirimi, ve olmak üzere iki sınıfı tanımlar `testClass1` `testClass2` .</span><span class="sxs-lookup"><span data-stu-id="a4811-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="a4811-159">Bildirim dosyasını kaydedin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a4811-159">Save and name the manifest file.</span></span> <span data-ttu-id="a4811-160">Bir bileşen bildiriminin adı, derleme kitaplığının adı ve ardından. manifest uzantısını izler.</span><span class="sxs-lookup"><span data-stu-id="a4811-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="a4811-161">Örneğin, myManagedComp.dll myManagedComp. manifest ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4811-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="a4811-162">Bileşen bildirimini derlemede bir kaynak olarak katıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4811-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="a4811-163">Yönetilen bir derlemede bir bileşen bildirimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="a4811-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="a4811-164">Aşağıdaki ifadeyi içeren bir kaynak betiği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a4811-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="a4811-165">Bu bildirimde, `myManagedComp.manifest` eklenen bileşen bildiriminin adıdır.</span><span class="sxs-lookup"><span data-stu-id="a4811-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="a4811-166">Bu örnek için, betik dosyası adı `myresource.rc` .</span><span class="sxs-lookup"><span data-stu-id="a4811-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="a4811-167">Microsoft Windows Kaynak derleyicisi (Rc.exe) kullanarak betiği derleyin.</span><span class="sxs-lookup"><span data-stu-id="a4811-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="a4811-168">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="a4811-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="a4811-169">Rc.exe `myresource.res` kaynak dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="a4811-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="a4811-170">Derlemenin kaynak dosyasını yeniden derleyin ve **/win32res** seçeneğini kullanarak kaynak dosyasını belirtin:</span><span class="sxs-lookup"><span data-stu-id="a4811-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="a4811-171">Yine, `myresource.res` gömülü kaynakları içeren kaynak dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="a4811-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4811-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4811-172">See also</span></span>

- [<span data-ttu-id="a4811-173">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="a4811-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="a4811-174">[Kayıtsız COM birlikte çalışma gereksinimleri](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4811-174">[Requirements for Registration-Free COM Interop](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="a4811-175">[Kayıt-ücretsiz etkinleştirme için COM bileşenlerini yapılandırma](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4811-175">[Configuring COM Components for Registration-Free Activation](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="a4811-176">[Kayıt-ücretsiz etkinleştirmesi. NET tabanlı bileşenler: Izlenecek yol](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a4811-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
