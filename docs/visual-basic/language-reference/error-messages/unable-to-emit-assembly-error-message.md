---
title: "Derleme oluşturulamıyor: &lt;hata iletisi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="bd975-102">Derleme oluşturulamıyor: &lt;hata iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="bd975-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="bd975-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici derleme oluşturma çıkması aşamasında hata raporlama bağlayıcı ile derleme bağlayıcı (bir derleme bir bildirim oluşturmak için Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="bd975-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="bd975-104">**Hata Kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="bd975-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd975-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bd975-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="bd975-106">Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) daha ayrıntılı bir açıklama ve öneriler için.</span><span class="sxs-lookup"><span data-stu-id="bd975-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="bd975-107">Derleme kullanarak el ile oturum açmayı deneyin [Al.exe (derleme bağlayıcı)](https://msdn.microsoft.com/library/c405shex) veya [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="bd975-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="bd975-108">Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="bd975-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="bd975-109">Derleme el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="bd975-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="bd975-110">Kullanım [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23) ortak/özel anahtar çifti dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="bd975-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="bd975-111">Bu dosya .snk uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bd975-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="bd975-112">Projenizden hata oluşturmadan COM başvurusu silin.</span><span class="sxs-lookup"><span data-stu-id="bd975-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="bd975-113">Windows **Başlat** menüsündeki **programları**, işaret **Microsoft Visual Studio 2008**, işaret **Visual Studio Araçları**, ve ardından **Visual Studio 2008 Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="bd975-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="bd975-114">Derleme sarmalayıcı eklemek istediğiniz yeri dizinine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="bd975-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="bd975-115">Aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="bd975-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="bd975-116">Girdiğiniz kod örneği aşağıdaki gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="bd975-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="bd975-117">Bir yol veya dosya boşluk içeriyorsa, çift tırnak işaretleri (") kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd975-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="bd975-118">İçinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yeni oluşturduğunuz dosyayı bir .NET derlemesi başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd975-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd975-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd975-119">See Also</span></span>  
 [<span data-ttu-id="bd975-120">Al.exe (derleme bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="bd975-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="bd975-121">Al.exe aracı hataları ve Uyarıları</span><span class="sxs-lookup"><span data-stu-id="bd975-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="bd975-122">Sn.exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="bd975-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="bd975-123">Nasıl yapılır: bir genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd975-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="bd975-124">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="bd975-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
