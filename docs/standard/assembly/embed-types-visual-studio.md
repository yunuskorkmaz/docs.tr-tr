---
title: 'İzlenecek yol: Visual Studio’da yönetilen bütünleştirilmiş kodlardan türleri ekleme'
description: Bu izlenecek yol, Visual Studio kullanarak .NET 'teki yönetilen derlemelerden türlerin nasıl ekleneceğini gösterir. Gömülü türler, sürüm bağımsızlığını destekleyebilir.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378979"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="556fc-104">İzlenecek yol: Visual Studio’da yönetilen bütünleştirilmiş kodlardan türleri ekleme</span><span class="sxs-lookup"><span data-stu-id="556fc-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="556fc-105">Tanımlayıcı adlı yönetilen bir derlemeden tür bilgilerini eklerseniz, sürüm bağımsızlığını elde etmek için bir uygulamada gevşek olarak birkaç tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556fc-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="556fc-106">Diğer bir deyişle, programınız her yeni sürüm için yeniden derlenmesi gerekmeden yönetilen bir kitaplığın herhangi bir sürümündeki türleri kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="556fc-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="556fc-107">Tür ekleme, genellikle Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="556fc-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="556fc-108">Tür bilgilerinin gömülmesi, farklı bilgisayarlarda farklı Microsoft Office sürümleriyle çalışmak için aynı programın derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="556fc-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="556fc-109">Ancak, tam olarak yönetilen çözümlerle tür eklemeyi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556fc-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="556fc-110">Katıştırılabilen ortak arabirimleri belirttikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="556fc-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="556fc-111">İstemci programı, genel arabirimleri içeren derlemeye başvurarak ve başvurusunun özelliğini ayarlayarak, tasarım zamanında arabirimlerin tür bilgilerini ekleyebilir `Embed Interop Types` `True` .</span><span class="sxs-lookup"><span data-stu-id="556fc-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="556fc-112">İstemci programı daha sonra bu arabirimler olarak yazılmış çalışma zamanı nesnelerinin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="556fc-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="556fc-113">Bu, komut satırı derleyicisini kullanmakla ve derlemeye, [-Link derleyici seçeneği](../../csharp/language-reference/compiler-options/link-compiler-option.md)kullanılarak başvurulmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="556fc-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="556fc-114">Güçlü adlandırılmış çalışma zamanı derlemenin yeni bir sürümünü oluşturursanız, istemci programın yeniden derlenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="556fc-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="556fc-115">İstemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak çalışma zamanı derlemesinin hangi sürümünün kullanılabilir olduğunu kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="556fc-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="556fc-116">Bu izlenecek yolda şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="556fc-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="556fc-117">Katıştırılabilen tür bilgilerini içeren bir ortak arabirim ile tanımlayıcı adlı bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="556fc-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="556fc-118">Ortak arabirimi uygulayan, tanımlayıcı adlı bir çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="556fc-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="556fc-119">Ortak arabirimden tür bilgilerini katıştıran bir istemci programı oluşturun ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="556fc-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="556fc-120">Çalışma zamanı derlemesini değiştirin ve yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="556fc-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="556fc-121">Yeniden derlenmesi gerekmeden, çalışma zamanı derlemesinin yeni sürümünü kullandığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="556fc-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="556fc-122">Koşullar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="556fc-122">Conditions and limitations</span></span>

<span data-ttu-id="556fc-123">Bir derlemeden tür bilgilerini aşağıdaki koşullarda ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="556fc-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="556fc-124">Derleme en az bir ortak arabirim kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="556fc-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="556fc-125">Katıştırılmış arabirimlere, `ComImport` `Guid` benzersiz GUID 'leri olan öznitelikler ve özniteliklerle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="556fc-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="556fc-126">Derlemeye, `ImportedFromTypeLib` özniteliğiyle veya `PrimaryInteropAssembly` özniteliğiyle ve derleme düzeyi özniteliğiyle açıklama eklenir `Guid` .</span><span class="sxs-lookup"><span data-stu-id="556fc-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="556fc-127">Visual C# ve Visual Basic proje şablonları varsayılan olarak bir derleme düzeyi `Guid` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="556fc-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="556fc-128">Ekleme türü birincil işlevi COM birlikte çalışma derlemelerini desteklemek olduğundan, tür bilgilerini tam olarak yönetilen bir çözüme eklediğinizde aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="556fc-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="556fc-129">Yalnızca COM birlikte çalışabilirliğine özgü öznitelikler katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="556fc-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="556fc-130">Diğer öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="556fc-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="556fc-131">Bir tür genel parametreler kullanıyorsa ve genel parametrenin türü gömülü bir türse, bu tür bir derleme sınırı boyunca kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="556fc-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="556fc-132">Bir derleme sınırının geçmesinin örnekleri, başka bir derlemeden bir yöntemi çağırmayı veya başka bir derlemede tanımlanan türden bir tür türetmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="556fc-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="556fc-133">Sabitler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="556fc-133">Constants are not embedded.</span></span>
- <span data-ttu-id="556fc-134"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>Sınıf, gömülü bir türü anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="556fc-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="556fc-135">Gömülü bir türü anahtar olarak desteklemek için kendi sözlük türünü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556fc-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="556fc-136">Arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="556fc-136">Create an interface</span></span>

<span data-ttu-id="556fc-137">İlk adım tür denklik arabirim derlemesini oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="556fc-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="556fc-138">Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="556fc-139">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="556fc-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="556fc-140">Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="556fc-141">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceInterface*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="556fc-142">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="556fc-142">The new project is created.</span></span>

1. <span data-ttu-id="556fc-143">**Çözüm Gezgini**' de, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklatın, **Yeniden Adlandır**' ı seçin ve dosyayı SınıfAdı SınıfAdı *' dan* *isampelınterface*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="556fc-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="556fc-144">Ayrıca sınıfını olarak yeniden adlandırmak için istemine **Evet** yanıtı verin `ISampleInterface` .</span><span class="sxs-lookup"><span data-stu-id="556fc-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="556fc-145">Bu sınıf, sınıfının genel arabirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="556fc-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="556fc-146">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="556fc-147">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve **Çıkış yolunu** bilgisayarınızdaki bir konuma (örneğin, *C:\TypeEquivalenceSample*) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="556fc-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="556fc-148">Bu izlenecek yol boyunca aynı konumu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="556fc-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="556fc-149">**Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="556fc-150">**Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="556fc-151">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="556fc-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="556fc-152">**Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="556fc-153">Kod düzenleyicisinde *ısamptaınterface* sınıf dosyasını açın ve aşağıdaki kodla içeriğini değiştirerek `ISampleInterface` arabirimi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="556fc-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="556fc-154">**Araçlar** menüsünde **GUID oluştur**' u seçin ve **Guid oluştur** iletişim kutusunda **kayıt defteri biçimi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="556fc-155">**Kopyala**' yı seçin ve ardından **Çıkış**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="556fc-156">`Guid`Kodunuzun özniteliğinde, örnek GUID 'yi KOPYALADıĞıNıZ GUID ile değiştirin ve ayraçları (**{}**) kaldırın.</span><span class="sxs-lookup"><span data-stu-id="556fc-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="556fc-157">**Çözüm Gezgini**, **Özellikler** klasörünü genişletin ve *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="556fc-158">Kod Düzenleyicisi 'nde, dosyaya aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="556fc-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="556fc-159">**Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="556fc-160">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="556fc-161">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen derleme çıkış yoluna kaydedilir, örneğin *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="556fc-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="556fc-162">Çalışma zamanı sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="556fc-162">Create a runtime class</span></span>

<span data-ttu-id="556fc-163">Sonra, tür eşdeğerlik çalışma zamanı sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="556fc-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="556fc-164">Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="556fc-165">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="556fc-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="556fc-166">Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="556fc-167">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceRuntime*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="556fc-168">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="556fc-168">The new project is created.</span></span>

1. <span data-ttu-id="556fc-169">**Çözüm Gezgini**, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklayın, **Yeniden Adlandır**' ı seçin ve dosyayı *SınıfAdı SınıfAdı* *' dan* SampleClass olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="556fc-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="556fc-170">Ayrıca sınıfını olarak yeniden adlandırmak için istemine **Evet** yanıtı verin `SampleClass` .</span><span class="sxs-lookup"><span data-stu-id="556fc-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="556fc-171">Bu sınıf, `ISampleInterface` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="556fc-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="556fc-172">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="556fc-173">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="556fc-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="556fc-174">**Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="556fc-175">**Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="556fc-176">**Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="556fc-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="556fc-177">**Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="556fc-178">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve başvuru **Ekle**' yi seçin  >  **Reference**.</span><span class="sxs-lookup"><span data-stu-id="556fc-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="556fc-179">**Başvuru Yöneticisi** iletişim kutusunda, **Araştır** ' ı seçin ve çıkış yolu klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="556fc-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="556fc-180">*TypeEquivalenceInterface. dll* dosyasını seçin, **Ekle**' yi seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="556fc-181">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="556fc-182">**Özellikler** bölmesinde, **belirli bir sürümü** henüz yoksa **yanlış** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="556fc-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="556fc-183">Kod düzenleyicisinde *SampleClass* sınıf dosyasını açın ve sınıfını oluşturmak için içeriğini aşağıdaki kodla değiştirin `SampleClass` :</span><span class="sxs-lookup"><span data-stu-id="556fc-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
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

1. <span data-ttu-id="556fc-184">**Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="556fc-185">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="556fc-186">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="556fc-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="556fc-187">İstemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="556fc-187">Create a client project</span></span>

<span data-ttu-id="556fc-188">Son olarak, arabirim derlemesine başvuran bir tür denklik istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="556fc-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="556fc-189">Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="556fc-190">**Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *konsol* yazın.</span><span class="sxs-lookup"><span data-stu-id="556fc-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="556fc-191">Listeden C# veya Visual Basic **konsol uygulaması (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="556fc-192">**Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceClient*yazın ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="556fc-193">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="556fc-193">The new project is created.</span></span>

1. <span data-ttu-id="556fc-194">**Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="556fc-195">**Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="556fc-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="556fc-196">**Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve başvuru **Ekle**' yi seçin  >  **Reference**.</span><span class="sxs-lookup"><span data-stu-id="556fc-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="556fc-197">**Başvuru Yöneticisi** iletişim kutusunda, **TypeEquivalenceInterface. dll** dosyası zaten listeleniyorsa, onu seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="556fc-198">Aksi takdirde, **Araştır**' ı seçin, çıkış yolu klasörüne gidin, *TypeEquivalenceInterface. dll* dosyasını ( *TypeEquivalenceRuntime. dll*değil) seçin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="556fc-199">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-199">Select **OK**.</span></span>

1. <span data-ttu-id="556fc-200">**Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="556fc-201">**Özellikler** bölmesinde, **birlikte çalışma türlerini katıştır** ' ı **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="556fc-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="556fc-202">Kod düzenleyicisinde *program.cs* veya *Module1. vb* dosyasını açın ve istemci programını oluşturmak için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="556fc-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. <span data-ttu-id="556fc-203">**Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="556fc-204">**Ctrl** + Programı derlemek ve çalıştırmak için CTRL**F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="556fc-205">Konsol çıkışının **1.0.0.0**derleme sürümünü döndürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="556fc-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="556fc-206">Arabirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="556fc-206">Modify the interface</span></span>

<span data-ttu-id="556fc-207">Şimdi, arabirim derlemesini değiştirin ve sürümünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="556fc-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="556fc-208">Visual Studio 'da **Dosya**  >  **Aç**  >  **Proje/çözüm**' ü seçin ve **TypeEquivalenceInterface** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="556fc-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="556fc-209">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="556fc-210">**Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="556fc-211">**Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="556fc-212">*SampleInterface.cs* veya *sampleınterface. vb* dosyasını açın ve aşağıdaki kod satırını `ISampleInterface` arabirime ekleyin:</span><span class="sxs-lookup"><span data-stu-id="556fc-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="556fc-213">**Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="556fc-214">**Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="556fc-215">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="556fc-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="556fc-216">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="556fc-216">Modify the runtime class</span></span>

<span data-ttu-id="556fc-217">Ayrıca çalışma zamanı sınıfını değiştirin ve sürümünü güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="556fc-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="556fc-218">Visual Studio 'da **Dosya**  >  **Aç**  >  **Proje/çözüm**' ü seçin ve **TypeEquivalenceRuntime** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="556fc-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="556fc-219">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="556fc-220">**Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="556fc-221">**Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="556fc-222">*SampleClass.cs* veya *SampleClass. vb* dosyasını açın ve sınıfına aşağıdaki kodu ekleyin `SampleClass` :</span><span class="sxs-lookup"><span data-stu-id="556fc-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="556fc-223">**Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.</span><span class="sxs-lookup"><span data-stu-id="556fc-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="556fc-224">**Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="556fc-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="556fc-225">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="556fc-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="556fc-226">Güncelleştirilmiş istemci programını çalıştır</span><span class="sxs-lookup"><span data-stu-id="556fc-226">Run the updated client program</span></span>

<span data-ttu-id="556fc-227">Yapı çıkış klasörü konumuna gidin ve *TypeEquivalenceClient. exe*' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="556fc-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="556fc-228">Konsol çıkışının artık, 2.0.0.0 derlemesinin yeni sürümünü, yeniden `TypeEquivalenceRuntime` Derlenmekte olan program *2.0.0.0*olmadan yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="556fc-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="556fc-229">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="556fc-229">See also</span></span>

- [<span data-ttu-id="556fc-230">-Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="556fc-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="556fc-231">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="556fc-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="556fc-232">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="556fc-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="556fc-233">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="556fc-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="556fc-234">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="556fc-234">Assemblies in .NET</span></span>](index.md)
