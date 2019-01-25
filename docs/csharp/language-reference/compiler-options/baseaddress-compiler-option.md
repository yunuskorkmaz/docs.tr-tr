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
ms.openlocfilehash: 6ff29a7a204cb8f20f2f67946d5d1ed9c976e7aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694587"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="b7540-102">-baseaddress (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b7540-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="b7540-103">**- Baseaddress** seçeneği bir DLL yüklemek için tercih edilen temel adresini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7540-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="b7540-104">Bu seçeneği kullanmak neden ve ne zaman hakkında daha fazla bilgi için bkz: [Larry Osterman'ın blog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="b7540-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7540-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7540-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7540-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7540-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="b7540-107">DLL için temel adres.</span><span class="sxs-lookup"><span data-stu-id="b7540-107">The base address for the DLL.</span></span> <span data-ttu-id="b7540-108">Bu adres, ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b7540-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7540-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7540-109">Remarks</span></span>  
 <span data-ttu-id="b7540-110">Bir DLL için varsayılan taban adresi, .NET Framework ortak dil çalışma zamanı tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b7540-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="b7540-111">Bu adres alt sıra Word'de yuvarlanacağı dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b7540-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="b7540-112">Örneğin, 0x11110001 belirtirseniz 0x11110000 için yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="b7540-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="b7540-113">Bir DLL için imzalama işlemini tamamlamak için SN kullanın. EXE -R seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b7540-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b7540-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b7540-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="b7540-115">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="b7540-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="b7540-116">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="b7540-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="b7540-117">Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b7540-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="b7540-118">Değiştirme **DLL temel adresi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="b7540-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="b7540-119">Bu derleyici seçeneğini program üzerinden ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="b7540-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7540-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7540-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b7540-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b7540-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="b7540-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b7540-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
