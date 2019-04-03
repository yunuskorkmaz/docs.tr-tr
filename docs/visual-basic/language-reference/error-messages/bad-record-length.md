---
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: f3df7819da0afddd7f238f282d496136d89cb052
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833483"
---
# <a name="bad-record-length"></a>Hatalı kayıt uzunluğu
Bu hatanın olası nedenleri arasında:  
  
-   Belirtilen bir kayıt değişken uzunluğu bir `FileGet`, `FileGetObject`, `FilePut` veya `FilePutObject` deyimi, ilgili belirtilen uzunluğu farklıdır `FileOpen` deyimi.  
  
-   Değişkeninde bir `FilePut` veya `FilePutObject` deyimi olduğundan veya değişken uzunluklu bir dize içerir.  
  
-   Değişkeninde bir `FilePut` veya `FilePutObject` içerir ya da bir `Variant` türü.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kayıt değişkenin türünü tanımlayan kullanıcı tanımlı tür, sabit uzunluklu değişkenlerin boyutlarının toplamı olduğundan, aynı, değeri bölümünde belirtildiği emin `FileOpen` deyimin `Len` yan tümcesi.  
  
2.  Varsa değişkeninde bir `FilePut` veya `FilePutObject` deyimi olduğunu veya bir değişken uzunluklu dize içeren, değişken uzunluklu dize en az 2 karakter belirtilen kayıt uzunluğu daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.  
  
3.  Varsa değişkeninde bir `FilePut` veya `FilePutObject` içerir ya da bir `Variant` değişken uzunluklu dize en az 4 bayt belirtilen kayıt uzunluğu daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
