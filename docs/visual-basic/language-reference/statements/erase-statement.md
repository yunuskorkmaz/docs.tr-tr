---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522446"
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
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
