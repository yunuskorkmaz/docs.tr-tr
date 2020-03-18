---
title: -baseaddress (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937206"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="56426-102">-baseaddress (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="56426-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="56426-103">**-baseaddress** seçeneği, DLL yüklemek için tercih edilen temel adresi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56426-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="56426-104">Bu seçeneğin ne zaman ve neden kullanılacağı hakkında daha fazla bilgi için [Larry Osterman'ın WebGünlüğü'ne](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)bakın.</span><span class="sxs-lookup"><span data-stu-id="56426-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56426-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56426-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="56426-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="56426-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="56426-107">DLL'nin temel adresi.</span><span class="sxs-lookup"><span data-stu-id="56426-107">The base address for the DLL.</span></span> <span data-ttu-id="56426-108">Bu adres ondalık, hexadecimal veya oksal sayı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="56426-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56426-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56426-109">Remarks</span></span>  
 <span data-ttu-id="56426-110">Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma süresi tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="56426-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="56426-111">Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="56426-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="56426-112">Örneğin, 0x111100001 belirtirseniz, 0x11110000 yuvarlatılır.</span><span class="sxs-lookup"><span data-stu-id="56426-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="56426-113">Bir DLL için imzalama işlemini tamamlamak için SN kullanın. -R seçeneği ile EXE.</span><span class="sxs-lookup"><span data-stu-id="56426-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="56426-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="56426-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="56426-115">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="56426-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="56426-116">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="56426-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="56426-117">**Gelişmiş** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="56426-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="56426-118">**DLL Temel Adres** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="56426-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="56426-119">Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>ayarlamak için bkz.</span><span class="sxs-lookup"><span data-stu-id="56426-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56426-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56426-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="56426-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="56426-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="56426-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="56426-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
