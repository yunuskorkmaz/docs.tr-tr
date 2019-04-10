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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea62f7dc5c47f52f94567857427e7add929b8b1c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336583"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="dc5a4-102">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dc5a4-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="dc5a4-103">Kayıtsız etkinleştirme için .NET Framework tabanlı bileşenler, yalnızca COM bileşenleri için olandan biraz daha karmaşık.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="dc5a4-104">Kurulum, iki bildirimleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="dc5a4-105">COM uygulamaları yönetilen bileşen tanımlamak için bir Win32 stili bildiriminin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="dc5a4-106">.NET framework tabanlı bileşenler, bileşen bildirimini etkinleştirme bilgi çalışma zamanında gereken olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="dc5a4-107">Bu konu, bir uygulama bildirimi uygulamayla ilişkilendirilecek açıklar; Bileşen bildirimi, bir bileşeniyle ilişkilendirme; ' i tıklatın ve bileşeni bildirimini derlemede katıştırmak.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="dc5a4-108">Bir uygulama bildirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dc5a4-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="dc5a4-109">Bir XML Düzenleyicisi'ni kullanarak oluşturun (veya değiştirme) bir veya daha fazla yönetilen bileşenleri ile birlikte COM uygulama sahibi uygulama bildirimi.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="dc5a4-110">Aşağıdaki standart üstbilgi dosyasının başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="dc5a4-111">Liste öğelerini ve onların öznitelikleri hakkında daha fazla bilgi için bkz. [uygulama bildirimleri](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="dc5a4-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="dc5a4-112">Bildirimin sahibi olacak kişileri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="dc5a4-113">Aşağıdaki örnekte, `myComApp` sürüm 1 sahip bildirim dosyası.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. <span data-ttu-id="dc5a4-114">Bağımlı derlemelerin belirleyin.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-114">Identify dependent assemblies.</span></span> <span data-ttu-id="dc5a4-115">Aşağıdaki örnekte, `myComApp` bağlıdır `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="dc5a4-116">Kaydet ve bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-116">Save and name the manifest file.</span></span> <span data-ttu-id="dc5a4-117">Bir uygulama bildirimi yürütülebilir derlemenin adını .manifest uzantısı tarafından izlenen adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="dc5a4-118">Örneğin, uygulama bildirim dosyası myComApp.exe myComApp.exe.manifest adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="dc5a4-119">Bir uygulama bildirimi, COM uygulama ile aynı dizinde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="dc5a4-120">Alternatif olarak, bunu bir kaynak olarak uygulamanın .exe dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="dc5a4-121">Daha fazla bilgi için ek bilgi için bkz. [yan yana derlemeler hakkında](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="dc5a4-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="dc5a4-122">Bileşen bildirimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dc5a4-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="dc5a4-123">Bir XML Düzenleyicisi'ni kullanarak yönetilen derlemeyi tanımlamak için bir bileşen bildirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="dc5a4-124">Aşağıdaki standart üstbilgi dosyasının başına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="dc5a4-125">Dosyanın sahibi olacak kişileri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-125">Identify the owner of the file.</span></span> <span data-ttu-id="dc5a4-126">`<assemblyIdentity>` Öğesinin `<dependentAssembly>` bileşen bildirimini bir uygulama bildirimi dosyasındaki öğesi eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="dc5a4-127">Aşağıdaki örnekte, `myManagedComp` sürüm 1.2.3.4 sahip bildirim dosyası.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="dc5a4-128">Derlemedeki her bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-128">Identify each class in the assembly.</span></span> <span data-ttu-id="dc5a4-129">Kullanım `<clrClass>` her derlemede sınıfı, yönetilen benzersiz olarak tanımlanabilmesi için öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="dc5a4-130">Bir alt öğesi olan öğe, `<assembly>` öğesi, aşağıdaki tabloda açıklanan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="dc5a4-131">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dc5a4-131">Attribute</span></span>|<span data-ttu-id="dc5a4-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc5a4-132">Description</span></span>|<span data-ttu-id="dc5a4-133">Gerekli</span><span class="sxs-lookup"><span data-stu-id="dc5a4-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="dc5a4-134">Belirten etkinleştirilmesi için sınıf tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="dc5a4-135">Evet</span><span class="sxs-lookup"><span data-stu-id="dc5a4-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="dc5a4-136">Kullanıcı bileşeni hakkında bilgilendiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-136">A string that informs the user about the component.</span></span> <span data-ttu-id="dc5a4-137">Boş bir dize varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-137">An empty string is the default.</span></span>|<span data-ttu-id="dc5a4-138">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc5a4-138">No</span></span>|  
    |`name`|<span data-ttu-id="dc5a4-139">Yönetilen sınıf temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-139">A string that represents the managed class.</span></span>|<span data-ttu-id="dc5a4-140">Evet</span><span class="sxs-lookup"><span data-stu-id="dc5a4-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="dc5a4-141">Geç bağlama etkinleştirmesi için kullanılan tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="dc5a4-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc5a4-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="dc5a4-143">COM iş parçacığı modeli.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-143">The COM threading model.</span></span> <span data-ttu-id="dc5a4-144">"Both" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-144">"Both" is the default value.</span></span>|<span data-ttu-id="dc5a4-145">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc5a4-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="dc5a4-146">Kullanılacak ortak dil çalışma zamanı (CLR) sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="dc5a4-147">Bu özniteliği belirtmezseniz ve CLR zaten yüklü değilse, bileşen CLR sürüm 4 önce en son yüklenen CLR ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="dc5a4-148">V1.0.3705, v1.1.4322 veya v2.0.50727 belirtirseniz, sürüm otomatik olarak ilet için en son yüklenen CLR sürümü CLR sürüm 4 (genellikle v2.0.50727) önce yapar.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="dc5a4-149">Başka bir CLR sürümü zaten yüklü olan ve belirtilen sürümü işlemdeki yan yana yüklenebilir, belirtilen sürümü yüklenir; Aksi takdirde, yüklü CLR kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="dc5a4-150">Bu yük başarısız olmasına neden.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-150">This might cause a load failure.</span></span>|<span data-ttu-id="dc5a4-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc5a4-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="dc5a4-152">Sınıf türü bilgilerini içeren tür kitaplığının tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="dc5a4-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc5a4-153">No</span></span>|  
  
     <span data-ttu-id="dc5a4-154">Tüm öznitelik etiketler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="dc5a4-155">CLSID, ProgIDs, modelleri ve çalışma zamanı sürümü, dışarı aktarılan tür kitaplığını derleme OLE/COM ObjectViewer (Oleview.exe) ile görüntüleyerek iş parçacığı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="dc5a4-156">İki sınıf aşağıdaki bileşen bildirimini tanımlar `testClass1` ve `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="dc5a4-157">Kaydet ve bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-157">Save and name the manifest file.</span></span> <span data-ttu-id="dc5a4-158">Bir bileşen bildirimini .manifest uzantısı tarafından izlenen derleme kitaplığının adı adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="dc5a4-159">Örneğin, myManagedComp.dll myManagedComp.manifest olur.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="dc5a4-160">Bir kaynak olarak bileşen bildirimini derlemesinde katıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="dc5a4-161">Yönetilen derlemede bir bileşen bildirimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="dc5a4-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="dc5a4-162">Aşağıdaki deyim içeren bir kaynak betiği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="dc5a4-163">Bu bildirimde `myManagedComp.manifest` katıştırılmış bileşen bildirimini adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="dc5a4-164">Bu örnekte, betik dosyası adı `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="dc5a4-165">Microsoft Windows Kaynak derleyicisi (Rc.exe) kullanarak betiği derleyin.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="dc5a4-166">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="dc5a4-167">RC.exe üretir `myresource.res` kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="dc5a4-168">Derlemenin kaynak dosyasını yeniden derleyin ve kullanarak kaynak dosyayı belirtin **/win32res** seçeneği:</span><span class="sxs-lookup"><span data-stu-id="dc5a4-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="dc5a4-169">Yeniden `myresource.res` gömülü kaynak içeren kaynak dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5a4-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5a4-170">See also</span></span>

- [<span data-ttu-id="dc5a4-171">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="dc5a4-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- [<span data-ttu-id="dc5a4-172">Kayıtsız COM Birlikte Çalışma için Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc5a4-172">Requirements for Registration-Free COM Interop</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [<span data-ttu-id="dc5a4-173">Kayıtsız Etkinleştirme için COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dc5a4-173">Configuring COM Components for Registration-Free Activation</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [<span data-ttu-id="dc5a4-174">Kayıtsız etkinleştirme. AĞ tabanlı bileşenler: İzlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="dc5a4-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
