---
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 9a59faf1b6f845858e36efcabdf0758e41ad75dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619741"
---
# <a name="bad-file-mode"></a><span data-ttu-id="173ba-102">Hatalı dosya modu</span><span class="sxs-lookup"><span data-stu-id="173ba-102">Bad file mode</span></span>
<span data-ttu-id="173ba-103">Dosya içerikleri düzenleme içinde kullanılan ifadeleri dosyası içinde açıldı moduna uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="173ba-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="173ba-104">Olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="173ba-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="173ba-105">A `FilePutObject` veya `FileGetObject` deyimi bir sıralı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="173ba-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="173ba-106">A `Print` deyim için bir erişim modu dışında açılmış bir dosyada belirtir `Output` veya `Append`.</span><span class="sxs-lookup"><span data-stu-id="173ba-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="173ba-107">Bir `Input` deyim için bir erişim modu dışında açılmış bir dosyasını belirtir `Input`</span><span class="sxs-lookup"><span data-stu-id="173ba-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="173ba-108">Salt okunur dosyaya yazma girişimi.</span><span class="sxs-lookup"><span data-stu-id="173ba-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="173ba-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="173ba-109">To correct this error</span></span>  
  
- <span data-ttu-id="173ba-110">Emin `FilePutObject` ve `FileGetObject` için açık olan dosyaları yalnızca başvuran `Random` veya `Binary` erişim.</span><span class="sxs-lookup"><span data-stu-id="173ba-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="173ba-111">Emin `Print` belirtir ya da için açılan bir dosyanın `Output` veya `Append` erişim modu.</span><span class="sxs-lookup"><span data-stu-id="173ba-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="173ba-112">Aksi halde veri dosyasına yerleştirmeniz farklı bir deyim kullanın veya uygun bir modda dosyayı tekrar açın.</span><span class="sxs-lookup"><span data-stu-id="173ba-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="173ba-113">Emin `Input` için açılan bir dosyanın belirtir `Input`.</span><span class="sxs-lookup"><span data-stu-id="173ba-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="173ba-114">Aksi durumda, farklı bir deyim veri dosyasında veya uygun bir modda dosyasını yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="173ba-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="173ba-115">Salt okunur dosya yazıyorsanız, dosya okuma/yazma durumunu değiştirebilir veya yazma çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="173ba-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="173ba-116">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.</span><span class="sxs-lookup"><span data-stu-id="173ba-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="173ba-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="173ba-118">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="173ba-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
