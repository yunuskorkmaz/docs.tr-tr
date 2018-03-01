---
title: "-filealign (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /filealign
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f00db0cfd191de060b67aee4618d99740cb81248
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="9c718-102">-filealign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9c718-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="9c718-103">**- Filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c718-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c718-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c718-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c718-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9c718-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="9c718-106">Çıktı dosyasında bölümlerin boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9c718-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="9c718-107">Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9c718-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="9c718-108">Bu değerler bayt cinsinden.</span><span class="sxs-lookup"><span data-stu-id="9c718-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c718-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c718-109">Remarks</span></span>  
 <span data-ttu-id="9c718-110">Her bölümü olan bir sınır ile hizalanır **- filealign** değeri.</span><span class="sxs-lookup"><span data-stu-id="9c718-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="9c718-111">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="9c718-111">There is no fixed default.</span></span> <span data-ttu-id="9c718-112">Varsa **- filealign** belirtilmezse, ortak dil çalışma zamanı derleme zamanında varsayılan seçer.</span><span class="sxs-lookup"><span data-stu-id="9c718-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="9c718-113">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkiler.</span><span class="sxs-lookup"><span data-stu-id="9c718-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="9c718-114">Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c718-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="9c718-115">Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için.</span><span class="sxs-lookup"><span data-stu-id="9c718-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9c718-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9c718-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="9c718-117">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="9c718-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="9c718-118">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="9c718-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="9c718-119">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9c718-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="9c718-120">Değiştirme **dosya hizalama** özelliği.</span><span class="sxs-lookup"><span data-stu-id="9c718-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="9c718-121">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c718-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c718-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c718-122">See Also</span></span>  
 [<span data-ttu-id="9c718-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9c718-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9c718-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="9c718-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
