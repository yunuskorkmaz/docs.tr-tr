---
title: Kodlama için hiçbir şey olacak şekilde ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 30b0b4a29fbdf931aa62263b75d1fa946e87b145
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58028446"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="e93b0-102">Kodlama için hiçbir şey olacak şekilde ayarlanamaz</span><span class="sxs-lookup"><span data-stu-id="e93b0-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="e93b0-103">Bir dosyaya yazma veya okuma girişimi başarısız oldu çünkü parametre `encoding` ayarlanmış `Nothing` ancak geçerli bir değer gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e93b0-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="e93b0-104"><xref:System.Text.Encoding> hangi dosyaya yazma sırasında kullanılacak kodlama belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e93b0-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="e93b0-105">Varsayılan değer UTF-8'dir.</span><span class="sxs-lookup"><span data-stu-id="e93b0-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e93b0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e93b0-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e93b0-107">İçin geçerli bir değer sağlamanız `encoding` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e93b0-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93b0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e93b0-108">See also</span></span>

- [<span data-ttu-id="e93b0-109">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="e93b0-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="e93b0-110">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="e93b0-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="e93b0-111">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="e93b0-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="e93b0-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="e93b0-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="e93b0-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="e93b0-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
