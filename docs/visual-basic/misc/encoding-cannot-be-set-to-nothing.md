---
title: Kodlama için hiçbir şey olacak şekilde ayarlanamaz
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 30b0b4a29fbdf931aa62263b75d1fa946e87b145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970332"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodlama için hiçbir şey olacak şekilde ayarlanamaz
Bir dosyaya yazma veya okuma girişimi başarısız oldu çünkü parametre `encoding` ayarlanmış `Nothing` ancak geçerli bir değer gerektirir.  
  
 <xref:System.Text.Encoding> hangi dosyaya yazma sırasında kullanılacak kodlama belirlemek için kullanılır. Varsayılan değer UTF-8'dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İçin geçerli bir değer sağlamanız `encoding` parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya Kodlamaları](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Dosyalardan Okuma](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
