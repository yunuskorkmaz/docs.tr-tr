---
title: 'İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)'
description: Bu kılavuzda dinamik nesneler oluşturma ve kullanma hakkında bilgi edinin. Özel bir dinamik nesne ve ' IronPython ' kitaplığı kullanan bir proje oluşturun.
ms.date: 03/24/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.openlocfilehash: 3b342f23a2974affdcd7a1e91093aaef504afb63
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111029"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="2417f-104">İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2417f-104">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="2417f-105">Dinamik nesneler, derleme zamanında değil, çalışma zamanında Özellikler ve yöntemler gibi üyeleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2417f-105">Dynamic objects expose members such as properties and methods at run time, instead of at compile time.</span></span> <span data-ttu-id="2417f-106">Bu, statik bir tür veya biçimle eşleşmeyen yapılarla çalışacak nesneler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2417f-106">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="2417f-107">Örneğin, geçerli HTML biçimlendirme öğelerinin ve özniteliklerin herhangi bir birleşimini içerebilen HTML Belge Nesne Modeli (DOM) başvurmak için dinamik bir nesne kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-107">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="2417f-108">Her HTML belgesi benzersiz olduğundan, belirli bir HTML belgesi üyeleri çalışma zamanında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2417f-108">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="2417f-109">Bir HTML öğesinin özniteliğine başvurmak için ortak bir yöntem özniteliğin adını `GetProperty` öğesi yöntemine geçirmektir.</span><span class="sxs-lookup"><span data-stu-id="2417f-109">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="2417f-110">`id`HTML öğesinin özniteliğine başvurmak için `<div id="Div1">` , önce öğesine bir başvuru alın `<div>` ve ardından öğesini kullanın `divElement.GetProperty("id")` .</span><span class="sxs-lookup"><span data-stu-id="2417f-110">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="2417f-111">Dinamik bir nesne kullanıyorsanız, `id` özniteliğe olarak başvurabilirsiniz `divElement.id` .</span><span class="sxs-lookup"><span data-stu-id="2417f-111">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>

 <span data-ttu-id="2417f-112">Dinamik nesneler IronPython ve IronRuby gibi dinamik dillere de kolay erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2417f-112">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="2417f-113">Çalışma zamanında yorumlanan dinamik bir betiğe başvurmak için dinamik bir nesne kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-113">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>

 <span data-ttu-id="2417f-114">Geç bağlamayı kullanarak dinamik bir nesneye başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-114">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="2417f-115">C# ' de, bir geç bağlantılı nesnenin türünü olarak belirtirsiniz `dynamic` .</span><span class="sxs-lookup"><span data-stu-id="2417f-115">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="2417f-116">Visual Basic, bir geç bağlantılı nesnenin türünü olarak belirtirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="2417f-116">In Visual Basic, you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="2417f-117">Daha fazla bilgi için bkz. [dinamik](../../language-reference/builtin-types/reference-types.md) ve [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span><span class="sxs-lookup"><span data-stu-id="2417f-117">For more information, see [dynamic](../../language-reference/builtin-types/reference-types.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>

 <span data-ttu-id="2417f-118">Ad alanındaki sınıfları kullanarak özel dinamik nesneler oluşturabilirsiniz <xref:System.Dynamic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2417f-118">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2417f-119">Örneğin, bir oluşturup <xref:System.Dynamic.ExpandoObject> çalışma zamanında o nesnenin üyelerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-119">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="2417f-120">Ayrıca, sınıfını devralan kendi türünü de oluşturabilirsiniz <xref:System.Dynamic.DynamicObject> .</span><span class="sxs-lookup"><span data-stu-id="2417f-120">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="2417f-121">Daha sonra <xref:System.Dynamic.DynamicObject> çalışma zamanı dinamik işlevselliği sağlamak için sınıfın üyelerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-121">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>

 <span data-ttu-id="2417f-122">Bu makale iki bağımsız izlenecek yol içerir:</span><span class="sxs-lookup"><span data-stu-id="2417f-122">This article contains two independent walkthroughs:</span></span>

- <span data-ttu-id="2417f-123">Bir metin dosyasının içeriğini dinamik olarak bir nesnenin özellikleri olarak sunan özel bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2417f-123">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>

- <span data-ttu-id="2417f-124">Kitaplığı kullanan bir proje oluşturun `IronPython` .</span><span class="sxs-lookup"><span data-stu-id="2417f-124">Create a project that uses an `IronPython` library.</span></span>

<span data-ttu-id="2417f-125">Bunlardan birini ya da her ikisini de yapabilirsiniz ve her ikisini de yaparsanız, sipariş önemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2417f-125">You can do either one of these or both of them, and if you do both, the order doesn't matter.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2417f-126">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2417f-126">Prerequisites</span></span>

* <span data-ttu-id="2417f-127">[Visual Studio 2019 sürüm 16,9 veya](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) **.net masaüstü geliştirme** iş yükünün yüklü olduğu sonraki bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="2417f-127">[Visual Studio 2019 version 16.9 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span> <span data-ttu-id="2417f-128">.NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2417f-128">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

* <span data-ttu-id="2417f-129">İkinci anlatım için [IronPython](https://ironpython.net/) for .net ' i yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="2417f-129">For the second walkthrough, install [IronPython](https://ironpython.net/) for .NET.</span></span> <span data-ttu-id="2417f-130">En son sürümü edinmek için [indirme sayfasına](https://ironpython.net/download/) gidin.</span><span class="sxs-lookup"><span data-stu-id="2417f-130">Go to their [Download page](https://ironpython.net/download/) to obtain the latest version.</span></span>

## <a name="create-a-custom-dynamic-object"></a><span data-ttu-id="2417f-131">Özel dinamik nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="2417f-131">Create a Custom Dynamic Object</span></span>

<span data-ttu-id="2417f-132">İlk izlenecek yol, bir metin dosyasının içeriğini arayan özel bir dinamik nesne tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2417f-132">The first walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="2417f-133">Dinamik bir özellik aranacak metni belirtir.</span><span class="sxs-lookup"><span data-stu-id="2417f-133">A dynamic property specifies the text to search for.</span></span> <span data-ttu-id="2417f-134">Örneğin, kod çağırma belirtiyorsa `dynamicFile.Sample` dinamik sınıf, dosyadaki "Sample" ile başlayan tüm satırları içeren bir dize genel listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2417f-134">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="2417f-135">Arama büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2417f-135">The search is case-insensitive.</span></span> <span data-ttu-id="2417f-136">Dinamik sınıf Ayrıca iki isteğe bağlı bağımsız değişkeni destekler.</span><span class="sxs-lookup"><span data-stu-id="2417f-136">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="2417f-137">İlk bağımsız değişken, dinamik sınıfın satır başlangıcında, satırın sonunda veya satırdaki herhangi bir yerde eşleşmelerin aranması gerektiğini belirten bir arama seçeneği enum değeridir.</span><span class="sxs-lookup"><span data-stu-id="2417f-137">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="2417f-138">İkinci bağımsız değişken, dinamik sınıfın, aramadan önce her satırdaki baştaki ve sondaki boşlukları kırpmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2417f-138">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="2417f-139">Örneğin, kod çağırma belirtiyorsa `dynamicFile.Sample(StringSearchOption.Contains)` dinamik sınıf, "Sample" öğesini bir satırda herhangi bir yerde arar.</span><span class="sxs-lookup"><span data-stu-id="2417f-139">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="2417f-140">Çağıran kod belirtiyorsa `dynamicFile.Sample(StringSearchOption.StartsWith, false)` , dinamik sınıf her satırın başlangıcında "Sample" arar ve baştaki ve sondaki boşlukları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="2417f-140">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="2417f-141">Dinamik sınıfın varsayılan davranışı, her satırın başlangıcında bir eşleşme aramak ve baştaki ve sondaki boşlukları kaldırmak içindir.</span><span class="sxs-lookup"><span data-stu-id="2417f-141">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="2417f-142">Özel bir dinamik sınıf oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2417f-142">To create a custom dynamic class</span></span>

1. <span data-ttu-id="2417f-143">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2417f-143">Start Visual Studio.</span></span>

1. <span data-ttu-id="2417f-144">**Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-144">Select **Create a new project**.</span></span>

1. <span data-ttu-id="2417f-145">**Yeni proje oluştur** Iletişim kutusunda C# veya Visual Basic ' yi seçin, **konsol uygulaması**' nı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-145">In the **Create a new project** dialog, select C# or Visual Basic, select **Console Application**, and then select **Next**.</span></span>

1. <span data-ttu-id="2417f-146">**Yeni projenizi yapılandırın** Iletişim kutusunda `DynamicSample` **Proje adı**' nı girin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-146">In the **Configure your new project** dialog, enter `DynamicSample` for the **Project name**, and then select **Next**.</span></span>

1. <span data-ttu-id="2417f-147">**Ek bilgi** Iletişim kutusunda **hedef çerçeve** Için **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-147">In the **Additional information** dialog, select **.NET 5.0 (Current)** for the **Target Framework**, and then select **Create**.</span></span>

   <span data-ttu-id="2417f-148">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2417f-148">The new project is created.</span></span>

1. <span data-ttu-id="2417f-149">**Çözüm Gezgini**, DynamicSample projesine sağ tıklayın ve sınıf **Ekle**' yi seçin  >  .</span><span class="sxs-lookup"><span data-stu-id="2417f-149">In **Solution Explorer**, right-click the DynamicSample project and select **Add** > **Class**.</span></span> <span data-ttu-id="2417f-150">**Ad** kutusuna yazın `ReadOnlyFile` ve ardından **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-150">In the **Name** box, type `ReadOnlyFile`, and then select **Add**.</span></span>

   <span data-ttu-id="2417f-151">ReadOnlyFile sınıfını içeren yeni bir dosya eklenir.</span><span class="sxs-lookup"><span data-stu-id="2417f-151">A new file is added that contains the ReadOnlyFile class.</span></span>

1. <span data-ttu-id="2417f-152">*ReadOnlyFile. cs* veya *ReadOnlyFile. vb* dosyasının en üstünde, <xref:System.IO?displayProperty=nameWithType> ve ad alanlarını içeri aktarmak için aşağıdaki kodu ekleyin <xref:System.Dynamic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2417f-152">At the top of the *ReadOnlyFile.cs* or *ReadOnlyFile.vb* file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]

1. <span data-ttu-id="2417f-153">Özel dinamik nesne, arama ölçütlerini bulmak için bir sabit listesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2417f-153">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="2417f-154">Class ifadesinden önce aşağıdaki sabit listesi tanımını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-154">Before the class statement, add the following enum definition.</span></span>

    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]

1. <span data-ttu-id="2417f-155">Aşağıdaki kod örneğinde gösterildiği gibi sınıfını devralması için Class ifadesini güncelleştirin `DynamicObject` .</span><span class="sxs-lookup"><span data-stu-id="2417f-155">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>

    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

1. <span data-ttu-id="2417f-156">`ReadOnlyFile`Dosya yolu ve sınıf için bir Oluşturucu için özel bir alan tanımlamak üzere sınıfına aşağıdaki kodu ekleyin `ReadOnlyFile` .</span><span class="sxs-lookup"><span data-stu-id="2417f-156">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>

    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]

1. <span data-ttu-id="2417f-157">`ReadOnlyFile` sınıfına aşağıdaki `GetPropertyValue` yöntemini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-157">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="2417f-158">`GetPropertyValue`Yöntemi giriş, arama ölçütü olarak alır ve bu arama ölçütleriyle eşleşen bir metin dosyasındaki satırları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2417f-158">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="2417f-159">Sınıfı tarafından sunulan dinamik yöntemler `ReadOnlyFile` , `GetPropertyValue` ilgili sonuçlarını almak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2417f-159">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]

1. <span data-ttu-id="2417f-160">Yönteminden sonra `GetPropertyValue` , sınıfının yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryGetMember%2A> <xref:System.Dynamic.DynamicObject> .</span><span class="sxs-lookup"><span data-stu-id="2417f-160">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="2417f-161"><xref:System.Dynamic.DynamicObject.TryGetMember%2A>Yöntemi, dinamik bir sınıfın bir üyesi istendiğinde ve hiçbir bağımsız değişken belirtilmediğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2417f-161">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="2417f-162">`binder`Bağımsız değişkeni başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişken belirtilen üye için döndürülen sonuca başvurur.</span><span class="sxs-lookup"><span data-stu-id="2417f-162">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="2417f-163"><xref:System.Dynamic.DynamicObject.TryGetMember%2A>Yöntemi, istenen üye varsa döndüren bir Boolean değer döndürür `true` ; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="2417f-163">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]

1. <span data-ttu-id="2417f-164">Yönteminden sonra `TryGetMember` , sınıfının yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> <xref:System.Dynamic.DynamicObject> .</span><span class="sxs-lookup"><span data-stu-id="2417f-164">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="2417f-165"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A>Yöntemi, bağımsız değişkenlerle bir dinamik sınıfın bir üyesi istendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2417f-165">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="2417f-166">`binder`Bağımsız değişkeni başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişken belirtilen üye için döndürülen sonuca başvurur.</span><span class="sxs-lookup"><span data-stu-id="2417f-166">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="2417f-167">`args`Bağımsız değişkeni, üyeye geçirilen bağımsız değişkenlerin bir dizisini içerir.</span><span class="sxs-lookup"><span data-stu-id="2417f-167">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="2417f-168"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A>Yöntemi, istenen üye varsa döndüren bir Boolean değer döndürür `true` ; Aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="2417f-168">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>

    <span data-ttu-id="2417f-169">Yöntemin özel sürümü, `TryInvokeMember` ilk bağımsız değişkenin `StringSearchOption` önceki adımda tanımladığınız numaralandırıcıdan bir değer olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="2417f-169">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="2417f-170">`TryInvokeMember`Yöntemi ikinci bağımsız değişkenin bir Boole değeri olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="2417f-170">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="2417f-171">Bağımsız değişkenlerden biri veya her ikisi de geçerli değerlerdir, `GetPropertyValue` sonuçları almak için yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2417f-171">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>

    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]

1. <span data-ttu-id="2417f-172">Dosyayı kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="2417f-172">Save and close the file.</span></span>

### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="2417f-173">Örnek metin dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2417f-173">To create a sample text file</span></span>

1. <span data-ttu-id="2417f-174">**Çözüm Gezgini**, DynamicSample projesine sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-174">In **Solution Explorer**, right-click the DynamicSample project and select **Add** > **New Item**.</span></span> <span data-ttu-id="2417f-175">**Yüklü şablonlar** bölmesinde, **genel**' i seçin ve sonra **metin dosyası** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-175">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="2417f-176">**Ad** kutusunda *TextFile1.txt* varsayılan adını bırakın ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2417f-176">Leave the default name of *TextFile1.txt* in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="2417f-177">Projeye yeni bir metin dosyası eklenir.</span><span class="sxs-lookup"><span data-stu-id="2417f-177">A new text file is added to the project.</span></span>

1. <span data-ttu-id="2417f-178">Aşağıdaki metni *TextFile1.txt* dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2417f-178">Copy the following text to the *TextFile1.txt* file.</span></span>

    ```text
    List of customers and suppliers

    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)
    Customer: Preston, Chris
    Customer: Hines, Patrick
    Customer: Cameron, Maria
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan
    Customer: Koch, Paul
    ```

1. <span data-ttu-id="2417f-179">Dosyayı kaydedin ve kapatın.</span><span class="sxs-lookup"><span data-stu-id="2417f-179">Save and close the file.</span></span>

### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="2417f-180">Özel dinamik nesneyi kullanan bir örnek uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2417f-180">To create a sample application that uses the custom dynamic object</span></span>

1. <span data-ttu-id="2417f-181">**Çözüm Gezgini**, Visual C# kullanıyorsanız, Visual Basic veya *program. cs* dosyasını kullanıyorsanız *program. vb* dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2417f-181">In **Solution Explorer**, double-click the *Program.vb* file if you're using Visual Basic or the *Program.cs* file if you're using Visual C#.</span></span>

2. <span data-ttu-id="2417f-182">`Main` `ReadOnlyFile` *TextFile1.txt* dosyasına sınıfının bir örneğini oluşturmak için aşağıdaki kodu yordama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-182">Add the following code to the `Main` procedure to create an instance of the `ReadOnlyFile` class for the *TextFile1.txt* file.</span></span> <span data-ttu-id="2417f-183">Kod, dinamik üyeleri çağırmak ve "Customer" dizesini içeren metnin satırlarını almak için geç bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2417f-183">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>

     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/Program.vb#8)]

3. <span data-ttu-id="2417f-184">Dosyayı kaydedin ve <kbd> </kdb> + uygulamayı derlemek ve çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2417f-184">Save the file and press <kbd>Ctrl</kdb>+<kbd>F5</kbd> to build and run the application.</span></span>

## <a name="call-a-dynamic-language-library"></a><span data-ttu-id="2417f-185">Dinamik dil kitaplığı çağırma</span><span class="sxs-lookup"><span data-stu-id="2417f-185">Call a dynamic language library</span></span>

<span data-ttu-id="2417f-186">Aşağıdaki izlenecek yol, IronPython dinamik dilinde yazılmış bir kitaplığa erişen bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2417f-186">The following walkthrough creates a project that accesses a library that is written in the dynamic language IronPython.</span></span>

### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="2417f-187">Özel bir dinamik sınıf oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2417f-187">To create a custom dynamic class</span></span>

1. <span data-ttu-id="2417f-188">Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-188">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="2417f-189">**Yeni proje oluştur** Iletişim kutusunda C# veya Visual Basic ' yi seçin, **konsol uygulaması**' nı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-189">In the **Create a new project** dialog, select C# or Visual Basic, select **Console Application**, and then select **Next**.</span></span>

1. <span data-ttu-id="2417f-190">**Yeni projenizi yapılandırın** Iletişim kutusunda `DynamicIronPythonSample` **Proje adı**' nı girin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-190">In the **Configure your new project** dialog, enter `DynamicIronPythonSample` for the **Project name**, and then select **Next**.</span></span>

1. <span data-ttu-id="2417f-191">**Ek bilgi** Iletişim kutusunda **hedef çerçeve** Için **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="2417f-191">In the **Additional information** dialog, select **.NET 5.0 (Current)** for the **Target Framework**, and then select **Create**.</span></span>

   <span data-ttu-id="2417f-192">Yeni proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2417f-192">The new project is created.</span></span>

1. <span data-ttu-id="2417f-193">[IronPython](https://www.nuget.org/packages/IronPython) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="2417f-193">Install the [IronPython](https://www.nuget.org/packages/IronPython) NuGet package.</span></span>

1. <span data-ttu-id="2417f-194">Visual Basic kullanıyorsanız, *program. vb* dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-194">If you're using Visual Basic, edit the *Program.vb* file.</span></span> <span data-ttu-id="2417f-195">Visual C# kullanıyorsanız *program. cs* dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-195">If you're using Visual C#, edit the *Program.cs* file.</span></span>

1. <span data-ttu-id="2417f-196">Dosyasının en üstüne, `Microsoft.Scripting.Hosting` ve ad `IronPython.Hosting` alanlarını IronPython kitaplıklarından ve ad alanından içeri aktarmak için aşağıdaki kodu ekleyin `System.Linq` .</span><span class="sxs-lookup"><span data-stu-id="2417f-196">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries and the `System.Linq` namespace.</span></span>

    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#1)]

1. <span data-ttu-id="2417f-197">Ana yöntemde, `Microsoft.Scripting.Hosting.ScriptRuntime` IronPython kitaplıklarını barındırmak üzere yeni bir nesne oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-197">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="2417f-198">`ScriptRuntime`Nesnesi IronPython kitaplığı modülünü Random.py yükler.</span><span class="sxs-lookup"><span data-stu-id="2417f-198">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#2)]

1. <span data-ttu-id="2417f-199">Random.py modülünü yüklemeye yönelik koddan sonra, bir tamsayılar dizisi oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2417f-199">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="2417f-200">Dizi, `shuffle` dizideki değerleri rastgele sıralayan Random.py modülünün yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2417f-200">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>

     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/Program.vb#3)]

1. <span data-ttu-id="2417f-201">Dosyayı kaydedin ve <kbd> </kdb> + uygulamayı derlemek ve çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2417f-201">Save the file and press <kbd>Ctrl</kdb>+<kbd>F5</kbd> to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2417f-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2417f-202">See also</span></span>

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="2417f-203">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="2417f-203">Using Type dynamic</span></span>](./using-type-dynamic.md)
- [<span data-ttu-id="2417f-204">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="2417f-204">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="2417f-205">dynamic</span><span class="sxs-lookup"><span data-stu-id="2417f-205">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="2417f-206">Dinamik arabirimleri uygulama (Microsoft TechNet 'ten indirilebilir PDF)</span><span class="sxs-lookup"><span data-stu-id="2417f-206">Implementing Dynamic Interfaces (downloadable PDF from Microsoft TechNet)</span></span>](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
