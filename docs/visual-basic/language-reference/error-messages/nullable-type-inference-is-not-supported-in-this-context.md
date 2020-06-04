---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409393"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
Değer türleri ve yapıları null yapılabilir olarak bildirilemez.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Ancak, null yapılabilir bildirimini tür çıkarımı ile birlikte kullanamazsınız. Aşağıdaki örnekler bu hataya neden olur.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Hata kimliği:** BC36629  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `As`Değişkeni null yapılabilir bir değer türü olarak bildirmek için bir yan tümce kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir değer türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
