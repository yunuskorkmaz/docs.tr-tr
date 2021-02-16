---
description: 'Hakkında daha fazla bilgi edinin: bağımsız değişken BasePath bir klasörün yolu olması gerekir'
title: Bağımsız değişken BasePath bir klasörün yolu olmalıdır
ms.date: 07/20/2015
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
ms.openlocfilehash: 314ccd8510a286fc7f01518600a625cac48e10af
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472312"
---
# <a name="argument-basepath-must-be-a-path-to-a-folder"></a><span data-ttu-id="7e4c0-103">Bağımsız değişken BasePath bir klasörün yolu olmalıdır</span><span class="sxs-lookup"><span data-stu-id="7e4c0-103">Argument BasePath must be a path to a folder</span></span>

<span data-ttu-id="7e4c0-104">Bağımsız değişken bir `BasePath` klasöre ait bir yoldan oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e4c0-104">The argument `BasePath` must consist of a path to a folder.</span></span> <span data-ttu-id="7e4c0-105">Bir dizeyi yanlış ayrışmış ve geçerli bir yol olarak tanınmayan bir değer sağlamaya çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e4c0-105">You may be parsing a string incorrectly and supplying a value that is not recognized as a valid path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e4c0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7e4c0-106">To correct this error</span></span>  
  
- <span data-ttu-id="7e4c0-107">`BasePath`Bir klasöre yönelik geçerli bir yol olduğundan emin olmak için için tedarik ettiğiniz değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7e4c0-107">Check the value you are supplying for `BasePath` to make sure it is a valid path to a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4c0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e4c0-108">See also</span></span>

- <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>
- <xref:System.Resources.ResXResourceWriter.BasePath%2A>
- <xref:System.Resources.ResXResourceReader.BasePath%2A>
- [<span data-ttu-id="7e4c0-109">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="7e4c0-109">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
