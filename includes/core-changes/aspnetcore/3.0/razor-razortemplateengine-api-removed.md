---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957698"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="69971-101">Razor: RazorTemplateEngine API 'SI kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="69971-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="69971-102">[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API 'si kaldırıldı ve ile değiştirildi <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="69971-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="69971-103">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).</span><span class="sxs-lookup"><span data-stu-id="69971-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="69971-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="69971-104">Version introduced</span></span>

<span data-ttu-id="69971-105">3.0</span><span class="sxs-lookup"><span data-stu-id="69971-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="69971-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="69971-106">Old behavior</span></span>

<span data-ttu-id="69971-107">Razor dosyalarının kodunu ayrıştırmak ve oluşturmak için bir şablon altyapısı oluşturulabilir ve kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69971-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="69971-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="69971-108">New behavior</span></span>

<span data-ttu-id="69971-109">`RazorProjectEngine` oluşturulabilir ve `RazorTemplateEngine` Razor dosyalarının kodunu ayrıştırmak ve oluşturmak için aynı tür bilgileri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="69971-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="69971-110">`RazorProjectEngine` Ayrıca ek yapılandırma düzeyleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="69971-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="69971-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="69971-111">Reason for change</span></span>

<span data-ttu-id="69971-112">`RazorTemplateEngine` var olan uygulamalarla çok sıkı şekilde bağlanmış.</span><span class="sxs-lookup"><span data-stu-id="69971-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="69971-113">Bu sıkı bir Razor ayrıştırma/oluşturma işlem hattını düzgün bir şekilde yapılandırmaya çalışırken daha fazla soruya yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="69971-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69971-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="69971-114">Recommended action</span></span>

<span data-ttu-id="69971-115">`RazorProjectEngine`Yerine kullanın `RazorTemplateEngine` .</span><span class="sxs-lookup"><span data-stu-id="69971-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="69971-116">Aşağıdaki örnekleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="69971-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="69971-117">RazorProjectEngine oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="69971-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="69971-118">Razor dosyası için kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="69971-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="69971-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="69971-119">Category</span></span>

<span data-ttu-id="69971-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69971-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69971-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="69971-121">Affected APIs</span></span>

- [<span data-ttu-id="69971-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="69971-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="69971-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="69971-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
