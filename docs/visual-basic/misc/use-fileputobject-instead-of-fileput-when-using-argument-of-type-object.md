---
title: "&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;
`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`. `FilePutObject`yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değiştir `FilePut` ile `FilePutObject`.  
  
-   Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
