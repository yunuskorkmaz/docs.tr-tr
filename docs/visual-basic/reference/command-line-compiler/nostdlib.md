---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 1c3c70b24de5163ca004b41a21017205a19d9730
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583369"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="c71ef-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c71ef-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="c71ef-103">Standart kitaplıkları otomatik olarak başvuruda bulunmamaya derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="c71ef-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c71ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c71ef-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="c71ef-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c71ef-105">Remarks</span></span>  
 <span data-ttu-id="c71ef-106">`-nostdlib` Seçeneği System.dll derleme otomatik başvuruyu kaldırır ve derleyici nezahrnovat dosyayı okumasını önler.</span><span class="sxs-lookup"><span data-stu-id="c71ef-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="c71ef-107">Vbc.exe dosyasıyla aynı dizinde bulunan nezahrnovat dosyasını yaygın olarak kullanılan .NET Framework derlemeleri atıfta bulunan ve içeri aktarır `System` ve `Microsoft.VisualBasic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="c71ef-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c71ef-108">Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin derlemeler her zaman başvurulur.</span><span class="sxs-lookup"><span data-stu-id="c71ef-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c71ef-109">`-nostdlib` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c71ef-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71ef-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c71ef-110">Example</span></span>  
 <span data-ttu-id="c71ef-111">Aşağıdaki kod derlenir `T2.vb` standart kitaplıklarına başvuruda bulunan olmadan.</span><span class="sxs-lookup"><span data-stu-id="c71ef-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="c71ef-112">Ayarlamalısınız `_MYTYPE` koşullu derleme sabiti'kaldırmak için "boş" dizeye `My` nesne.</span><span class="sxs-lookup"><span data-stu-id="c71ef-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c71ef-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c71ef-113">See also</span></span>

- [<span data-ttu-id="c71ef-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="c71ef-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="c71ef-115">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c71ef-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c71ef-116">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c71ef-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c71ef-117">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c71ef-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
