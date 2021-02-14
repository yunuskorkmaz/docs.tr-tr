---
description: Hakkında daha fazla bilgi edinin:-Win32Resource
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
ms.openlocfilehash: a6f14fd2eb1349940c1e208a5baaa4205647f666
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433490"
---
# <a name="-win32resource"></a><span data-ttu-id="45c3a-103">-win32resource</span><span class="sxs-lookup"><span data-stu-id="45c3a-103">-win32resource</span></span>

<span data-ttu-id="45c3a-104">Çıktı dosyasına bir Win32 kaynak dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="45c3a-104">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c3a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="45c3a-105">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="45c3a-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="45c3a-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="45c3a-107">Çıkış dosyanıza eklenecek kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="45c3a-107">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="45c3a-108">Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="45c3a-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45c3a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45c3a-109">Remarks</span></span>  

 <span data-ttu-id="45c3a-110">Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45c3a-110">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="45c3a-111">Win32 kaynağı, uygulamanızın **Dosya Gezgini**'nde tanımlanmasına yardımcı olan sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="45c3a-111">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="45c3a-112">Belirtmezseniz `-win32resource` , derleyici derleme sürümüne göre sürüm bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45c3a-112">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="45c3a-113">`-win32resource`Ve `-win32icon` seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="45c3a-113">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="45c3a-114">Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](resource.md) .</span><span class="sxs-lookup"><span data-stu-id="45c3a-114">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45c3a-115">`-win32resource`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45c3a-115">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c3a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="45c3a-116">Example</span></span>  

 <span data-ttu-id="45c3a-117">Aşağıdaki kod `In.vb` , bir Win32 kaynak dosyasını derler ve iliştirir `Rf.res` :</span><span class="sxs-lookup"><span data-stu-id="45c3a-117">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="45c3a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45c3a-118">See also</span></span>

- [<span data-ttu-id="45c3a-119">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="45c3a-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="45c3a-120">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="45c3a-120">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
