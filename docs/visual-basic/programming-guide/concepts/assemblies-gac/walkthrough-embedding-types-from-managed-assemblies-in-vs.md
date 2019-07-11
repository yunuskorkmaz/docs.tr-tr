---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 0c0de529a0005c9dbaf1f8d0f25957b217280e31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753014"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="d3544-102">İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="d3544-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="d3544-103">Tanımlayıcı adlı bir yönetilen bütünleştirilmiş koddan tür bilgilerini katıştırma, sürüm bağımsızlığı elde etmek için bir uygulama türlerinde gevşek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d3544-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="d3544-104">Diğer bir deyişle, programınız her sürüm için derlenmesi zorunda kalmadan bir yönetilen kitaplık birden çok sürümünden türler kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="d3544-105">Ekleme türü Microsoft Office'ten Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3544-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="d3544-106">Tür bilgilerini katıştırma farklı bilgisayarlarda Microsoft Office'in farklı sürümlerinde çalışmak için bir programın aynı yapısının sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3544-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="d3544-107">Ancak, tam olarak yönetilen bir Çözümle ekleme türü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3544-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="d3544-108">Tür bilgileri aşağıdaki özelliklere sahip bir derlemeden eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="d3544-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="d3544-109">Derleme en az bir ortak arabirim kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d3544-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="d3544-110">Katıştırılmış arabirimleri ile açıklamalı olan bir `ComImport` özniteliği ve `Guid` özniteliği (ve benzersiz bir GUID).</span><span class="sxs-lookup"><span data-stu-id="d3544-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="d3544-111">Derleme ile açıklanıyor `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliğini ve bir derleme düzeyi `Guid` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3544-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="d3544-112">(Varsayılan olarak, Visual Basic proje şablonları, bir derleme düzeyi dahil `Guid` özniteliği.)</span><span class="sxs-lookup"><span data-stu-id="d3544-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="d3544-113">Eklenebilecek Ortak arabirimlerin belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıflar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3544-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="d3544-114">Bir istemci programını sonra bu arabirimleri için tasarım zamanında tür bilgilerini genel arabirimleri ve ayar içeren derleme başvurarak katıştırabilirsiniz `Embed Interop Types` özelliği için başvuru `True`.</span><span class="sxs-lookup"><span data-stu-id="d3544-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="d3544-115">Bu komut satırı derleyicisini kullanarak ve kullanarak derlemenin başvurduğu eşdeğerdir `/link` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3544-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="d3544-116">İstemci programı daha sonra bu arabirimleri olarak yazılan, çalışma zamanı nesnelerinin örneklerini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3544-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="d3544-117">Çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kodunuzda yeni bir sürümü oluşturursanız, güncelleştirilmiş çalışma zamanı derleme ile derlenmesi istemci program yok.</span><span class="sxs-lookup"><span data-stu-id="d3544-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="d3544-118">Bunun yerine, istemci programı, ortak arabirimler için gömülü tür bilgileri kullanarak hangi çalışma zamanı derleme sürümü, kullanıma hazır kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="d3544-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="d3544-119">Tür bilgilerini COM birlikte çalışma derlemelerini, destekliyoruz türü ekleme birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d3544-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="d3544-120">Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d3544-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="d3544-121">Bir tür genel parametreleri kullanan ve katıştırılmış tür genel parametre türü ise, bu tür bir bütünleştirilmiş kod sınırları arasında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d3544-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="d3544-122">Başka bir derlemeden bir yöntemi çağırmak bir derleme sınırı aşan örnekleri şunlardır veya başka bir derlemede tanımlanan bir türü türetilen bir tür.</span><span class="sxs-lookup"><span data-stu-id="d3544-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="d3544-123">Sabitler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="d3544-123">Constants are not embedded.</span></span>

- <span data-ttu-id="d3544-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıfı, bir anahtar olarak gömülü bir türünü desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="d3544-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="d3544-125">Katıştırılmış tür olarak bir anahtar desteklemek için kendi Sözlük türü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3544-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

 <span data-ttu-id="d3544-126">Bu kılavuzda, aşağıdakileri yapmanız:</span><span class="sxs-lookup"><span data-stu-id="d3544-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="d3544-127">Eklenebilecek tür bilgilerini içeren bir ortak arabirim kesin adlandırılmış bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3544-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="d3544-128">Genel arabirimi uygulayan bir çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kod oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3544-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="d3544-129">Ortak arabirim tür bilgilerini katıştırır ve çalışma zamanı derlemenin sınıfının bir örneğini oluşturan bir istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3544-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="d3544-130">Değiştirin ve çalışma zamanı derleme yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="d3544-131">İstemcinin yeniden derlemenize gerek kalmadan yeni çalışma zamanı derleme sürümünü kullanılmakta olduğunu görmek için istemci programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3544-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="d3544-132">Bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3544-132">Creating an Interface</span></span>

### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="d3544-133">Tür eşdeğerliği arabirimi projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3544-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="d3544-134">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="d3544-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3544-135">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3544-136">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d3544-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3544-137">İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d3544-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="d3544-138">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3544-138">The new project is created.</span></span>

3. <span data-ttu-id="d3544-139">İçinde **Çözüm Gezgini**Class1.vb dosyaya sağ tıklayın ve tıklayın **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="d3544-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="d3544-140">Dosyayı Yeniden Adlandır `ISampleInterface.vb` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d3544-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="d3544-141">Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="d3544-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="d3544-142">Bu sınıf, sınıf için ortak arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d3544-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="d3544-143">TypeEquivalenceInterface projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3544-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="d3544-144">Tıklayın **derleme** sekmesi. Çıkış yolu geçerli bir konum, geliştirme bilgisayarınızda gibi ayarlamak `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3544-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="d3544-145">Bu konum, ayrıca bu izlenecek yolda bir sonraki adımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3544-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="d3544-146">Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3544-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3544-147">İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >** .</span><span class="sxs-lookup"><span data-stu-id="d3544-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="d3544-148">İçinde **anahtar dosya adı** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3544-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3544-149">NET **anahtar dosyamı bir parolayla korumak** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="d3544-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3544-150">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d3544-150">Click **OK**.</span></span>

6. <span data-ttu-id="d3544-151">ISampleInterface.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d3544-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="d3544-152">Aşağıdaki kodu ISampleInterface arabirimi oluşturmak için ISampleInterface sınıf dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. <span data-ttu-id="d3544-153">Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="d3544-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="d3544-154">İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**.</span><span class="sxs-lookup"><span data-stu-id="d3544-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="d3544-155">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3544-155">Click **Exit**.</span></span>

8. <span data-ttu-id="d3544-156">İçinde `Guid` özniteliği, örnek GUID silin ve kopyalama GUID yapıştırın **GUID Oluştur** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d3544-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="d3544-157">Küme ayraçları Kaldır ({}) kopyalanan Guid'den.</span><span class="sxs-lookup"><span data-stu-id="d3544-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="d3544-158">Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="d3544-158">On the **Project** menu, click **Show All Files**.</span></span>

10. <span data-ttu-id="d3544-159">İçinde **Çözüm Gezgini**, genişletme **Projem** klasör.</span><span class="sxs-lookup"><span data-stu-id="d3544-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="d3544-160">AssemblyInfo.vb çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3544-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="d3544-161">Dosyaya şu özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-161">Add the following attribute to the file.</span></span>

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    <span data-ttu-id="d3544-162">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-162">Save the file.</span></span>

11. <span data-ttu-id="d3544-163">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-163">Save the project.</span></span>

12. <span data-ttu-id="d3544-164">TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="d3544-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3544-165">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="d3544-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="d3544-166">Bir çalışma zamanı sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3544-166">Creating a Runtime Class</span></span>

### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="d3544-167">Tür eşdeğerliği çalışma zamanı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3544-167">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="d3544-168">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="d3544-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3544-169">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3544-170">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d3544-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3544-171">İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d3544-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="d3544-172">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3544-172">The new project is created.</span></span>

3. <span data-ttu-id="d3544-173">İçinde **Çözüm Gezgini**Class1.vb dosyaya sağ tıklayın ve tıklayın **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="d3544-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="d3544-174">Dosyayı Yeniden Adlandır `SampleClass.vb` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d3544-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="d3544-175">Dosya yeniden adlandırılırken da yeniden adlandırır sınıfa `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="d3544-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="d3544-176">Bu sınıf uygulayacak `ISampleInterface` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d3544-176">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="d3544-177">TypeEquivalenceRuntime projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3544-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3544-178">Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3544-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="d3544-179">Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3544-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3544-180">İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >** .</span><span class="sxs-lookup"><span data-stu-id="d3544-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="d3544-181">İçinde **anahtar dosya adı** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3544-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3544-182">NET **anahtar dosyamı bir parolayla korumak** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="d3544-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3544-183">          **Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d3544-183">Click **OK**.</span></span>

6. <span data-ttu-id="d3544-184">TypeEquivalenceRuntime projeyi sağ tıklatıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d3544-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="d3544-185">Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="d3544-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3544-186">TypeEquivalenceInterface.dll dosyasını seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d3544-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="d3544-187">Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="d3544-187">On the **Project** menu, click **Show All Files**.</span></span>

8. <span data-ttu-id="d3544-188">İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="d3544-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3544-189">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d3544-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3544-190">TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **belirli sürüm** özelliğini **False**.</span><span class="sxs-lookup"><span data-stu-id="d3544-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

9. <span data-ttu-id="d3544-191">Aşağıdaki kodu SampleClass sınıfı oluşturmak için SampleClass sınıf dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

    ```vb
    Imports TypeEquivalenceInterface

    Public Class SampleClass
        Implements ISampleInterface

        Private p_UserInput As String
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
            Get
                Return p_UserInput
            End Get
        End Property

        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
            Console.WriteLine("Please enter a value:")
            p_UserInput = Console.ReadLine()
        End Sub
    End Class
    ```

10. <span data-ttu-id="d3544-192">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-192">Save the project.</span></span>

11. <span data-ttu-id="d3544-193">TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="d3544-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3544-194">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="d3544-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="d3544-195">Bir istemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3544-195">Creating a Client Project</span></span>

### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="d3544-196">Tür eşdeğerliği istemci projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3544-196">To create the type equivalence client project</span></span>

1. <span data-ttu-id="d3544-197">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="d3544-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3544-198">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3544-199">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="d3544-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="d3544-200">İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d3544-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="d3544-201">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3544-201">The new project is created.</span></span>

3. <span data-ttu-id="d3544-202">TypeEquivalenceClient projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3544-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="d3544-203">Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3544-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="d3544-204">TypeEquivalenceClient projeyi sağ tıklatıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d3544-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="d3544-205">Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="d3544-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3544-206">TypeEquivalenceInterface.dll dosyası (TypeEquivalenceRuntime.dll değil) seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d3544-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="d3544-207">Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="d3544-207">On the **Project** menu, click **Show All Files**.</span></span>

6. <span data-ttu-id="d3544-208">İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="d3544-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3544-209">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d3544-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3544-210">TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğini **True**.</span><span class="sxs-lookup"><span data-stu-id="d3544-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

7. <span data-ttu-id="d3544-211">İstemci programı oluşturma işleminin Module1.vb dosyaya aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-211">Add the following code to the Module1.vb file to create the client program.</span></span>

    ```vb
    Imports TypeEquivalenceInterface
    Imports System.Reflection

    Module Module1

        Sub Main()
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
            Dim sampleClass As ISampleInterface = CType( _
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
            sampleClass.GetUserInput()
            Console.WriteLine(sampleClass.UserInput)
            Console.WriteLine(sampleAssembly.GetName().Version)
            Console.ReadLine()
        End Sub

    End Module
    ```

8. <span data-ttu-id="d3544-212">Derleme ve programı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d3544-212">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="d3544-213">Arabirim değiştirme</span><span class="sxs-lookup"><span data-stu-id="d3544-213">Modifying the Interface</span></span>

### <a name="to-modify-the-interface"></a><span data-ttu-id="d3544-214">Arabirim değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d3544-214">To modify the interface</span></span>

1. <span data-ttu-id="d3544-215">Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="d3544-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="d3544-216">İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projeye sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3544-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="d3544-217">Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d3544-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3544-218">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3544-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="d3544-219">ISampleInterface.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d3544-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="d3544-220">Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-220">Add the following line of code to the ISampleInterface interface.</span></span>

    ```vb
    Function GetDate() As Date
    ```

    <span data-ttu-id="d3544-221">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-221">Save the file.</span></span>

4. <span data-ttu-id="d3544-222">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-222">Save the project.</span></span>

5. <span data-ttu-id="d3544-223">TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="d3544-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3544-224">Sınıf kitaplığı .dll dosyasını yeni bir sürümü derlenmiş ve belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="d3544-225">Çalışma zamanı sınıf değiştirme</span><span class="sxs-lookup"><span data-stu-id="d3544-225">Modifying the Runtime Class</span></span>

### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="d3544-226">Çalışma zamanı sınıf değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="d3544-226">To modify the runtime class</span></span>

1. <span data-ttu-id="d3544-227">Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="d3544-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="d3544-228">İçinde **Proje Aç** iletişim kutusuna TypeEquivalenceRuntime projeye sağ tıklayın ve tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d3544-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3544-229">Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d3544-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3544-230">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3544-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="d3544-231">SampleClass.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d3544-231">Open the SampleClass.vb file.</span></span> <span data-ttu-id="d3544-232">Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3544-232">Add the following lines of code to the SampleClass class.</span></span>

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    <span data-ttu-id="d3544-233">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-233">Save the file.</span></span>

4. <span data-ttu-id="d3544-234">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d3544-234">Save the project.</span></span>

5. <span data-ttu-id="d3544-235">TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="d3544-235">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3544-236">Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d3544-236">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="d3544-237">Dosya Gezgini'nde, çıkış yolu klasörü (örneğin, C:\TypeEquivalenceSample) açın.</span><span class="sxs-lookup"><span data-stu-id="d3544-237">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="d3544-238">Programı çalıştırmak üzere TypeEquivalenceClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3544-238">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="d3544-239">Program, yeniden derlenen kalmadan TypeEquivalenceRuntime derlemenin yeni sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="d3544-239">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3544-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3544-240">See also</span></span>

- [<span data-ttu-id="d3544-241">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3544-241">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="d3544-242">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="d3544-242">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="d3544-243">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="d3544-243">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d3544-244">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="d3544-244">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
