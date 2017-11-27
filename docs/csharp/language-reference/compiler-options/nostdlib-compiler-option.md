---
title: "-nostdlib (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad3ca7775512623de43c7fe6b7fe1cf481ccca87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="nostdlib-c-compiler-options"></a><span data-ttu-id="c7dce-102">/nostdlib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c7dce-102">/nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="c7dce-103">**/ nostdlib** tüm sistem ad alanını tanımlayan mscorlib.dll alma engeller.</span><span class="sxs-lookup"><span data-stu-id="c7dce-103">**/nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7dce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7dce-104">Syntax</span></span>  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7dce-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7dce-105">Remarks</span></span>  
 <span data-ttu-id="c7dce-106">Tanımlayın veya kendi sistem ad alanı ve nesneleri oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7dce-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="c7dce-107">Belirtmezseniz, **/nostdlib**, mscorlib.dll programınıza içeri aktarılacak (belirtme aynı **/nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="c7dce-107">If you do not specify **/nostdlib**, mscorlib.dll will be imported into your program (same as specifying **/nostdlib-**).</span></span> <span data-ttu-id="c7dce-108">Belirtme **/nostdlib** belirtme aynı **/nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="c7dce-108">Specifying **/nostdlib** is the same as specifying **/nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c7dce-109">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c7dce-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c7dce-110">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="c7dce-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="c7dce-111">Tıklatın **yapı** Özellikler sayfası.</span><span class="sxs-lookup"><span data-stu-id="c7dce-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="c7dce-112">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c7dce-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="c7dce-113">Değiştirme **mscorlib.dll başvurmadığından** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7dce-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="c7dce-114">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7dce-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7dce-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7dce-115">See Also</span></span>  
 [<span data-ttu-id="c7dce-116">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c7dce-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
