---
title: "Üye &#39;türü; &lt;membername&gt;&#39; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c09a71675275758220691ad09eeab48e53309f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a>Üye &#39;türü; &lt;membername&gt;&#39; CLS uyumlu değil
Bu üye olmadığı için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS). Bu, bileşen içinde bir hata olmadığından [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bu veri türünü destekler. Ancak, başka bir bileşen kesinlikle CLS uyumlu kod içinde yazılmış bu veri türünü desteklemiyor olabilir. Bu tür bir bileşeni başarıyla bileşeni ile etkileşim mümkün olmayabilir.  
  
 Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:  
  
-   [SByte veri türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uınteger veri türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong veri türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort veri türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40025  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Bileşeniniz yalnızca diğer arabirimleri varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bileşenleri veya yoksa diğer bileşenlerle birlikte arabirim, değişikliği gerekmez.  
  
-   İçin yazılmaz bileşeniyle arabirim varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], belirlemek, her iki aracılığıyla yansıma kullanabilir veya belgelerinden destekleyip bu veri türü. Aşması durumunda değişikliği gerekmez.  
  
-   Bu veri türü desteklemeyen bir bileşeni arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir. Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.  
  
-   Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Örneğin, `uint` diğer ortamlarda 16 bit görülür. Bir 16 bit bağımsız değişkeni tür bileşen geçirilirse, olarak bildirme `UShort` yerine `UInteger` , yönetilen içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansıma](../../../framework/reflection-and-codedom/reflection.md)  
 [\<PAVE üzerinden > CLS uyumlu kod yazma](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
