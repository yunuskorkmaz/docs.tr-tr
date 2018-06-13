---
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587390"
---
# <a name="bad-file-mode"></a><span data-ttu-id="0a806-102">Hatalı dosya modu</span><span class="sxs-lookup"><span data-stu-id="0a806-102">Bad file mode</span></span>
<span data-ttu-id="0a806-103">Dosya içerikleri düzenleme kullanılan ifadeleri dosyanın açılmış olduğu moduna uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a806-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="0a806-104">Olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0a806-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="0a806-105">A `FilePutObject` veya `FileGetObject` deyimi sıralı bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a806-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="0a806-106">A `Print` deyimi dışında bir erişim modu için açık bir dosyayı belirtir `Output` veya `Append`.</span><span class="sxs-lookup"><span data-stu-id="0a806-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="0a806-107">Bir `Input` deyimi dışında bir erişim modu için açık bir dosyayı belirtir `Input`</span><span class="sxs-lookup"><span data-stu-id="0a806-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="0a806-108">Bir salt okunur dosyaya yazma girişimi.</span><span class="sxs-lookup"><span data-stu-id="0a806-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a806-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0a806-109">To correct this error</span></span>  
  
-   <span data-ttu-id="0a806-110">Emin olun `FilePutObject` ve `FileGetObject` için açık dosyalara yalnızca başvuran `Random` veya `Binary` erişim.</span><span class="sxs-lookup"><span data-stu-id="0a806-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="0a806-111">Emin olun `Print` için açık bir dosyayı belirtir `Output` veya `Append` erişim modu.</span><span class="sxs-lookup"><span data-stu-id="0a806-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="0a806-112">Değilse, veri dosyasında yerleştirmek için farklı bir deyimi kullanın veya uygun bir mod dosyasında yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="0a806-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="0a806-113">Emin olun `Input` için açık bir dosyayı belirtir `Input`.</span><span class="sxs-lookup"><span data-stu-id="0a806-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="0a806-114">Aksi durumda, veri dosyasına yerleştirin veya uygun bir mod dosyayı yeniden için farklı bir deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a806-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="0a806-115">Bir salt okunur dosyaya yazıyorsanız, dosya okuma/yazma durumunu değiştirme veya yazma çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="0a806-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="0a806-116">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0a806-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a806-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a806-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="0a806-118">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="0a806-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
