---
title: "'<typename>' türü tanımlı değil"
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825046"
---
# <a name="type-typename-is-not-defined"></a>Türü '\<typename >' tanımlı değil
İfade tanımlanmadı bir türe başvuru yaptı. Bir bildirim deyiminde gibi bir tür tanımlayabilirsiniz `Enum`, `Structure`, `Class`, veya `Interface`.  
  
 **Hata Kimliği:** BC30002  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tür tanımını ve onun başvurusu aynı yazım kullandığınızdan emin olun.  
  
-   Tür tanımını başvuru erişilebilir olduğundan emin olun. Örneğin, tür başka bir modül ve bildirilmiş `Private`, tür tanımını başvuran modülüne taşıyın veya bildirirken `Public`.  
  
-   Türün ad alanı içinde projenizi yeniden değil emin olun. İse, kullanın `Global` tür adı tam olarak nitelemek için anahtar sözcüğü. Örneğin, bir proje adındaki bir ad tanımlar `System`, <xref:System.Object?displayProperty=nameWithType> türü ile tam olmadığı sürece erişilemez `Global` anahtar sözcüğü: `Global.System.Object`.  
  
-   Türü tanımlandı, ancak nesne kitaplığı veya tür kitaplığı içinde tanımlanmış olduğu Visual Basic, tıklama kayıtlı değil **Başvuru Ekle** üzerinde **proje** menüsüne ve ardından uygun nesne kitaplık veya tür kitaplığı.  
  
-   Türü hedeflenen .NET Framework profilinin bir parçası olan bir derlemede olduğundan emin olun. Daha fazla bilgi için [.NET Framework hedefleme hataları giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
