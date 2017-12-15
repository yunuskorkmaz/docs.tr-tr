---
title: "İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b07b940d6287de0caf41c7d15f3036ad4041ad0
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="dccd1-102">İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="dccd1-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="dccd1-103">Tanımlayıcı adlı Yönetilen derleme tür bilgilerini katıştırma, geniş sürüm bağımsızlığı elde etmek için bir uygulamada türü eşleştiği.</span><span class="sxs-lookup"><span data-stu-id="dccd1-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="dccd1-104">Diğer bir deyişle, her sürüm için derlenmesi gerek kalmadan yönetilen kitaplık birden fazla sürümünü türlerinden kullanmak için program yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="dccd1-105">Türü katıştırma Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dccd1-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="dccd1-106">Tür bilgilerini katıştırma Microsoft Office'in farklı sürümlerinde farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dccd1-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="dccd1-107">Ancak, tam olarak yönetilen bir çözüm katıştırma türü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dccd1-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="dccd1-108">Aşağıdaki özelliklere sahip bir derlemeden tür bilgileri katıştırılabilen:</span><span class="sxs-lookup"><span data-stu-id="dccd1-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="dccd1-109">Derleme en az bir ortak arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="dccd1-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="dccd1-110">Katıştırılmış arabirimleri ile Açıklama eklenen bir `ComImport` özniteliğini ve bir `Guid` özniteliği (ve benzersiz bir GUID).</span><span class="sxs-lookup"><span data-stu-id="dccd1-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="dccd1-111">Derleme ile Açıklama `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliği ve derleme düzeyi `Guid` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dccd1-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="dccd1-112">(Varsayılan olarak, Visual C# proje şablonları derleme düzeyi dahil `Guid` özniteliği.)</span><span class="sxs-lookup"><span data-stu-id="dccd1-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="dccd1-113">Katıştırılabilen genel arabirimler belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dccd1-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="dccd1-114">Bir istemci programı daha sonra bu arabirimleri tasarım zamanında tür bilgileri ayarı ve ortak arabirimleri içeren derlemenin başvurarak eklenebilir `Embed Interop Types` referansı özelliğinin `True`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="dccd1-115">Bu komut satırı derleyicisini kullanarak ve kullanarak bütünleştirilmiş başvurma eşdeğerdir `/link` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dccd1-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="dccd1-116">İstemci programı daha sonra bu arabirimleri olarak belirtilmiş, çalışma zamanı nesnelerinin örneklerini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="dccd1-117">Tanımlayıcı adlı çalışma zamanı derlemesi yeni bir sürümünü oluşturursanız, istemci programı ile güncelleştirilmiş çalışma zamanı derlemesi derlenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dccd1-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="dccd1-118">Bunun yerine, istemcinin hangi sürümü çalışma zamanı derlemesi için ortak arabirimleri katıştırılmış tür bilgileri kullanarak, kullanılabilir kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="dccd1-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="dccd1-119">COM birlikte çalışma derlemeleri türü bilgilerin destekliyoruz türü katıştırma birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="dccd1-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="dccd1-120">Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="dccd1-121">Genel parametreler bir türünü kullanır ve katıştırılmış türünün genel parametresi türü ise, bu tür bir derleme sınırından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dccd1-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="dccd1-122">Başka bir derlemeye ait bir yöntemi çağırma bir derleme sınırını geçmesinden örnekleri dahil edin veya başka bir derlemede tanımlanan bir türü türetme bir türü.</span><span class="sxs-lookup"><span data-stu-id="dccd1-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="dccd1-123">Sabitler katıştırılmış değil.</span><span class="sxs-lookup"><span data-stu-id="dccd1-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="dccd1-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıf anahtarı olarak katıştırılmış bir türü desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="dccd1-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="dccd1-125">Katıştırılmış bir tür bir anahtar olarak desteklemek için kendi Sözlük türü uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dccd1-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="dccd1-126">Bu kılavuzda, aşağıdakileri:</span><span class="sxs-lookup"><span data-stu-id="dccd1-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="dccd1-127">Katıştırılabilen tür bilgileri içeren ortak bir arabirim tanımlayıcı adlı bir derleme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dccd1-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="dccd1-128">Ortak arabirimi uygulayan bir tanımlayıcı adlı çalışma zamanı derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dccd1-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="dccd1-129">Ortak arabirimi tür bilgilerini katıştırır ve çalışma zamanı derlemesinden sınıfının bir örneği oluşturan bir istemci program oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dccd1-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="dccd1-130">Değiştirme ve çalışma zamanı derlemesi derleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="dccd1-131">Çalışma zamanı derlemesi yeni sürümünü istemci programı yeniden derlemenize gerek kalmadan kullanıldığını görmek için istemci programını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="dccd1-132">Bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="dccd1-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="dccd1-133">Tür denkliği arabirimi projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dccd1-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="dccd1-134">Visual Studio'da üzerinde **dosya** menüsünde seçin **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="dccd1-135">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="dccd1-136">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="dccd1-137">İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="dccd1-138">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dccd1-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="dccd1-139">İçinde **Çözüm Gezgini**, Class1.cs dosyası sağ tıklatın ve **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="dccd1-140">Dosyayı Yeniden Adlandır `ISampleInterface.cs` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="dccd1-141">Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="dccd1-142">Bu sınıf, sınıf için ortak arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dccd1-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="dccd1-143">TypeEquivalenceInterface projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="dccd1-144">Tıklatın **yapı** sekmesi. Çıkış yolu geliştirme bilgisayarınızda geçerli bir konuma ayarlı `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="dccd1-145">Bu konum, bu kılavuzda bir sonraki adımda de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dccd1-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="dccd1-146">Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dccd1-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="dccd1-147">İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="dccd1-148">İçinde **anahtar dosya adını** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="dccd1-149">Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="dccd1-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="dccd1-150">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="dccd1-151">ISampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="dccd1-152">ISampleInterface arabirimi oluşturmak üzere ISampleInterface sınıfı dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="dccd1-153">Üzerinde **Araçları** menüsünde tıklatın **Create GUID**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="dccd1-154">İçinde **Create GUID** iletişim kutusu, tıklatın **kayıt defteri biçimi** ve ardından **kopya**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="dccd1-155">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="dccd1-156">İçinde `Guid` özniteliği, örnek GUID silme ve kopyalama GUID yapıştırın **Create GUID** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="dccd1-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="dccd1-157">Kaşlı ayraçlar adresinden kopyalanan GUID kaldırın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="dccd1-158">İçinde **Çözüm Gezgini**, genişletin **özellikleri** klasör.</span><span class="sxs-lookup"><span data-stu-id="dccd1-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="dccd1-159">AssemblyInfo.cs dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="dccd1-160">Aşağıdaki öznitelik dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="dccd1-161">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-161">Save the file.</span></span>  
  
10. <span data-ttu-id="dccd1-162">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-162">Save the project.</span></span>  
  
11. <span data-ttu-id="dccd1-163">TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="dccd1-164">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="dccd1-165">Bir çalışma zamanı sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="dccd1-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="dccd1-166">Tür denkliği çalışma zamanı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dccd1-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="dccd1-167">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="dccd1-168">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="dccd1-169">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="dccd1-170">İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="dccd1-171">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dccd1-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="dccd1-172">İçinde **Çözüm Gezgini**, Class1.cs dosyası sağ tıklatın ve **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="dccd1-173">Dosyayı Yeniden Adlandır `SampleClass.cs` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="dccd1-174">Dosyayı yeniden adlandırmak de yeniden adlandırır sınıfına `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="dccd1-175">Bu sınıf gerçekleştireceksiniz `ISampleInterface` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="dccd1-176">TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="dccd1-177">Tıklatın **yapı** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="dccd1-178">Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dccd1-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="dccd1-179">İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="dccd1-180">İçinde **anahtar dosya adını** kutusuna `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="dccd1-181">Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="dccd1-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="dccd1-182">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="dccd1-183">TypeEquivalenceRuntime projeyi sağ tıklatın ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="dccd1-184">Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="dccd1-185">TypeEquivalenceInterface.dll dosyasını tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="dccd1-186">İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="dccd1-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="dccd1-187">TypeEquivalenceInterface referans'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="dccd1-188">TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **belirli bir sürüm** özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="dccd1-189">SampleClass sınıfı oluşturmak için SampleClass sınıfı dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
  
9. <span data-ttu-id="dccd1-190">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-190">Save the project.</span></span>  
  
10. <span data-ttu-id="dccd1-191">TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="dccd1-192">Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="dccd1-193">Bir istemci projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dccd1-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="dccd1-194">Tür denkliği istemci projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dccd1-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="dccd1-195">Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="dccd1-196">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="dccd1-197">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="dccd1-198">İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="dccd1-199">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dccd1-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="dccd1-200">TypeEquivalenceClient projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="dccd1-201">Tıklatın **yapı** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="dccd1-202">TypeEquivalenceClient projeyi sağ tıklatın ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="dccd1-203">Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="dccd1-204">TypeEquivalenceInterface.dll dosyasını (TypeEquivalenceRuntime.dll değil) tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="dccd1-205">İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör.</span><span class="sxs-lookup"><span data-stu-id="dccd1-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="dccd1-206">TypeEquivalenceInterface referans'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="dccd1-207">TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="dccd1-208">İstemci programı oluşturmak için Program.cs dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
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
  
7.  <span data-ttu-id="dccd1-209">Derleme ve programı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="dccd1-210">Arabirim değiştirme</span><span class="sxs-lookup"><span data-stu-id="dccd1-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="dccd1-211">Arabirim değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="dccd1-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="dccd1-212">Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="dccd1-213">İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projesine sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="dccd1-214">Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="dccd1-215">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="dccd1-216">SampleInterface.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="dccd1-217">Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="dccd1-218">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="dccd1-219">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="dccd1-220">TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="dccd1-221">Yeni bir sınıf kitaplığı .dll dosyasının sürümünü derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="dccd1-222">Çalışma zamanı sınıfını değiştirme</span><span class="sxs-lookup"><span data-stu-id="dccd1-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="dccd1-223">Çalışma zamanı sınıf değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="dccd1-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="dccd1-224">Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="dccd1-225">İçinde **Proje Aç** iletişim kutusunda, TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="dccd1-226">Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dccd1-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="dccd1-227">Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="dccd1-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="dccd1-228">SampleClass.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="dccd1-229">Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="dccd1-230">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="dccd1-231">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dccd1-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="dccd1-232">TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**.</span><span class="sxs-lookup"><span data-stu-id="dccd1-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="dccd1-233">Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dccd1-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="dccd1-234">Dosya Gezgini'nde, çıkış yolunu klasörünü (örneğin, C:\TypeEquivalenceSample) açın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="dccd1-235">Programı çalıştırmak için TypeEquivalenceClient.exe çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dccd1-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="dccd1-236">Program, yeniden derlenmesi olmadan TypeEquivalenceRuntime derlemesinin yeni sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="dccd1-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccd1-237">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dccd1-237">See Also</span></span>  
 [<span data-ttu-id="dccd1-238">/ Link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="dccd1-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="dccd1-239">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dccd1-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dccd1-240">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="dccd1-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="dccd1-241">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="dccd1-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
