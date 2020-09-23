---
title: Bağımsız değişken BasePath bir klasörün yolu olmalıdır
ms.date: 07/20/2015
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
ms.openlocfilehash: 3c8d17db7cc03490ff437c91814db967612942a0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079756"
---
# <a name="argument-basepath-must-be-a-path-to-a-folder"></a><span data-ttu-id="e42f0-102">Bağımsız değişken BasePath bir klasörün yolu olmalıdır</span><span class="sxs-lookup"><span data-stu-id="e42f0-102">Argument BasePath must be a path to a folder</span></span>

<span data-ttu-id="e42f0-103">Bağımsız değişken bir `BasePath` klasöre ait bir yoldan oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e42f0-103">The argument `BasePath` must consist of a path to a folder.</span></span> <span data-ttu-id="e42f0-104">Bir dizeyi yanlış ayrışmış ve geçerli bir yol olarak tanınmayan bir değer sağlamaya çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e42f0-104">You may be parsing a string incorrectly and supplying a value that is not recognized as a valid path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e42f0-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e42f0-105">To correct this error</span></span>  
  
- <span data-ttu-id="e42f0-106">`BasePath`Bir klasöre yönelik geçerli bir yol olduğundan emin olmak için için tedarik ettiğiniz değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e42f0-106">Check the value you are supplying for `BasePath` to make sure it is a valid path to a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42f0-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e42f0-107">See also</span></span>

- <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>
- <xref:System.Resources.ResXResourceWriter.BasePath%2A>
- <xref:System.Resources.ResXResourceReader.BasePath%2A>
- [<span data-ttu-id="e42f0-108">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="e42f0-108">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
