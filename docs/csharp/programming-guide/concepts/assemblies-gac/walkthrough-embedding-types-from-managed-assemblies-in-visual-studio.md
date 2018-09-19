---
title: "İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 1900c62d1ebaf611f141f8f1bdf95f8d11f82140
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004331"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="6771e-102">İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="6771e-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="6771e-103">Tanımlayıcı adlı bir yönetilen bütünleştirilmiş koddan tür bilgilerini katıştırma, sürüm bağımsızlığı elde etmek için bir uygulama türlerinde gevşek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6771e-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="6771e-104">Diğer bir deyişle, programınız her sürüm için derlenmesi zorunda kalmadan bir yönetilen kitaplık birden çok sürümünden türler kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="6771e-105">Ekleme türü Microsoft Office'ten Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6771e-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="6771e-106">Tür bilgilerini katıştırma farklı bilgisayarlarda Microsoft Office'in farklı sürümlerinde çalışmak için bir programın aynı yapısının sağlar.</span><span class="sxs-lookup"><span data-stu-id="6771e-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="6771e-107">Ancak, tam olarak yönetilen bir Çözümle ekleme türü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6771e-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="6771e-108">Tür bilgileri aşağıdaki özelliklere sahip bir derlemeden eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="6771e-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="6771e-109">Derleme en az bir ortak arabirim kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6771e-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="6771e-110">Katıştırılmış arabirimleri ile açıklamalı olan bir `ComImport` özniteliği ve `Guid` özniteliği (ve benzersiz bir GUID).</span><span class="sxs-lookup"><span data-stu-id="6771e-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="6771e-111">Derleme ile açıklanıyor `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliğini ve bir derleme düzeyi `Guid` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6771e-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="6771e-112">(Varsayılan olarak, Visual C# proje şablonlarında derleme düzeyi dahil `Guid` özniteliği.)</span><span class="sxs-lookup"><span data-stu-id="6771e-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="6771e-113">Eklenebilecek Ortak arabirimlerin belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıflar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6771e-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="6771e-114">Bir istemci programını sonra bu arabirimleri için tasarım zamanında tür bilgilerini genel arabirimleri ve ayar içeren derleme başvurarak katıştırabilirsiniz `Embed Interop Types` özelliği için başvuru `True`.</span><span class="sxs-lookup"><span data-stu-id="6771e-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="6771e-115">Bu komut satırı derleyicisini kullanarak ve kullanarak derlemenin başvurduğu eşdeğerdir `/link` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6771e-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="6771e-116">İstemci programı daha sonra bu arabirimleri olarak yazılan, çalışma zamanı nesnelerinin örneklerini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6771e-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="6771e-117">Çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kodunuzda yeni bir sürümü oluşturursanız, güncelleştirilmiş çalışma zamanı derleme ile derlenmesi istemci program yok.</span><span class="sxs-lookup"><span data-stu-id="6771e-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="6771e-118">Bunun yerine, istemci programı, ortak arabirimler için gömülü tür bilgileri kullanarak hangi çalışma zamanı derleme sürümü, kullanıma hazır kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="6771e-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="6771e-119">Tür bilgilerini COM birlikte çalışma derlemelerini, destekliyoruz türü ekleme birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="6771e-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="6771e-120">Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="6771e-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="6771e-121">Bir tür genel parametreleri kullanan ve katıştırılmış tür genel parametre türü ise, bu tür bir bütünleştirilmiş kod sınırları arasında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6771e-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="6771e-122">Başka bir derlemeden bir yöntemi çağırmak bir derleme sınırı aşan örnekleri şunlardır veya başka bir derlemede tanımlanan bir türü türetilen bir tür.</span><span class="sxs-lookup"><span data-stu-id="6771e-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="6771e-123">Sabitler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="6771e-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="6771e-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıfı, bir anahtar olarak gömülü bir türünü desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="6771e-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="6771e-125">Katıştırılmış tür olarak bir anahtar desteklemek için kendi Sözlük türü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6771e-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="6771e-126">Bu kılavuzda, aşağıdakileri yapmanız:</span><span class="sxs-lookup"><span data-stu-id="6771e-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="6771e-127">Eklenebilecek tür bilgilerini içeren bir ortak arabirim kesin adlandırılmış bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6771e-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="6771e-128">Genel arabirimi uygulayan bir çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kod oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6771e-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="6771e-129">Ortak arabirim tür bilgilerini katıştırır ve çalışma zamanı derlemenin sınıfının bir örneğini oluşturan bir istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6771e-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="6771e-130">Değiştirin ve çalışma zamanı derleme yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="6771e-131">İstemcinin yeniden derlemenize gerek kalmadan yeni çalışma zamanı derleme sürümünü kullanılmakta olduğunu görmek için istemci programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6771e-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="6771e-132">Bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="6771e-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="6771e-133">Tür eşdeğerliği arabirimi projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6771e-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="6771e-134">Visual Studio'da üzerinde **dosya** menüsünde seçin **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="6771e-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6771e-135">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6771e-136">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6771e-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="6771e-137">İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6771e-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="6771e-138">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6771e-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6771e-139">İçinde **Çözüm Gezgini**, Class1.cs dosyasını sağ tıklatıp **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="6771e-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="6771e-140">Dosyayı Yeniden Adlandır `ISampleInterface.cs` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6771e-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="6771e-141">Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="6771e-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="6771e-142">Bu sınıf, sınıf için ortak arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6771e-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="6771e-143">TypeEquivalenceInterface projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6771e-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="6771e-144">Tıklayın **derleme** sekmesi. Çıkış yolu geçerli bir konum, geliştirme bilgisayarınızda gibi ayarlamak `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="6771e-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="6771e-145">Bu konum, ayrıca bu izlenecek yolda bir sonraki adımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6771e-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="6771e-146">Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6771e-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="6771e-147">İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >**.</span><span class="sxs-lookup"><span data-stu-id="6771e-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="6771e-148">İçinde **anahtar dosya adı** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="6771e-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="6771e-149">NET **anahtar dosyamı bir parolayla korumak** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="6771e-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="6771e-150">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6771e-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6771e-151">ISampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6771e-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="6771e-152">Aşağıdaki kodu ISampleInterface arabirimi oluşturmak için ISampleInterface sınıf dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="6771e-153">Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="6771e-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="6771e-154">İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**.</span><span class="sxs-lookup"><span data-stu-id="6771e-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="6771e-155">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6771e-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="6771e-156">İçinde `Guid` özniteliği, örnek GUID silin ve kopyalama GUID yapıştırın **GUID Oluştur** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6771e-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="6771e-157">Küme ayraçları Kaldır ({}) kopyalanan Guid'den.</span><span class="sxs-lookup"><span data-stu-id="6771e-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="6771e-158">İçinde **Çözüm Gezgini**, genişletme **özellikleri** klasör.</span><span class="sxs-lookup"><span data-stu-id="6771e-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="6771e-159">AssemblyInfo.cs dosyasını çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6771e-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="6771e-160">Dosyaya şu özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="6771e-161">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-161">Save the file.</span></span>  
  
10. <span data-ttu-id="6771e-162">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-162">Save the project.</span></span>  
  
11. <span data-ttu-id="6771e-163">TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="6771e-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="6771e-164">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="6771e-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="6771e-165">Bir çalışma zamanı sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="6771e-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="6771e-166">Tür eşdeğerliği çalışma zamanı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6771e-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="6771e-167">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="6771e-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6771e-168">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6771e-169">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6771e-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="6771e-170">İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6771e-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="6771e-171">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6771e-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6771e-172">İçinde **Çözüm Gezgini**, Class1.cs dosyasını sağ tıklatıp **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="6771e-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="6771e-173">Dosyayı Yeniden Adlandır `SampleClass.cs` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6771e-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="6771e-174">Dosya yeniden adlandırılırken da yeniden adlandırır sınıfa `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="6771e-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="6771e-175">Bu sınıf uygulayacak `ISampleInterface` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6771e-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="6771e-176">TypeEquivalenceRuntime projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6771e-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="6771e-177">Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="6771e-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="6771e-178">Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6771e-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="6771e-179">İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >**.</span><span class="sxs-lookup"><span data-stu-id="6771e-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="6771e-180">İçinde **anahtar dosya adı** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="6771e-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="6771e-181">NET **anahtar dosyamı bir parolayla korumak** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="6771e-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="6771e-182">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6771e-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6771e-183">TypeEquivalenceRuntime projeyi sağ tıklatıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6771e-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="6771e-184">Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="6771e-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="6771e-185">TypeEquivalenceInterface.dll dosyasını seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6771e-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="6771e-186">İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="6771e-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="6771e-187">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="6771e-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="6771e-188">TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **belirli sürüm** özelliğini **False**.</span><span class="sxs-lookup"><span data-stu-id="6771e-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="6771e-189">Aşağıdaki kodu SampleClass sınıfı oluşturmak için SampleClass sınıf dosyası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
    )  
    ```  
  
9. <span data-ttu-id="6771e-190">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-190">Save the project.</span></span>  
  
10. <span data-ttu-id="6771e-191">TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="6771e-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="6771e-192">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="6771e-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="6771e-193">Bir istemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6771e-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="6771e-194">Tür eşdeğerliği istemci projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6771e-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="6771e-195">Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="6771e-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6771e-196">İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6771e-197">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6771e-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="6771e-198">İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6771e-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="6771e-199">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6771e-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6771e-200">TypeEquivalenceClient projeyi sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6771e-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="6771e-201">Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="6771e-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="6771e-202">TypeEquivalenceClient projeyi sağ tıklatıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6771e-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="6771e-203">Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="6771e-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="6771e-204">TypeEquivalenceInterface.dll dosyası (TypeEquivalenceRuntime.dll değil) seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6771e-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="6771e-205">İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="6771e-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="6771e-206">TypeEquivalenceInterface başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="6771e-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="6771e-207">TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğini **True**.</span><span class="sxs-lookup"><span data-stu-id="6771e-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="6771e-208">İstemci programı oluşturmak için Program.cs dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
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
  
7.  <span data-ttu-id="6771e-209">Derleme ve programı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="6771e-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="6771e-210">Arabirim değiştirme</span><span class="sxs-lookup"><span data-stu-id="6771e-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="6771e-211">Arabirim değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="6771e-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="6771e-212">Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="6771e-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="6771e-213">İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projeye sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6771e-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="6771e-214">Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6771e-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="6771e-215">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6771e-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="6771e-216">SampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6771e-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="6771e-217">Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="6771e-218">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="6771e-219">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="6771e-220">TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="6771e-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="6771e-221">Sınıf kitaplığı .dll dosyasını yeni bir sürümü derlenmiş ve belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="6771e-222">Çalışma zamanı sınıf değiştirme</span><span class="sxs-lookup"><span data-stu-id="6771e-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="6771e-223">Çalışma zamanı sınıf değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="6771e-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="6771e-224">Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="6771e-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="6771e-225">İçinde **Proje Aç** iletişim kutusuna TypeEquivalenceRuntime projeye sağ tıklayın ve tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6771e-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="6771e-226">Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6771e-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="6771e-227">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="6771e-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="6771e-228">SampleClass.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6771e-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="6771e-229">Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6771e-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="6771e-230">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="6771e-231">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6771e-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="6771e-232">TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**.</span><span class="sxs-lookup"><span data-stu-id="6771e-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="6771e-233">Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6771e-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="6771e-234">Dosya Gezgini'nde, çıkış yolu klasörü (örneğin, C:\TypeEquivalenceSample) açın.</span><span class="sxs-lookup"><span data-stu-id="6771e-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="6771e-235">Programı çalıştırmak üzere TypeEquivalenceClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6771e-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="6771e-236">Program, yeniden derlenen kalmadan TypeEquivalenceRuntime derlemenin yeni sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="6771e-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6771e-237">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6771e-237">See Also</span></span>

- [<span data-ttu-id="6771e-238">/ Link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6771e-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
- [<span data-ttu-id="6771e-239">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6771e-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6771e-240">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="6771e-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
- [<span data-ttu-id="6771e-241">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="6771e-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
