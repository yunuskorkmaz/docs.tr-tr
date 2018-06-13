---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644192"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="c9537-102">İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="c9537-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="c9537-103">Tanımlayıcı adlı Yönetilen derleme tür bilgilerini katıştırma, geniş sürüm bağımsızlığı elde etmek için bir uygulamada türü eşleştiği.</span><span class="sxs-lookup"><span data-stu-id="c9537-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="c9537-104">Diğer bir deyişle, her sürüm için derlenmesi gerek kalmadan yönetilen kitaplık birden fazla sürümünü türlerinden kullanmak için program yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="c9537-105">Türü katıştırma Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9537-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="c9537-106">Tür bilgilerini katıştırma Microsoft Office'in farklı sürümlerinde farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9537-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="c9537-107">Ancak, tam olarak yönetilen bir çözüm katıştırma türü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9537-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="c9537-108">Aşağıdaki özelliklere sahip bir derlemeden tür bilgileri katıştırılabilen:</span><span class="sxs-lookup"><span data-stu-id="c9537-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="c9537-109">Derleme en az bir ortak arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="c9537-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="c9537-110">Katıştırılmış arabirimleri ile Açıklama eklenen bir `ComImport` özniteliğini ve bir `Guid` özniteliği (ve benzersiz bir GUID).</span><span class="sxs-lookup"><span data-stu-id="c9537-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="c9537-111">Derleme ile Açıklama `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliği ve derleme düzeyi `Guid` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c9537-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="c9537-112">(Varsayılan olarak, Visual Basic proje şablonları derleme düzeyi dahil `Guid` özniteliği.)</span><span class="sxs-lookup"><span data-stu-id="c9537-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="c9537-113">Katıştırılabilen genel arabirimler belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9537-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="c9537-114">Bir istemci programı daha sonra bu arabirimleri tasarım zamanında tür bilgileri ayarı ve ortak arabirimleri içeren derlemenin başvurarak eklenebilir `Embed Interop Types` referansı özelliğinin `True`.</span><span class="sxs-lookup"><span data-stu-id="c9537-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="c9537-115">Bu komut satırı derleyicisini kullanarak ve kullanarak bütünleştirilmiş başvurma eşdeğerdir `/link` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c9537-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="c9537-116">İstemci programı daha sonra bu arabirimleri olarak belirtilmiş, çalışma zamanı nesnelerinin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="c9537-117">Tanımlayıcı adlı çalışma zamanı derlemesi yeni bir sürümünü oluşturursanız, istemci programı ile güncelleştirilmiş çalışma zamanı derlemesi derlenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c9537-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="c9537-118">Bunun yerine, istemcinin hangi sürümü çalışma zamanı derlemesi için ortak arabirimleri katıştırılmış tür bilgileri kullanarak, kullanılabilir kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="c9537-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="c9537-119">COM birlikte çalışma derlemeleri türü bilgilerin destekliyoruz türü katıştırma birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="c9537-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="c9537-120">Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="c9537-121">Genel parametreler bir türünü kullanır ve katıştırılmış türünün genel parametresi türü ise, bu tür bir derleme sınırından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c9537-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="c9537-122">Başka bir derlemeye ait bir yöntemi çağırma bir derleme sınırını geçmesinden örnekleri dahil edin veya başka bir derlemede tanımlanan bir türü türetme bir türü.</span><span class="sxs-lookup"><span data-stu-id="c9537-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="c9537-123">Sabitler katıştırılmış değil.</span><span class="sxs-lookup"><span data-stu-id="c9537-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="c9537-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıf anahtarı olarak katıştırılmış bir türü desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="c9537-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="c9537-125">Katıştırılmış bir tür bir anahtar olarak desteklemek için kendi Sözlük türü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9537-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="c9537-126">Bu kılavuzda, aşağıdakileri:</span><span class="sxs-lookup"><span data-stu-id="c9537-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="c9537-127">Katıştırılabilen tür bilgileri içeren ortak bir arabirim tanımlayıcı adlı bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9537-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="c9537-128">Ortak arabirimi uygulayan bir tanımlayıcı adlı çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9537-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="c9537-129">Ortak arabirimi tür bilgilerini katıştırır ve çalışma zamanı derlemesinden sınıfının bir örneği oluşturan bir istemci program oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9537-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="c9537-130">Değiştirme ve çalışma zamanı derlemesi derleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="c9537-131">Çalışma zamanı derlemesi yeni sürümünü istemci programı yeniden derlemenize gerek kalmadan kullanıldığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9537-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="c9537-132">Bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9537-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="c9537-133">Tür denkliği arabirimi projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c9537-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="c9537-134">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="c9537-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c9537-135">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="c9537-136">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c9537-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="c9537-137">İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9537-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="c9537-138">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9537-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="c9537-139">İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="c9537-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="c9537-140">Dosyayı Yeniden Adlandır `ISampleInterface.vb` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c9537-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="c9537-141">Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="c9537-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="c9537-142">Bu sınıf, sınıf için ortak arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9537-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="c9537-143">TypeEquivalenceInterface projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c9537-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="c9537-144">Tıklatın **derleme** sekmesi. Çıkış yolu geliştirme bilgisayarınızda geçerli bir konuma ayarlı `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="c9537-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="c9537-145">Bu konum, bu kılavuzda bir sonraki adımda de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9537-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="c9537-146">Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c9537-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="c9537-147">İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**.</span><span class="sxs-lookup"><span data-stu-id="c9537-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="c9537-148">İçinde **anahtar dosya adını** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="c9537-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="c9537-149">Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="c9537-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="c9537-150">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c9537-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c9537-151">ISampleInterface.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c9537-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="c9537-152">ISampleInterface arabirimi oluşturmak üzere ISampleInterface sınıfı dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="c9537-153">Üzerinde **Araçları** menüsünde tıklatın **Create GUID**.</span><span class="sxs-lookup"><span data-stu-id="c9537-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="c9537-154">İçinde **Create GUID** iletişim kutusu, tıklatın **kayıt defteri biçimi** ve ardından **kopya**.</span><span class="sxs-lookup"><span data-stu-id="c9537-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="c9537-155">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9537-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="c9537-156">İçinde `Guid` özniteliği, örnek GUID silme ve kopyalama GUID yapıştırın **Create GUID** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="c9537-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="c9537-157">Küme ayraçları Kaldır ({}) kopyalanan Guid'den.</span><span class="sxs-lookup"><span data-stu-id="c9537-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="c9537-158">Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="c9537-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="c9537-159">İçinde **Çözüm Gezgini**, genişletin **My proje** klasör.</span><span class="sxs-lookup"><span data-stu-id="c9537-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="c9537-160">AssemblyInfo.vb çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9537-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="c9537-161">Aşağıdaki öznitelik dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="c9537-162">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-162">Save the file.</span></span>  
  
11. <span data-ttu-id="c9537-163">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-163">Save the project.</span></span>  
  
12. <span data-ttu-id="c9537-164">TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="c9537-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="c9537-165">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="c9537-166">Bir çalışma zamanı sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9537-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="c9537-167">Tür denkliği çalışma zamanı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c9537-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="c9537-168">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="c9537-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c9537-169">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="c9537-170">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c9537-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="c9537-171">İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9537-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="c9537-172">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9537-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="c9537-173">İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="c9537-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="c9537-174">Dosyayı Yeniden Adlandır `SampleClass.vb` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c9537-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="c9537-175">Dosyayı yeniden adlandırmak de yeniden adlandırır sınıfına `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="c9537-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="c9537-176">Bu sınıf gerçekleştireceksiniz `ISampleInterface` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c9537-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="c9537-177">TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c9537-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="c9537-178">Tıklatın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="c9537-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="c9537-179">Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c9537-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="c9537-180">İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**.</span><span class="sxs-lookup"><span data-stu-id="c9537-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="c9537-181">İçinde **anahtar dosya adını** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="c9537-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="c9537-182">Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="c9537-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="c9537-183">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c9537-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c9537-184">TypeEquivalenceRuntime projeyi sağ tıklatın ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c9537-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="c9537-185">Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın.</span><span class="sxs-lookup"><span data-stu-id="c9537-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="c9537-186">TypeEquivalenceInterface.dll dosyasını tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9537-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="c9537-187">Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="c9537-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="c9537-188">İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="c9537-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="c9537-189">TypeEquivalenceInterface referans'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c9537-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="c9537-190">TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **belirli bir sürüm** özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="c9537-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="c9537-191">SampleClass sınıfı oluşturmak için SampleClass sınıfı dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
  
10. <span data-ttu-id="c9537-192">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-192">Save the project.</span></span>  
  
11. <span data-ttu-id="c9537-193">TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="c9537-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="c9537-194">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="c9537-195">Bir istemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9537-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="c9537-196">Tür denkliği istemci projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c9537-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="c9537-197">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="c9537-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c9537-198">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="c9537-199">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c9537-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="c9537-200">İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9537-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="c9537-201">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9537-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="c9537-202">TypeEquivalenceClient projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c9537-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="c9537-203">Tıklatın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="c9537-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="c9537-204">TypeEquivalenceClient projeyi sağ tıklatın ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c9537-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="c9537-205">Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın.</span><span class="sxs-lookup"><span data-stu-id="c9537-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="c9537-206">TypeEquivalenceInterface.dll dosyasını (TypeEquivalenceRuntime.dll değil) tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c9537-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="c9537-207">Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="c9537-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="c9537-208">İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="c9537-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="c9537-209">TypeEquivalenceInterface referans'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c9537-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="c9537-210">TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="c9537-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="c9537-211">İstemci programı oluşturmak için Module1.vb dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
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
  
8.  <span data-ttu-id="c9537-212">Derleme ve programı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c9537-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="c9537-213">Arabirim değiştirme</span><span class="sxs-lookup"><span data-stu-id="c9537-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="c9537-214">Arabirim değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c9537-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="c9537-215">Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="c9537-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="c9537-216">İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projesine sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c9537-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="c9537-217">Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c9537-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="c9537-218">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="c9537-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="c9537-219">ISampleInterface.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c9537-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="c9537-220">Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="c9537-221">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="c9537-222">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="c9537-223">TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="c9537-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="c9537-224">Yeni bir sınıf kitaplığı .dll dosyasının sürümünü derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="c9537-225">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="c9537-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="c9537-226">Çalışma zamanı sınıf değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c9537-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="c9537-227">Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="c9537-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="c9537-228">İçinde **Proje Aç** iletişim kutusunda, TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c9537-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="c9537-229">Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c9537-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="c9537-230">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="c9537-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="c9537-231">SampleClass.vbfile açın.</span><span class="sxs-lookup"><span data-stu-id="c9537-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="c9537-232">Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9537-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="c9537-233">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="c9537-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="c9537-234">TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="c9537-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="c9537-235">Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c9537-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="c9537-236">Dosya Gezgini'nde, çıkış yolunu klasörünü (örneğin, C:\TypeEquivalenceSample) açın.</span><span class="sxs-lookup"><span data-stu-id="c9537-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="c9537-237">Programı çalıştırmak için TypeEquivalenceClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9537-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="c9537-238">Program, yeniden derlenmesi olmadan TypeEquivalenceRuntime derlemesinin yeni sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="c9537-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9537-239">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9537-239">See Also</span></span>  
 [<span data-ttu-id="c9537-240">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9537-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="c9537-241">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="c9537-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="c9537-242">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="c9537-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="c9537-243">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9537-243">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
