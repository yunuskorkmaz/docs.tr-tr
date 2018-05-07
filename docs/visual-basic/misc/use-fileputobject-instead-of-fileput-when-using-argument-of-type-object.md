---
title: Kullanım &#39;FilePutObject&#39; yerine &#39;FilePut&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>Kullanım &#39;FilePutObject&#39; yerine &#39;FilePut&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;
`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`. `FilePutObject` yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değiştir `FilePut` ile `FilePutObject`.  
  
-   Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
