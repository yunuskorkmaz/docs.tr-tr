---
title: Anlam Analizi ile çalışmaya başlama
description: Bu öğretici, .NET derleyici SDK'sını kullanarak anlam Analizi ile çalışmaya genel bir bakış sağlar.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 188104c3430b4ca32578cd35d3e161a6eb0e0e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61676072"
---
# <a name="get-started-with-semantic-analysis"></a><span data-ttu-id="1a02c-103">Anlam Analizi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1a02c-103">Get started with semantic analysis</span></span>

<span data-ttu-id="1a02c-104">Bu öğreticide söz dizimi API ile ilgili bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="1a02c-104">This tutorial assumes you're familiar with the Syntax API.</span></span> <span data-ttu-id="1a02c-105">[Söz dizimi Analizi ile çalışmaya başlama](syntax-analysis.md) makale yeterli giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a02c-105">The [get started with syntax analysis](syntax-analysis.md) article provides sufficient introduction.</span></span>

<span data-ttu-id="1a02c-106">Bu öğreticide, Keşif **sembol** ve **bağlama API'leri**.</span><span class="sxs-lookup"><span data-stu-id="1a02c-106">In this tutorial, you explore the **Symbol** and **Binding APIs**.</span></span> <span data-ttu-id="1a02c-107">Bu API'ler hakkında bilgi sağlar. _anlam_ programının.</span><span class="sxs-lookup"><span data-stu-id="1a02c-107">These APIs provide information about the _semantic meaning_ of a program.</span></span> <span data-ttu-id="1a02c-108">Soru sormak ve programınızda herhangi bir simge ile temsil edilen türleri hakkında soruları yanıtlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1a02c-108">They enable you to ask and answer questions about the types represented by any symbol in your program.</span></span>

<span data-ttu-id="1a02c-109">Yüklemeniz gerekir **.NET derleyici Platformu SDK'sı**:</span><span class="sxs-lookup"><span data-stu-id="1a02c-109">You'll need to install the **.NET Compiler Platform SDK**:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a><span data-ttu-id="1a02c-110">Derlemeleri anlama ve semboller</span><span class="sxs-lookup"><span data-stu-id="1a02c-110">Understanding Compilations and Symbols</span></span>

<span data-ttu-id="1a02c-111">Daha fazla .NET derleyici SDK'sı ile çalışırken, söz dizimi API ve anlam API arasındaki farklılıklar hakkında bilgi sahibi olur.</span><span class="sxs-lookup"><span data-stu-id="1a02c-111">As you work more with the .NET Compiler SDK, you become familiar with the distinctions between Syntax API and the Semantic API.</span></span> <span data-ttu-id="1a02c-112">**Söz dizimi API** görmenize olanak tanır _yapısı_ programının.</span><span class="sxs-lookup"><span data-stu-id="1a02c-112">The **Syntax API** allows you to look at the _structure_ of a program.</span></span> <span data-ttu-id="1a02c-113">Ancak, genellikle daha zengin bilgi semantiği istersiniz veya _anlamı_ programının.</span><span class="sxs-lookup"><span data-stu-id="1a02c-113">However, often you want richer information about the semantics or _meaning_ of a program.</span></span> <span data-ttu-id="1a02c-114">Gevşek bir kod dosyası veya VB veya C# kod parçacığını yalıtım modunda sözdizimsel olarak çözümlenebilir olsa, "Bu değişken türünde bir boşlukta nedir" gibi sorular sorun anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-114">While a loose code file or snippet of VB or C# code can be syntactically analyzed in isolation, it's not meaningful to ask questions such as "what's the type of this variable" in a vacuum.</span></span> <span data-ttu-id="1a02c-115">Bir tür adı anlamını derleme başvuruları, ad alanı içeri aktarmaları veya diğer kod dosyaları bağımlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-115">The meaning of a type name may be dependent on assembly references, namespace imports, or other code files.</span></span> <span data-ttu-id="1a02c-116">Kullanarak bu soruları yanıtlanır **anlam API**, özellikle <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-116">Those questions are answered using the **Semantic API**, specifically the <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="1a02c-117">Örneği <xref:Microsoft.CodeAnalysis.Compilation> derleyici tarafından görülen şekilde tek bir projeye benzer ve Visual Basic veya C# programı derlemek için gereken her şeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a02c-117">An instance of <xref:Microsoft.CodeAnalysis.Compilation> is analogous to a single project as seen by the compiler and represents everything needed to compile a Visual Basic or C# program.</span></span> <span data-ttu-id="1a02c-118">**Derleme** derlenecek kaynak dosyaları, bütünleştirilmiş kod başvuruları ve derleyici seçenekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-118">The **compilation** includes the set of source files to be compiled, assembly references, and compiler options.</span></span> <span data-ttu-id="1a02c-119">Bu bağlam içinde ve diğer bilgileri kullanarak kodun anlamı hakkında neden.</span><span class="sxs-lookup"><span data-stu-id="1a02c-119">You can reason about the meaning of the code using all the other information in this context.</span></span> <span data-ttu-id="1a02c-120">A <xref:Microsoft.CodeAnalysis.Compilation> bulmanıza olanak tanır **sembolleri** -türleri, ad alanları, üyeleri ve adları ve diğer ifadeler başvuran değişkenler gibi varlıklar.</span><span class="sxs-lookup"><span data-stu-id="1a02c-120">A <xref:Microsoft.CodeAnalysis.Compilation> allows you to find **Symbols** - entities such as types, namespaces, members, and variables which names and other expressions refer to.</span></span> <span data-ttu-id="1a02c-121">Adlar ve ifadeler ile ilişkilendirme işlemi **sembolleri** çağrılır **bağlama**.</span><span class="sxs-lookup"><span data-stu-id="1a02c-121">The process of associating names and expressions with **Symbols** is called **Binding**.</span></span>

<span data-ttu-id="1a02c-122">Gibi <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> soyut bir sınıf dile bağlı türevleri ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-122">Like <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> is an abstract class with language-specific derivatives.</span></span> <span data-ttu-id="1a02c-123">Derleme örneğini oluştururken, üzerinde bir fabrika yöntemini çağırmanız gerekir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-123">When creating an instance of Compilation, you must invoke a factory method on the <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (or <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) class.</span></span>

## <a name="querying-symbols"></a><span data-ttu-id="1a02c-124">Semboller sorgulama</span><span class="sxs-lookup"><span data-stu-id="1a02c-124">Querying symbols</span></span>

<span data-ttu-id="1a02c-125">Bu öğreticide, "Hello World" programı tekrar bakın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-125">In this tutorial, you look at the "Hello World" program again.</span></span> <span data-ttu-id="1a02c-126">Bu kez, programın ne bu sembolleri temsil türlerini anlamak için sembolleri sorgulayın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-126">This time, you query the symbols in the program to understand what types those symbols represent.</span></span> <span data-ttu-id="1a02c-127">Bir ad alanı içindeki türleri için sorgulama ve türe göre uygun olan yöntemler bulmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1a02c-127">You query for the types in a namespace, and learn to find the methods available on a type.</span></span>

<span data-ttu-id="1a02c-128">Bu örnek için tamamlanan kodu gördüğünüz [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).</span><span class="sxs-lookup"><span data-stu-id="1a02c-128">You can see the finished code for this sample in [our GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).</span></span>

> [!NOTE]
> <span data-ttu-id="1a02c-129">Sözdizimi ağacı türleri devralma programı farklı konumlarda geçerli olan farklı bir sözdizimi öğeleri tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-129">The Syntax Tree types use inheritance to describe the different syntax elements that are valid at different locations in the program.</span></span> <span data-ttu-id="1a02c-130">Genellikle bu API'leri kullanarak, atama özellikleri veya belirli türetilen türler için koleksiyon üyelerini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-130">Using these APIs often means casting properties or collection members to specific derived types.</span></span> <span data-ttu-id="1a02c-131">Aşağıdaki örneklerde, atama ve atamaları açıkça yazılmış değişkenler kullanarak ayrı deyim olan.</span><span class="sxs-lookup"><span data-stu-id="1a02c-131">In the following examples, the assignment and the casts are separate statements, using explicitly typed variables.</span></span> <span data-ttu-id="1a02c-132">API dönüş türleri ve döndürülen nesnelerin çalışma zamanı türü görmek için kodu okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a02c-132">You can read the code to see the return types of the API and the runtime type of the objects returned.</span></span> <span data-ttu-id="1a02c-133">Uygulamada, türü örtük olarak belirlenmiş değişkenlerin ve incelenmekte olan nesnelerin türünü tanımlamak için API adlara dayalı daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="1a02c-133">In practice, it's more common to use implicitly typed variables and rely on API names to describe the type of objects being examined.</span></span>

<span data-ttu-id="1a02c-134">Yeni C# oluşturma **tek başına kod analizi aracı** proje:</span><span class="sxs-lookup"><span data-stu-id="1a02c-134">Create a new C# **Stand-Alone Code Analysis Tool** project:</span></span>

* <span data-ttu-id="1a02c-135">Visual Studio'da **dosya** > **yeni** > **proje** yeni proje iletişim kutusu görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="1a02c-135">In Visual Studio, choose **File** > **New** > **Project** to display the New Project dialog.</span></span>
* <span data-ttu-id="1a02c-136">Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**.</span><span class="sxs-lookup"><span data-stu-id="1a02c-136">Under **Visual C#** > **Extensibility**, choose **Stand-Alone Code Analysis Tool**.</span></span>
* <span data-ttu-id="1a02c-137">Projenizi adlandırın "**SemanticQuickStart**" ve Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-137">Name your project "**SemanticQuickStart**" and click OK.</span></span>

<span data-ttu-id="1a02c-138">Temel "Hello World!" analiz etmek için gideceğinizi</span><span class="sxs-lookup"><span data-stu-id="1a02c-138">You're going to analyze the basic "Hello World!"</span></span> <span data-ttu-id="1a02c-139">daha önce gösterilen programı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-139">program shown earlier.</span></span>
<span data-ttu-id="1a02c-140">İçinde bir sabit olarak Hello World programı için metin ekleyin, `Program` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="1a02c-140">Add the text for the Hello World program as a constant in your `Program` class:</span></span>

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

<span data-ttu-id="1a02c-141">Ardından, kod metni için söz dizimi ağacı oluşturmak için aşağıdaki kodu ekleyin `programText` sabit.</span><span class="sxs-lookup"><span data-stu-id="1a02c-141">Next, add the following code to build the syntax tree for the code text in the `programText` constant.</span></span>  <span data-ttu-id="1a02c-142">Aşağıdaki satırı ekleyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1a02c-142">Add the following line to your `Main` method:</span></span>

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

<span data-ttu-id="1a02c-143">Ardından, yapı bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> zaten oluşturduğunuz ağaç.</span><span class="sxs-lookup"><span data-stu-id="1a02c-143">Next, build a <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> from the tree you already created.</span></span> <span data-ttu-id="1a02c-144">"Hello World" örnek dayanan <xref:System.String> ve <xref:System.Console> türleri.</span><span class="sxs-lookup"><span data-stu-id="1a02c-144">The "Hello World" sample relies on the <xref:System.String> and <xref:System.Console> types.</span></span> <span data-ttu-id="1a02c-145">Bu iki tür derlemenizdeki bildiren derlemesine başvuru gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1a02c-145">You need to reference the assembly that declares those two types in your compilation.</span></span> <span data-ttu-id="1a02c-146">Aşağıdaki satırı ekleyin, `Main` yöntemi, söz dizimi ağacının uygun derlemesine başvuru dahil olmak üzere bir derleme oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="1a02c-146">Add the following line to your `Main` method to create a compilation of your syntax tree, including the reference to the appropriate assembly:</span></span>

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<span data-ttu-id="1a02c-147"><xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Yöntemi derleme başvurularını ekler.</span><span class="sxs-lookup"><span data-stu-id="1a02c-147">The <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> method adds references to the compilation.</span></span> <span data-ttu-id="1a02c-148"><xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Yöntemi bir başvuru olarak bir derleme yükler.</span><span class="sxs-lookup"><span data-stu-id="1a02c-148">The <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> method loads an assembly as a reference.</span></span>

## <a name="querying-the-semantic-model"></a><span data-ttu-id="1a02c-149">Anlam modeli sorgulama</span><span class="sxs-lookup"><span data-stu-id="1a02c-149">Querying the semantic model</span></span>

<span data-ttu-id="1a02c-150">Sonra bir <xref:Microsoft.CodeAnalysis.Compilation> bunları istemeniz bir <xref:Microsoft.CodeAnalysis.SemanticModel> herhangi <xref:Microsoft.CodeAnalysis.SyntaxTree> uygulamasında yer alan <xref:Microsoft.CodeAnalysis.Compilation>.</span><span class="sxs-lookup"><span data-stu-id="1a02c-150">Once you have a <xref:Microsoft.CodeAnalysis.Compilation> you can ask it for a <xref:Microsoft.CodeAnalysis.SemanticModel> for any <xref:Microsoft.CodeAnalysis.SyntaxTree> contained in that <xref:Microsoft.CodeAnalysis.Compilation>.</span></span> <span data-ttu-id="1a02c-151">Anlam modeli, normalde IntelliSense'de elde edebileceğiniz bilgi kaynağı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a02c-151">You can think of the semantic model as the source for all the information you would normally get from intellisense.</span></span> <span data-ttu-id="1a02c-152">A <xref:Microsoft.CodeAnalysis.SemanticModel> soruları "Adı bu konumda kapsamda nelerdir?", ister "hangi üyelerinin bu yöntemden erişilebilir?", "Bu metin bloğu içinde hangi değişkenleri kullanılır?" ve "Ne bu adı/ifadesi başvurmak?"</span><span class="sxs-lookup"><span data-stu-id="1a02c-152">A <xref:Microsoft.CodeAnalysis.SemanticModel> can answer questions like "What names are in scope at this location?", "What members are accessible from this method?", "What variables are used in this block of text?", and "What does this name/expression refer to?"</span></span> <span data-ttu-id="1a02c-153">Anlam modeli oluşturmak için bu deyimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1a02c-153">Add this statement to create the semantic model:</span></span>

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a><span data-ttu-id="1a02c-154">Bir ad bağlama</span><span class="sxs-lookup"><span data-stu-id="1a02c-154">Binding a name</span></span>

<span data-ttu-id="1a02c-155"><xref:Microsoft.CodeAnalysis.Compilation> Oluşturur <xref:Microsoft.CodeAnalysis.SemanticModel> gelen <xref:Microsoft.CodeAnalysis.SyntaxTree>.</span><span class="sxs-lookup"><span data-stu-id="1a02c-155">The <xref:Microsoft.CodeAnalysis.Compilation> creates the  <xref:Microsoft.CodeAnalysis.SemanticModel> from the <xref:Microsoft.CodeAnalysis.SyntaxTree>.</span></span> <span data-ttu-id="1a02c-156">Model oluşturduktan sonra ilk bulmak için sorgulayabilirsiniz `using` yönergesi için Sembol bilgilerini almanıza ve `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-156">After creating the model, you can query it to find the first `using` directive, and retrieve the symbol information for the `System` namespace.</span></span> <span data-ttu-id="1a02c-157">Bu iki satırları ekleyin, `Main` anlam modeli oluşturma ve ilk simgesini almak için yöntem using deyimi:</span><span class="sxs-lookup"><span data-stu-id="1a02c-157">Add these two lines to your `Main` method to create the semantic model and retrieve the symbol for the first using statement:</span></span>

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

<span data-ttu-id="1a02c-158">Yukarıdaki kod ilk adı bağlama gösterilmektedir `using` alınacak yönergesi bir <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> için `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-158">The preceding code shows how to bind the name in the first `using` directive to retrieve a <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> for the `System` namespace.</span></span> <span data-ttu-id="1a02c-159">Yukarıdaki kod, ayrıca kullanmanızı gösterir **söz dizimi modeli** ; kod yapısını bulmak için kullandığınız **anlam modeli** anlamını anlamak için.</span><span class="sxs-lookup"><span data-stu-id="1a02c-159">The preceding code also illustrates that you use the **syntax model** to find the structure of the code; you use the **semantic model** to understand its meaning.</span></span> <span data-ttu-id="1a02c-160">**Söz dizimi modeli** bulur `System` kullanarak deyimi.</span><span class="sxs-lookup"><span data-stu-id="1a02c-160">The **syntax model** finds the string `System` in the using statement.</span></span> <span data-ttu-id="1a02c-161">**Anlam modeli** tanımlanan türleri hakkında tüm bilgiler `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-161">The **semantic model** has all the information about the types defined in the `System` namespace.</span></span>

<span data-ttu-id="1a02c-162">Gelen <xref:Microsoft.CodeAnalysis.SymbolInfo> edinebilirsiniz nesne <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> kullanarak <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1a02c-162">From the <xref:Microsoft.CodeAnalysis.SymbolInfo> object you can obtain the <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> using the <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1a02c-163">Bu özellik, bu ifade için başvuruyor sembol döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a02c-163">This property returns the symbol this expression refers to.</span></span> <span data-ttu-id="1a02c-164">Bu özellik başvuran yoksa şeye (örneğin, sayısal değişmez değerler) ifadeler için olan `null`.</span><span class="sxs-lookup"><span data-stu-id="1a02c-164">For expressions that don't refer to anything (such as numeric literals) this property is `null`.</span></span> <span data-ttu-id="1a02c-165">Zaman <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> null değil <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> simgenin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-165">When the <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> is not null, the <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> denotes the type of the symbol.</span></span> <span data-ttu-id="1a02c-166">Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a02c-166">In this example, the <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> property is a <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a02c-167">Aşağıdaki kodu ekleyin, `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a02c-167">Add the following code to your `Main` method.</span></span> <span data-ttu-id="1a02c-168">Simgesini alır `System` tüm alt ad alanlarında bildirilen ad alanı ve görüntüler `System` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="1a02c-168">It retrieves the symbol for the `System` namespace and then displays all the child namespaces declared in the `System` namespace:</span></span>

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

<span data-ttu-id="1a02c-169">Programı çalıştırın ve aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1a02c-169">Run the program and you should see the following output:</span></span>

```
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> <span data-ttu-id="1a02c-170">Çıktı bir alt ad alanı, her ad alanı içermeyen `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1a02c-170">The output does not include every namespace that is a child namespace of the `System` namespace.</span></span> <span data-ttu-id="1a02c-171">Bu derlemede, yalnızca derlemenin başvuran mevcut olan her ad alanı görüntüler burada `System.String` bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-171">It displays every namespace that is present in this compilation, which only references the assembly where `System.String` is declared.</span></span> <span data-ttu-id="1a02c-172">Diğer derlemeler içinde bildirilen tüm ad alanları için bu derleme bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="1a02c-172">Any namespaces declared in other assemblies are not known to this compilation</span></span>

### <a name="binding-an-expression"></a><span data-ttu-id="1a02c-173">Bir ifade bağlama</span><span class="sxs-lookup"><span data-stu-id="1a02c-173">Binding an expression</span></span>

<span data-ttu-id="1a02c-174">Yukarıdaki kod, bir ad bağlayarak bir sembol Bul işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a02c-174">The preceding code shows how to find a symbol by binding to a name.</span></span> <span data-ttu-id="1a02c-175">Adı olmayan başka ifadelere bağlanabilir bir C# programı vardır.</span><span class="sxs-lookup"><span data-stu-id="1a02c-175">There are other expressions in a C# program that can be bound that aren't names.</span></span> <span data-ttu-id="1a02c-176">Bu özellik göstermek için şimdi basit dize sabit değeri için bağlama erişin.</span><span class="sxs-lookup"><span data-stu-id="1a02c-176">To demonstrate this capability, let's access the binding to a simple string literal.</span></span>

<span data-ttu-id="1a02c-177">"Hello World" programını içeren bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="1a02c-177">The "Hello World" program contains a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, the "Hello, World!"</span></span> <span data-ttu-id="1a02c-178">konsolda görüntülenen dize.</span><span class="sxs-lookup"><span data-stu-id="1a02c-178">string displayed to the console.</span></span>

<span data-ttu-id="1a02c-179">"Hello, World!" bulun</span><span class="sxs-lookup"><span data-stu-id="1a02c-179">You find the "Hello, World!"</span></span> <span data-ttu-id="1a02c-180">tek bir dize programda değişmez değer bulma tarafından kullanılan dize.</span><span class="sxs-lookup"><span data-stu-id="1a02c-180">string by locating the single string literal in the program.</span></span> <span data-ttu-id="1a02c-181">Daha sonra sözdizimi düğümü bulunan sonra anlam modeli Bu düğüm için tür bilgilerini alın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-181">Then, once you've located the syntax node, get the type info for that node from the semantic model.</span></span> <span data-ttu-id="1a02c-182">Aşağıdaki kodu ekleyin, `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1a02c-182">Add the following code to your `Main` method:</span></span>

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<span data-ttu-id="1a02c-183"><xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Yapı içeren bir <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> değişmez değer türü hakkında anlam bilgilerine erişim sağlayan bir özellik.</span><span class="sxs-lookup"><span data-stu-id="1a02c-183">The <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> struct includes a <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> property that enables access to the semantic information about the type of the literal.</span></span> <span data-ttu-id="1a02c-184">Bu örnekte, o `string` türü.</span><span class="sxs-lookup"><span data-stu-id="1a02c-184">In this example, that's the `string` type.</span></span> <span data-ttu-id="1a02c-185">Bu özellik yerel bir değişkene atar bir bildirimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1a02c-185">Add a declaration that assigns this property to a local variable:</span></span>

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

<span data-ttu-id="1a02c-186">Bu öğreticiyi tamamlamak için tüm genel yöntemleri bildirilen üzerinde bir dizi oluşturur bir LINQ Sorgu oluşturalım `string` türü döndüren bir `string`.</span><span class="sxs-lookup"><span data-stu-id="1a02c-186">To finish this tutorial, let's build a LINQ query that creates a sequence of all the public methods declared on the `string` type that return a `string`.</span></span> <span data-ttu-id="1a02c-187">Bu sorgu karmaşık, bu nedenle şimdi bu yapı satır alır, tek bir sorgu yeniden yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="1a02c-187">This query gets complex, so let's build it line by line, then reconstruct it as a single query.</span></span> <span data-ttu-id="1a02c-188">Bu sorgu için kaynak üzerinde bildirilen tüm üyelerle dizisidir `string` türü:</span><span class="sxs-lookup"><span data-stu-id="1a02c-188">The source for this query is the sequence of all members declared on the `string` type:</span></span>

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

<span data-ttu-id="1a02c-189">Bu kaynak dizisi özellikler ve alanları dahil olmak üzere tüm üyeleri içerir, böylece kullanarak filtre <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> Bul öğeleri yönteme <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> nesneler:</span><span class="sxs-lookup"><span data-stu-id="1a02c-189">That source sequence contains all members, including properties and fields, so filter it using the <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> method to find elements that are <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> objects:</span></span>

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

<span data-ttu-id="1a02c-190">Ardından, genel ve dönüş yöntemleri döndürülecek başka bir filtre Ekle bir `string`:</span><span class="sxs-lookup"><span data-stu-id="1a02c-190">Next, add another filter to return only those methods that are public and return a `string`:</span></span>

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

<span data-ttu-id="1a02c-191">Name özelliği yalnızca ve yalnızca DISTINCT adları tüm aşırı yüklemeler kaldırarak seçin:</span><span class="sxs-lookup"><span data-stu-id="1a02c-191">Select only the name property, and only distinct names by removing any overloads:</span></span>

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

<span data-ttu-id="1a02c-192">Ayrıca LINQ Sorgu söz dizimi kullanarak tam bir sorgu oluşturun ve sonra konsolda yöntem adları görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="1a02c-192">You can also build the full query using the LINQ query syntax, and then display all the method names in  the console:</span></span>

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

<span data-ttu-id="1a02c-193">Programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1a02c-193">Build and run the program.</span></span> <span data-ttu-id="1a02c-194">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1a02c-194">You should see the following output:</span></span>

```
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```

<span data-ttu-id="1a02c-195">Bulmak ve bu programın bir parçası olan simgeler hakkında bilgi görüntülemek için anlamsal API kullandınız.</span><span class="sxs-lookup"><span data-stu-id="1a02c-195">You've used the Semantic API to find and display information about the symbols that are part of this program.</span></span>
