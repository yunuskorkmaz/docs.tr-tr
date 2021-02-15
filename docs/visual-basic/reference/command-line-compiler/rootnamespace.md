---
description: :-RootNamespace hakkında daha fazla bilgi edinin
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 0e034999a65bf5294e63c8f9cec1a4ce4de39a4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474089"
---
# <a name="-rootnamespace"></a><span data-ttu-id="a883e-103">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="a883e-103">-rootnamespace</span></span>

<span data-ttu-id="a883e-104">Tüm tür bildirimleri için bir ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a883e-104">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a883e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a883e-105">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="a883e-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a883e-106">Arguments</span></span>  
  
|<span data-ttu-id="a883e-107">Terim</span><span class="sxs-lookup"><span data-stu-id="a883e-107">Term</span></span>|<span data-ttu-id="a883e-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="a883e-108">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="a883e-109">Geçerli proje için tüm tür bildirimlerinin içine alınacağı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="a883e-109">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a883e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a883e-110">Remarks</span></span>  

 <span data-ttu-id="a883e-111">Visual Studio tümleşik geliştirme ortamında oluşturulan bir projeyi derlemek için Visual Studio çalıştırılabilir dosyasını (Devenv.exe) kullanıyorsanız, `-rootnamespace` özelliğin değerini belirtmek için kullanın <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="a883e-111">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="a883e-112">Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) .</span><span class="sxs-lookup"><span data-stu-id="a883e-112">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="a883e-113">`Ildasm.exe`Çıkış dosyanızdaki ad alanı adlarını görüntülemek için ortak dil çalışma zamanı MSIL Disassembler () kullanın.</span><span class="sxs-lookup"><span data-stu-id="a883e-113">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="a883e-114">Visual Studio tümleşik geliştirme ortamında Set-RootNamespace</span><span class="sxs-lookup"><span data-stu-id="a883e-114">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a883e-115">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a883e-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a883e-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a883e-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="a883e-117">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a883e-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="a883e-118">3. **kök ad alanı** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a883e-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a883e-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a883e-119">Example</span></span>  

 <span data-ttu-id="a883e-120">Aşağıdaki kod, `In.vb` ad alanındaki tüm tür bildirimlerini derler ve içine alır `mynamespace` .</span><span class="sxs-lookup"><span data-stu-id="a883e-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a883e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a883e-121">See also</span></span>

- [<span data-ttu-id="a883e-122">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a883e-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a883e-123">Ildasm.exe (Il ayırıcı)</span><span class="sxs-lookup"><span data-stu-id="a883e-123">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="a883e-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a883e-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
