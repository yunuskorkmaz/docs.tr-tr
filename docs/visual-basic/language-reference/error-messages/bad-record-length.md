---
title: "Hatalı kayıt uzunluğu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
