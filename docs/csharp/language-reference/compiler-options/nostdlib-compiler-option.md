---
title: "-nostdlib (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dd9d2b6a4a9c774aa339e840ad0020ee39cb10d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="c9ecb-102">-nostdlib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c9ecb-102">-nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="c9ecb-103">**-nostdlib** tüm sistem ad alanını tanımlayan mscorlib.dll alma engeller.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ecb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9ecb-104">Syntax</span></span>  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9ecb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9ecb-105">Remarks</span></span>  
 <span data-ttu-id="c9ecb-106">Tanımlayın veya kendi sistem ad alanı ve nesneleri oluşturmak istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="c9ecb-107">Belirtmezseniz, **- nostdlib**, mscorlib.dll programınıza içeri aktarılacak (belirtme aynı **- nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="c9ecb-107">If you do not specify **-nostdlib**, mscorlib.dll will be imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="c9ecb-108">Belirtme **- nostdlib** belirtme aynı **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c9ecb-109">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c9ecb-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c9ecb-110">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="c9ecb-111">Tıklatın **yapı** Özellikler sayfası.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="c9ecb-112">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="c9ecb-113">Değiştirme **mscorlib.dll başvurmadığından** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="c9ecb-114">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ecb-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ecb-115">See Also</span></span>  
 [<span data-ttu-id="c9ecb-116">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c9ecb-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
