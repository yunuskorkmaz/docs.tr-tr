---
title: -kontrol edildi (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173776"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="20e04-102">-kontrol edildi (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="20e04-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="20e04-103">**Denetlenen** seçenek, veri türünün kapsamı dışında bir değerle sonuçlanan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) anahtar kelime kapsamında olmayan bir tamsayı aritmetik deyiminin çalışma zamanı özel durum larına neden olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="20e04-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20e04-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="20e04-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20e04-105">Remarks</span></span>  
 <span data-ttu-id="20e04-106">Bir veya `checked` `unchecked` anahtar kelime kapsamında olan bir tamsayı aritmetik **deyimi- işaretli** seçeneğin etkisine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="20e04-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="20e04-107">Bir `checked` veya `unchecked` anahtar kelime kapsamında olmayan bir tamsayı aritmetik deyimi, veri türünün aralığı dışında bir değerle sonuçlanır ve **-denetlenmiş+** (veya **-denetlenmiş)** derlemede kullanılırsa, bu ifade çalışma zamanında özel bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20e04-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="20e04-108">**Derlemede -denetlenen-** kullanılırsa, bu deyim çalışma zamanında özel bir özel durum neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="20e04-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="20e04-109">Bu seçeneğin varsayılan değeri **-işaretli-**; taşma denetimi devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="20e04-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="20e04-110">Bazen, büyük uygulamalar oluşturmak için kullanılan otomatik araçlar ayarlanır -+' olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="20e04-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="20e04-111">-denetlenen- kullanmak için bir senaryo, -denetlenmiş- belirterek aracın genel varsayılanGeçersiz kılmaktır.</span><span class="sxs-lookup"><span data-stu-id="20e04-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="20e04-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="20e04-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="20e04-113">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="20e04-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="20e04-114">Daha fazla bilgi için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="20e04-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="20e04-115">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="20e04-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="20e04-116">**Gelişmiş** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="20e04-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="20e04-117">**Aritmetik taşma** özelliği için Denetimi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20e04-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="20e04-118">Bu derleyici seçeneğine programlı <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>olarak erişmek için bkz.</span><span class="sxs-lookup"><span data-stu-id="20e04-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e04-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="20e04-119">Example</span></span>  
 <span data-ttu-id="20e04-120">Aşağıdaki komut derler. `t2.cs`</span><span class="sxs-lookup"><span data-stu-id="20e04-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="20e04-121">`-checked` Komutun kullanımı, dosyadaki bir `checked` veya `unchecked` anahtar kelime kapsamında olmayan herhangi bir tamsayı aritmetik deyiminin veri türünün kapsamı dışında bir değerle sonuçlandığını ve çalışma zamanında bir özel durum almasına neden olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="20e04-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="20e04-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20e04-122">See also</span></span>

- [<span data-ttu-id="20e04-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="20e04-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="20e04-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="20e04-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
