---
title: -Checked (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606993"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="12a97-102">-Checked (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="12a97-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="12a97-103">**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="12a97-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12a97-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="12a97-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12a97-105">Remarks</span></span>  
 <span data-ttu-id="12a97-106">`checked` Or`unchecked` anahtar sözcüğünün kapsamındaki bir tamsayı aritmetik bildirim, **-Checked** seçeneğinin etkisine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="12a97-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="12a97-107">`checked` Or`unchecked` anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik ifade, veri türü aralığı dışında bir değer ile sonuçlanır ve **-Checked +** (veya **-Checked**) derlemede kullanılırsa, bu ifade bir çalışma zamanında özel durum.</span><span class="sxs-lookup"><span data-stu-id="12a97-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="12a97-108">**-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="12a97-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="12a97-109">Bu seçenek için varsayılan değer **-denetlenir-** ; taşma denetimi devre dışı.</span><span class="sxs-lookup"><span data-stu-id="12a97-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="12a97-110">Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12a97-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="12a97-111">' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12a97-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="12a97-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="12a97-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="12a97-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="12a97-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="12a97-114">Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="12a97-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="12a97-115">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="12a97-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="12a97-116">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="12a97-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="12a97-117">**Aritmetik taşma/yetersiz** yer özelliğinin denetimini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12a97-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="12a97-118">Bu derleyici seçeneğine program aracılığıyla erişmek için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a97-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12a97-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="12a97-119">Example</span></span>  
 <span data-ttu-id="12a97-120">Aşağıdaki komut derlenir `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="12a97-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="12a97-121">Komutunda öğesinin `-checked` kullanımı, bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan dosyada herhangi bir tamsayı aritmetik deyimin olduğunu ve veri türü aralığının dışında bir değer oluşmasına neden olduğunu belirtir ışınızda.</span><span class="sxs-lookup"><span data-stu-id="12a97-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="12a97-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12a97-122">See also</span></span>

- [<span data-ttu-id="12a97-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="12a97-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="12a97-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="12a97-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
