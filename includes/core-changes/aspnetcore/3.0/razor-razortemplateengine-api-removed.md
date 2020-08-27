---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957698"
---
### <a name="razor-razortemplateengine-api-removed"></a>Razor: RazorTemplateEngine API 'SI kaldırıldı

[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API 'si kaldırıldı ve ile değiştirildi <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Razor dosyalarının kodunu ayrıştırmak ve oluşturmak için bir şablon altyapısı oluşturulabilir ve kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

`RazorProjectEngine` oluşturulabilir ve `RazorTemplateEngine` Razor dosyalarının kodunu ayrıştırmak ve oluşturmak için aynı tür bilgileri sağlayabilir. `RazorProjectEngine` Ayrıca ek yapılandırma düzeyleri sağlar.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`RazorTemplateEngine` var olan uygulamalarla çok sıkı şekilde bağlanmış. Bu sıkı bir Razor ayrıştırma/oluşturma işlem hattını düzgün bir şekilde yapılandırmaya çalışırken daha fazla soruya yol açmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

`RazorProjectEngine`Yerine kullanın `RazorTemplateEngine` . Aşağıdaki örnekleri göz önünde bulundurun.

##### <a name="create-and-configure-the-razorprojectengine"></a>RazorProjectEngine oluşturma ve yapılandırma

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

##### <a name="generate-code-for-a-razor-file"></a>Razor dosyası için kod oluşturma

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

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [RazorTemplateEngineOptions](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
