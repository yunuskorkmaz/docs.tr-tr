---
title: "Ad &lt;namespacename&gt; kök ad alanındaki &lt;fullnamespacename&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a89f8cfe4038a81002777886de1155bea72ba22
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>Ad &lt;namespacename&gt; kök ad alanındaki &lt;fullnamespacename&gt; CLS uyumlu değil
Bir derlemeyi olarak işaretlenmiş `<CLSCompliant(True)>`, ancak kök ad alanı adı öğesi bir alt çizgi ile başlayan (`_`).  
  
 Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi, içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), alt çizgi ile değil başlamalı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40039  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektiriyorsa, kök ad alanı adı öğelerinden hiçbiri alt çizgiyle başlıyorsa şekilde değiştirin.  
  
-   Ad alanı adı değişmeden gerektiriyorsa, ardından kaldırın <xref:System.CLSCompliantAttribute> derlemesinden veya olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Namespace Deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 
