---
title: AssemblyInfo özellikleri
description: Derleme öznitelikleri ve bunların .NET Core 2,1 ve sonraki sürümlerindeki MSBuild özelliklerine nasıl karşılık geldiğini öğrenin.
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192892"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a><span data-ttu-id="6dcef-103">AssemblyInfo özniteliklerini özelliklerle eşleyin</span><span class="sxs-lookup"><span data-stu-id="6dcef-103">Map AssemblyInfo attributes to properties</span></span>

<span data-ttu-id="6dcef-104">Genellikle .NET Core 2,0 ve önceki sürümlerde bir *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) , .NET Core 2,1 ' den itibaren MSBuild özelliklerinden otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6dcef-104">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file in .NET Core 2.0 and earlier versions are automatically generated from MSBuild properties, starting in .NET Core 2.1.</span></span>

## <a name="properties-per-attribute"></a><span data-ttu-id="6dcef-105">Öznitelik başına Özellikler</span><span class="sxs-lookup"><span data-stu-id="6dcef-105">Properties per attribute</span></span>

<span data-ttu-id="6dcef-106">Aşağıdaki tabloda gösterildiği gibi, her bir öznitelik, içeriğini denetleyen karşılık gelen bir özelliğe sahiptir ve oluşturulmasını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="6dcef-106">As shown in the following table, each attribute has a corresponding property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="6dcef-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6dcef-107">Attribute</span></span>                                                      | <span data-ttu-id="6dcef-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="6dcef-108">Property</span></span>               | <span data-ttu-id="6dcef-109">Devre dışı bırakılacak Özellik</span><span class="sxs-lookup"><span data-stu-id="6dcef-109">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="6dcef-110">Notlar:</span><span class="sxs-lookup"><span data-stu-id="6dcef-110">Notes:</span></span>

- <span data-ttu-id="6dcef-111">`AssemblyVersion` ve `FileVersion` sonek olmadan değerine varsayılan değer `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="6dcef-111">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="6dcef-112">Örneğin, ise, `$(Version)` `1.2.3-beta.4` değer olacaktır `1.2.3` .</span><span class="sxs-lookup"><span data-stu-id="6dcef-112">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="6dcef-113">`InformationalVersion` Varsayılan değer olarak değeridir `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="6dcef-113">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="6dcef-114">`$(SourceRevisionId)`Özelliği varsa, öğesine eklenir `InformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="6dcef-114">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="6dcef-115">Kullanarak bu davranışı devre dışı bırakabilirsiniz `IncludeSourceRevisionInInformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="6dcef-115">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="6dcef-116">`Copyright``Description`Ayrıca, NuGet meta verileri için de Özellikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6dcef-116">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="6dcef-117">`Configuration`, varsayılan olarak `Debug` , tüm MSBuild hedefleri ile paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="6dcef-117">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="6dcef-118">Bunu, `--configuration` `dotnet` Örneğin [DotNet Pack](../tools/dotnet-pack.md)gibi komutlar seçeneği aracılığıyla ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dcef-118">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>

## <a name="generateassemblyinfo"></a><span data-ttu-id="6dcef-119">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="6dcef-119">GenerateAssemblyInfo</span></span>

<span data-ttu-id="6dcef-120">AssemblyInfo üretimini sağlayan veya devre dışı bırakan bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6dcef-120">A Boolean that enables or disables the AssemblyInfo generation.</span></span> <span data-ttu-id="6dcef-121">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6dcef-121">The default value is `true`.</span></span>

## <a name="generatedassemblyinfofile"></a><span data-ttu-id="6dcef-122">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="6dcef-122">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="6dcef-123">Oluşturulan derleme bilgi dosyasının göreli veya mutlak yolu.</span><span class="sxs-lookup"><span data-stu-id="6dcef-123">The relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="6dcef-124">Varsayılan olarak *[proje-adı] adlı bir dosya olarak adlandırılır. AssemblyInfo. [CS | vb]* `$(IntermediateOutputPath)` (*obj*) dizininde.</span><span class="sxs-lookup"><span data-stu-id="6dcef-124">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (*obj*) directory.</span></span>
