---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249506"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
Değer türleri ve yapıları geçersiz ilan edilebilir.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Ancak, geçersiz bildirimi tür çıkarımlarıyla birlikte kullanamazsınız. Aşağıdaki örnekler bu hataya neden olur.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Hata Kimliği:** BC36629  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Değişkeni `As` nullable değer türü olarak bildirmek için bir yan tümce kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Yerel Tür Arabirimi](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
