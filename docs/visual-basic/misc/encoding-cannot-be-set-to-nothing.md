---
description: 'Daha fazla bilgi edinin: kodlama Nothing olarak ayarlanamaz'
title: Kodlama Nothing olarak ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 4fa9cbd9488501b5295da8d8ace41ef06a706c12
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463001"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="a2b3a-103">Kodlama Nothing olarak ayarlanamaz</span><span class="sxs-lookup"><span data-stu-id="a2b3a-103">Encoding cannot be set to Nothing</span></span>

<span data-ttu-id="a2b3a-104">Parametre `encoding` olarak ayarlandığı `Nothing` ancak geçerli bir değer gerektirdiğinden bir dosyayı okuma veya yazma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a2b3a-104">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="a2b3a-105"><xref:System.Text.Encoding> bir dosyaya yazarken kullanılacak kodlamayı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2b3a-105"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="a2b3a-106">Varsayılan değer UTF-8’dir.</span><span class="sxs-lookup"><span data-stu-id="a2b3a-106">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2b3a-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a2b3a-107">To correct this error</span></span>  
  
- <span data-ttu-id="a2b3a-108">Parametre için geçerli bir değer sağlayın `encoding` .</span><span class="sxs-lookup"><span data-stu-id="a2b3a-108">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b3a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b3a-109">See also</span></span>

- [<span data-ttu-id="a2b3a-110">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="a2b3a-110">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="a2b3a-111">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="a2b3a-111">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="a2b3a-112">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="a2b3a-112">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="a2b3a-113">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="a2b3a-113">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="a2b3a-114">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="a2b3a-114">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
