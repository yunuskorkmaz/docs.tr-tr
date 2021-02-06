---
description: "Hakkında daha fazla bilgi edinin: BC30002: Type ' <typename> ' tanımlanmadı"
title: "'<typename>' türü tanımlı değil"
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 48ee0c38492769aea8c1be2e9d54eaa537e35766
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641134"
---
# <a name="bc30002-type-typename-is-not-defined"></a>BC30002: ' \<typename> ' türü tanımlı değil

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
