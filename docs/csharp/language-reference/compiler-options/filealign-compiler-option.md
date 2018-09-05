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
ms.openlocfilehash: 39b5aeecba39c0e5377fd4f76902dae4b678c324
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530408"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="67de6-102">-filealign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="67de6-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="67de6-103">**- Filealign** seçeneği, çıkış dosyasında bölümlerin boyutunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="67de6-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67de6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67de6-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="67de6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="67de6-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="67de6-106">Çıkış dosyasına bölümlerin boyutunu belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="67de6-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="67de6-107">Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:.</span><span class="sxs-lookup"><span data-stu-id="67de6-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="67de6-108">Bu değerler bayt.</span><span class="sxs-lookup"><span data-stu-id="67de6-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67de6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67de6-109">Remarks</span></span>  
 <span data-ttu-id="67de6-110">Her bölümde katları olan bir sınır üzerinde hizalanır **- filealign** değeri.</span><span class="sxs-lookup"><span data-stu-id="67de6-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="67de6-111">Sabit varsayılan yok.</span><span class="sxs-lookup"><span data-stu-id="67de6-111">There is no fixed default.</span></span> <span data-ttu-id="67de6-112">Varsa **- filealign** belirtilmezse, ortak dil çalışma zamanı varsayılan derleme zamanında seçer.</span><span class="sxs-lookup"><span data-stu-id="67de6-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="67de6-113">Bölüm boyutu belirterek, çıkış dosyasının boyutu etkiler.</span><span class="sxs-lookup"><span data-stu-id="67de6-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="67de6-114">Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="67de6-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="67de6-115">Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) , çıkış dosyası bölümleri hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="67de6-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="67de6-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="67de6-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="67de6-117">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="67de6-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="67de6-118">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="67de6-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="67de6-119">Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="67de6-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="67de6-120">Değiştirme **dosya hizalama** özelliği.</span><span class="sxs-lookup"><span data-stu-id="67de6-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="67de6-121">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="67de6-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67de6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67de6-122">See Also</span></span>  

- [<span data-ttu-id="67de6-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="67de6-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="67de6-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="67de6-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
