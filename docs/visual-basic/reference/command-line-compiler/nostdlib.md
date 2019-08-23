---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964358"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="56f4b-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56f4b-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="56f4b-103">Derleyicinin standart kitaplıklara otomatik olarak başvurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="56f4b-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56f4b-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="56f4b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56f4b-105">Remarks</span></span>  
 <span data-ttu-id="56f4b-106">`-nostdlib` Seçeneği, System. dll derlemesine otomatik başvuruyu kaldırır ve derleyicinin Vbc. rsp dosyasını okumasını önler.</span><span class="sxs-lookup"><span data-stu-id="56f4b-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="56f4b-107">Vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="56f4b-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56f4b-108">Mscorlib. dll ve Microsoft. VisualBasic. dll derlemelerine her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="56f4b-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56f4b-109">Bu `-nostdlib` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56f4b-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56f4b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="56f4b-110">Example</span></span>  
 <span data-ttu-id="56f4b-111">Aşağıdaki kod standart kitaplıklara `T2.vb` başvurulmadan derlenir.</span><span class="sxs-lookup"><span data-stu-id="56f4b-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="56f4b-112">Nesneyi kaldırmak için `_MYTYPE` koşullu derleme sabitinin "Empty" dizesini ayarlamanız gerekir. `My`</span><span class="sxs-lookup"><span data-stu-id="56f4b-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="56f4b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56f4b-113">See also</span></span>

- [<span data-ttu-id="56f4b-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="56f4b-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="56f4b-115">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="56f4b-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="56f4b-116">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="56f4b-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="56f4b-117">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="56f4b-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
