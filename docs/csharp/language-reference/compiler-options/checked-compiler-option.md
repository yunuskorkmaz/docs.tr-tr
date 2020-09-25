---
description: -Checked (C# derleyici seçenekleri)
title: -Checked (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: c92ad61b2f482631230e0e6aeb0af5716a4fcb61
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196838"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="1833b-103">-Checked (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1833b-103">-checked (C# Compiler Options)</span></span>

<span data-ttu-id="1833b-104">**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1833b-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1833b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1833b-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="1833b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1833b-106">Remarks</span></span>  

 <span data-ttu-id="1833b-107">Or anahtar sözcüğünün kapsamındaki bir tamsayı aritmetik bildirim, `checked` `unchecked` **-Checked** seçeneğinin etkisine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="1833b-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="1833b-108">Bir veya anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik ifade, `checked` `unchecked` veri türü aralığı dışındaki bir değer ile sonuçlanır ve **-Checked +** (veya **-Checked**) derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="1833b-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="1833b-109">**-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="1833b-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="1833b-110">Bu seçenek için varsayılan değer **-denetlenir-**; taşma denetimi devre dışı.</span><span class="sxs-lookup"><span data-stu-id="1833b-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="1833b-111">Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1833b-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="1833b-112">' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1833b-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1833b-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1833b-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1833b-114">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="1833b-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="1833b-115">Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="1833b-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="1833b-116">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1833b-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="1833b-117">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1833b-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="1833b-118">**Aritmetik taşma Için denetimi** değiştirin özelliği.</span><span class="sxs-lookup"><span data-stu-id="1833b-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="1833b-119">Bu derleyici seçeneğine program aracılığıyla erişmek için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> ..</span><span class="sxs-lookup"><span data-stu-id="1833b-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1833b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1833b-120">Example</span></span>  

 <span data-ttu-id="1833b-121">Aşağıdaki komut derlenir `t2.cs` .</span><span class="sxs-lookup"><span data-stu-id="1833b-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="1833b-122">Komutunda öğesinin kullanımı `-checked` , bir veya anahtar sözcüğünün kapsamında olmayan, dosyadaki tüm tamsayı aritmetik deyimlerine `checked` `unchecked` ve veri türü aralığının dışında bir değer oluşmasına neden olur, çalışma zamanında bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="1833b-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="1833b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1833b-123">See also</span></span>

- [<span data-ttu-id="1833b-124">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1833b-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1833b-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1833b-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
