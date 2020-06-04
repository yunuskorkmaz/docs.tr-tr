---
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
ms.openlocfilehash: b6a2f3ba0772d8f8c8c6a762a1be01703d21b778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403141"
---
# <a name="-rootnamespace"></a><span data-ttu-id="7bb0c-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="7bb0c-102">-rootnamespace</span></span>
<span data-ttu-id="7bb0c-103">Tüm tür bildirimleri için bir ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb0c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7bb0c-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="7bb0c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7bb0c-105">Arguments</span></span>  
  
|<span data-ttu-id="7bb0c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7bb0c-106">Term</span></span>|<span data-ttu-id="7bb0c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7bb0c-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="7bb0c-108">Geçerli proje için tüm tür bildirimlerinin içine alınacağı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb0c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bb0c-109">Remarks</span></span>  
 <span data-ttu-id="7bb0c-110">Visual Studio tümleşik geliştirme ortamında oluşturulan bir projeyi derlemek için Visual Studio yürütülebilir dosyası (devenv. exe) kullanırsanız, `-rootnamespace` özelliğinin değerini belirtmek için kullanın <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="7bb0c-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="7bb0c-111">Daha fazla bilgi için bkz. [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) .</span><span class="sxs-lookup"><span data-stu-id="7bb0c-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="7bb0c-112">`Ildasm.exe`Çıkış dosyanızdaki ad alanı adlarını görüntülemek için ortak dil çalışma zamanı MSIL Disassembler () kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="7bb0c-113">Visual Studio tümleşik geliştirme ortamında Set-RootNamespace</span><span class="sxs-lookup"><span data-stu-id="7bb0c-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7bb0c-114">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7bb0c-115">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7bb0c-116">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="7bb0c-117">3. **kök ad alanı** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7bb0c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bb0c-118">Example</span></span>  
 <span data-ttu-id="7bb0c-119">Aşağıdaki kod, `In.vb` ad alanındaki tüm tür bildirimlerini derler ve içine alır `mynamespace` .</span><span class="sxs-lookup"><span data-stu-id="7bb0c-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bb0c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb0c-120">See also</span></span>

- [<span data-ttu-id="7bb0c-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7bb0c-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7bb0c-122">Ildadsm. exe (Il ayırıcı)</span><span class="sxs-lookup"><span data-stu-id="7bb0c-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="7bb0c-123">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7bb0c-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
