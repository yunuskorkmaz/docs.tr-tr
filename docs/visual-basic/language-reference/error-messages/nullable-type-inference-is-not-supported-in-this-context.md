---
title: "Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords: BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
Değer türleri ve yapıları boş değer atanabilir bildirilebilir.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Ancak, boş değer atanabilir bildirimi tür çıkarımı ile birlikte kullanamazsınız. Aşağıdaki örnekler, bu hataya neden.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Hata Kimliği:** BC36629  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım bir `As` değişkeni boş değer atanabilir olarak bildirmek için yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Boş değer atanabilen değer türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
