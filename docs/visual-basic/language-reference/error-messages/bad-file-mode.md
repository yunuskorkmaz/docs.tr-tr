---
title: Hatalı dosya modu
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409875"
---
# <a name="bad-file-mode"></a><span data-ttu-id="94bf5-102">Hatalı dosya modu</span><span class="sxs-lookup"><span data-stu-id="94bf5-102">Bad file mode</span></span>
<span data-ttu-id="94bf5-103">Dosya içeriğini düzenleme bölümünde kullanılan deyimler, dosyanın açıldığı moda uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94bf5-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="94bf5-104">Olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="94bf5-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="94bf5-105">`FilePutObject`Or `FileGetObject` deyimleri sıralı bir dosya belirtir.</span><span class="sxs-lookup"><span data-stu-id="94bf5-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="94bf5-106">Bir `Print` ifade, veya dışında bir erişim modu için açılan bir dosya `Output` belirtir `Append` .</span><span class="sxs-lookup"><span data-stu-id="94bf5-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="94bf5-107">Bir `Input` ifade, bir erişim modu için açılan bir dosyayı belirtir`Input`</span><span class="sxs-lookup"><span data-stu-id="94bf5-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="94bf5-108">Salt okunurdur bir dosyaya yazma girişimi.</span><span class="sxs-lookup"><span data-stu-id="94bf5-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="94bf5-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="94bf5-109">To correct this error</span></span>  
  
- <span data-ttu-id="94bf5-110">' In `FilePutObject` `FileGetObject` yalnızca veya erişim için açık olan dosyalara başvuruda bulunduğundan emin olun `Random` `Binary` .</span><span class="sxs-lookup"><span data-stu-id="94bf5-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="94bf5-111">`Print`Ya da erişim modu için açılmış bir dosya belirttiğinden emin olun `Output` `Append` .</span><span class="sxs-lookup"><span data-stu-id="94bf5-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="94bf5-112">Aksi takdirde, verileri dosyaya yerleştirmek için farklı bir ifade kullanın veya dosyayı uygun bir modda yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="94bf5-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="94bf5-113">`Input`İçin açılmış bir dosya belirttiğinden emin olun `Input` .</span><span class="sxs-lookup"><span data-stu-id="94bf5-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="94bf5-114">Aksi takdirde, verileri dosyaya yerleştirmek veya uygun modda dosyayı yeniden açmak için farklı bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="94bf5-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="94bf5-115">Salt okunurdur bir dosyaya yazıyorsanız dosyanın okuma/yazma durumunu değiştirin veya yazmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="94bf5-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="94bf5-116">Nesnesinde bulunan işlevleri kullanın `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="94bf5-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bf5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94bf5-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="94bf5-118">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="94bf5-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
