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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603015"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="6f06f-102">-filealign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6f06f-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="6f06f-103">**-filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f06f-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f06f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f06f-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f06f-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6f06f-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="6f06f-106">Çıktı dosyasındaki bölümlerin boyutunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6f06f-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="6f06f-107">Geçerli değerler 512, 1024, 2048, 4096 ve 8192'dir.</span><span class="sxs-lookup"><span data-stu-id="6f06f-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="6f06f-108">Bu değerler baytlardadır.</span><span class="sxs-lookup"><span data-stu-id="6f06f-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f06f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f06f-109">Remarks</span></span>  
 <span data-ttu-id="6f06f-110">Her bölüm **-filealign** değerinin katları olan bir sınır üzerinde hizalanır.</span><span class="sxs-lookup"><span data-stu-id="6f06f-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="6f06f-111">Sabit bir varsayılan yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f06f-111">There is no fixed default.</span></span> <span data-ttu-id="6f06f-112">**-filealign** belirtilmemişse, ortak dil çalışma zamanı derleme zamanında varsayılan ı seçer.</span><span class="sxs-lookup"><span data-stu-id="6f06f-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="6f06f-113">Bölüm boyutunu belirterek, çıktı dosyasının boyutunu etkilersiniz.</span><span class="sxs-lookup"><span data-stu-id="6f06f-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="6f06f-114">Bölüm boyutunu değiştirmek, daha küçük aygıtlarda çalışacak programlar için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f06f-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="6f06f-115">Çıktı dosyanızdaki bölümlerle ilgili bilgileri görmek için [DUMPBIN'i](/cpp/build/reference/dumpbin-options) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f06f-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6f06f-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6f06f-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6f06f-117">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="6f06f-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6f06f-118">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6f06f-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6f06f-119">**Gelişmiş** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6f06f-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="6f06f-120">Dosya **Hizalama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6f06f-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="6f06f-121">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A></span><span class="sxs-lookup"><span data-stu-id="6f06f-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f06f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f06f-122">See also</span></span>

- [<span data-ttu-id="6f06f-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6f06f-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6f06f-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6f06f-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
