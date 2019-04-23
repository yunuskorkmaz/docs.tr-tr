---
title: -filealign (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
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
ms.openlocfilehash: f3ce1bb864c4cb0b1c330de7d96649f9870231e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328705"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="6ea85-102">-filealign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6ea85-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="6ea85-103">**- Filealign** seçeneği, çıkış dosyasında bölümlerin boyutunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ea85-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ea85-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ea85-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ea85-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="6ea85-106">Çıkış dosyasına bölümlerin boyutunu belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="6ea85-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="6ea85-107">Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:.</span><span class="sxs-lookup"><span data-stu-id="6ea85-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="6ea85-108">Bu değerler bayt.</span><span class="sxs-lookup"><span data-stu-id="6ea85-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ea85-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ea85-109">Remarks</span></span>  
 <span data-ttu-id="6ea85-110">Her bölümde katları olan bir sınır üzerinde hizalanır **- filealign** değeri.</span><span class="sxs-lookup"><span data-stu-id="6ea85-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="6ea85-111">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="6ea85-111">There is no fixed default.</span></span> <span data-ttu-id="6ea85-112">Varsa **- filealign** belirtilmezse, ortak dil çalışma zamanı varsayılan derleme zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="6ea85-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="6ea85-113">Bölüm boyutu belirterek, çıkış dosyasının boyutu etkiler.</span><span class="sxs-lookup"><span data-stu-id="6ea85-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="6ea85-114">Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ea85-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="6ea85-115">Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) , çıkış dosyası bölümleri hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6ea85-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6ea85-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6ea85-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6ea85-117">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="6ea85-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6ea85-118">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="6ea85-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6ea85-119">Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6ea85-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="6ea85-120">Değiştirme **dosya hizalama** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ea85-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="6ea85-121">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="6ea85-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea85-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea85-122">See also</span></span>

- [<span data-ttu-id="6ea85-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6ea85-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="6ea85-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6ea85-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
