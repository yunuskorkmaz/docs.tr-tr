---
title: "Türü &#39; &lt;typename&gt;&#39; tanımlı değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Türü &#39; &lt;typename&gt;&#39; tanımlı değil
Deyim tanımlanmamış bir tür referansı yaptı. Bir bildirim deyiminde gibi bir tür tanımlayabilirsiniz `Enum`, `Structure`, `Class`, veya `Interface`.  
  
 **Hata Kimliği:** BC30002  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tür tanımı ve kendi başvuru her ikisi de aynı yazım kullandığınızdan emin olun.  
  
-   Tür tanımı referansı erişilebilir olduğundan emin olun. Örneğin, türü başka bir modülde ise ve bildirilmiş `Private`, tür tanımı için başvuru modülü taşımak veya bildirirken `Public`.  
  
-   Türünün ad alanını, projeyi yeniden değil emin olun. Gerekiyorsa, kullanın `Global` tür adı tam olarak nitelemek için anahtar sözcüğü. Örneğin, bir proje adlı bir ad alanını tanımlayan `System`, <xref:System.Object?displayProperty=nameWithType> türü ile tam olmadığı sürece erişilemiyor `Global` anahtar sözcüğü: `Global.System.Object`.  
  
-   Tür tanımlandı, ancak nesne kitaplığı ya da tanımlanmış tür kitaplığı içinde kayıtlı değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], tıklatın **Başvuru Ekle** üzerinde **proje** menüsüne ve ardından uygun nesnesi kitaplığı veya tür kitaplığı.  
  
-   Türü hedef .NET Framework profilinin parçası olan bir derlemede olduğundan emin olun. Daha fazla bilgi için bkz: [.NET Framework hedefleme hataları giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
