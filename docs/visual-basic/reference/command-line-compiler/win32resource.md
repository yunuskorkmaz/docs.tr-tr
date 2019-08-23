---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961297"
---
# <a name="-win32resource"></a><span data-ttu-id="16600-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="16600-102">-win32resource</span></span>
<span data-ttu-id="16600-103">Çıktı dosyasına bir Win32 kaynak dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="16600-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16600-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16600-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="16600-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="16600-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="16600-106">Çıkış dosyanıza eklenecek kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="16600-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="16600-107">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="16600-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16600-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16600-108">Remarks</span></span>  
 <span data-ttu-id="16600-109">Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16600-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="16600-110">Win32 kaynağı, uygulamanızın **Dosya Gezgini**'nde tanımlanmasına yardımcı olan sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="16600-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="16600-111">Belirtmezseniz `-win32resource`, derleyici derleme sürümüne göre sürüm bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16600-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="16600-112">`-win32resource` Ve`-win32icon` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="16600-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="16600-113">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) .</span><span class="sxs-lookup"><span data-stu-id="16600-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16600-114">Bu `-win32resource` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16600-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16600-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="16600-115">Example</span></span>  
 <span data-ttu-id="16600-116">Aşağıdaki kod, `Rf.res`bir `In.vb` Win32 kaynak dosyasını derler ve iliştirir:</span><span class="sxs-lookup"><span data-stu-id="16600-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="16600-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16600-117">See also</span></span>

- [<span data-ttu-id="16600-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="16600-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="16600-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="16600-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
