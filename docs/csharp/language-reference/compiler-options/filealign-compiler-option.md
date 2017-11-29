---
title: "-filealign (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe2d1df6d88baa2957068514abe728f29cb74636
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="filealign-c-compiler-options"></a><span data-ttu-id="ae942-102">/filealign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ae942-102">/filealign (C# Compiler Options)</span></span>
<span data-ttu-id="ae942-103">**/Filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae942-103">The **/filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae942-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae942-104">Syntax</span></span>  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae942-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae942-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="ae942-106">Çıktı dosyasında bölümlerin boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ae942-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="ae942-107">Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ae942-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="ae942-108">Bu değerler bayt cinsinden.</span><span class="sxs-lookup"><span data-stu-id="ae942-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae942-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae942-109">Remarks</span></span>  
 <span data-ttu-id="ae942-110">Her bölümü olan bir sınır ile hizalanır **/filealign** değeri.</span><span class="sxs-lookup"><span data-stu-id="ae942-110">Each section will be aligned on a boundary that is a multiple of the **/filealign** value.</span></span> <span data-ttu-id="ae942-111">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="ae942-111">There is no fixed default.</span></span> <span data-ttu-id="ae942-112">Varsa **/filealign** belirtilmezse, ortak dil çalışma zamanı derleme zamanında varsayılan seçer.</span><span class="sxs-lookup"><span data-stu-id="ae942-112">If **/filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="ae942-113">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkiler.</span><span class="sxs-lookup"><span data-stu-id="ae942-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="ae942-114">Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae942-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="ae942-115">Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için.</span><span class="sxs-lookup"><span data-stu-id="ae942-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ae942-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ae942-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ae942-117">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="ae942-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ae942-118">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="ae942-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ae942-119">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ae942-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="ae942-120">Değiştirme **dosya hizalama** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae942-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="ae942-121">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae942-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae942-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae942-122">See Also</span></span>  
 [<span data-ttu-id="ae942-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ae942-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ae942-124">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="ae942-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
