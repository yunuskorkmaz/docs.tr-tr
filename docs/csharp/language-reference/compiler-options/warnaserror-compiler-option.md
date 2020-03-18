---
title: -warnaserror (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503482"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="77966-102">-warnaserror (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="77966-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="77966-103">**-warnaserror+** seçeneği tüm uyarıları hata olarak ele almaz</span><span class="sxs-lookup"><span data-stu-id="77966-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77966-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77966-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="77966-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77966-105">Remarks</span></span>  
 <span data-ttu-id="77966-106">Normalde uyarı olarak bildirilecek iletiler hata olarak bildirilir ve yapı işlemi durdurulur (çıktı dosyası oluşturulmaz).</span><span class="sxs-lookup"><span data-stu-id="77966-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="77966-107">Varsayılan olarak, **-warnaserror-** geçerlidir, bu da bir çıktı dosyasının oluşumunu engellememeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="77966-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="77966-108">**-warnaserror**, **-warnaserror+** ile aynıdır, uyarılar hata olarak ele alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="77966-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="77966-109">İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak ele alınmasını istiyorsanız, hata olarak ele almak için virgülle ayrılmış bir uyarı numaraları listesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77966-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="77966-110">Tüm nullability uyarılar kümesi **nullable** steno ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="77966-110">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="77966-111">Derleyicinin görüntülemesini istediğiniz uyarıların düzeyini belirtmek için [-uyar'ı](./warn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="77966-111">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="77966-112">Bazı [-nowarn](./nowarn-compiler-option.md) uyarıları devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77966-112">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="77966-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="77966-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="77966-114">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="77966-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="77966-115">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77966-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="77966-116">Uyarıları **Hata Olarak Ele'de** değiştirin özelliği.</span><span class="sxs-lookup"><span data-stu-id="77966-116">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="77966-117">Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>ayarlamak için bkz.</span><span class="sxs-lookup"><span data-stu-id="77966-117">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77966-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="77966-118">Example</span></span>  
 <span data-ttu-id="77966-119">Derleyicinin hiçbir uyarı görüntülemesini `in.cs` ve derlemesini ve görüntülemesini gerek:</span><span class="sxs-lookup"><span data-stu-id="77966-119">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="77966-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77966-120">See also</span></span>

- [<span data-ttu-id="77966-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="77966-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="77966-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="77966-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
