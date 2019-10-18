---
title: "İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme"
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1a37a3bcc3b1bc352d6a2f59691819e0b2403d3d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523901"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="58dec-102">İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme</span><span class="sxs-lookup"><span data-stu-id="58dec-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="58dec-103">Tanımlayıcı adlı yönetilen bir derlemeden tür bilgilerini eklerseniz, sürüm bağımsızlığını elde etmek için bir uygulamada gevşek olarak birkaç tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dec-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="58dec-104">Diğer bir deyişle, programınız her yeni sürüm için yeniden derlenmesi gerekmeden yönetilen bir kitaplığın herhangi bir sürümündeki türleri kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="58dec-105">Tür ekleme, genellikle Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58dec-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="58dec-106">Tür bilgilerinin gömülmesi, farklı bilgisayarlarda farklı Microsoft Office sürümleriyle çalışmak için aynı programın derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="58dec-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="58dec-107">Ancak, tam olarak yönetilen çözümlerle tür eklemeyi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dec-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="58dec-108">Katıştırılabilen ortak arabirimleri belirttikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="58dec-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="58dec-109">İstemci programı, genel arabirimleri içeren derlemeye başvurarak ve `True` başvurusunun `Embed Interop Types` özelliğini ayarlayarak, arabirimlerin tür bilgilerini tasarım zamanında ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="58dec-110">İstemci programı daha sonra bu arabirimler olarak yazılmış çalışma zamanı nesnelerinin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="58dec-111">Bu, komut satırı derleyicisini kullanma ve `/link` derleyici seçeneği kullanılarak derlemeye başvurma ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="58dec-111">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> 

<span data-ttu-id="58dec-112">Güçlü adlandırılmış çalışma zamanı derlemenin yeni bir sürümünü oluşturursanız, istemci programın yeniden derlenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="58dec-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="58dec-113">İstemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak çalışma zamanı derlemesinin hangi sürümünün kullanılabilir olduğunu kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="58dec-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="58dec-114">Bu izlenecek yolda şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58dec-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="58dec-115">Katıştırılabilen tür bilgilerini içeren bir ortak arabirim ile tanımlayıcı adlı bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58dec-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="58dec-116">Ortak arabirimi uygulayan, tanımlayıcı adlı bir çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58dec-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="58dec-117">Ortak arabirimden tür bilgilerini katıştıran bir istemci programı oluşturun ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58dec-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="58dec-118">Çalışma zamanı derlemesini değiştirin ve yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="58dec-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="58dec-119">Yeniden derlenmesi gerekmeden, çalışma zamanı derlemesinin yeni sürümünü kullandığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58dec-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="58dec-120">Koşullar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="58dec-120">Conditions and limitations</span></span>

<span data-ttu-id="58dec-121">Bir derlemeden tür bilgilerini aşağıdaki koşullarda ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58dec-121">You can embed type information from an assembly under the following conditions:</span></span> 

- <span data-ttu-id="58dec-122">Derleme en az bir ortak arabirim kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="58dec-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="58dec-123">Katıştırılmış arabirimlere, `ComImport` öznitelikleri ve benzersiz GUID 'Ler `Guid` öznitelikleriyle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="58dec-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="58dec-124">Derlemeye `ImportedFromTypeLib` özniteliğiyle veya `PrimaryInteropAssembly` özniteliğiyle ve derleme düzeyi `Guid` özniteliğiyle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="58dec-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="58dec-125">Görsel C# ve Visual Basic proje şablonları varsayılan olarak bir derleme düzeyi `Guid` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="58dec-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="58dec-126">Ekleme türü birincil işlevi COM birlikte çalışma derlemelerini desteklemek olduğundan, tür bilgilerini tam olarak yönetilen bir çözüme eklediğinizde aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="58dec-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="58dec-127">Yalnızca COM birlikte çalışabilirliğine özgü öznitelikler katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="58dec-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="58dec-128">Diğer öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="58dec-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="58dec-129">Bir tür genel parametreler kullanıyorsa ve genel parametrenin türü gömülü bir türse, bu tür bir derleme sınırı boyunca kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="58dec-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="58dec-130">Bir derleme sınırının geçmesinin örnekleri, başka bir derlemeden bir yöntemi çağırmayı veya başka bir derlemede tanımlanan türden bir tür türetmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="58dec-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="58dec-131">Sabitler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="58dec-131">Constants are not embedded.</span></span>
- <span data-ttu-id="58dec-132">@No__t_0 sınıfı, gömülü bir türü anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="58dec-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="58dec-133">Gömülü bir türü anahtar olarak desteklemek için kendi sözlük türünü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dec-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="58dec-134">Arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="58dec-134">Create an interface</span></span>

<span data-ttu-id="58dec-135">İlk adım tür denklik arabirim derlemesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="58dec-135">The first step is to create the type equivalence interface assembly.</span></span> 

1. <span data-ttu-id="58dec-136">Visual Studio 'da **dosya**  > **Yeni**  > **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58dec-137">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58dec-138">Listeden C# ya da vb **sınıf kitaplığı (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-138">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58dec-139">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceInterface*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="58dec-140">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="58dec-140">The new project is created.</span></span>
   
1. <span data-ttu-id="58dec-141">**Çözüm Gezgini**' de, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklatın, **Yeniden Adlandır**' ı seçin ve dosyayı SınıfAdı SınıfAdı *' dan* *isampelınterface*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="58dec-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="58dec-142">Ayrıca, `ISampleInterface` sınıfını yeniden adlandırmak için komut istemine **Evet** yanıtı yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="58dec-143">Bu sınıf, sınıfının genel arabirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58dec-143">This class represents the public interface for the class.</span></span>
   
1. <span data-ttu-id="58dec-144">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span> 
   
1. <span data-ttu-id="58dec-145">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve **Çıkış yolunu** bilgisayarınızdaki bir konuma (örneğin, *C:\TypeEquivalenceSample*) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="58dec-146">Bu izlenecek yol boyunca aynı konumu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="58dec-146">You use the same location throughout this walkthrough.</span></span> 
   
1. <span data-ttu-id="58dec-147">**Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58dec-148">**Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58dec-149">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58dec-150">**Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-151">Kod düzenleyicisinde *ısamptaınterface* sınıf dosyasını açın ve `ISampleInterface` arabirimini oluşturmak için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="58dec-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>
   
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
   
   ```vb
   Imports System.Runtime.InteropServices
   
   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```
   
1. <span data-ttu-id="58dec-152">**Araçlar** menüsünde **GUID oluştur**' u seçin ve **Guid oluştur** iletişim kutusunda **kayıt defteri biçimi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="58dec-153">**Kopyala**' yı seçin ve ardından **Çıkış**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-153">Select **Copy**, and then select **Exit**.</span></span>
   
1. <span data-ttu-id="58dec-154">Kodunuzun `Guid` özniteliğinde, örnek GUID 'yi kopyaladığınız GUID ile değiştirin ve ayraçları ( **{}** ) kaldırın.</span><span class="sxs-lookup"><span data-stu-id="58dec-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>
   
1. <span data-ttu-id="58dec-155">**Çözüm Gezgini**, **Özellikler** klasörünü genişletin ve *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="58dec-156">Kod Düzenleyicisi 'nde, dosyaya aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58dec-156">In the code editor, add the following attribute to the file:</span></span>
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. <span data-ttu-id="58dec-157">Dosyaları ve projeyi kaydetmek için  >  **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL** +**SHIFT** +**S** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58dec-158">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58dec-159">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen derleme çıkış yoluna kaydedilir, örneğin *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58dec-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="58dec-160">Çalışma zamanı sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="58dec-160">Create a runtime class</span></span>

<span data-ttu-id="58dec-161">Sonra, tür eşdeğerlik çalışma zamanı sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58dec-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="58dec-162">Visual Studio 'da **dosya**  > **Yeni**  > **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58dec-163">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58dec-164">Listeden C# ya da vb **sınıf kitaplığı (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-164">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58dec-165">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceRuntime*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="58dec-166">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="58dec-166">The new project is created.</span></span>
   
1. <span data-ttu-id="58dec-167">**Çözüm Gezgini**, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklayın, **Yeniden Adlandır**' ı seçin ve dosyayı *SınıfAdı SınıfAdı* *' dan* SampleClass olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="58dec-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="58dec-168">Ayrıca, `SampleClass` sınıfını yeniden adlandırmak için komut istemine **Evet** yanıtı yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="58dec-169">Bu sınıf `ISampleInterface` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="58dec-169">This class implements the `ISampleInterface` interface.</span></span>
   
1. <span data-ttu-id="58dec-170">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58dec-171">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58dec-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58dec-172">**Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58dec-173">**Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58dec-174">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58dec-175">**Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-176">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve  > **başvuru** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58dec-177">**Başvuru Yöneticisi** iletişim kutusunda, **Araştır** ' ı seçin ve çıkış yolu klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="58dec-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="58dec-178">*TypeEquivalenceInterface. dll* dosyasını seçin, **Ekle**' yi seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-179">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58dec-180">**Özellikler** bölmesinde, **belirli bir sürümü** henüz yoksa **yanlış** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>
   
1. <span data-ttu-id="58dec-181">Kod düzenleyicisinde *SampleClass* sınıf dosyasını açın ve `SampleClass` sınıfını oluşturmak için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="58dec-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>
   
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
   
1. <span data-ttu-id="58dec-182">Dosyaları ve projeyi kaydetmek için  >  **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL** +**SHIFT** +**S** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58dec-183">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58dec-184">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="58dec-185">İstemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="58dec-185">Create a client project</span></span>

<span data-ttu-id="58dec-186">Son olarak, arabirim derlemesine başvuran bir tür denklik istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58dec-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="58dec-187">Visual Studio 'da **dosya**  > **Yeni**  > **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58dec-188">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *konsol* yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="58dec-189">Listeden C# ya da vb **konsol uygulaması (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-189">Select either the C# or VB **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58dec-190">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceClient*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="58dec-191">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="58dec-191">The new project is created.</span></span>
   
1. <span data-ttu-id="58dec-192">**Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58dec-193">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58dec-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58dec-194">**Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve  > **başvuru** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58dec-195">**Başvuru Yöneticisi** iletişim kutusunda, **TypeEquivalenceInterface. dll** dosyası zaten listeleniyorsa, onu seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="58dec-196">Aksi takdirde, **Araştır**' ı seçin, çıkış yolu klasörüne gidin, *TypeEquivalenceInterface. dll* dosyasını ( *TypeEquivalenceRuntime. dll*değil) seçin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="58dec-197">**Tamam ' ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-197">Select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-198">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58dec-199">**Özellikler** bölmesinde, **birlikte çalışma türlerini katıştır** ' ı **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>
   
1. <span data-ttu-id="58dec-200">Kod düzenleyicisinde *program.cs* veya *Module1. vb* dosyasını açın ve istemci programını oluşturmak için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="58dec-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>
   
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
   
1. <span data-ttu-id="58dec-201">Dosyaları ve projeyi kaydetmek için  >  **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL** +**SHIFT** +**S** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58dec-202">Programı derlemek ve çalıştırmak için **Ctrl** +**F5** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="58dec-203">Konsol çıkışının **1.0.0.0**derleme sürümünü döndürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span> 
   
## <a name="modify-the-interface"></a><span data-ttu-id="58dec-204">Arabirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="58dec-204">Modify the interface</span></span>

<span data-ttu-id="58dec-205">Şimdi, arabirim derlemesini değiştirin ve sürümünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="58dec-205">Now, modify the interface assembly, and change its version.</span></span> 

1. <span data-ttu-id="58dec-206">Visual Studio 'da  >  **Dosya** ' yı seçin  > **Proje/çözüm**' i**açın** ve **TypeEquivalenceInterface** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="58dec-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>
   
1. <span data-ttu-id="58dec-207">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58dec-208">**Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58dec-209">**Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-210">*SampleInterface.cs* veya *sampleınterface. vb* dosyasını açın ve aşağıdaki kod satırını `ISampleInterface` arabirimine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58dec-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. <span data-ttu-id="58dec-211">Dosyaları ve projeyi kaydetmek için  >  **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL** +**SHIFT** +**S** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58dec-212">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58dec-213">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="58dec-214">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="58dec-214">Modify the runtime class</span></span>

<span data-ttu-id="58dec-215">Ayrıca çalışma zamanı sınıfını değiştirin ve sürümünü güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="58dec-215">Also modify the runtime class and update its version.</span></span> 

1. <span data-ttu-id="58dec-216">Visual Studio 'da  >  **Dosya** ' yı seçin  > **Proje/çözüm**' i**açın** ve **TypeEquivalenceRuntime** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="58dec-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>
   
1. <span data-ttu-id="58dec-217">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58dec-218">**Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58dec-219">**Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58dec-220">*SampleClass.cs* veya *SampleClass. vb* dosyasını açın ve `SampleClass` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58dec-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>
   
   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```
   
   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```
   
1. <span data-ttu-id="58dec-221">Dosyaları ve projeyi kaydetmek için  >  **Dosya** **Tümünü Kaydet** ' i seçin veya **CTRL** +**SHIFT** +**S** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="58dec-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58dec-222">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="58dec-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58dec-223">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="58dec-224">Güncelleştirilmiş istemci programını çalıştır</span><span class="sxs-lookup"><span data-stu-id="58dec-224">Run the updated client program</span></span> 

<span data-ttu-id="58dec-225">Yapı çıkış klasörü konumuna gidin ve *TypeEquivalenceClient. exe*' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58dec-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="58dec-226">Konsol çıkışının artık, yeniden Derlenmekte olan program olmadan, *2.0.0.0*`TypeEquivalenceRuntime` derlemesinin yeni sürümünü yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58dec-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="58dec-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58dec-227">See also</span></span>

- [<span data-ttu-id="58dec-228">-Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="58dec-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="58dec-229">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dec-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="58dec-230">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="58dec-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="58dec-231">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dec-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="58dec-232">Bütünleştirilmiş kod içeren program</span><span class="sxs-lookup"><span data-stu-id="58dec-232">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="58dec-233">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="58dec-233">Assemblies in .NET</span></span>](index.md)
