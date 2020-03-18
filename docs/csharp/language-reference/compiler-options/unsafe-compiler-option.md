---
title: -güvenli değil (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877989"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="618fe-102">-güvenli değil (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="618fe-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="618fe-103">**-güvenli olmayan** derleyici seçeneği derlemek için [güvenli olmayan](../keywords/unsafe.md) anahtar kelime kullanan kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="618fe-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="618fe-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="618fe-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="618fe-105">Remarks</span></span>

<span data-ttu-id="618fe-106">Güvenli olmayan kod hakkında daha fazla bilgi için [Güvenli Olmayan Kod ve İşaretçiler'e](../../programming-guide/unsafe-code-pointers/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="618fe-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="618fe-107">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="618fe-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="618fe-108">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="618fe-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="618fe-109">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="618fe-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="618fe-110">Güvenli **Olmayan Koda İzin Ver** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="618fe-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="618fe-111">Bu seçeneği bir csproj dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="618fe-111">To add this option in a csproj file</span></span>

<span data-ttu-id="618fe-112">Bir proje için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="618fe-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="618fe-113">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A></span><span class="sxs-lookup"><span data-stu-id="618fe-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="618fe-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="618fe-114">Example</span></span>

<span data-ttu-id="618fe-115">Güvenli `in.cs` olmayan mod için derleme:</span><span class="sxs-lookup"><span data-stu-id="618fe-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="618fe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618fe-116">See also</span></span>

- [<span data-ttu-id="618fe-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="618fe-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="618fe-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="618fe-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
