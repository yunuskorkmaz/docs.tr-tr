---
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603015"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="f6dbd-102">-filealign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f6dbd-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="f6dbd-103">**-Filealign** seçeneği, çıkış dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6dbd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6dbd-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6dbd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6dbd-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="f6dbd-106">Çıkış dosyasındaki bölümlerin boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="f6dbd-107">Geçerli değerler 512, 1024, 2048, 4096 ve 8192.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="f6dbd-108">Bu değerler baytlardır.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6dbd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6dbd-109">Remarks</span></span>  
 <span data-ttu-id="f6dbd-110">Her bölüm, **-filealign** değerinin katı olan bir sınıra göre hizalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="f6dbd-111">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-111">There is no fixed default.</span></span> <span data-ttu-id="f6dbd-112">**-Filealign** belirtilmemişse, ortak dil çalışma zamanı derleme zamanında bir varsayılan değer seçer.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="f6dbd-113">Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkilersiniz.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="f6dbd-114">Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="f6dbd-115">Çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için [dumpbin](/cpp/build/reference/dumpbin-options) ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f6dbd-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f6dbd-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f6dbd-117">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f6dbd-118">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="f6dbd-119">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="f6dbd-120">**Dosya hizalama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="f6dbd-121">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6dbd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6dbd-122">See also</span></span>

- [<span data-ttu-id="f6dbd-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f6dbd-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f6dbd-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="f6dbd-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
