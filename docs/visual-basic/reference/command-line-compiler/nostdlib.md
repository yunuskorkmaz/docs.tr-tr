---
description: :-Nostdlib hakkında daha fazla bilgi edinin (Visual Basic)
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4a00ad21bc0038a6bf42f1dd6943ccc15c1a8abb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434881"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="bbb2e-103">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbb2e-103">-nostdlib (Visual Basic)</span></span>

<span data-ttu-id="bbb2e-104">Derleyicinin standart kitaplıklara otomatik olarak başvurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-104">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb2e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbb2e-105">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="bbb2e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbb2e-106">Remarks</span></span>  

 <span data-ttu-id="bbb2e-107">`-nostdlib`Seçeneği System.dll derlemesine otomatik başvuruyu kaldırır ve derleyicinin Vbc. rsp dosyasını okumasını önler.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-107">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="bbb2e-108">Vbc.exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-108">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbb2e-109">Mscorlib.dll ve Microsoft.VisualBasic.dll derlemelerine her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-109">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbb2e-110">`-nostdlib`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-110">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb2e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbb2e-111">Example</span></span>  

 <span data-ttu-id="bbb2e-112">Aşağıdaki kod `T2.vb` Standart kitaplıklara başvurulmadan derlenir.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-112">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="bbb2e-113">`_MYTYPE`Nesneyi kaldırmak için koşullu derleme sabitinin "Empty" dizesini ayarlamanız gerekir `My` .</span><span class="sxs-lookup"><span data-stu-id="bbb2e-113">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbb2e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb2e-114">See also</span></span>

- [<span data-ttu-id="bbb2e-115">-noconfig</span><span class="sxs-lookup"><span data-stu-id="bbb2e-115">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="bbb2e-116">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bbb2e-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bbb2e-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bbb2e-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="bbb2e-118">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bbb2e-118">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
