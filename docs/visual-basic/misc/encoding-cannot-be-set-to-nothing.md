---
title: Kodlama Nothing olarak ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394485"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="91110-102">Kodlama Nothing olarak ayarlanamaz</span><span class="sxs-lookup"><span data-stu-id="91110-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="91110-103">Parametre `encoding` olarak ayarlandığı `Nothing` ancak geçerli bir değer gerektirdiğinden bir dosyayı okuma veya yazma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="91110-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="91110-104"><xref:System.Text.Encoding>bir dosyaya yazarken kullanılacak kodlamayı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91110-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="91110-105">Varsayılan değer UTF-8’dir.</span><span class="sxs-lookup"><span data-stu-id="91110-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91110-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="91110-106">To correct this error</span></span>  
  
- <span data-ttu-id="91110-107">Parametre için geçerli bir değer sağlayın `encoding` .</span><span class="sxs-lookup"><span data-stu-id="91110-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91110-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91110-108">See also</span></span>

- [<span data-ttu-id="91110-109">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="91110-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="91110-110">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="91110-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="91110-111">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="91110-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="91110-112">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="91110-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="91110-113">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="91110-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
