---
title: Kullanım &#39;FileGetObject&#39; yerine &#39;FileGet&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Kullanım &#39;FileGetObject&#39; yerine &#39;FileGet&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;
`FileGet` Yöntemi içerir türünde bir bağımsız değişken `Object`. `FileGetObject` yerine kullanılmalıdır `FileGet` belirsizlikleri önlemek için.  
  
 İşlevselliği sunduğu bildirimi `My.Computer.Filesystem` büyük kullanım kolaylığı ve performans ya da daha sunar `FileGet` veya `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Değiştir `FileGet` ile `FileGetObject`.  
  
2.  Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
