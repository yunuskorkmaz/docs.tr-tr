---
title: "&#39;kullan; FileGetObject &#39; yerine &#39; FileGet &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>&#39;kullan; FileGetObject &#39; yerine &#39; FileGet &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;
`FileGet` Yöntemi içerir türünde bir bağımsız değişken `Object`. `FileGetObject`yerine kullanılmalıdır `FileGet` belirsizlikleri önlemek için.  
  
 İşlevselliği sunduğu bildirimi `My.Computer.Filesystem` büyük kullanım kolaylığı ve performans ya da daha sunar `FileGet` veya `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Değiştir `FileGet` ile `FileGetObject`.  
  
2.  Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
