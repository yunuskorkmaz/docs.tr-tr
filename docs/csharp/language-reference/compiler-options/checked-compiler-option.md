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
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239698"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="fc5ef-102">-Checked (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fc5ef-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="fc5ef-103">**-Checked** seçeneği, veri türü aralığının dışında olan ve [denetlenen](../keywords/checked.md) veya [işaretlenmemiş](../keywords/unchecked.md) bir anahtar sözcüğünün kapsamında olmayan bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin bir çalışma zamanı özel durumuna neden olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc5ef-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="fc5ef-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc5ef-105">Remarks</span></span>  
 <span data-ttu-id="fc5ef-106">Bir `checked` veya `unchecked` anahtar sözcüğünün kapsamındaki tamsayı aritmetik bir ifade, **-Checked** seçeneğinin etkisine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="fc5ef-107">Bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik bildirim, derlemede bir değer ve **-Checked +** (veya **-Checked**) kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="fc5ef-108">**-Checked-** derlemede kullanılırsa, bu ifade çalışma zamanında bir özel duruma neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="fc5ef-109">Bu seçenek için varsayılan değer **-denetlenir-** ; taşma denetimi devre dışı.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="fc5ef-110">Bazen, büyük uygulamalar oluşturmak için kullanılan otomatikleştirilmiş araçlar + ' a ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="fc5ef-111">' In kullanılmasına yönelik bir senaryo,-Checked-belirterek aracın genel varsayılanını geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fc5ef-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fc5ef-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="fc5ef-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="fc5ef-114">Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="fc5ef-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="fc5ef-115">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="fc5ef-116">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="fc5ef-117">**Aritmetik taşma Için denetimi** değiştirin özelliği.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="fc5ef-118">Bu derleyici seçeneğine program aracılığıyla erişmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc5ef-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc5ef-119">Example</span></span>  
 <span data-ttu-id="fc5ef-120">Aşağıdaki komut `t2.cs`derler.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="fc5ef-121">Komutunda `-checked` kullanımı, dosyasında bir `checked` veya `unchecked` anahtar sözcüğünün kapsamında olmayan herhangi bir tamsayı aritmetik deyimin olduğunu ve veri türünün aralığı dışında bir değer oluşmasına neden olur, çalışma zamanında bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc5ef-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc5ef-122">See also</span></span>

- [<span data-ttu-id="fc5ef-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fc5ef-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fc5ef-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="fc5ef-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
