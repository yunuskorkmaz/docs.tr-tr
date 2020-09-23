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
# <a name="encoding-cannot-be-set-to-nothing"></a>Kodlama Nothing olarak ayarlanamaz

Parametre `encoding` olarak ayarlandığı `Nothing` ancak geçerli bir değer gerektirdiğinden bir dosyayı okuma veya yazma girişimi başarısız oldu.  
  
 <xref:System.Text.Encoding> bir dosyaya yazarken kullanılacak kodlamayı belirlemek için kullanılır. Varsayılan değer UTF-8’dir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Parametre için geçerli bir değer sağlayın `encoding` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya Kodlamaları](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [Dosyalardan Okuma](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My. Computer. FileSystem. ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My. Computer. FileSystem. WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
