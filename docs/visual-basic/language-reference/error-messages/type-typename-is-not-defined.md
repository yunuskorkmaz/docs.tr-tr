---
title: "'<typename>' türü tanımlı değil"
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386938"
---
# <a name="type-typename-is-not-defined"></a>'\<typename>' türü tanımlı değil
İfade tanımlanmamış bir türe başvuru yaptı. ,,, Veya gibi bir bildirim bildiriminde bir türü tanımlayabilirsiniz `Enum` `Structure` `Class` `Interface` .  
  
 **Hata kimliği:** BC30002  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tür tanımının ve başvurusunun her ikisi de aynı yazımı kullandığından emin olun.  
  
- Tür tanımına başvuru tarafından erişilebildiğinden emin olun. Örneğin, tür başka bir modülse ve bildirilirse `Private` , tür tanımını başvuran modüle taşıyın veya bildirin `Public` .  
  
- Türün ad alanının projeniz içinde yeniden tanımlanmadığından emin olun. Varsa, `Global` tür adını tam olarak nitelemek için anahtar sözcüğünü kullanın. Örneğin, bir proje adlı bir ad alanını tanımlarsa `System` , <xref:System.Object?displayProperty=nameWithType> tür anahtar sözcüğüyle tam nitelendirilmediği takdirde türe erişilemez `Global` `Global.System.Object` .  
  
- Tür tanımlanmışsa, ancak tanımlanmış olduğu nesne kitaplığı veya tür kitaplığı Visual Basic kayıtlı değilse, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayın ve ardından uygun nesne kitaplığı veya tür kitaplığı ' nı seçin.  
  
- Türün hedeflenen .NET Framework profilinin parçası olan bir derlemede bulunduğundan emin olun. Daha fazla bilgi için bkz. [.NET Framework Hedefleme hatalarını giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Ad Alanları](../../programming-guide/program-structure/namespaces.md)
- [Enum Deyimi](../statements/enum-statement.md)
- [Structure Yapısı](../statements/structure-statement.md)
- [Class Deyimi](../statements/class-statement.md)
- [Interface Deyimi](../statements/interface-statement.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
