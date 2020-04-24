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
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004966"
---
# <a name="-win32resource"></a><span data-ttu-id="78a3f-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="78a3f-102">-win32resource</span></span>
<span data-ttu-id="78a3f-103">Çıktı dosyasına bir Win32 kaynak dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="78a3f-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78a3f-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="78a3f-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="78a3f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="78a3f-106">Çıkış dosyanıza eklenecek kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="78a3f-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="78a3f-107">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="78a3f-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78a3f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78a3f-108">Remarks</span></span>  
 <span data-ttu-id="78a3f-109">Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78a3f-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="78a3f-110">Win32 kaynağı, uygulamanızın **Dosya Gezgini**'nde tanımlanmasına yardımcı olan sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="78a3f-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="78a3f-111">Belirtmezseniz `-win32resource`, derleyici derleme sürümüne göre sürüm bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78a3f-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="78a3f-112">`-win32resource` Ve `-win32icon` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="78a3f-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="78a3f-113">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) .</span><span class="sxs-lookup"><span data-stu-id="78a3f-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78a3f-114">Bu `-win32resource` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78a3f-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a3f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="78a3f-115">Example</span></span>  
 <span data-ttu-id="78a3f-116">Aşağıdaki kod, `Rf.res`bir `In.vb` Win32 kaynak dosyasını derler ve iliştirir:</span><span class="sxs-lookup"><span data-stu-id="78a3f-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="78a3f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78a3f-117">See also</span></span>

- [<span data-ttu-id="78a3f-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="78a3f-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="78a3f-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="78a3f-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
