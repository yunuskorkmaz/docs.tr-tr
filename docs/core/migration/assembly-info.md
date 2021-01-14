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
# <a name="map-assemblyinfo-attributes-to-properties"></a>AssemblyInfo özniteliklerini özelliklerle eşleyin

Genellikle .NET Core 2,0 ve önceki sürümlerde bir *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) , .NET Core 2,1 ' den itibaren MSBuild özelliklerinden otomatik olarak oluşturulur.

## <a name="properties-per-attribute"></a>Öznitelik başına Özellikler

Aşağıdaki tabloda gösterildiği gibi, her bir öznitelik, içeriğini denetleyen karşılık gelen bir özelliğe sahiptir ve oluşturulmasını devre dışı bırakır:

| Öznitelik                                                      | Özellik               | Devre dışı bırakılacak Özellik                             |
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

Notlar:

- `AssemblyVersion` ve `FileVersion` sonek olmadan değerine varsayılan değer `$(Version)` . Örneğin, ise, `$(Version)` `1.2.3-beta.4` değer olacaktır `1.2.3` .
- `InformationalVersion` Varsayılan değer olarak değeridir `$(Version)` .
- `$(SourceRevisionId)`Özelliği varsa, öğesine eklenir `InformationalVersion` . Kullanarak bu davranışı devre dışı bırakabilirsiniz `IncludeSourceRevisionInInformationalVersion` .
- `Copyright``Description`Ayrıca, NuGet meta verileri için de Özellikler kullanılır.
- `Configuration`, varsayılan olarak `Debug` , tüm MSBuild hedefleri ile paylaşılır. Bunu, `--configuration` `dotnet` Örneğin [DotNet Pack](../tools/dotnet-pack.md)gibi komutlar seçeneği aracılığıyla ayarlayabilirsiniz.

## <a name="generateassemblyinfo"></a>Generateassemblyınfo

AssemblyInfo üretimini sağlayan veya devre dışı bırakan bir Boole değeri. `true` varsayılan değerdir.

## <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Oluşturulan derleme bilgi dosyasının göreli veya mutlak yolu. Varsayılan olarak *[proje-adı] adlı bir dosya olarak adlandırılır. AssemblyInfo. [CS | vb]* `$(IntermediateOutputPath)` (*obj*) dizininde.
