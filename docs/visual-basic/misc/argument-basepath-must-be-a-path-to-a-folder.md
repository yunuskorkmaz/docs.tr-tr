---
title: Bağımsız değişken BasePath bir klasörün yolu olmalıdır
ms.date: 07/20/2015
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
ms.openlocfilehash: 5b55c1510e7a9607e71c2afb4771eb23ace2faad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368100"
---
# <a name="argument-basepath-must-be-a-path-to-a-folder"></a><span data-ttu-id="33d87-102">Bağımsız değişken BasePath bir klasörün yolu olmalıdır</span><span class="sxs-lookup"><span data-stu-id="33d87-102">Argument BasePath must be a path to a folder</span></span>
<span data-ttu-id="33d87-103">Bağımsız değişken bir `BasePath` klasöre ait bir yoldan oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33d87-103">The argument `BasePath` must consist of a path to a folder.</span></span> <span data-ttu-id="33d87-104">Bir dizeyi yanlış ayrışmış ve geçerli bir yol olarak tanınmayan bir değer sağlamaya çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33d87-104">You may be parsing a string incorrectly and supplying a value that is not recognized as a valid path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33d87-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="33d87-105">To correct this error</span></span>  
  
- <span data-ttu-id="33d87-106">`BasePath`Bir klasöre yönelik geçerli bir yol olduğundan emin olmak için için tedarik ettiğiniz değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33d87-106">Check the value you are supplying for `BasePath` to make sure it is a valid path to a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d87-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33d87-107">See also</span></span>

- <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>
- <xref:System.Resources.ResXResourceWriter.BasePath%2A>
- <xref:System.Resources.ResXResourceReader.BasePath%2A>
- [<span data-ttu-id="33d87-108">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="33d87-108">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
