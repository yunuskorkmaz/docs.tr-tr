---
title: Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774231"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
`FilePut` Yöntemi türünde bir bağımsız değişken içeren `Object`. `FilePutObject` yerine kullanılması gereken `FilePut` belirsizlikleri önlemek için.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   `FilePut` yerine `FilePutObject` yazın.  
  
-   Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
