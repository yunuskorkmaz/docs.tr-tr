---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 5828e28b84ec62c7ed674757090806d73c61caea
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966742"
---
# <a name="erase-statement-visual-basic"></a>Erase Deyimi (Visual Basic)
Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan bellek ayırması için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Bölümler  
 `arraylist`  
 Gerekli. Silinecek şekilde dizi değişkenleri listesi. Birden fazla değişken virgülle ayrılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Erase` Deyimi yalnızca yordamı düzeyinde görünebilir. Başka bir deyişle, bir yordam içinde ancak sınıf veya modül düzeyinde diziler serbest bırakabilirsiniz.  
  
 `Erase` Deyimi, atama için `Nothing` her dizi değişkeni için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Erase` dizilerinin temizleyin ve kendi bellek boş deyim (1000 ve 100 depolama öğeleri sırasıyla). `ReDim` İfadesi üç boyutlu diziye yeni bir dizi örneği atar.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
