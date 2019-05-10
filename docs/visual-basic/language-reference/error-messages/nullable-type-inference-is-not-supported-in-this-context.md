---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 3ab8028062402e33b787a5a8649d93d975918393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665702"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
Değer türleri ve yapıları boş değer atanabilir bildirilebilir.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Ancak, boş değer atanabilir bildirimi tür çıkarımı birlikte kullanamazsınız. Aşağıdaki örnekler, bu hataya neden.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Hata Kimliği:** BC36629  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kullanım bir `As` olarak boş değer atanabilir bir değişken bildirmek için yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
