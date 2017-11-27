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
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;
`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`. `FilePutObject`yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değiştir `FilePut` ile `FilePutObject`.  
  
-   Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IN derleme değil: FilePutObject işlevi](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [My.Computer.FileSystem nesnesi](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [My.Computer.FileSystem.WriteAllBytes yöntemi](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
