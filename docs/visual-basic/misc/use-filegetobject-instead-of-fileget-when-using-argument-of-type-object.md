---
title: Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723400"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
`FileGet` Yöntemi türünde bir bağımsız değişken içeren `Object`. `FileGetObject` yerine kullanılması gereken `FileGet` belirsizlikleri önlemek için.  
  
 Tarafından sağlanan işlev bildirimi `My.Computer.Filesystem` kullanım ve performans büyük bir kolaylıkla ya da daha sunar `FileGet` veya `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  `FileGet` yerine `FileGetObject` yazın.  
  
2.  Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
