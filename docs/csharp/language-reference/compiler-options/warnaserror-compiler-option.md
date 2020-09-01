---
description: -warnaserror (C# derleyici seçenekleri)
title: -warnaserror (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 3ccd4546402dbc8e5d9245af6411ba2d831d4959
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127249"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="14d47-103">-warnaserror (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="14d47-103">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="14d47-104">**-Warnaserror +** seçeneği tüm uyarıları hata olarak değerlendirir</span><span class="sxs-lookup"><span data-stu-id="14d47-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d47-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="14d47-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="14d47-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14d47-106">Remarks</span></span>  
 <span data-ttu-id="14d47-107">Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir ve derleme işlemi durdurulur (çıktı dosyası derlenmemiştir).</span><span class="sxs-lookup"><span data-stu-id="14d47-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="14d47-108">Varsayılan olarak, **-warnaserror-** , bir çıkış dosyasının oluşturulmasını engellemez uyarısı oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="14d47-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="14d47-109">- **warnaserror +** ile aynı olan **warnaserror**, uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="14d47-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="14d47-110">İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14d47-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="14d47-111">Tüm null olabilme uyarıları kümesi **Nullable toplu değer** ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="14d47-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="14d47-112">Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için [-Warn](./warn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="14d47-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="14d47-113">Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="14d47-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="14d47-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="14d47-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="14d47-115">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="14d47-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="14d47-116">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="14d47-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="14d47-117">**Uyarıları hata olarak değerlendir** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14d47-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="14d47-118">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors> ..</span><span class="sxs-lookup"><span data-stu-id="14d47-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14d47-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="14d47-119">Example</span></span>  
 <span data-ttu-id="14d47-120">Derle `in.cs` ve derleyicinin hiçbir uyarı görüntülememe:</span><span class="sxs-lookup"><span data-stu-id="14d47-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="14d47-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14d47-121">See also</span></span>

- [<span data-ttu-id="14d47-122">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="14d47-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="14d47-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="14d47-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
