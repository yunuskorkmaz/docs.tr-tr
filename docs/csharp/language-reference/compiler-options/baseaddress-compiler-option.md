---
description: -BaseAddress (C# derleyici seçenekleri)
title: -BaseAddress (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 17bca4f03c75f7d617e4e99ebab4d1602bb3214e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537255"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="a7f50-103">-BaseAddress (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a7f50-103">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="a7f50-104">**-BaseAddress** SEÇENEĞI, dll 'nin yükleneceği tercih edilen temel adresi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7f50-104">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="a7f50-105">Bu seçeneğin ne zaman ve neden kullanıldığı hakkında daha fazla bilgi için bkz. [Larry Osterman 'ın Web günlüğü](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="a7f50-105">For more information about when and why to use this option, see [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f50-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7f50-106">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7f50-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a7f50-107">Arguments</span></span>  
 `address`  
 <span data-ttu-id="a7f50-108">DLL 'nin temel adresi.</span><span class="sxs-lookup"><span data-stu-id="a7f50-108">The base address for the DLL.</span></span> <span data-ttu-id="a7f50-109">Bu adres ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7f50-109">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7f50-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f50-110">Remarks</span></span>  
 <span data-ttu-id="a7f50-111">Bir DLL için varsayılan temel adres, .NET ortak dil çalışma zamanı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a7f50-111">The default base address for a DLL is set by the .NET common language runtime.</span></span>  
  
 <span data-ttu-id="a7f50-112">Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a7f50-112">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="a7f50-113">Örneğin, 0x11110001 belirtirseniz, 0x11110000 ' ya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="a7f50-113">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="a7f50-114">DLL imzalama işlemini gerçekleştirmek için,-R seçeneğiyle SN.EXE kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7f50-114">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a7f50-115">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a7f50-115">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a7f50-116">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="a7f50-116">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a7f50-117">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a7f50-117">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a7f50-118">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a7f50-118">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="a7f50-119">**Dll taban adresi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a7f50-119">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="a7f50-120">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A> ..</span><span class="sxs-lookup"><span data-stu-id="a7f50-120">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f50-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f50-121">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a7f50-122">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a7f50-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a7f50-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a7f50-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
