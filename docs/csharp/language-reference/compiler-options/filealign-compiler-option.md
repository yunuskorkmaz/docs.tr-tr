---
description: -filealign (C# derleyici seçenekleri)
title: -filealign (C# derleyici seçenekleri)
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
ms.openlocfilehash: d4abe6c3825de211d737f402a745c8953adca4b8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125715"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="f8eba-103">-filealign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f8eba-103">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="f8eba-104">**-Filealign** seçeneği, çıkış dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8eba-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8eba-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f8eba-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8eba-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f8eba-106">Arguments</span></span>  
 `number`  
 <span data-ttu-id="f8eba-107">Çıkış dosyasındaki bölümlerin boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f8eba-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="f8eba-108">Geçerli değerler 512, 1024, 2048, 4096 ve 8192.</span><span class="sxs-lookup"><span data-stu-id="f8eba-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="f8eba-109">Bu değerler baytlardır.</span><span class="sxs-lookup"><span data-stu-id="f8eba-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8eba-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8eba-110">Remarks</span></span>  
 <span data-ttu-id="f8eba-111">Her bölüm, **-filealign** değerinin katı olan bir sınıra göre hizalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f8eba-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="f8eba-112">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="f8eba-112">There is no fixed default.</span></span> <span data-ttu-id="f8eba-113">**-Filealign** belirtilmemişse, ortak dil çalışma zamanı derleme zamanında bir varsayılan değer seçer.</span><span class="sxs-lookup"><span data-stu-id="f8eba-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="f8eba-114">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkilersiniz.</span><span class="sxs-lookup"><span data-stu-id="f8eba-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="f8eba-115">Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8eba-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="f8eba-116">Çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için [dumpbin](/cpp/build/reference/dumpbin-options) ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8eba-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f8eba-117">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f8eba-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f8eba-118">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="f8eba-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f8eba-119">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8eba-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="f8eba-120">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8eba-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="f8eba-121">**Dosya hizalama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8eba-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="f8eba-122">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A> ..</span><span class="sxs-lookup"><span data-stu-id="f8eba-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8eba-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8eba-123">See also</span></span>

- [<span data-ttu-id="f8eba-124">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f8eba-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f8eba-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="f8eba-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
