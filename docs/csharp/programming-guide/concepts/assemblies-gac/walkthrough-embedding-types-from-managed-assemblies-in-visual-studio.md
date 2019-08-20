---
title: "İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (C#)"
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595799"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="70635-102">İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="70635-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>

<span data-ttu-id="70635-103">Tanımlayıcı adlı yönetilen bir derlemeden tür bilgilerini eklerseniz, sürüm bağımsızlığını elde etmek için bir uygulamada gevşek olarak birkaç tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70635-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="70635-104">Diğer bir deyişle, programınız her sürüm için yeniden derlenmesi gerekmeden yönetilen bir kitaplığın birden çok sürümündeki türleri kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="70635-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="70635-105">Tür ekleme, genellikle Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70635-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="70635-106">Tür bilgilerinin gömülmesi, farklı bilgisayarlarda farklı Microsoft Office sürümleriyle çalışmak için aynı programın derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="70635-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="70635-107">Ancak, tam olarak yönetilen bir çözümle tür ekleme özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70635-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="70635-108">Tür bilgileri, aşağıdaki özelliklere sahip bir derlemeden gömülebilir:</span><span class="sxs-lookup"><span data-stu-id="70635-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="70635-109">Derleme en az bir ortak arabirim kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="70635-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="70635-110">Katıştırılmış arabirimlere bir `ComImport` öznitelik ve bir `Guid` öznitelik (ve benzersiz bir GUID) eklenir.</span><span class="sxs-lookup"><span data-stu-id="70635-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="70635-111">Derlemeye, `ImportedFromTypeLib` özniteliğiyle `PrimaryInteropAssembly` veya özniteliğiyle ve derleme düzeyi `Guid` özniteliğiyle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="70635-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="70635-112">(Varsayılan olarak, görsel C# proje şablonları derleme düzeyi `Guid` bir öznitelik içerir.)</span><span class="sxs-lookup"><span data-stu-id="70635-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="70635-113">Katıştırılabilen ortak arabirimleri belirledikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70635-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="70635-114">Bir istemci program, ortak arabirimleri içeren derlemeye başvurarak ve `Embed Interop Types` `True`başvurusunun özelliğini ayarlayarak bu arabirimlerin tür bilgilerini tasarım zamanında ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70635-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="70635-115">Bu, komut satırı derleyicisini kullanma ve `/link` derleyici seçeneği kullanılarak derlemeye başvurma ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="70635-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="70635-116">İstemci programı daha sonra bu arabirimler olarak yazılmış çalışma zamanı nesnelerinizin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70635-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="70635-117">Güçlü adlandırılmış çalışma zamanı derlemenin yeni bir sürümünü oluşturursanız, istemci programın güncelleştirilmiş çalışma zamanı derlemesi ile yeniden derlenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="70635-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="70635-118">Bunun yerine, istemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak çalışma zamanı derlemesinin hangi sürümünün kullanılabilir olduğunu kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="70635-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="70635-119">Ekleme türü birincil işlevi, COM birlikte çalışma derlemelerinden tür bilgilerinin gömülmesini destekletiğinden, tür bilgilerini tam olarak yönetilen bir çözüme eklediğinizde aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="70635-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="70635-120">Yalnızca COM birlikte çalışabilirliğine özgü öznitelikler katıştırılır; diğer öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="70635-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="70635-121">Bir tür genel parametreler kullanıyorsa ve genel parametrenin türü gömülü bir türse, bu tür bir derleme sınırı boyunca kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="70635-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="70635-122">Bir derleme sınırının geçmesinin örnekleri, başka bir derlemeden bir yöntemi çağırmayı ya da başka bir derlemede tanımlanan türden bir tür türetmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="70635-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="70635-123">Sabitler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="70635-123">Constants are not embedded.</span></span>

- <span data-ttu-id="70635-124">Sınıf <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> , gömülü bir türü anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="70635-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="70635-125">Gömülü bir türü anahtar olarak desteklemek için kendi sözlük türünü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70635-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

<span data-ttu-id="70635-126">Bu izlenecek yolda şunları yapacaksınız:</span><span class="sxs-lookup"><span data-stu-id="70635-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="70635-127">Katıştırılabilen tür bilgilerini içeren bir ortak arabirime sahip güçlü adlı bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70635-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="70635-128">Bu ortak arabirimi uygulayan, tanımlayıcı adlı bir çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70635-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="70635-129">Ortak arabirimden tür bilgilerini katıştıran bir istemci programı oluşturun ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70635-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="70635-130">Çalışma zamanı derlemesini değiştirin ve yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="70635-131">İstemci programını yeniden derlemek zorunda kalmadan çalışma zamanı derlemesinin yeni sürümünün kullanıldığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70635-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="70635-132">Arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="70635-132">Creating an Interface</span></span>

#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="70635-133">Tür denklik arabirimi projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="70635-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="70635-134">Visual Studio 'da, **Dosya** menüsünde **Yeni** ' yi seçin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>

2. <span data-ttu-id="70635-135">**Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="70635-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="70635-136">**Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="70635-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="70635-137">**Ad** kutusuna yazın `TypeEquivalenceInterface`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="70635-138">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="70635-138">The new project is created.</span></span>

3. <span data-ttu-id="70635-139">**Çözüm Gezgini**, Class1.cs dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="70635-140">Dosyayı olarak `ISampleInterface.cs` yeniden adlandırın ve ENTER 'a basın.</span><span class="sxs-lookup"><span data-stu-id="70635-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="70635-141">Dosyanın yeniden adlandırılması de sınıfı olarak `ISampleInterface`yeniden adlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="70635-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="70635-142">Bu sınıf, sınıfının genel arabirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70635-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="70635-143">TypeEquivalenceInterface projesine sağ tıklayın ve **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="70635-144">**Derleme** sekmesine tıklayın. Çıkış yolunu, geliştirme bilgisayarınızda, `C:\TypeEquivalenceSample`gibi geçerli bir konuma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70635-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="70635-145">Bu konum, Bu izlenecek yolda daha sonraki bir adımda de kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="70635-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="70635-146">Proje özelliklerini hala düzenleirken **imzalama** sekmesine tıklayın. **Derlemeyi imzala** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="70635-147">**Tanımlayıcı ad seçin anahtar dosyası** listesinde  **\<yeni... öğesine tıklayın. >** .</span><span class="sxs-lookup"><span data-stu-id="70635-147">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="70635-148">**Anahtar dosya adı** kutusuna yazın `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="70635-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="70635-149">**Anahtar dosyamı parolayla koru** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="70635-150">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="70635-150">Click **OK**.</span></span>

6. <span data-ttu-id="70635-151">ISampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="70635-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="70635-152">Iamptaınterface arabirimini oluşturmak için ısamptaınterface sınıf dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace TypeEquivalenceInterface
    {
        [ComImport]
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
        public interface ISampleInterface
        {
            void GetUserInput();
            string UserInput { get; }
        }
    }
    ```

7. <span data-ttu-id="70635-153">**Araçlar** menüsünde **GUID oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="70635-154">**GUID oluştur** iletişim kutusunda, **kayıt defteri biçimi** ' ne ve ardından **Kopyala**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="70635-155">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-155">Click **Exit**.</span></span>

8. <span data-ttu-id="70635-156">Özniteliğinde, örnek GUID 'yi silin ve **GUID oluştur** iletişim kutusundan kopyaladığınız GUID 'ye yapıştırın. `Guid`</span><span class="sxs-lookup"><span data-stu-id="70635-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="70635-157">Kopyalanmış GUID 'den küme{}ayracı () kaldırın.</span><span class="sxs-lookup"><span data-stu-id="70635-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="70635-158">**Çözüm Gezgini**, **Özellikler** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="70635-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="70635-159">AssemblyInfo.cs dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="70635-160">Dosyasına aşağıdaki özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-160">Add the following attribute to the file.</span></span>

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     <span data-ttu-id="70635-161">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-161">Save the file.</span></span>

10. <span data-ttu-id="70635-162">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-162">Save the project.</span></span>

11. <span data-ttu-id="70635-163">TypeEquivalenceInterface projesine sağ tıklayın ve **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="70635-164">Sınıf kitaplığı. dll dosyası derlenir ve belirtilen derleme çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="70635-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="70635-165">Çalışma zamanı sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="70635-165">Creating a Runtime Class</span></span>

#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="70635-166">Tür denklik çalışma zamanı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="70635-166">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="70635-167">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="70635-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="70635-168">**Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="70635-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="70635-169">**Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="70635-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="70635-170">**Ad** kutusuna yazın `TypeEquivalenceRuntime`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="70635-171">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="70635-171">The new project is created.</span></span>

3. <span data-ttu-id="70635-172">**Çözüm Gezgini**, Class1.cs dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="70635-173">Dosyayı olarak `SampleClass.cs` yeniden adlandırın ve ENTER 'a basın.</span><span class="sxs-lookup"><span data-stu-id="70635-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="70635-174">Dosyanın yeniden adlandırılması de sınıfını olarak `SampleClass`yeniden adlandırır.</span><span class="sxs-lookup"><span data-stu-id="70635-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="70635-175">Bu sınıf, `ISampleInterface` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="70635-175">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="70635-176">TypeEquivalenceRuntime projesine sağ tıklayın ve **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="70635-177">**Derleme** sekmesine tıklayın. Çıkış yolunu, TypeEquivalenceInterface projesinde kullandığınız konuma ayarlayın, örneğin, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="70635-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="70635-178">Proje özelliklerini hala düzenleirken **imzalama** sekmesine tıklayın. **Derlemeyi imzala** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="70635-179">**Tanımlayıcı ad seçin anahtar dosyası** listesinde  **\<yeni... öğesine tıklayın. >** .</span><span class="sxs-lookup"><span data-stu-id="70635-179">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="70635-180">**Anahtar dosya adı** kutusuna yazın `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="70635-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="70635-181">**Anahtar dosyamı parolayla koru** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="70635-182">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="70635-182">Click **OK**.</span></span>

6. <span data-ttu-id="70635-183">TypeEquivalenceRuntime projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="70635-184">**Araştır** sekmesine tıklayın ve çıkış yolu klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="70635-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="70635-185">TypeEquivalenceInterface. dll dosyasını seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="70635-186">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="70635-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="70635-187">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="70635-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="70635-188">TypeEquivalenceInterface başvurusu için Özellikler penceresi, **belirli sürüm** özelliğini **false**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70635-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

8. <span data-ttu-id="70635-189">SampleClass sınıfını oluşturmak için SampleClass sınıf dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;

    namespace TypeEquivalenceRuntime
    {
        public class SampleClass : ISampleInterface
        {
            private string p_UserInput;
            public string UserInput { get { return p_UserInput; } }

            public void GetUserInput()
            {
                Console.WriteLine("Please enter a value:");
                p_UserInput = Console.ReadLine();
            }
        }
    }
    ```

9. <span data-ttu-id="70635-190">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-190">Save the project.</span></span>

10. <span data-ttu-id="70635-191">TypeEquivalenceRuntime projesine sağ tıklayın ve **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="70635-192">Sınıf kitaplığı. dll dosyası derlenir ve belirtilen derleme çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="70635-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="70635-193">Istemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="70635-193">Creating a Client Project</span></span>

#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="70635-194">Tür eşdeğerlik istemci projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="70635-194">To create the type equivalence client project</span></span>

1. <span data-ttu-id="70635-195">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="70635-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="70635-196">**Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="70635-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="70635-197">**Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="70635-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="70635-198">**Ad** kutusuna yazın `TypeEquivalenceClient`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="70635-199">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="70635-199">The new project is created.</span></span>

3. <span data-ttu-id="70635-200">TypeEquivalenceClient projesine sağ tıklayın ve **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="70635-201">**Derleme** sekmesine tıklayın. Çıkış yolunu, TypeEquivalenceInterface projesinde kullandığınız konuma ayarlayın, örneğin, `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="70635-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="70635-202">TypeEquivalenceClient projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="70635-203">**Araştır** sekmesine tıklayın ve çıkış yolu klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="70635-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="70635-204">TypeEquivalenceInterface. dll dosyasını (TypeEquivalenceRuntime. dll değil) seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="70635-205">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="70635-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="70635-206">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="70635-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="70635-207">TypeEquivalenceInterface başvurusu için Özellikler penceresi, **birlikte çalışma türlerini katıştır** özelliğini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70635-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

6. <span data-ttu-id="70635-208">İstemci programını oluşturmak için aşağıdaki kodu Program.cs dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-208">Add the following code to the Program.cs file to create the client program.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;
    using System.Reflection;

    namespace TypeEquivalenceClient
    {
        class Program
        {
            static void Main(string[] args)
            {
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
                ISampleInterface sampleClass =
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
                sampleClass.GetUserInput();
                Console.WriteLine(sampleClass.UserInput);
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());
                Console.ReadLine();
            }
        }
    }
    ```

7. <span data-ttu-id="70635-209">Programı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="70635-209">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="70635-210">Arabirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="70635-210">Modifying the Interface</span></span>

#### <a name="to-modify-the-interface"></a><span data-ttu-id="70635-211">Arabirimi değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="70635-211">To modify the interface</span></span>

1. <span data-ttu-id="70635-212">Visual Studio 'da, **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Proje/çözüm**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="70635-213">**Proje Aç** Iletişim kutusunda TypeEquivalenceInterface projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="70635-214">**Uygulama** sekmesine tıklayın. **Derleme bilgileri** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="70635-215">**Derleme sürümünü** ve **dosya sürümü** değerlerini olarak `2.0.0.0`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70635-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="70635-216">SampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="70635-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="70635-217">Aşağıdaki kod satırını ısamptaınterface arabirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-217">Add the following line of code to the ISampleInterface interface.</span></span>

    ```csharp
    DateTime GetDate();
    ```

    <span data-ttu-id="70635-218">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-218">Save the file.</span></span>

4. <span data-ttu-id="70635-219">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-219">Save the project.</span></span>

5. <span data-ttu-id="70635-220">TypeEquivalenceInterface projesine sağ tıklayın ve **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="70635-221">Sınıf kitaplığı. dll dosyasının yeni bir sürümü, belirtilen derleme çıkış yolunda derlenir ve kaydedilir (örneğin, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="70635-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="70635-222">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="70635-222">Modifying the Runtime Class</span></span>

#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="70635-223">Çalışma zamanı sınıfını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="70635-223">To modify the runtime class</span></span>

1. <span data-ttu-id="70635-224">Visual Studio 'da, **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Proje/çözüm**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="70635-225">**Proje Aç** Iletişim kutusunda TypeEquivalenceRuntime projesine sağ tıklayın ve **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="70635-226">**Uygulama** sekmesine tıklayın. **Derleme bilgileri** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="70635-227">**Derleme sürümünü** ve **dosya sürümü** değerlerini olarak `2.0.0.0`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70635-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="70635-228">SampleClass.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="70635-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="70635-229">Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70635-229">Add the following lines of code to the SampleClass class.</span></span>

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    <span data-ttu-id="70635-230">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-230">Save the file.</span></span>

4. <span data-ttu-id="70635-231">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="70635-231">Save the project.</span></span>

5. <span data-ttu-id="70635-232">TypeEquivalenceRuntime projesine sağ tıklayın ve **Oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="70635-233">Sınıf kitaplığı. dll dosyasının güncelleştirilmiş bir sürümü, daha önce belirtilen derleme çıkış yolunda derlenir ve kaydedilir (örneğin, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="70635-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="70635-234">Dosya Gezgini 'nde çıkış yolu klasörünü açın (örneğin, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="70635-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="70635-235">Programı çalıştırmak için TypeEquivalenceClient. exe dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70635-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="70635-236">Program, TypeEquivalenceRuntime derlemesinin yeni sürümünü yeniden derlenmeden yansıtır.</span><span class="sxs-lookup"><span data-stu-id="70635-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="70635-237">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70635-237">See also</span></span>

- [<span data-ttu-id="70635-238">/Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="70635-238">/link (C# Compiler Options)</span></span>](../../../language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="70635-239">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70635-239">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="70635-240">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="70635-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="70635-241">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="70635-241">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
