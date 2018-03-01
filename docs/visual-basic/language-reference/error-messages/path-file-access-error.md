---
title: "Yol dosya erişim hatası"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a><span data-ttu-id="ab55b-102">Yol/Dosya erişim hatası</span><span class="sxs-lookup"><span data-stu-id="ab55b-102">Path/File access error</span></span>
<span data-ttu-id="ab55b-103">Bir dosya erişim veya disk erişimi işlemi sırasında işletim sistemi yolunu ve dosya adı arasında bir bağlantı yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ab55b-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab55b-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ab55b-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ab55b-105">Dosya belirtiminin doğru biçimlendirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab55b-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="ab55b-106">Bir dosya adı bir tam (mutlak) veya göreli içerebilir yolu.</span><span class="sxs-lookup"><span data-stu-id="ab55b-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="ab55b-107">(Yolu, başka bir sürücüdeyse) tam nitelenmiş bir yol sürücü adıyla başlar ve kök dosyasının açık yolunu listeler.</span><span class="sxs-lookup"><span data-stu-id="ab55b-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="ab55b-108">Tam olmayan tüm geçerli sürücü ve dizine göreli yoludur.</span><span class="sxs-lookup"><span data-stu-id="ab55b-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="ab55b-109">Varolan salt okunur dosya değiştirirler bir dosyayı kaydetmek denemedi emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab55b-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="ab55b-110">Bu durumda, hedef dosya salt okunur özniteliğini değiştirmek veya dosyayı farklı bir dosya adıyla kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ab55b-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="ab55b-111">Değil dener salt okunur bir dosya olarak sıralı açmak emin olun `Output` veya `Append` modu.</span><span class="sxs-lookup"><span data-stu-id="ab55b-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="ab55b-112">Bu durumda, dosyayı açma `Input` modu veya değişiklik dosyasının salt okunur özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ab55b-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="ab55b-113">Değil dener değiştirmek emin olun bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projesi bir veritabanı veya belge içinde.</span><span class="sxs-lookup"><span data-stu-id="ab55b-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab55b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab55b-114">See Also</span></span>  
 [<span data-ttu-id="ab55b-115">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="ab55b-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
