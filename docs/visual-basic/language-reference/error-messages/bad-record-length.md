---
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-record-length"></a>Hatalı kayıt uzunluğu
Bu hatanın olası nedenleri arasında şunlardır:  
  
-   Belirtilen bir kayıt değişkeni uzunluğu bir `FileGet`, `FileGetObject`, `FilePut` veya `FilePutObject` deyimi farklı ilgili belirtilen uzunluk olarak `FileOpen` deyimi.  
  
-   Değişken bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içerir.  
  
-   Değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` türü.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kayıt değişkenin türü tanımlama kullanıcı tanımlı türünde sabit uzunluklu değişkenlerin boyutlarının toplamıdır aynı değeri de belirtildiği gibi emin olun `FileOpen` deyiminin `Len` yan tümcesi.  
  
2.  Varsa değişkenin bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içeriyorsa, değişken uzunlukta bir dize en az 2 karakter belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.  
  
3.  Varsa değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` değişken uzunlukta bir dize en az 4 bayt belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
