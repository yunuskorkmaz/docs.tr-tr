---
title: Yol-dosya erişim hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799187"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="f388f-102">Yol/Dosya erişim hatası</span><span class="sxs-lookup"><span data-stu-id="f388f-102">Path/File access error</span></span>
<span data-ttu-id="f388f-103">Bir dosya erişim veya disk erişimi işlemi sırasında işletim sistemi yolu ve dosya adı arasında bir bağlantı yapamadı.</span><span class="sxs-lookup"><span data-stu-id="f388f-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f388f-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f388f-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f388f-105">Dosya belirtimi doğru biçimlendirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f388f-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="f388f-106">Bir dosya adı bir tam (tam) veya göreli içerebilir yolu.</span><span class="sxs-lookup"><span data-stu-id="f388f-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="f388f-107">(Yol, başka bir sürücüdeyse) tam yolu sürücü adıyla başlar ve kök dosyasının açık yolu listeler.</span><span class="sxs-lookup"><span data-stu-id="f388f-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="f388f-108">Tam olmayan herhangi geçerli bir sürücü ve dizini göreli yoludur.</span><span class="sxs-lookup"><span data-stu-id="f388f-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="f388f-109">Varolan bir salt okunur dosyanın yerini alır bir dosyayı kaydetmeye denemedi emin olun.</span><span class="sxs-lookup"><span data-stu-id="f388f-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="f388f-110">Bu durumda, hedef dosyanın salt okunur özniteliği değiştirin veya dosyayı farklı bir dosya adıyla kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f388f-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="f388f-111">Siz deneme salt okunur bir dosya içinde sıralı açmak emin `Output` veya `Append` modu.</span><span class="sxs-lookup"><span data-stu-id="f388f-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="f388f-112">Bu durumda, dosyayı açma `Input` modu veya değişiklik dosyanın salt okunur özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f388f-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="f388f-113">Bir veritabanı ya da belge içinde bir Visual Basic projesi değiştirmek denemedi emin olun.</span><span class="sxs-lookup"><span data-stu-id="f388f-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f388f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f388f-114">See also</span></span>

- [<span data-ttu-id="f388f-115">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="f388f-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
