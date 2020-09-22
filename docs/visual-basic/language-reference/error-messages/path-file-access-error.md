---
title: Yol/Dosya erişim hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 70de8f9cb33ab3d889f4916ae3d5de48cd218092
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871191"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="1c812-102">Yol/Dosya erişim hatası</span><span class="sxs-lookup"><span data-stu-id="1c812-102">Path/File access error</span></span>

<span data-ttu-id="1c812-103">Dosya erişimi veya disk erişimi işlemi sırasında, işletim sistemi yol ve dosya adı arasında bir bağlantı kuramadı.</span><span class="sxs-lookup"><span data-stu-id="1c812-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c812-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1c812-104">To correct this error</span></span>  
  
1. <span data-ttu-id="1c812-105">Dosya belirtiminin doğru biçimlendirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c812-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="1c812-106">Bir dosya adı, tam olarak nitelenmiş (mutlak) veya göreli yol içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1c812-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="1c812-107">Tam nitelikli bir yol sürücü adı ile başlar (yol başka bir sürücüdeyse) ve kökten açık yolu dosya olarak listeler.</span><span class="sxs-lookup"><span data-stu-id="1c812-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="1c812-108">Tam nitelikli olmayan herhangi bir yol, geçerli sürücü ve dizine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1c812-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="1c812-109">Varolan bir salt okunurdur dosyanın yerini alacak bir dosyayı kaydetmeyi denediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c812-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="1c812-110">Bu durumda, hedef dosyanın salt okunurdur özniteliğini değiştirin veya dosyayı farklı bir dosya adı ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1c812-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="1c812-111">Salt biçimli bir dosyayı sıralı veya modda açmaya çalışmayın emin olun `Output` `Append` .</span><span class="sxs-lookup"><span data-stu-id="1c812-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="1c812-112">Bu durumda, dosyayı `Input` modda açın veya dosyanın salt okunurdur özniteliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1c812-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="1c812-113">Bir veritabanı veya belge içinde Visual Basic projesi değiştirmeyi denediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c812-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c812-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c812-114">See also</span></span>

- [<span data-ttu-id="1c812-115">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="1c812-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
