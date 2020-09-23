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
ms.openlocfilehash: d146f5967058b05795026cd7726ed5eda7ba3153
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095414"
---
# <a name="-win32resource"></a><span data-ttu-id="0e800-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="0e800-102">-win32resource</span></span>

<span data-ttu-id="0e800-103">Çıktı dosyasına bir Win32 kaynak dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="0e800-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e800-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e800-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e800-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="0e800-105">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="0e800-106">Çıkış dosyanıza eklenecek kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="0e800-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="0e800-107">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="0e800-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e800-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e800-108">Remarks</span></span>  

 <span data-ttu-id="0e800-109">Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e800-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="0e800-110">Win32 kaynağı, uygulamanızın **Dosya Gezgini**'nde tanımlanmasına yardımcı olan sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0e800-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="0e800-111">Belirtmezseniz `-win32resource` , derleyici derleme sürümüne göre sürüm bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e800-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="0e800-112">`-win32resource`Ve `-win32icon` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="0e800-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0e800-113">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](resource.md) .</span><span class="sxs-lookup"><span data-stu-id="0e800-113">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e800-114">`-win32resource`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e800-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e800-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e800-115">Example</span></span>  

 <span data-ttu-id="0e800-116">Aşağıdaki kod `In.vb` , bir Win32 kaynak dosyasını derler ve iliştirir `Rf.res` :</span><span class="sxs-lookup"><span data-stu-id="0e800-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e800-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e800-117">See also</span></span>

- [<span data-ttu-id="0e800-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="0e800-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0e800-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="0e800-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
