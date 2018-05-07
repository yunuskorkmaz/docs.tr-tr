---
title: Tür &#39; &lt;typename&gt; &#39; tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Tür &#39; &lt;typename&gt; &#39; tanımlı değil
Deyim tanımlanmamış bir tür referansı yaptı. Bir bildirim deyiminde gibi bir tür tanımlayabilirsiniz `Enum`, `Structure`, `Class`, veya `Interface`.  
  
 **Hata Kimliği:** BC30002  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tür tanımı ve kendi başvuru her ikisi de aynı yazım kullandığınızdan emin olun.  
  
-   Tür tanımı referansı erişilebilir olduğundan emin olun. Örneğin, türü başka bir modülde ise ve bildirilmiş `Private`, tür tanımı için başvuru modülü taşımak veya bildirirken `Public`.  
  
-   Türünün ad alanını, projeyi yeniden değil emin olun. Gerekiyorsa, kullanın `Global` tür adı tam olarak nitelemek için anahtar sözcüğü. Örneğin, bir proje adlı bir ad alanını tanımlayan `System`, <xref:System.Object?displayProperty=nameWithType> türü ile tam olmadığı sürece erişilemiyor `Global` anahtar sözcüğü: `Global.System.Object`.  
  
-   Tür tanımlandı, ancak nesne kitaplığı ya da tanımlanmış tür kitaplığı Visual Basic, tıklatın kaydedilmemiş **Başvuru Ekle** üzerinde **proje** menüsüne ve ardından uygun nesnesi kitaplığı veya tür kitaplığı.  
  
-   Türü hedef .NET Framework profilinin parçası olan bir derlemede olduğundan emin olun. Daha fazla bilgi için bkz: [.NET Framework hedefleme hataları giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
