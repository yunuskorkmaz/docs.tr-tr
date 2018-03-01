---
title: "Örtük dönüştürme &#39; &lt;typename1&gt;&#39; çok &#39;&lt; TypeName2&gt;&#39; değeri &#39; kopyalama ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; eşleşen bağımsız değişkene geri."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Örtük dönüştürme &#39; &lt;typename1&gt;&#39; çok &#39;&lt; TypeName2&gt;&#39; değeri &#39; kopyalama ByRef &#39; Parametre &#39; &lt;parametername&gt;&#39; eşleşen bağımsız değişkene geri.
Bir yordam ile adlı bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) bağımsız değişkeni, karşılık gelen bir parametre daha farklı bir türde.  
  
 Bir bağımsız değişken geçirirseniz `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bazen bir başvuru geçirme yerine yordamdaki yerel bir değişken bağımsız değişken değeri kopyalar. Yordamın geri döndüğünde, böyle bir durumda, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sonra yerel değişken değerini geri çağırma kodu değişkeninde kopyalamanız gerekir.  
  
 Varsa bir `ByRef` bağımsız değişken değeri yordama kopyalanır ve bağımsız değişkeni ve parametre aynı tür dönüştürme gerekli değildir. Ancak türleri farklıysa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] her iki yönde de dönüştürmeniz gerekir. Kullanamadığından `CType` veya diğer dönüşüm anahtar sözcükleri bir yordam bağımsız değişkenini veya parametresi, bu tür dönüştürme olan her zaman örtük.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC41999  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, aynı türden çağıran bir bağımsız değişken yordamı parametre olarak kullanın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] herhangi bir dönüştürmeye yapmak gerekmez.  
  
-   Yordam bağımsız değişkeni çağrısı gerekiyorsa parametre türünden farklı yazın ancak gerekmez çağırma bağımsız değişkeni bir değer döndürmesi, olması için parametre tanımlayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) yerine `ByRef`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
