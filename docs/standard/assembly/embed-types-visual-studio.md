---
title: "İzim: Visual Studio'da yönetilen derlemelerden türleri gömme"
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338553"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="361b5-102">İzim: Visual Studio'da yönetilen derlemelerden türleri gömme</span><span class="sxs-lookup"><span data-stu-id="361b5-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="361b5-103">Güçlü adlandırılmış yönetilen bir derlemeden tür bilgilerini katıştırmak, sürüm bağımsızlığı elde etmek için bir uygulamada gevşek çift türleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="361b5-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="361b5-104">Diğer bir diğer olarak, programınız, her yeni sürüm için yeniden derlenmek zorunda kalmadan yönetilen kitaplığın herhangi bir sürümünden türleri kullanmak üzere yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="361b5-105">Tür katıştırma, Microsoft Office'in otomasyon nesnelerini kullanan bir uygulama gibi COM interop'uyla sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="361b5-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="361b5-106">Tür bilgilerini katıştırma, bir programın aynı yapısının farklı bilgisayarlarda Microsoft Office'in farklı sürümleriyle çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="361b5-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="361b5-107">Ancak, tam olarak yönetilen çözümlerle tür katıştırma da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="361b5-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="361b5-108">Katıştırılmış ortak arabirimleri belirttikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="361b5-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="361b5-109">İstemci programı, ortak arabirimleri içeren derlemeye başvurarak ve başvurunun özelliğini `Embed Interop Types` ayarlayarak, arabirimlerin tür `True`bilgilerini tasarım zamanında katıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="361b5-110">İstemci programı daha sonra bu arabirimler olarak yazılan çalışma zamanı nesnelerinin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="361b5-111">Bu komut satırı derleyicisi kullanarak ve [-link derleyici seçeneği](../../csharp/language-reference/compiler-options/link-compiler-option.md)kullanarak derleme başvuru eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="361b5-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="361b5-112">Güçlü adlandırılmış çalışma zamanı derlemenizin yeni bir sürümünü oluşturursanız, istemci programının yeniden derlenmesine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="361b5-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="361b5-113">İstemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak, çalışma zamanı derlemesinin hangi sürümünü kullanabilirse kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="361b5-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="361b5-114">Bu gözden geçirmede, siz:</span><span class="sxs-lookup"><span data-stu-id="361b5-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="361b5-115">Katıştırılmış tür bilgilerini içeren ortak arabirimiçeren güçlü adlandırılmış bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="361b5-116">Ortak arabirimi uygulayan güçlü adlandırılmış bir çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="361b5-117">Ortak arabirimden tür bilgilerini gömen ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturan bir istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="361b5-118">Çalışma zamanı montajını değiştirin ve yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="361b5-119">Yeniden derlenmek zorunda kalmadan çalışma zamanı derlemesinin yeni sürümünü kullandığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="361b5-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="361b5-120">Koşullar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="361b5-120">Conditions and limitations</span></span>

<span data-ttu-id="361b5-121">Bir derlemeden tür bilgilerini aşağıdaki koşullar altında katıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="361b5-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="361b5-122">Derleme, en az bir ortak arabirimi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="361b5-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="361b5-123">Katıştılı arabirimler, benzersiz `ComImport` GUID'lere sahip öznitelikler ve `Guid` özniteliklerle açıklamalı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="361b5-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="361b5-124">Derleme öznitelik veya `ImportedFromTypeLib` `PrimaryInteropAssembly` öznitelik ve derleme düzeyinde `Guid` öznitelik ile açıklamalı.</span><span class="sxs-lookup"><span data-stu-id="361b5-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="361b5-125">Visual C# ve Visual Basic proje şablonları `Guid` varsayılan olarak montaj düzeyinde bir öznitelik içerir.</span><span class="sxs-lookup"><span data-stu-id="361b5-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="361b5-126">Tür katıştırma birincil işlevi COM interop derlemeleri desteklemek olduğundan, tam yönetilen bir çözüme tür bilgilerini katıştırdığınızda aşağıdaki sınırlamalar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="361b5-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="361b5-127">Yalnızca COM interop'a özgü öznitelikler gömülür.</span><span class="sxs-lookup"><span data-stu-id="361b5-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="361b5-128">Diğer öznitelikler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="361b5-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="361b5-129">Bir tür genel parametreler kullanıyorsa ve genel parametre türü katıştırılmış bir türse, bu tür derleme sınırı boyunca kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="361b5-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="361b5-130">Derleme sınırını aşmaya örnek olarak yöntem başka bir derlemeden çağrı veya başka bir derlemede tanımlanan bir türden tür elde etmek verilebilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="361b5-131">Sabitler gömülü değildir.</span><span class="sxs-lookup"><span data-stu-id="361b5-131">Constants are not embedded.</span></span>
- <span data-ttu-id="361b5-132">Sınıf, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> anahtar olarak katışılmış bir türü desteklemez.</span><span class="sxs-lookup"><span data-stu-id="361b5-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="361b5-133">Katıştırılmış bir türü anahtar olarak desteklemek için kendi sözlük türünüzü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="361b5-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="361b5-134">Arayüz oluşturma</span><span class="sxs-lookup"><span data-stu-id="361b5-134">Create an interface</span></span>

<span data-ttu-id="361b5-135">İlk adım türü eşdeğerlik arabirim derlemeoluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="361b5-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="361b5-136">Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="361b5-137">Yeni **proje** iletişim kutusu oluştur kutusunda, **şablonları ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="361b5-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="361b5-138">Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="361b5-139">Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı**altında , *TypeEquivalenceInterface*yazın ve ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="361b5-140">Yeni proje oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="361b5-140">The new project is created.</span></span>

1. <span data-ttu-id="361b5-141">**Solution Explorer'da** *Class1.cs* veya *Class1.vb* dosyasına sağ tıklayın, **Yeniden Adlandır'ı**seçin ve dosyayı *Class1'den* *ISampleInterface'e*yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="361b5-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="361b5-142">Sınıfı yeniden adlandırmak için istem `ISampleInterface`için **Evet'i** yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="361b5-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="361b5-143">Bu sınıf, sınıfın ortak arabirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="361b5-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="361b5-144">**Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="361b5-145">**Özellikler** ekranının sol bölmesine **Yap'ı** seçin ve **Çıktı yolunu** *bilgisayarınızdaki C:\TypeEquivalenceSample*gibi bir konuma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="361b5-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="361b5-146">Bu yol boyunca aynı konumu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="361b5-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="361b5-147">**Özellikler** ekranının sol bölmesine **İmzala'yı** seçin ve ardından montaj onay kutusunu **imzala'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="361b5-148">**Güçlü bir ad tuşu dosyası seç**için açılan açılır durumda Yeni'yi seçin. **New**</span><span class="sxs-lookup"><span data-stu-id="361b5-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="361b5-149">Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda, **Anahtar dosya adı**altında , *key.snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="361b5-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="361b5-150">Parola onay **kutusuyla anahtar dosyamı koruyun'un** select'ini seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="361b5-151">Kod düzenleyicisinde *ISampleInterface* sınıf dosyasını açın ve arabirimi oluşturmak `ISampleInterface` için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="361b5-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="361b5-152">**Araçlar** menüsünde **Guid Oluştur'u**ve **GUID Oluştur** iletişim kutusunda Kayıt **Defteri Biçimi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="361b5-153">**Kopyala'yı**seçin ve ardından **Çıkış'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="361b5-154">Kodunuzu `Guid` öznitelik olarak, örnek GUID'i kopyaladiğiniz GUID ile değiştirin ve ayraçları kaldırın (**{ }**).</span><span class="sxs-lookup"><span data-stu-id="361b5-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="361b5-155">**Solution Explorer'da** **Özellikler** klasörünü genişletin ve *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="361b5-156">Kod düzenleyicisinde, dosyaya aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="361b5-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="361b5-157">**Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="361b5-158">**Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="361b5-159">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıktı yoluna kaydedilir, örneğin *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="361b5-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="361b5-160">Çalışma zamanı sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="361b5-160">Create a runtime class</span></span>

<span data-ttu-id="361b5-161">Ardından, tür eşdeğerliği çalışma zamanı sınıfını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="361b5-162">Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="361b5-163">Yeni **proje** iletişim kutusu oluştur kutusunda, **şablonları ara** kutusuna *sınıf kitaplığı* yazın.</span><span class="sxs-lookup"><span data-stu-id="361b5-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="361b5-164">Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="361b5-165">Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı**altında , *TypeEquivalenceRuntime*yazın ve ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="361b5-166">Yeni proje oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="361b5-166">The new project is created.</span></span>

1. <span data-ttu-id="361b5-167">**Çözüm Gezgini'nde,** *Class1.cs* veya *Class1.vb* dosyasına sağ tıklayın, **Yeniden Adlandır'ı**seçin ve dosyayı *Class1'den* *SampleClass'a*yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="361b5-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="361b5-168">Sınıfı yeniden adlandırmak için istem `SampleClass`için **Evet'i** yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="361b5-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="361b5-169">Bu sınıf `ISampleInterface` arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="361b5-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="361b5-170">**Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Özellikleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="361b5-171">**Özellikler** ekranının sol bölmesine **Yapı'yı** seçin ve çıktı **yolunu** TypeEquivalenceInterface projesi için kullandığınız konuma ayarlayın, örneğin *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="361b5-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="361b5-172">**Özellikler** ekranının sol bölmesine **İmzala'yı** seçin ve ardından montaj onay kutusunu **imzala'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="361b5-173">**Güçlü bir ad tuşu dosyası seç**için açılan açılır durumda Yeni'yi seçin. **New**</span><span class="sxs-lookup"><span data-stu-id="361b5-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="361b5-174">Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda, **Anahtar dosya adı**altında , *key.snk*yazın.</span><span class="sxs-lookup"><span data-stu-id="361b5-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="361b5-175">Parola onay **kutusuyla anahtar dosyamı koruyun'un** select'ini seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="361b5-176">**Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesine sağ tıklayın ve**Referans** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="361b5-177">Başvuru **Yöneticisi** iletişim kutusunda **Gözat'ı** seçin ve çıktı yolu klasörüne göz atın.</span><span class="sxs-lookup"><span data-stu-id="361b5-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="361b5-178">*TypeEquivalenceInterface.dll* dosyasını seçin, **Ekle'yi**seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="361b5-179">**Solution**Explorer'da, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurualanını seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="361b5-180">**Özellikler** bölmesinde, zaten değilse **Belirli Sürümü** **False** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="361b5-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="361b5-181">Kod düzenleyicisinde *SampleClass* sınıf dosyasını açın ve sınıfı oluşturmak için `SampleClass` içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="361b5-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="361b5-182">**Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="361b5-183">**Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Build'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="361b5-184">Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıktı yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="361b5-185">İstemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="361b5-185">Create a client project</span></span>

<span data-ttu-id="361b5-186">Son olarak, arabirim derlemesine başvuran bir tür eşdeğerlik istemci programı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="361b5-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="361b5-187">Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="361b5-188">Yeni **bir proje** oluştur iletişim kutusunda **şablonara** kutusuna *konsol* yazın.</span><span class="sxs-lookup"><span data-stu-id="361b5-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="361b5-189">Listeden C# veya Visual Basic **Console App (.NET Framework)** şablonundan birini seçin ve ardından **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="361b5-190">Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı altında**, *TypeEquivalenceClient*yazın ve ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="361b5-191">Yeni proje oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="361b5-191">The new project is created.</span></span>

1. <span data-ttu-id="361b5-192">**Çözüm Gezgini'nde** **TypeEquivalenceClient** projesini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="361b5-193">**Özellikler** ekranının sol bölmesine **Yapı'yı** seçin ve çıktı **yolunu** TypeEquivalenceInterface projesi için kullandığınız konuma ayarlayın, örneğin *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="361b5-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="361b5-194">**Çözüm Gezgini'nde** **TypeEquivalenceClient** projesine sağ tıklayın ve**Referans** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="361b5-195">Başvuru **Yöneticisi** iletişim kutusunda, **TypeEquivalenceInterface.dll** dosyası zaten listelenmişse, bu dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="361b5-196">Değilse, **Gözat**seçin , çıkış yolu klasörüne göz atın, *TypeEquivalenceInterface.dll* dosyasını seçin *(TypeEquivalenceRuntime.dll*değil), ve **Ekle**seçin .</span><span class="sxs-lookup"><span data-stu-id="361b5-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="361b5-197">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-197">Select **OK**.</span></span>

1. <span data-ttu-id="361b5-198">**Solution**Explorer'da, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurualanını seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="361b5-199">**Özellikler** bölmesinde, **Embed Interop Türlerini** **True**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="361b5-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="361b5-200">Kod düzenleyicisindeki *Program.cs* veya *Module1.vb* dosyasını açın ve istemci programını oluşturmak için içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="361b5-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

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

1. <span data-ttu-id="361b5-201">**Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="361b5-202">Programı oluşturmak ve çalıştırmak için **Ctrl**+**F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="361b5-203">Konsol çıkışının montaj sürümünü **1.0.0.0**döndürür.</span><span class="sxs-lookup"><span data-stu-id="361b5-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="361b5-204">Arabirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="361b5-204">Modify the interface</span></span>

<span data-ttu-id="361b5-205">Şimdi, arabirim montajını değiştirin ve sürümünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="361b5-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="361b5-206">Visual Studio'da **Dosya** > **Açık** > **Projesi/Çözümü'nü**seçin ve **TypeEquivalenceInterface** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="361b5-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="361b5-207">**Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Özellikleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="361b5-208">**Özellikler** ekranının sol bölmesine **Uygulama'yı** seçin ve ardından **Derleme Bilgileri'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="361b5-209">Derleme **Bilgileri** iletişim kutusunda, **Derleme sürümü** ve Dosya **sürüm** değerlerini *2.0.0.0*olarak değiştirin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="361b5-210">*SampleInterface.cs* veya *SampleInterface.vb* dosyasını açın ve arabirime `ISampleInterface` aşağıdaki kod satırını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="361b5-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="361b5-211">**Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="361b5-212">**Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="361b5-213">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve yapı çıktı yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="361b5-214">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="361b5-214">Modify the runtime class</span></span>

<span data-ttu-id="361b5-215">Ayrıca çalışma zamanı sınıfını değiştirin ve sürümünü güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="361b5-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="361b5-216">Visual Studio'da **Dosya** > **Açık** > **Projesi/Çözümü'nü**seçin ve **TypeEquivalenceRuntime** projesini açın.</span><span class="sxs-lookup"><span data-stu-id="361b5-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="361b5-217">**Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Özellikleri**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="361b5-218">**Özellikler** ekranının sol bölmesine **Uygulama'yı** seçin ve ardından **Derleme Bilgileri'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="361b5-219">Derleme **Bilgileri** iletişim kutusunda, **Derleme sürümü** ve Dosya **sürüm** değerlerini *2.0.0.0*olarak değiştirin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="361b5-220">*SampleClass.cs* veya *SampleClass.vb* dosyasını `SampleClass` açın ve sınıfa aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="361b5-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="361b5-221">**Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="361b5-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="361b5-222">**Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Build'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="361b5-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="361b5-223">Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve yapı çıktı yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="361b5-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="361b5-224">Güncelleştirilmiş istemci programını çalıştırın</span><span class="sxs-lookup"><span data-stu-id="361b5-224">Run the updated client program</span></span>

<span data-ttu-id="361b5-225">Yapı çıktı klasörü konumuna gidin ve *TypeEquivalenceClient.exe'yi*çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="361b5-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="361b5-226">Konsol çıkışının artık `TypeEquivalenceRuntime` derlemenin yeni sürümünü yansıttığını unutmayın, *2.0.0.0*, program yeniden derlenmeden.</span><span class="sxs-lookup"><span data-stu-id="361b5-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="361b5-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="361b5-227">See also</span></span>

- [<span data-ttu-id="361b5-228">-link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="361b5-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="361b5-229">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="361b5-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="361b5-230">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="361b5-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="361b5-231">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="361b5-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="361b5-232">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="361b5-232">Assemblies in .NET</span></span>](index.md)
