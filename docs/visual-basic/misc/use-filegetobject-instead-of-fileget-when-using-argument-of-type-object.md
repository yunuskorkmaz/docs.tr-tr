---
title: "' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059411"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın

`FileGet`Yöntemi türünde bir bağımsız değişken içerir `Object` . `FileGetObject``FileGet`belirsizlikleri kaçınmak için yerine kullanılmalıdır.  
  
 Tarafından sunulan işlevselliğin, `My.Computer.Filesystem` ya da ' den daha fazla kullanım kolaylığı ve performans sunduğuna dikkat edin `FileGet` `FileGetObject` .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `FileGet` yerine `FileGetObject` yazın.  
  
2. `Object`Bağımsız değişkeni daha belirli bir türe atayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
