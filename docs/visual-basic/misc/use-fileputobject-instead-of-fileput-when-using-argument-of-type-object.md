---
description: "Hakkında daha fazla bilgi edinin: ' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın"
title: "' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460104"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın

`FilePut`Yöntemi türünde bir bağımsız değişken içerir `Object` . `FilePutObject``FilePut`belirsizlikleri kaçınmak için yerine kullanılmalıdır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `FilePut` yerine `FilePutObject` yazın.  
  
- `Object`Bağımsız değişkeni daha belirli bir türe atayın.  
  
- Nesnesinde bulunan işlevleri kullanın `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My. Computer. FileSystem. WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
