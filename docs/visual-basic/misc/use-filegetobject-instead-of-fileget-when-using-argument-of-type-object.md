---
title: Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306930"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
`FileGet` Yöntemi türünde bir bağımsız değişken içeren `Object`. `FileGetObject` yerine kullanılması gereken `FileGet` belirsizlikleri önlemek için.  
  
 Tarafından sağlanan işlev bildirimi `My.Computer.Filesystem` kullanım ve performans büyük bir kolaylıkla ya da daha sunar `FileGet` veya `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `FileGet` yerine `FileGetObject` yazın.  
  
2. Cast `Object` daha belirli bir tür bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
