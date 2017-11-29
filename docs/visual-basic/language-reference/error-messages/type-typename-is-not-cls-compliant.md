---
title: "Tür &lt;typename&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d45da3b061dff0f82c1155daf5724033261bbdaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Tür &lt;typename&gt; CLS uyumlu değil
Değişken, özellik veya işlev dönüş CLS ile uyumlu olmayan bir veri türüyle bildirildi.  
  
 Bir uygulama ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.  
  
 Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:  
  
-   [SByte veri türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uınteger veri türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong veri türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort veri türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Hata Kimliği:** BC40041  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uygulamanızı CLS ile uyumlu olması gerekiyorsa, bu öğenin veri türü için en yakın CLS uyumlu türünü değiştirin. Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.  
  
-   Uygulamanızı CLS ile uyumlu olması gerekmez, değişikliği gerekmez. Ancak kendi uyumsuzluğunu, farkında olmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<PAVE üzerinden > CLS uyumlu kod yazma](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
