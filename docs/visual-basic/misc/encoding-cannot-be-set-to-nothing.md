---
title: Kodlama için hiçbir şey olacak şekilde ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691339"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodlama için hiçbir şey olacak şekilde ayarlanamaz
Bir dosyaya yazma veya okuma girişimi başarısız oldu çünkü parametre `encoding` ayarlanmış `Nothing` ancak geçerli bir değer gerektirir.  
  
 <xref:System.Text.Encoding> hangi dosyaya yazma sırasında kullanılacak kodlama belirlemek için kullanılır. Varsayılan değer UTF-8'dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İçin geçerli bir değer sağlamanız `encoding` parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Dosya Kodlamaları](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Dosyalardan Okuma](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
