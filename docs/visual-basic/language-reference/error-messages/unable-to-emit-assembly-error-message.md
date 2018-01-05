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
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="cbf57-102">Derleme oluşturulamıyor: &lt;hata iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="cbf57-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="cbf57-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici derleme oluşturma çıkması aşamasında hata raporlama bağlayıcı ile derleme bağlayıcı (bir derleme bir bildirim oluşturmak için Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="cbf57-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="cbf57-104">**Hata Kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="cbf57-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbf57-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cbf57-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="cbf57-106">Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="cbf57-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="cbf57-107">Daha fazla açıklama ve öneriler için.</span><span class="sxs-lookup"><span data-stu-id="cbf57-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="cbf57-108">Derleme kullanarak el ile oturum açmayı deneyin [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cbf57-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="cbf57-109">Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="cbf57-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="cbf57-110">Derleme el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="cbf57-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="cbf57-111">[Sn.exe (tanımlayıcı ad aracı)] kullanın[Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) ortak/özel anahtar çifti dosya oluşturulamadı.</span><span class="sxs-lookup"><span data-stu-id="cbf57-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="cbf57-112">Bu dosya .snk uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cbf57-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="cbf57-113">Projenizden hata oluşturmadan COM başvurusu silin.</span><span class="sxs-lookup"><span data-stu-id="cbf57-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="cbf57-114">Windows **Başlat** menüsündeki **programları**, işaret **Microsoft Visual Studio 2008**, işaret **Visual Studio Araçları**, ve ardından **Visual Studio 2008 Komut İstemi**.</span><span class="sxs-lookup"><span data-stu-id="cbf57-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="cbf57-115">Derleme sarmalayıcı eklemek istediğiniz yeri dizinine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="cbf57-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="cbf57-116">Aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="cbf57-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="cbf57-117">Girdiğiniz kod örneği aşağıdaki gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cbf57-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="cbf57-118">Bir yol veya dosya boşluk içeriyorsa, çift tırnak işaretleri (") kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbf57-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="cbf57-119">İçinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yeni oluşturduğunuz dosyayı bir .NET derlemesi başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cbf57-119">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf57-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbf57-120">See Also</span></span>  
 
 <span data-ttu-id="cbf57-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="cbf57-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="cbf57-122">[Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="cbf57-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="cbf57-123">Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbf57-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="cbf57-124">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="cbf57-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
