---
title: Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725564"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
`FilePut` Yöntemi türünde bir bağımsız değişken içeren `Object`. `FilePutObject` yerine kullanılması gereken `FilePut` belirsizlikleri önlemek için.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   `FilePut` yerine `FilePutObject` yazın.  
  
-   Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
-   Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
