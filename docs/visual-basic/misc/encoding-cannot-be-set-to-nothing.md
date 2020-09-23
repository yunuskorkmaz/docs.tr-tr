---
title: Kodlama Nothing olarak ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 0356098ca3fb41804ea396b0ff792cf2990b3340
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077546"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="653fa-102">Kodlama Nothing olarak ayarlanamaz</span><span class="sxs-lookup"><span data-stu-id="653fa-102">Encoding cannot be set to Nothing</span></span>

<span data-ttu-id="653fa-103">Parametre `encoding` olarak ayarlandığı `Nothing` ancak geçerli bir değer gerektirdiğinden bir dosyayı okuma veya yazma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="653fa-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="653fa-104"><xref:System.Text.Encoding> bir dosyaya yazarken kullanılacak kodlamayı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="653fa-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="653fa-105">Varsayılan değer UTF-8’dir.</span><span class="sxs-lookup"><span data-stu-id="653fa-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="653fa-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="653fa-106">To correct this error</span></span>  
  
- <span data-ttu-id="653fa-107">Parametre için geçerli bir değer sağlayın `encoding` .</span><span class="sxs-lookup"><span data-stu-id="653fa-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653fa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="653fa-108">See also</span></span>

- [<span data-ttu-id="653fa-109">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="653fa-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="653fa-110">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="653fa-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="653fa-111">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="653fa-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="653fa-112">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="653fa-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="653fa-113">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="653fa-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
