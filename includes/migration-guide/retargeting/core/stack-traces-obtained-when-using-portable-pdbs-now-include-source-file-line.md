---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614800"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="98991-101">Taşınabilir pdb 'leri kullanıldığında elde edilen yığın izlemeleri artık, istenirse kaynak dosya ve satır bilgilerini içerir</span><span class="sxs-lookup"><span data-stu-id="98991-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="98991-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="98991-102">Details</span></span>

<span data-ttu-id="98991-103">.NET Framework 4.7.2 ile başlayarak, taşınabilir pdb 'leri dahil edildiğinde yığın izlemeleri, istendiğinde kaynak dosya ve satır bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="98991-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="98991-104">.NET Framework 4.7.2 ' den önceki sürümlerde, açık bir şekilde istenmiş olsa bile taşınabilir pdb 'leri kullanılırken kaynak dosya ve satır bilgileri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98991-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="98991-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="98991-105">Suggestion</span></span>

<span data-ttu-id="98991-106">.NET Framework 4.7.2 ' i hedefleyen uygulamalar için, taşınabilir pdb 'leri kullanırken, dosyanın bölümüne aşağıdakileri ekleyerek kaynak dosya ve satır bilgilerini devre dışı bırakabilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="98991-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="98991-107">.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.7.2 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakileri ekleyerek taşınabilir pdb 'leri kullanırken kaynak dosya ve satır bilgilerini kabul edebilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="98991-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="98991-108">Name</span><span class="sxs-lookup"><span data-stu-id="98991-108">Name</span></span>    | <span data-ttu-id="98991-109">Değer</span><span class="sxs-lookup"><span data-stu-id="98991-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="98991-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="98991-110">Scope</span></span>   | <span data-ttu-id="98991-111">Edge</span><span class="sxs-lookup"><span data-stu-id="98991-111">Edge</span></span>        |
| <span data-ttu-id="98991-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="98991-112">Version</span></span> | <span data-ttu-id="98991-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="98991-113">4.7.2</span></span>       |
| <span data-ttu-id="98991-114">Tür</span><span class="sxs-lookup"><span data-stu-id="98991-114">Type</span></span>    | <span data-ttu-id="98991-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="98991-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="98991-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="98991-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
